---
date: '2011-04-18 11:38:01'
layout: post
slug: magento-core-api
status: publish
title: Accessing Magento core api
wordpress_id: '155'
categories:
- magento
---

load up mage with:
{% codeblock lang:php %}
<?php
require_once dirname(__FILE__).'/../htdocs/shop/app/Mage.php';
Mage::app()->setCurrentStore(Mage_Core_Model_App::ADMIN_STORE_ID);
?>
{% endcodeblock %}

## Models


Products, Orders and plenty more can be accessed in the same way. By changing your choice of model, you can get all products or all orders!

{% codeblock lang:php %}
<?php 
Mage::getModel('sales/order')->getCollection()->load();
Mage::getModel('catalog/product')->getCollection();
?>
{% endcodeblock %}

### get All products
{% codeblock lang:php %}
<?php
$productCollection = Mage::getModel('catalog/product')->getCollection();
?>
{% endcodeblock %}
### Get some products (by attribute)

{% codeblock lang:php %}
<?php
$product = Mage::getModel('catalog/product')->loadByAttribute('sku','myexamplesku']);
?>
{% endcodeblock %}

### Product attributes

Products also have magic get/set methods for all their attributes, as follows

{% codeblock lang:php %}
<?php
$product->setColour('blue');
$product->save();
echo $product->getColour();
?>
{% endcodeblock %}

### Get all product data

{% codeblock lang:php %}
<? php print_r($product->getData()); ?>
{% endcodeblock %}