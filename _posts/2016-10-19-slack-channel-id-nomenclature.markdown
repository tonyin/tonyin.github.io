---
layout: post
title: Slack Channel ID Nomenclature
image: "/assets/img/2016/10/service_512.png"
date: '2016-10-19 03:59:58'
tags:
- code
- slack
- bots
- naming-conventions
- channels
- nomenclature
---

Short and sweet post. I searched around and could not find anything on this topic, so hopefully the information below helps someone.

[Slack bots](https://api.slack.com/bot-users) are (were?) all the rage. If you are building a Slack bot and sending some messages in channels, and realize that there is no documentation on the nomenclature for the Slack channel IDs, then here 'tis:

- **D** prefix = Direct message
- **G** prefix = Group/private channel
- **P** prefix = Public channel

![](/assets/img/2016/10/service_512-1.png)