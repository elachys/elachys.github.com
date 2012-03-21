---
date: '2011-06-29 11:10:42'
layout: post
slug: magento-remove-item-from-cart
status: publish
title: Magento remove item from cart
wordpress_id: '287'
categories:
- magento
---

Remove product with the SKU 'promo'.

`define('PROMO_SKU','promo');
$session = Mage::getSingleton('checkout/session');
$quote = $session->getQuote();`

`$cart = Mage::getModel('checkout/cart');
$cartItems = $cart->getItems();`

`foreach($cartItems as $item) {
if ($item->getSku() == PROMO_SKU){
$quote->removeItem($item->getId())->save();
}
}

`



`Mage::getSingleton('checkout/session')->setCartWasUpdated(true);
$cart->init();
`
