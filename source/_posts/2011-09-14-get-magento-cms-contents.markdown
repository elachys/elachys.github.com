---
date: '2011-09-14 10:53:29'
layout: post
slug: get-magento-cms-contents
status: publish
title: Get magento cms contents
wordpress_id: '302'
categories:
- magento
- PHP
---

To display content from cms pages or static blocks in your view.



## CMS Static blocks


getLayout()->createBlock('cms/block')->setBlockId('MY-BLOCK-IDENTIFIER')->toHtml(); ?>



## CMS page contents


$page = Mage::getModel('cms/page')->load('MY-CMS-IDENTIFIER', 'identifier')->getContent();
