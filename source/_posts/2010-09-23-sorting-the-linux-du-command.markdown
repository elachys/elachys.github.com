---
date: '2010-09-23 10:30:39'
layout: post
slug: sorting-the-linux-du-command
status: publish
title: Sorting the linux du command
wordpress_id: '106'
categories:
- Linux
---

du -ak / | sort -nr | less

This gives you all the files and directories on the system, in descending order by size. Directories are listed along with files and show the total blocks in the subtree under them.

Basically, it gives all the objects (files and directories) in descending order by size.
