---
date: '2011-06-21 04:35:33'
layout: post
slug: typo3-page-bits
status: publish
title: typo3 page bits
wordpress_id: '253'
categories:
- typo3
---

## Current page url


`t3lib_div::getIndpEnv('TYPO3_REQUEST_URL')`



## Current page id in a module


` echo $GLOBALS['TSFE']->page['uid']; `



## Typo3 link to any page (based on page id)


` echo $GLOBALS['TSFE']->cObj->getTypoLink_URL(12345678); `



## Get Typoscript value in a module




### Typoscript


`somethingtoaccess {
aproperty = some value
anotherproperty = bleh lah lah lah
}
somethingtoaccess.athirdproperty = falalalala
`


### PHP


` echo $GLOBALS['TSFE']->tmpl->setup['somethingtoaccess.']['aproperty']; `



## Get page properties from a uid


Note: the root page will have a pid (parent id) of 0
`$pageSelect = t3lib_div::makeInstance('t3lib_pageSelect');
$page = $pageSelect->getPage_noCheck($uid,false);
`
