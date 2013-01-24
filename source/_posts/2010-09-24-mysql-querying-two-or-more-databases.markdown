---
date: '2010-09-24 05:04:21'
layout: post
slug: mysql-querying-two-or-more-databases
status: publish
title: MySQL Querying two or more databases
wordpress_id: '109'
categories:
- MySQL
---

First, you need to grant permissions to one user for both databases.

then, when running queries you specify your database at the begining. eg:

    SELECT * from `database1`.`table`
    UNION
    SELECT * from `database2`.`table` ORDER BY 1

This will merge the results together removing duplicates and the order by will happen to both tables.

If you want to see duplicate rows. You need to use UNION ALL instead of plain UNION

WHERE portions of queries must be run in both queries.
