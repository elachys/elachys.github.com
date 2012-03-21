---
date: '2011-06-29 11:07:53'
layout: post
slug: magento-adding-an-item-to-your-cart
status: publish
title: 'Magento: adding an item to your cart'
wordpress_id: '285'
categories:
- magento
---

The code below will add the product with the sku "promo" to your basket.

`define('THESKU','promo');
$product = Mage::getModel('catalog/product')->setStoreId(Mage::app()->getStore()->getId());
$product->load($product->getIdBySku(THESKU));`

`$cart = Mage::getSingleton('checkout/cart');
$cart->init();
$cart->getQuote()->cleanModelCache();

`

` try {
$cart->addProduct($product, array('qty' => 1));
$cart->save();
Mage::getSingleton('checkout/session')->setCartWasUpdated(true);
} catch(Exception $e) {
die($e->getMessage());
}
`
