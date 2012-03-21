---
date: '2011-06-24 09:09:16'
layout: post
slug: set-pear-to-use-beta-channel
status: publish
title: Set pear to use beta channel
wordpress_id: '281'
categories:
- Linux
- PHP
---

Sometimes you just need a little danger in your life.
If you have php pear installed, you can set it to install beta packages as follows:
`sudo pear config-set preferred_state beta`

Afterwards, you can set it back by using the following command:
`sudo pear config-set preferred_state stable`

Note: if you only need to do it for one package. You can always just do:
`pear -d preferred_state=beta install PHP_Beautifier`
