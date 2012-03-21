---
date: '2011-04-18 09:33:20'
layout: post
slug: xhprof-setup-install
status: publish
title: Xhprof setup / install
wordpress_id: '150'
categories:
- PHP
---

XHProf is a tool released by facebook to help profile where you might have bottlenecks in your php applications.  
[XHProf usage instructions can be found here](http://mirror.facebook.net/facebook/xhprof/doc.html)


`sudo apt-get install php5-dev`


Pecl's version is very out of date, so compile from source after checking out with git.


`git clone https://github.com/facebook/xhprof.git xhprof
cd xhprof/
cd extension/
phpize
./configure
make
sudo make install`


Once you're done. Restart apache:


`sudo apache2ctl restart`


You'll need to set where xhprof stores it's output and include the extension in php


`vi /etc/php5/conf.d/xhprof.ini

[xhprof]
extension=xhprof.so
;
; directory used by default implementation of the iXHProfRuns
; interface (namely, the XHProfRuns_Default class) for storing
; XHProf runs.
;
xhprof.output_dir=/var/log/xhprof`


Then make the directory. You may also need to chmod it.


`sudo mkdir /var/log/xhprof`


## Trouble shooting




If you get the following error when running callgraph.php


`failed to execute cmd: " dot -Tpng". stderr: `sh: dot: not found`


You probably need to install graphviz


`sudo apt-get install graphviz`
