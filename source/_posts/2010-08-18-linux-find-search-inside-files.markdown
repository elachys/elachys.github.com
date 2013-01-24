---
date: '2010-08-18 10:45:26'
layout: post
slug: linux-find-search-inside-files
status: publish
title: Linux find / search inside files
wordpress_id: '91'
categories:
- Linux
---

    find /path/to/search -name '*.php' -type f -exec grep -i "string to search for" {} \; -print
