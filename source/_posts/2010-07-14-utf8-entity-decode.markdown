---
date: '2010-07-14 10:52:05'
layout: post
slug: utf8-entity-decode
status: publish
title: UTF8 entity decode
wordpress_id: '65'
categories:
- PHP
---

Taken from PHP.net

if you get issues with quotes, wrap it in `htmlentities($text,ENT_QUOTES,'UTF-8')` on output.
{% codeblock lang:php %}
<?php
function utf8_replaceEntity($result){
    $value = (int)$result[1];
    $string = '';

    $len = round(pow($value,1/8));

    for($i=$len;$i>0;$i--){
        $part = ($value & (255>>2)) | pow(2,7);
        if ( $i == 1 ) $part |= 255<<(8-$len);
            $string = chr($part) . $string;
        $value >>= 6;
    }

    return $string;
}

function utf8_html_entity_decode($string){
    return preg_replace_callback(
        '/&#([0-9]+);/u',
        'utf8_replaceEntity',
        $string
    );
}

$string = '&#8217;&#8216; &#8211; &#8220;  &#8221;'
.'&#61607; &#263; &#324; &#345;';
$string = utf8_html_entity_decode($string,null,'UTF-8');
header('Content-Type: text/html; charset=UTF-8');
echo '<li>'.$string;
?>
{% endcodeblock %}