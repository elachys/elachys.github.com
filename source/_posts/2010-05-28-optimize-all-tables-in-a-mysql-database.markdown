---
date: '2010-05-28 09:04:41'
layout: post
slug: optimize-all-tables-in-a-mysql-database
status: publish
title: Optimize All Tables In A MySQL Database
wordpress_id: '39'
categories:
- MySQL
- PHP
---

{%codeblock lang:php %}
<?php
$alltables = mysql_query("SHOW TABLES");

while ($table = mysql_fetch_assoc($alltables)) {
    foreach ($table as $db => $tablename) {
        mysql_query("OPTIMIZE TABLE '". mysql_real_escape_string($tablename) ."'");
    }
}
?>
{% endcodeblock %}
