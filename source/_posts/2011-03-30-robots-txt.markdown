---
date: '2011-03-30 09:58:54'
layout: post
slug: robots-txt
status: publish
title: robots.txt
wordpress_id: '142'
categories:
- SEO
---

`User-agent: *`
your staple first line. No reason to block things for specific search engines really...

Example conditions:
`Disallow: /*?options=cart$`
`Disallow: /*?limit=all`
`Disallow: /customer/`

Reference:
`$ = ending delimiter`
`* = any number of characters until the next character`

To block everything after a certain part of the URL, you don't include the ending delimiter. Eg. to block the entire checkout process:
`Disallow: /checkout/`

To allow everything:
`Allow: /`

To include your sitemap in your robots.txt:
`Sitemap: http://www.mydomainname.com/sitemap.xml`
