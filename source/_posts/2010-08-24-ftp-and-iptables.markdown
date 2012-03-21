---
date: '2010-08-24 05:33:07'
layout: post
slug: ftp-and-iptables
status: publish
title: ftp and iptables
wordpress_id: '95'
categories:
- Linux
---

make sure your  /etc/sysconfig/iptables-config contains the following line:
`IPTABLES_MODULES="ip_conntrack_ftp"`
You will probably have to modify the existing line.

iptables rules themselves should be as follows (you can view your rules at /etc/sysconfig/iptables)
`
-A INPUT -p tcp -m tcp --dport 20 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 21 -j ACCEPT
`

Make sure your last line is someting like:
`
-A INPUT -j REJECT --reject-with icmp-port-unreachable
`

If this line is before the end. You'll reject the ftp ports and it won't work :-(

save ip tables with:
`service iptables save`
restart with:
`service iptables restart`

If it still doesn't connect. Try
`
modprobe ip_conntrack_ftp
`
