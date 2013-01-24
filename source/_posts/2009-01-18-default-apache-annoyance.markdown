---
date: '2009-01-18 06:56:57'
layout: post
slug: default-apache-annoyance
status: publish
title: Default Apache Annoyance
wordpress_id: '15'
categories:
- Linux
---

.htaccess files are not used by default in apache. This freaked me out the first time i set up a server.

You must change /etc/httpd/conf/httpd.conf

    AllowOverride None

to

    AllowOverride All

then restart apache with:

    sudo httpd -k graceful
