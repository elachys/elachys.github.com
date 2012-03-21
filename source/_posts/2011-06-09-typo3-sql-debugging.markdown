---
date: '2011-06-09 10:49:21'
layout: post
slug: typo3-sql-debugging
status: publish
title: typo3 sql debugging
wordpress_id: '246'
categories:
- typo3
---

Add the following to the bottom of your typo3conf/localconf.php file to get sent to a pretty looking error page when a sql error occurs.

`

$TYPO3_CONF_VARS['SYS']['displayErrors'] = '1';
$TYPO3_CONF_VARS['SYS']['devIPmask'] = '*';
$TYPO3_CONF_VARS['SYS']['errorHandler'] = 't3lib_error_ErrorHandler';
$TYPO3_CONF_VARS['SYS']['errorHandlerErrors'] = E_ALL ^ E_NOTICE;
$TYPO3_CONF_VARS['SYS']['exceptionalErrors'] = E_ALL ^ E_NOTICE ^ E_WARNING ^ E_USER_ERROR ^ E_USER_NOTICE ^ E_USER_WARNING;
$TYPO3_CONF_VARS['SYS']['debugExceptionHandler'] = 't3lib_error_DebugExceptionHandler';
$TYPO3_CONF_VARS['SYS']['productionExceptionHandler'] = 't3lib_error_DebugExceptionHandler';
$TYPO3_CONF_VARS['SYS']['systemLogLevel'] = '0';
$TYPO3_CONF_VARS['SYS']['systemLog'] = 'mail,YOUR@EMAILHERE.COM,4;error_log,,2;syslog,LOCAL0,,3;file,/var/www/vhosts/SITEURL/logs/typo3error.log';
$TYPO3_CONF_VARS['SYS']['enable_errorDLOG'] = '1';
$TYPO3_CONF_VARS['SYS']['enable_exceptionDLOG'] = '1';
$TYPO3_CONF_VARS['SYS']['curlUse'] = '1';
$TYPO3_CONF_VARS['SYS']['devIPmask'] = '127.0.0.1,::1,YOUR_IP_HERE';
$TYPO3_CONF_VARS['SYS']['sqlDebug'] = '1';
$TYPO3_CONF_VARS['SYS']['enable_DLOG'] = true;
$TYPO3_CONF_VARS['SYS']['enable_errorDLOG'] = '1';
$TYPO3_CONF_VARS['SYS']['enable_exceptionDLOG'] = '1';

$TYPO3_CONF_VARS['SYS']['useCachingFramework'] = '1';

$TYPO3_CONF_VARS['FE']['debug'] = '1';
`
