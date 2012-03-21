---
date: '2010-06-30 04:42:41'
layout: post
slug: ssh-mysql-user-databas
status: publish
title: create new user / database for mysql from SSH
wordpress_id: '54'
categories:
- Linux
- PHP
---

`[admin@suncentre root]$ mysql -uadmin`

`mysql> use mysql;`

first check if the user already exists:

`mysql> select * from user WHERE `User` = 'wp1user';`
`Empty set (0.00 sec)`

The user wp1user didn't exist so assess if the database exists;

`mysql> select `Db` from db;`

It didn't... so lets create a new database

`mysql> create database wp1;`

then we assign a new user to the database.

`mysql> GRANT ALL PRIVILEGES ON wp1.* TO "wp1user@localhost";`
`ERROR 1047: Unknown command`

well... that's new. So i tried flushing the privileges...

`mysql> FLUSH PRIVILEGES;`
`Query OK, 0 rows affected (0.03 sec)`

whoop looking good

`mysql> GRANT ALL PRIVILEGES ON wp1.* TO "wp1user@localhost";`
`ERROR 1145: The host or user argument to GRANT is too long`

ok, so it turns out according the mysql manual, you have to quote them seperately...

`mysql> GRANT ALL PRIVILEGES ON wp1.* TO "wp1user"@"localhost";`
`Query OK, 0 rows affected (0.00 sec)`

whoot. now set a password!

`mysql> set password for wp1user = password('wp1pass');`
`Query OK, 0 rows affected (0.03 sec)`

flush again to clear everything up...

`mysql> FLUSH PRIVILEGES;`

and finally exit.

`mysql> exit`

`Bye`
