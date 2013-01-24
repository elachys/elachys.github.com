---
date: '2011-11-16 10:39:53'
layout: post
slug: canonical-tags-on-cms-pages
status: publish
title: Canonical tags on cms pages
wordpress_id: '344'
categories:
- magento
---

For product / category pages there is a config option for this in the magento admin. But for normal CMS pages you need to add the following to the "design" tab on each page (obviously change the URL to the correct one)

{% codeblock lang:xml %}
<reference name="head">
    <action method="addLinkRel">
        <rel>canonical</rel>
        <href>http://www.somrandomdomainname.com/</href>
    </action>
</reference>
{% endcodeblock %}