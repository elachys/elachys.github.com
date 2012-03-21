---
date: '2011-05-30 13:26:19'
layout: post
slug: sphinx-installation-usage
status: publish
title: Install, index and test Sphinx (search engine)
wordpress_id: '184'
categories:
- Linux
- MySQL
- PHP
---

## Installation


download and extract the source:
`wget http://sphinxsearch.com/files/sphinx-2.0.1-beta.tar.gz
tar xvzf sphinx-2.0.1-beta.tar.gz
`

Try and configure it (prefix is the path to install sphinx to)
`./configure --prefix=/usr/local/sphinx`
It will most likely error. In my case, i had to install the mysql-devel package, fix the problems and re-run configure until it works.

`make`
At this point, i got the error:
`... line 512: exec: g++: not found`
I took this to mean i didn't have g++ installed...
`yum install gcc gcc-c++ make`
Then install
`make install`


## Configuration


If you've installed to the same location as me, make the config file in:
`/usr/local/sphinx/etc/sphinx.conf`
I like to use the following config file here. It gives me all the basic options for all sites on the server, but also allows me to drop a per-site config file into the folder that will also be included.
`
#!/bin/bash`

`cat <<-EOL
indexer
{
mem_limit = 32M
}`

`searchd
{
# IP address to bind on
# optional, default is 0.0.0.0 (ie. listen on all interfaces)
#
# address                           	= 127.0.0.1
# address                           	= 192.168.0.1

# searchd TCP port number
# mandatory, default is 3312
port                        	= 3312

# log file, searchd run info is logged here
# optional, default is 'searchd.log'
log                                 	= /var/log/sphinx/searchd.log

# query log file, all search queries are logged here
# optional, default is empty (do not log queries)
query_log                   	= /var/log/sphinx/query.log

# client read timeout, seconds
# optional, default is 5
read_timeout        	= 5

# maximum amount of children to fork (concurrent searches to run)
# optional, default is 0 (unlimited)
max_children        	= 30

# PID file, searchd process ID file name
# mandatory
pid_file                    	= /var/log/sphinx/searchd.pid

# max amount of matches the daemon ever keeps in RAM, per-index
# WARNING, THERE'S ALSO PER-QUERY LIMIT, SEE SetLimits() API CALL
# default is 1000 (just like Google)
max_matches                 	= 100000

# seamless rotate, prevents rotate stalls if precaching huge datasets
# optional, default is 1
seamless_rotate     	= 1

# whether to forcibly preopen all indexes on startup
# optional, default is 0 (do not preopen)
preopen_indexes     	= 0

# whether to unlink .old index copies on succesful rotation.
# optional, default is 1 (do unlink)
unlink_old                  	= 1
workers = threads
}
EOL

find . -name '*.include' -exec bash {} \;`

In this example config, we'll be reading from a MySQL database . Note: sphinx also supports Postgres. Our catalog is called catalog :-) you should name it something different for each different "thing" you'll be indexing.
`
#!/bin/bash

cat <<-EOL
source catalog
{
type = mysql

sql_host = localhost
sql_user = dbuser
sql_pass = dbpassword
sql_db = dbtablename
sql_sock = /var/lib/mysql/mysql.sock
sql_port = 3306

# indexer query
# document_id MUST be the very first field
# document_id MUST be positive (non-zero, non-negative)
# document_id MUST fit into 32 bits
# document_id MUST be unique
sql_query = SELECT id,field1 FROM tablename;

#sql_group_column = query

# document info query
# ONLY used by search utility to display document information
# MUST be able to fetch document info by its id, therefore
# MUST contain '$id' macro
#
sql_query_info = SELECT * FROM tablename WHERE id=\$id

}

index catalog
{
source = catalog
path = /var/data/sphinx/catalog
morphology = stem_en

#min_word_len = 3
#min_prefix_len = 0
#min_infix_len = 3
}

EOL
`



## Indexing & Testing


Move to your config directory
`cd /usr/local/sphinx/etc`

Once everything is setup, you'll need to do an index of your data. Usually, the following command will do this:
`sudo /usr/local/sphinx/bin/indexer --all`
 You can then use the following to test (where your search term is "travel")
`/usr/local/sphinx/bin/search travel`
