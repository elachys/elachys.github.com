---
date: '2010-07-14 08:36:14'
layout: post
slug: svn-permission
status: publish
title: SVN User specific read write permissions
wordpress_id: '61'
categories:
- Linux
---

apache config:

    DAV             svn
    SVNPath         /path/to/svnroot/barneyb

    AuthType        Basic
    AuthName        "Subversion/Trac"
    AuthUserFile    /path/to/apache/conf/htpasswd

    AuthzSVNAccessFile  /path/to/apache/conf/authz.conf

    Satisfy     any
    Require     valid-user

    AuthzSVNAccessFile
    [/bicycle_dashboard] denotes a specific directory.

    [/]
    barneyb = rw

    [/bicycle_dashboard]
    * = r
    barneyb = rw