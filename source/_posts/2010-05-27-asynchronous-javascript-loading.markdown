---
date: '2010-05-27 10:58:36'
layout: post
slug: asynchronous-javascript-loading
status: publish
title: Asynchronous javascript loading
wordpress_id: '35'
categories:
- Javascript
---

Using the same idea as google analytic's new code.

here's an example of swf object:
{% codeblock lang:js %}
(function() {
var sw = document.createElement('script'); sw.type = 'text/javascript'; sw.async = true;
sw.src = 'http://ajax.googleapis.com/ajax/libs/swfobject/2/swfobject.js';
var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(sw, s);
})();
{% endcodeblock %}

Using this instead of a standard script tag seriously decreases load time.
