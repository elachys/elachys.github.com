---
date: '2011-09-20 06:11:27'
layout: post
slug: open-utf-8-csvs-in-excel
status: publish
title: Open UTF-8 CSV's in Excel
wordpress_id: '323'
categories:
- PHP
---

Excel requires a BOM at the beginning of the file. For UTF-8 it can be represented as:
{% codeblock lang:php %}
<?php echo "\xef\xbb\xbf"; ?>

<?php $fixedcsv = "\xef\xbb\xbf" . $brokencsv; ?>
{% endcodeblock %}
