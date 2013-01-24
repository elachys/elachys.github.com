---
date: '2011-09-19 10:20:26'
layout: post
slug: logged-in-only-pages
status: publish
title: Logged in only pages
wordpress_id: '315'
categories:
- magento
- PHP
---

Add the following code to your controller if you don't want it to be accessible by users who aren't logged in.
{% codeblock lang:php %}
<?php
public function preDispatch() {
    parent::preDispatch();

    if (!Mage::getSingleton('customer/session')->authenticate($this)) {
        $this->setFlag('', 'no-dispatch', true);
    }
}
?>
{% endcodeblock %}