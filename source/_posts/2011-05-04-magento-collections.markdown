---
date: '2011-05-04 09:27:02'
layout: post
slug: magento-collections
status: publish
title: Magento Collections
wordpress_id: '172'
categories:
- magento
---

More often than not, when working with the magento core api you'll end up doing something along the lines of:
`Mage::getModel('sales/order')->getCollection();`
So here's a quick overview of some of the fun things you can do with it.


## Iterating, Ordering and getting single items




### Iterating:


`$orders = Mage::getModel('sales/order')->getCollection();
foreach($orders as $order) {
echo 'Order created : ' . $order->getCreatedAt() . PHP_EOL;
}
`


### Ordering:


`$orders = Mage::getModel('sales/order')->getCollection();
$orders->getSelect()->order('created_at','ASC');
`


### Equivalent of count($orders) or sizeof($orders):


`$orders = Mage::getModel('sales/order')->getCollection();
$orders->getSize();
`


### Equivalent of `$orders[0]`


This gets the created date of the first order in your collection.
`$orders = Mage::getModel('sales/order')->getCollection();
echo $orders->getFirstItem()->getCreatedAt();
`


## Filtering and Joining


Get all completed orders for a specific product SKU (where MY_PRODUCT_SKU is a defined as the SKU you wish to use).
`$orderItems = Mage::getModel('sales/order_item')->getCollection()
->addAttributeToFilter('sku', MY_PRODUCT_SKU)
->addFieldToFilter('`order`.`created_at`',Array('gt'=>ORDER_BEGIN_DATE))
->addFieldToFilter('`order`.`created_at`',Array('lt'=>ORDER_END_DATE))
->join('order', 'order_id=entity_id')
->addFieldToFilter('status',Mage_Sales_Model_Order::STATE_COMPLETE);
`
