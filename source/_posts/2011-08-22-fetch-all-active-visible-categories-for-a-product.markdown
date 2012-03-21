---
date: '2011-08-22 05:51:49'
layout: post
slug: fetch-all-active-visible-categories-for-a-product
status: publish
title: Fetch all active (visible) categories for a product
wordpress_id: '297'
categories:
- magento
---

I've seen people doing: `$category = $product->getCategoryCollection()->getFirstItem()->load();`

Which is fine, until someone hide categories, then some links randomly won't work if the product is in multiple categories.

The following will filter the category collection to only include active (not hidden) categories.

`$category = $product->getCategoryCollection()->addIsActiveFilter()->getFirstItem()->load();`
