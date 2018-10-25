---
layout: post
title: How I set this blog up
date: '2014-06-17 17:55:53'
tags:
- howto
- ghost-tag
- code
- forever
- digitalocean
- nginx
---

I realized the other day how important it is to document all of our processes, especially if you spent time piecing together different tools and resources. Here I outline exactly how I set this Ghost blog up, with links to corresponding instructions.

Note: This tutorial is for a manual installation of Ghost; more automated options are available as well.

Good luck!

---

### 1. Register a domain

Get something clever, like `yourname.com`. There are a lot of domain registrars out there, but my research took me to [Namecheap](https://www.namecheap.com/) for ease of use, price, and functionality.

### 2. Set up web hosting

I used [DigitalOcean](https://www.digitalocean.com/?refcode=0162abfbe338) (disclaimer: my referral link) for their ease of use and price. I also met the co-founders this year, really great guys and passionate about what they're doing.
New droplet settings:

* **Hostname**: ghost
* **Size**: 512MB / 1 CPU / 20GB SSD
* **Region**: New York 2
* **Image**: Ubuntu 14.04 x64
* **Settings**: Enable VirtIO

You will need a terminal and SSH access later. DigitalOcean has a community tutorial on [setting up SSH keys](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2) if you need a primer.

### 3. Point your domain

We need to point the domain you registered in step 1 to your web host in step 2. In my case, I changed my DNS info on Namecheap to:

1. NS1.DIGITALOCEAN.COM
2. NS2.DIGITALOCEAN.COM
3. NS3.DIGITALOCEAN.COM

And on DigitalOcean, under "DNS", I added my domain name "tonyy.in" with my "ghost" droplet.

### 4. Install Ghost

Follow "Step 1: Install npm" from [this community tutorial](https://www.digitalocean.com/community/tutorials/how-to-host-ghost-with-nginx-on-digitalocean):

    ssh root@yourname.com
    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get install python-software-properties python g++ make
    sudo add-apt-repository ppa:chris-lea/node.js
    sudo apt-get install nodejs

Follow "Install and Run Ghost" from [the Ghost docs](http://docs.ghost.org/installation/linux/):

    cd ~/
    curl -L https://ghost.org/zip/ghost-latest.zip -o ghost.zip
    sudo apt-get install unzip
    unzip -uo ghost.zip -d ghost
    cd ghost/
	npm install --production
    npm start

Check to make sure ghost is installed properly, and Ctrl+C to stop the process.

### 5. Configure Ghost

Add in your domain name to Ghost's config.js settings.

    cd ~/ghost/
    nano config.js
    
Under `// ### Production` change the url:

    production: {
        url: 'http://yourname.com',

### 6. Run Ghost

Follow "Making Ghost run forever" using "Forever" from [the Ghost docs](http://docs.ghost.org/installation/deploy/):

    cd ~/ghost/
    npm install forever -g
    NODE_ENV=production forever start index.js

### 7. Install Nginx web server

Now that we have Ghost installed and running, we need a web server for public viewing.

Follow "Setting up Ghost with a domain name" from [the Ghost docs](http://docs.ghost.org/installation/deploy/):

    sudo apt-get install nginx
    cd /etc/nginx/sites-available
    nano ghost.conf
    
Copy & paste the following into `ghost.conf`:

    server {
        listen 80;
        server_name yourname.com;

        location / {
            proxy_set_header   X-Real-IP $remote_addr;
            proxy_set_header   Host      $http_host;
            proxy_pass         http://127.0.0.1:2368;
        }
    }
    
Then:

    sudo ln -s /etc/nginx/sites-available/ghost.conf /etc/nginx/sites-enabled/ghost.conf
    sudo service nginx restart

### 8. Done!

Sign in and start writing on your new Ghost blog at yourdomain.com/ghost.

I installed a custom Ghost theme called [StayPuft](https://github.com/dlecina/StayPuft), you can check out the different themes available on the [Ghost marketplace](http://marketplace.ghost.org/). Thanks for reading!

---
**Update (7/4/14)**: My friend Dan wrote a [followup post](http://swrhim.com/configure-your-ghost-servers-email/) on his blog about setting up an email service on your Ghost blog, check it out!