---
date: '2011-04-27 10:13:57'
layout: post
slug: fputcsv-outpu
status: publish
title: fputcsv to something other than a file
wordpress_id: '165'
categories:
- PHP
---

PHP doesn't have a csv function to convert an array to a csv (it can pass strings as csv's though).

Usually you would use:
`$res = fopen('output.csv','w');
fputcsv($res,array('field1','field2','field3'));
fclose($res);
`
Then read the contents of the file back to get the string. This sucks.



## Output to screen


`$res = fopen('php://output','w');
fputcsv($res,array('field1','field2','field3'));
fclose($res);
`



## Output to string


`$res = fopen('php://temp','w');
fputcsv($res,array('field1','field2','field3'));
rewind($res);
$csv = fgets($res);
`
