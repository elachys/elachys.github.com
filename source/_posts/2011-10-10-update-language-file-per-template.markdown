---
date: '2011-10-10 04:05:57'
layout: post
slug: update-language-file-per-template
status: publish
title: Update language file per template
wordpress_id: '329'
categories:
- magento
---

If you wanted to change "Cart" to "Basket" on a multisite install but only make the change on one site. You can update the text on a per-template basis.

Make the following file in your template:

/app/design/frontend/_template_/default/locale/en_US/translate.csv

File format as follows:

`"Cart","Basket"
"Your Shopping Cart","Your Shopping Basket"
"to cart","to basket"
"You have no items in your shopping cart.","You have no items in your shopping basket."
"Total in Cart:","Total in Basket:"
"view cart","view basket"`
