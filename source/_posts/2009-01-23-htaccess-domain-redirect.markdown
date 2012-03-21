---
date: '2009-01-23 09:48:14'
layout: post
slug: htaccess-domain-redirect
status: publish
title: .htaccess domain redirect
wordpress_id: '27'
categories:
- Linux
---

Redirecting a domain name from non-www to www can be a life saver for seo. The easiest way to do this under apache is to create a .htaccess file in the root of your website.

The following code will do the redirection for you (replace mydomain.com with your domain name).

`
Options -Indexes`

RewriteEngine On

RewriteCond %{HTTP_HOST} !^www.mydomain.com$ [NC]
RewriteRule ^(.*)$ http://www.mydomain.com/$1 [R=301,L] 
