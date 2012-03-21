---
date: '2009-01-18 15:22:19'
layout: post
slug: adding-gd-support
status: publish
title: Adding GD support
wordpress_id: '22'
categories:
- Linux
---

Quickest way to add GD support to an existing php installation under Fedora.
`
yum install php-gd
`

Once That has finished. Restart Apache. I tend to use:
`
httpd -k graceful
`
