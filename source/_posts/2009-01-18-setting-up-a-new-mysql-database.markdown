---
date: '2009-01-18 14:35:09'
layout: post
slug: setting-up-a-new-mysql-database
status: publish
title: Setting up a mysql database
wordpress_id: '18'
categories:
- Linux
---

### Creating the database


`Create Database mydbname;`


### Granting the user


` GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP  ON mydatabase.* TO 'username'@'localhost' IDENTIFIED BY 'mypassword';
`
