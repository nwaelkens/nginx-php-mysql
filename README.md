PHP7 - Mysql - NginX - Shell
=================

# Summary
Dockerized Development Environment. 

- PHP7\
  based on php:7-fpm\
  With OpCache, XDebug, Git, Composer, Curl, MySQL-client, ...
- NginX\
  based on nginx:latest
  With configfiles for Symfony or Sulu CMS
- MySQL\
  mysql:latest
  

# Description
Simple, but complete PHP development environment with as base principal: __nothing should be installed on the host__.
Basic dev tools are available in the PHP container. Your .ssh folder is made available in 
the PHP container through volume mapping. 
See the Basic Usage section. 

When using bash in a PHP container some great little tools are made available like GIT completion and the prompt known from debian distributions.

There's still a lot to add - which I'll do while using this DDE (Dockerized Development Environment). 
If you find any issues let me know through the issue tracker (https://github.com/nwaelkens/nginx-php-mysql/issues) or send me an e-mail (nathan@imigo.nl). 

# Basic usage

Every project (/.) has it's own development environment (/docker) and codebase (/app).   

/.\
/app\
/docker

### Start containers
To start the containers run from your projectroot: 

```
$ docker-compose build
$ docker-compose up -d
```

### Shell
To work on your projectfiles from a shell: 
```
$ docker-compose exec php bash
```

### nginx
The webserver will present your artwork by default on dev.project.org:80

### mysql
Use the 'docker-compose-key' as dbhost from within linked containers. Default DB settings are: 
- DBHost: db
- DBUser: root
- DBPass: changeme

Start the mysql-client from within the PHP container:
```
$ mysql -hdb -uroot -p
```
Start the mysql-client from your host machine:
```
$ docker-compose exec php mysql -hdb -uroot -p
```


# Before you start

- [ ] change your User Git name in docker/php/.gitconfig
- [ ] change your User Git email address in docker/php/.gitconfig
- [ ] change your Xdebug remote host IP address in docker/php/xdebug.ini
- [ ] Set up nginx: Choose between the default symfony.cms.conf of sylu.cms.conf configuration or add your own in docker/nginx/
 Make sure you copy the right configuration to your container by editing docker/nginx/Dockerfile
 At last, check the NginX server name and NginX root path in your NginX config file. You can use all the defaults if you like - but don't forget to add 127.0.0.1 dev.project.org to your /etc/hosts file.
- [ ] add your servername to your hostsfile: `127.0.0.1 dev.project.org` 