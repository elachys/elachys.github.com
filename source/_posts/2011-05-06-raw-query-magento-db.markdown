---
date: '2011-05-06 10:24:03'
layout: post
slug: raw-query-magento-db
status: publish
title: Querying the database in magento
wordpress_id: '190'
categories:
- magento
---

So, sometimes you end up inherriting code that doesn't use MVC, or even objects. But you need data from it's db tables, well you can utilize magento's existing mysql connection as follows:

`$dbc = Mage::getSingleton('core/resource')->getConnection('core_read');
$result = $dbc->fetchAll("SELECT * FROM `TABLE` WHERE `FIELD` = 'VALUE'");`

Note: you may also need to put: `$app = Mage::app('default');` above the following. and you also need to actually include mage... A full example would look something like:
`require_once dirname(__FILE__).'/../htdocs/shop/app/Mage.php';
$app = Mage::app('default');
$dbc = Mage::getSingleton('core/resource')->getConnection('core_read');
$result = $dbc->fetchAll("SELECT * FROM `table`");
print_r($result);
`
