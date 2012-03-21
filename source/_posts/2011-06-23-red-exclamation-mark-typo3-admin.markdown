---
date: '2011-06-23 06:02:03'
layout: post
slug: red-exclamation-mark-typo3-admin
status: publish
title: Red exclamation / question mark buttons in typo3 admin
wordpress_id: '274'
categories:
- typo3
---

If you've just installed a new module and all your icons in the admin change to red buttons with white exclamation marks in, you simply need to set write permissions on your typo3temp folder.

Just do:
`sudo chmod -R 777 ./htdocs/typo3temp`

Or you might just be able to delete the contents of typo3temp...
