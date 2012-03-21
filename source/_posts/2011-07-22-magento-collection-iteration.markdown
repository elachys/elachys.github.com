---
date: '2011-07-22 06:49:41'
layout: post
slug: magento-collection-iteration
status: publish
title: Magento collection iteration
wordpress_id: '294'
categories:
- magento
---

When you get a collection, most of the time you'll just be able to do:
`$products = Mage::getModel('catalog/product')->getCollection()
->addAttributeToFilter('status',array('eq' => 1))
->addAttributeToFilter('visibility',array('in' => array(2,4)))
->setPage($i,PER_PAGE);
foreach($products as $product){
echo $product->getSku() . PHP_EOL;
}
`

However, if the collection is very large, you can actually run out of ram doing this. Instead, you should do the following:

`function productCallback($args)
{
echo $args['row']['sku'] . PHP_EOL;
}
$products = Mage::getModel('catalog/product')->getCollection()
->addAttributeToFilter('status',array('eq' => 1))
->addAttributeToFilter('visibility',array('in' => array(2,4)))
->setPage($i,PER_PAGE);`

Mage::getSingleton('core/resource_iterator')->walk($products->getSelect(), array('productCallback'), array('res'=>$res));


