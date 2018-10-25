---
layout: post
title: Migrating to Raspberry Pi
image: "/content/images/2016/03/rpi2b-1.jpg"
date: '2016-03-20 22:58:26'
tags:
- tutorial
- howto
- raspberry-pi
- nodejs
- ghost-tag
- code
- node
- raspbian
- hosting
- raspi
---

Or, *how to make Raspbian, Nodejs, and Ghost play nicely with each other*

Another year another new home. **tonyy.in** sprang into existence in a steamy Lower East Side summer, when Robin Williams was still alive and I was still 24. My tales were just a droplet in the digital ocean of blogs and webapps. For 5 months I did not spend a single dime except for the 100 of them required to reserve "tonyy" from the Indian internet authorities.

One year later I came to my senses and stopped bleeding $5 per month in favor of whatever Netflix uses, which happened to be free for me at the time. It was one-year-later Tony's problem to figure out what to do when that stopped being free.

We have one-year-previous Tony and a thoughtful gift from a friend to thank for today's post.

---

*Raspbian GNU/Linux 7 (wheezy)*

### 1. Install Nodejs

Nodejs and NPM are pains to install and this time was no exception. As of this writing, the latest version of Nodejs that both has a Linux ARM Pi build and is [supported by Ghost](http://support.ghost.org/supported-node-versions/) (what happened to `0.11.*`?) is `0.10.28`. I am sure newer versions will be available in due time so just check the [Nodejs releases](https://nodejs.org/download/release/).

```
cd ~/downloads
wget https://nodejs.org/download/release/v0.10.28/node-v0.10.28-linux-arm-pi.tar.gz
cd /usr/local
sudo tar xzvf ~/downloads/node-v0.10.28-linux-arm-pi.tar.gz --strip=1
node -v
npm -v
```

Ref: http://stackoverflow.com/questions/32563173/installing-node-js-on-raspberry-pi-2

### 2. Install Ghost

I expected Ghost installation to be straightforward but alas. Ghost versions `0.7.*` are incompatible with whatever I am running (probably Nodejs 0.10), so we must use `0.6.4` for now. Check the [Ghost releases](https://github.com/TryGhost/Ghost/releases) if you feel compelled.

```
cd ~/downloads
wget https://github.com/TryGhost/Ghost/releases/download/0.6.4/Ghost-0.6.4.zip
unzip -d ../tonyy.in Ghost-0.6.4.zip
```

The other caveat that took some googling is a permissions issue. For some reason, when installing using `sudo` does not work properly and we need to instead use a `--unsafe-perm` option.

```
cd ~/tonyy.in
npm install --production --unsafe-perm
```

### 3. ???

Set up your config.js, Forever, and Nginx as per my [previous entry](http://tonyy.in/how-i-set-up-this-blog/).

### 4. Done!
