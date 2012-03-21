---
date: '2011-05-04 09:38:58'
layout: post
slug: magento-guest-checkout-customer-details
status: publish
title: Magento, customer details, and guest checkout
wordpress_id: '176'
categories:
- magento
---

If you want to get the customer's details of a specific order, you'd think the following would work (where MY_ORDER_ID is the order ID)
`$order = Mage::getModel('sales/order')->load (MY_ORDER_ID);
$customer = Mage::getModel('customer/customer')->load($order->getCustomerId());
print_r($customer->getData());
`
And it does, but! This will only work for users that didn't use the guest checkout. Guests don't have a customer id, so you have to do things a little differently.

`$order = Mage::getModel('sales/order')->load (MY_ORDER_ID);
//If they have no customer id, they're a guest.
if($order->getCustomerId() === NULL){
echo $order->getBillingAddress()->getFirstname();
}
//else, they're a normal registered user.
else {
$customer = Mage::getModel('customer/customer')->load($order->getCustomerId());
$customer->getDefaultBillingAddress()->getFirstname();
}
`
