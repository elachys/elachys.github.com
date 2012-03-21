---
date: '2011-06-03 05:03:16'
layout: post
slug: tabs-in-modules
status: publish
title: Tabs in Modules
wordpress_id: '238'
categories:
- typo3
---

open: 
`./typo3conf/ext/YOUREXTENSION/ext_tables.php`
You need to add `'dividers2tabs' => TRUE`
To show in context:
`
$TCA["tx_3evmedia_general"] = Array (
	"ctrl" => Array (
		'title' => 'LLL:EXT:3ev_media/locallang_db.xml:tx_3evmedia_general',		
		'label' => 'title',	
		'tstamp' => 'tstamp',
		'crdate' => 'crdate',
		'cruser_id' => 'cruser_id',
		"sortby" => "sorting",	
		"delete" => "deleted",
		"enablecolumns" => Array (		
			"disabled" => "hidden",	
			"starttime" => "starttime",	
			"endtime" => "endtime",	
			"fe_group" => "fe_group",
		),
		"dynamicConfigFile" => t3lib_extMgm::extPath($_EXTKEY)."tca.php",
		"iconfile" => t3lib_extMgm::extRelPath($_EXTKEY)."icon_tx_3evmedia_general.gif",
		'dividers2tabs' => TRUE,	
	),
	"feInterface" => Array (
		"fe_admin_fieldList" => "hidden, starttime, endtime, fe_group, category, title, description, image, yotube_id, attachment, attachment_logged_in, publish_date",
	)
);
`

You then need to set your tabs in tca.php --div--; starts a new tab. In this example, the two tabs are called "General" and "Poll"
`
	"types" => Array (
		"0" => Array("showitem" => "--div--;General,hidden;;1;;1-1-1, category, title;;;;2-2-2, description;;;richtext[paste|bold|italic|underline|formatblock|class|left|center|right|orderedlist|unorderedlist|outdent|indent|link|image]:rte_transform[mode=ts];3-3-3, image, yotube_id, attachment, attachment_logged_in, publish_date,
		                          --div--;Poll,image")
	),
`
