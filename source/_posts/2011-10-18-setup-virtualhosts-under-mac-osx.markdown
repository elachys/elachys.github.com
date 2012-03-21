---
date: '2011-10-18 12:38:13'
layout: post
slug: setup-virtualhosts-under-mac-osx
status: publish
title: Setup virtualhosts under mac osx
wordpress_id: '340'
categories:
- Useful Utilities
---

Start apache with: `sudo httpd -k start`

The easiest way i've found to create virtual hosts is with this handy [virtualhost.sh script](https://github.com/pgib/virtualhost.sh).

You can install it with the following

`cd ~
git clone https://github.com/pgib/virtualhost.sh.git virtualhost
PATH=$PATH\:~/virtualhost
`

Then add each virtual host with:
`sudo virtualhost.sh YOURVIRTUALHOSTNAME`
