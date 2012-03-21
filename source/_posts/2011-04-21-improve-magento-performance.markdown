---
date: '2011-04-21 03:24:15'
layout: post
slug: improve-magento-performance
status: publish
title: Improve Magento Performance
wordpress_id: '162'
categories:
- Linux
- magento
- PHP
---

## Quick & Easy Wins





	
  * Install Fooman Speedster

	
  * Enable Gzip Compression in .htaccess

	
  * HTTP KeepAlives enabled

	
  * Disable open_basedir




## Mysql Settings


my.cf should contain something like:
`key-buffer = 512M
max-allowed_packet = 64M
table-cache = 512
sort-buffer-size = 4M
read-buffer-size = 4M
read-rnd-buffer-size = 2M
myisam-sort-buffer-size 64M
tmp-table-size = 128M
thread-cache-size = 8
max-connections = 400
wait-timeout = 1800
connect_timeout = 120`


## APC Caching


Turn off the magento compiler module when using apc.stat=0
`apc.stat = 0
apc.shm_size = 512`
Modify app/etc/local.xml. Place the following just inside the <global> tag:
`<cache>
<backend>apc</backend>
<prefix>alphanumeric</prefix>
</cache>`


## Memory FS


For when you have ram to burn. Dump the sessions and cache in ram (presuming you're using file based sessions).
`mount -t tmpfs -o size=256M,mode=0777 tmpfs /var/www/vhosts/yourmagentostore.com/httpdocs/var/cache
mount -t tmpfs -o size=64M,mode=0777 tmpfs /var/www/vhosts/yourmagentostore.com/httpdocs/var/session/`


## Database Sessions


Add the following to your app/etc/local.xml after </resources> (inside <global> )
`<session_save><![CDATA[db]]></session_save>`
