---
date: '2011-02-01 10:54:28'
layout: post
slug: update-centos-to-php5-3
status: publish
title: Update CentOS to PHP5.3
wordpress_id: '133'
categories:
- Linux
- PHP
---

firstly, check you're running centOS. eg:
`# cat /etc/*-release
CentOS release 5.5 (Final)`

then use this wonderful persons repo from the posting [here](http://www.webtatic.com/blog/2009/06/php-530-on-centos-5/).

Posted below for reference:

To install, first you must tell rpm to accept rpm’s signed by me, then add the yum repository information to yum:
`
rpm -ivh http://repo.webtatic.com/yum/centos/5/`uname -i`/webtatic-release-5-1.noarch.rpm
`

Now you can install php by doing:
`
yum --enablerepo=webtatic install php
`
Or update an existing installation of php, which will also update all of the other php modules installed:
`
yum --enablerepo=webtatic update php
`
If this does not work correctly, try disabling all other repositories while installing/updating, by adding the –disablerepo=* option. This will stop other dependencies from being installed, so you may want to install them first.
`
yum --disablerepo=* --enablerepo=webtatic update php
`
