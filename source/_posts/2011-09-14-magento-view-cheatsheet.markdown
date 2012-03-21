---
date: '2011-09-14 11:28:43'
layout: post
slug: magento-view-cheatsheet
status: publish
title: View / Template Cheatsheet
wordpress_id: '304'
categories:
- magento
- PHP
---

## Currencies and prices


`<?php echo Mage::helper('core')->currency($_product->getFinalPrice(),true,false); ?>`

Price without currency symbol
`<?php echo Mage::getModel('directory/currency')->format($item->getData('price'), array('display'=>Zend_Currency::NO_SYMBOL), false); ?>`


## Current page url


`echo $this->helper('core/url')->getCurrentUrl(); ?>`


## Sanitize user data


`<?php echo $this->stripTags($_product->getName(), null, true); ?>`


## Scaled, Resized image url


`<?php echo $this->helper('catalog/image')
->init($_product, 'image')
->constrainOnly(TRUE)
->keepAspectRatio(TRUE)
->keepFrame(FALSE)
->resize(180,null); ?>`


## Dates


`<?php echo $this->formatDate($order->getCreatedAt(),Mage_Core_Model_Locale::FORMAT_TYPE_FULL); ?>`
possible options include:
`Mage_Core_Model_Locale::FORMAT_TYPE_FULL
Mage_Core_Model_Locale::FORMAT_TYPE_LONG
Mage_Core_Model_Locale::FORMAT_TYPE_MEDIUM
Mage_Core_Model_Locale::FORMAT_TYPE_SHORT`



## Dynamically link to other controllers




This method of linking shouldn't break when you update code in your controllers and can be used in any view.


`<?php echo $this->getUrl('model/controller/action'); ?>`
for example
`<?php echo $this->getUrl('customer/account'); ?>`
