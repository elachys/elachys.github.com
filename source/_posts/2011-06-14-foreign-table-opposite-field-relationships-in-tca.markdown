---
date: '2011-06-14 06:28:02'
layout: post
slug: foreign-table-opposite-field-relationships-in-tca
status: publish
title: Foreign table opposite field relationships in tca
wordpress_id: '250'
categories:
- typo3
---

I had a select box setup in my tca. But in the typo3 admin it always selected the first option.

You can fix this with `  'MM_opposite_field' => 'oppositetable_id'`

This causes typo3 to look for it's currently select option in your foreign table.
