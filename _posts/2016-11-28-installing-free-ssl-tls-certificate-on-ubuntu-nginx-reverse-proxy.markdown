---
layout: post
title: Installing free SSL/TLS certificate on Ubuntu Nginx reverse proxy
image: "/assets/img/2016/11/exploded.gif"
date: '2016-11-28 00:55:53'
tags:
- howto
- ghost-tag
- code
- tls
- letsencrypt
- security
- certbot
- ubuntu
- ssl
- nginx
- guides
---

We write for ourselves but it is also nice when others can discover the content we put out there. Adding an [SSL/TLS certificate](https://en.wikipedia.org/wiki/Transport_Layer_Security) increases your ranking for search results, so I did that today. Thankfully there are free SSL/TLS certificate services like [letsencrypt](https://letsencrypt.org/) which make things super easy. Some poking around required.

---

### Specs

- [Digital Ocean](https://m.do.co/c/0162abfbe338) droplet (my referral link)
- Ubuntu 16.04.1 LTS xenial (`lsb_release -a`)
- Nginx 1.10.0 (`nginx -v`) reverse proxy running Ghost blog

# Tutorial

## 1. Install letsencrypt

    sudo apt-get install letsencrypt

## 2. Enable authorization checking

We will be using the `certonly --webroot` option per the recommended [certbot instructions](https://certbot.eff.org/#ubuntuxenial-nginx). This installation method requires specifying where certificate credentials will be placed as well as your domains.

First we need to make sure your top-level domain directory exists; skip this step if you already have one:

    sudo mkdir /var/www/yourdomain

Then we need to allow nginx to recognize your directory. Add to your nginx configuration, using something like `sudo vim /etc/nginx/sites-available/yourdomain`, the following code:

    location /.well-known {
        alias /var/www/yourdomain/.well-known;
    }

Then restart your nginx server:

    sudo service nginx restart

If you need help with your nginx configuration, see my previous tutorial on [setting up a Ghost blog](https://tonyy.in/how-i-set-up-this-blog/).

## 3. Request certificate

Now we can request a certificate from letsencrypt and certbot.

    sudo letsencrypt certonly --webroot -w /var/www/yourdomain -d yourdomain

If everything worked, you will get a message like

> IMPORTANT NOTES:
>
> \- Congratulations! Your certificate and chain have been saved at
   /etc/letsencrypt/live/tonyy.in/fullchain.pem. Your cert will expire
   on 2017-02-25. To obtain a new version of the certificate in the
   future, simply run Let's Encrypt again.

Note: People have raised concerns about granting root privilege to letsencrypt. You can read more at the [official FAQs](https://certbot.eff.org/faq/#does-certbot-require-root-administrator-privileges).

## 4. Add HTTPS routing

We now enable HTTPS routing on our nginx server. Open your nginx configuration again with `sudo vim /etc/nginx/sites-available/yourdomain` and replace your `listen 80` block. The full configuration will look something like this:

    server {
        listen 443 ssl http2;
        server_name yourdomain;

        ssl_certificate /etc/letsencrypt/live/yourdomain/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/yourdomain/privkey.pem;
        ssl_stapling on;
        ssl_stapling_verify on;

        location /.well-known {
            alias /var/www/yourdomain/.well-known;
        }

        location / {
            proxy_set_header    Host $host;
            proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header    X-Forwarded-Proto $scheme;
            proxy_set_header    X-Real-IP $remote_addr;
            proxy_pass          http://127.0.0.1:2368;
        }
    }

Restart your nginx server again with `sudo service nginx restart` and hit your new secure HTTPS domain to see if it works. You should now have a verified TLS certificate on `https://yourdomain`!

Per [StackExchange tutorial](http://serverfault.com/questions/768509/lets-encrypt-with-an-nginx-reverse-proxy) you can redirect your unencrypted traffic to your encrypted domain by adding another server block:

    server {
        listen 80;
        server_name yourdomain;
        return 301 https://$server_name$request_uri;
    }

Restart your nginx server and try hitting the unencrypted endpoint again to see the redirect.

And that's it! Remember to renew your certificate every 90 days, or set auto-renew. I left auto-renew off because 90 days seems like a good point to re-check security measures.

*If you liked this post, please recommend or just leave a comment below!*