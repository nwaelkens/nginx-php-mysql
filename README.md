PHP7 - Mysql - NginX - Shell
=================


## Summary
Dockerized Development Environment containing: 

- PHP7\
  based on php:7-fpm\
  With OpCache, XDebug, Curl  
- NginX - based on nginx:latest
- MySQL - mysql:latest


## Description
Complete PHP developmentenvironment with as base principal: besides Docker, nothing should be installed on the host.
Git, composer, vim, etc are all present in a dedicated shell-container.


Mention
SSH env available in containers
GIT completion
Nice PROMPT



## Basic usage

@ToDo



## Details

### Variables to think about ###
Git Name
Git Email
Xdebug host IP address
NginX server name
NginX root path
Which www-pool configuration do you want to use: Symony's of Sulu's?
Optional: Database name


### opcache ###

@ToDo



### xdebug

Using XDebug and Opcache together note that XDebug needs to be loaded last
You can check this with php -v

$ php -v
PHP 7.1.5 (cli) (built: Jun  2 2017 19:54:52) ( NTS )
Copyright (c) 1997-2017 The PHP Group
Zend Engine v3.1.0, Copyright (c) 1998-2017 Zend Technologies
    with Zend OPcache v7.1.5, Copyright (c) 1999-2017, by Zend Technologies
    with Xdebug v2.5.5, Copyright (c) 2002-2017, by Derick Rethans

;xdebug.remote_host = 192.168.1.143
xdebug.remote_host = 192.168.178.69

fastcgi_read_timeout set to 1 hour


### performance ngingx and php-fpm

See: https://tweaked.io/guide/nginx/




