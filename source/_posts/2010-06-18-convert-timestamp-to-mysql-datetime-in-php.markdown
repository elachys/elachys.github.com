---
date: '2010-06-18 09:59:17'
layout: post
slug: convert-timestamp-to-mysql-datetime-in-php
status: publish
title: convert timestamp to mysql datetime in PHP
wordpress_id: '49'
categories:
- MySQL
- PHP
---
{% codeblock lang:php %}
<?php echo date("Y-m-d H:i:s",$timestamp); ?>
{% endcodeblock %}