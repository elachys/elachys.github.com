---
date: '2011-06-24 09:06:51'
layout: post
slug: surpress-error-message-in-linux-commands
status: publish
title: Surpress error message in linux commands
wordpress_id: '279'
categories:
- Linux
---

When using a command like find, you can pipe all errors to dev null using the following syntax
`find / -name "somefilename" 2>/dev/null`
