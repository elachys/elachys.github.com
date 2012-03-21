---
date: '2010-09-03 10:46:34'
layout: post
slug: load-balancing-high-availability-for-the-lamp-stack
status: publish
title: Load balancing / high availability for the LAMP stack
wordpress_id: '101'
categories:
- Linux
- MySQL
- PHP
---

# Load balancers


Load balancers sit in-front of the web and database servers. These decide which web server each HTTP request from a client goes to.

After your firewall, this is the first thing that gets it.

Pen is a linux app which does this extremely simply and can be installed from apt-get. An example syntax would be:
`sudo pen –df 80 192.168.1.105 192.168.1.106`

-df keeps pen running in the foreground and also displays debug info (not what you want for a production configuration). You need to use sudo for pen on ports below 1024.

80 is the port pen is monitoring (the HTTP port)

After that it’s just a space separated list of your web servers.


## PHP Considerations


Your PHP file based sessions will no longer work, switch to network storage or use mysql. Your web servers are now stateless as the user could arrive on a different server for each request.



* * *




# Web servers


Just your standard installs of apache and php running. No need for mysql here. I would recommend keeping the same httpd.conf file on each server to reduce confusion. These servers are cheap and disposable.


## PHP Considerations


Saving state across multiple webservers might become a problem. Standard PHP file based sessions will be bound to one webserver if no network storage is used. Alternatively, switching your sessions to MySQL keeps your webservers stateless and is much easier. You can overwrite PHP’s standard sessions handler pretty easily and replace it with a MySQL one.



* * *




# Database servers


Linux installs running MySQL. These are generally broken into two types, master and slave. There is usually a single master who handles all the writes (INSERT / UPDATE queries) .

The complex reads (SELECT queries) are handled by any of the mysql slaves. Spend your money on a good master as you only get one without mysql enterprise as standard MySQL doesn’t support  a multimaster setup out of the box.


## PHP Considerations


PHP’s mysql_connect should use your mysql servers hostnames and not localhost.

You might want to separate your reads and writes to point to the seperate MySQL master / slave hostnames. This is not mandatory as you can use mysql-proxy to monitor each request and send it to either the master or a slave. Although i would suggest using mysql-proxy in this way only for legacy systems where code changes are not an option.

You will also want to keep a reference to each of your mysql connections.



* * *




# Conclusions


One thing I noticed is that using IP addresses in your configuration files could get seriously confusing. I would suggest making some dummy hostnames and settings the IP’s in the hosts file for each machine. That way, if IP addresses change, you only have to update one file on each host.

Also, I wouldn’t use pen for anything big. Instead, invest in a good hardware load balancer. Preferably two with heartbeat so if one goes down the other takes over. Ultramonkey might also offer a solution if hardware load balancers are too expensive.
