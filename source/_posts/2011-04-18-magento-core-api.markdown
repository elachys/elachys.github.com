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
`require_once dirname(__FILE__).'/../htdocs/shop/app/Mage.php';
Mage::app()->setCurrentStore(Mage_Core_Model_App::ADMIN_STORE_ID);`



## Models




Products, Orders and plenty more can be accessed in the same way. By changing your choice of model, you can get all products or all orders!


`Mage::getModel('sales/order')->getCollection()->load();
Mage::getModel('catalog/product')->getCollection();`



### get All products


`$productCollection = Mage::getModel('catalog/product')->getCollection();`


### Get some products (by attribute)


`$product = Mage::getModel('catalog/product')->loadByAttribute('sku','myexamplesku']);`


### Product attributes




Products also have magic get/set methods for all their attributes, as follows


`$product->setColour('blue');
$product->save();`
`$product->getColour()`


### Get all product data


`$product->getData(); `
