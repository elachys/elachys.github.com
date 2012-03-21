---
date: '2011-05-16 03:07:47'
layout: post
slug: extending-magento-classes
status: publish
title: Extending / Overwriting Magento classes
wordpress_id: '193'
categories:
- magento
---

Create a module in the normal fashion. My module in this case is called "example"


## General Overwriting


You'll need at least two files, the file you're overwriting and a config.xml file (telling magento what you're overwriting).


### overwriting a Controller


In this example, we'll be overwriting app/code/core/Mage/Adminhtml/controllers/CustomerController.php

Make your changes in: /app/code/local/example/Adminhtml/controllers/CustomerController.php
You'll need to include the existing controller. So the top of your class will look something like:
`
require_once 'Mage/Adminhtml/controllers/CustomerController.php';
class Example_Adminhtml_CustomerController extends Mage_Adminhtml_CustomerController {
`


#### ./etc/config.xml


`
<?xml version="1.0"?>
<config>
<admin>
<routers>
<adminhtml>
<args>
<modules>
<Example_Adminhtml before="Mage_Adminhtml">Example_Adminhtml</Example_Adminhtml>
</modules>
</args>
</adminhtml>
</routers>
</admin>
</config>
`


### Overwriting a Model


In this example, we'll be overwriting /app/code/core/Mage/Customer/Model/Entity/Customer.php

You should make your model changes here (remember to extend the existing core model). You need to copy magento's core directory structure:
/app/code/local/example/Customer/Model/Entity/Customer.php


#### ./etc/config.xml


/app/code/local/example/Customer/etc/config.xml
`
<?xml version="1.0"?>
<config>
<modules>
<Example_Customer>
<version>0.1.0</version>
<active>true</active>
<codePool>local</codePool>
</Example_Customer>
</modules>
<global>
<models>
<customer_entity>
<rewrite>
<customer>Example_Customer_Model_Entity_Customer</customer>
</rewrite>
</customer_entity>
</models>
</global>
</config>`
