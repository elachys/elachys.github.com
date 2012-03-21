---
date: '2011-05-05 08:44:55'
layout: post
slug: finding-large-files
status: publish
title: Finding large files
wordpress_id: '181'
categories:
- Linux
---

Easiest way to find the largest files / directories on a system

`du -k | sort -n | perl -ne 'if ( /^(\d+)\s+(.*$)/){$l=log($1+.1);$m=int($l/log(1024)); printf  ("%6.1f\t%s\t%25s  %s\n",($1/(2**(10*$m))),(("K","M","G","T","P")[$m]),"*"x (1.5*$l),$2);}'`
