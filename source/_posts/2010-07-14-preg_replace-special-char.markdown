---
date: '2010-07-14 10:15:57'
layout: post
slug: preg_replace-special-char
status: publish
title: PHP preg_replace special char with char
wordpress_id: '63'
categories:
- PHP
---

Replace special chars that are html encoded with their plain text equivalents

eg. Turns &#8216; into a normal character

`preg_replace('/&#(\d+);/e','chr($1)','my weird string');`
