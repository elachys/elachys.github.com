---
date: '2011-09-21 04:35:52'
layout: post
slug: set-page-title-tag-from-controller
status: publish
title: Set page title tag from controller
wordpress_id: '325'
categories:
- magento
---

    $this->getLayout()->getBlock('head')->setTitle($this->__('My Account'));

eg:
{% codeblock lang:php %}
<?php
public function indexAction(){
    $this->loadLayout();
    $this->_initLayoutMessages('customer/session');
    $this->getLayout()->getBlock('head')->setTitle($this->__('My Account'));
    $this->renderLayout();
}
?>
{% endcodeblock %}