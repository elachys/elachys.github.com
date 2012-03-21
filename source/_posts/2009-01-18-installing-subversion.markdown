---
date: '2009-01-18 06:11:18'
layout: post
slug: installing-subversion
status: publish
title: Installing Subversion
wordpress_id: '5'
categories:
- Linux
---

Firstly, get subversion using your favorite package manager.
`
yum install subversion`

To see if subversion is now installed use:
`
rpm -qa |grep subversion
`


### Mod_dav_svn


`yum install mod_dav_svn`


### Setting up subversion repositories


`
mkdir /var/www/html/svn.mydomain.com
mkdir -p /var/www/html/svn.mydomain.com/repos
mkdir /var/www/html/svn.mydomain.com/users
mkdir /var/www/html/svn.mydomain.com/permissions
`
and now we set our permissions
`
chown -fhR apache.apache /var/www/html/svn.mydomain.com`


### Creating our first repository


`
svnadmin create /var/www/html/svn.mydomain.com/reposname
`


### Apache configuration


add to /etc/httpd/conf.d/subversion.conf
`
<Location /svn>
DAV svn
SVNParentPath /var/www/html/svn.mydomain.com/repos`

# Limit write permission to list of valid users.
#   <LimitExcept GET PROPFIND OPTIONS REPORT>
# Require SSL connection for password protection.
# SSLRequireSSL

AuthType Basic
AuthName "Subversion Repos"
AuthUserFile /etc/svn-passwd
Require valid-user
#   </LimitExcept>
</Location>


### Creating a subversion user


`
htpasswd -c /etc/svn-passwd myusername
`
Then enter your chosen password


### Initial Import


`
svn import -m "initial release" http://svn.domain.com/svn/reposname
`


### Standard Repository Layout


The first thing you should do is make the following directories:
branches,tags,trunk

branches - experimental releases / "spin off's" of your initial project
tags - copies of the trunk that are ready for a release
trunk - latest project files (where you work from)

you should check in/out your project from http://svn.mydomain.com/svn/myrepos/trunk
