---
date: '2010-06-16 05:27:15'
layout: post
slug: php-remember-me-saving-session
status: publish
title: PHP "Remember Me" Saving Session
wordpress_id: '44'
categories:
- PHP
---

You can add a remember me button to an existing login system in PHP with the following (where $_POST['remember'] is the remember me checkbox in the form).
{% codeblock lang:php %}
<?php
session_start();
// Unset all of the session variables.
$_SESSION = array();

/*
If it's desired to kill the session, also delete the session cookie.
 Note: This will destroy the session, and not just the session data!
 */

if (ini_get("session.use_cookies")) {
    $params = session_get_cookie_params();
    setcookie(session_name(), '', time() - 42000, $params["path"], $params["domain"], $params["secure"]);
}
session_destroy();

if($_POST['remember'] == "y"){
    session_set_cookie_params(31556926); //1 year in seconds.
}
?>
{% endcodeblock %}