FROM php:7-fpm

# create new useraccount
# -m: with homedir
# -s: define the name of the users login shell
# vagrant: just a name, has nothing to do Vagrant, the virtual machine provisioning software
# wait with running commands as vagrant though, let's run first commands with root privileges

RUN useradd -ms /bin/bash vagrant



# install packages and PHP extensions

RUN apt-get update && apt-get install -y \
  git \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libmcrypt-dev \
  libpng12-dev \
  mysql-client \
  unzip \
  vim \
  zip \
  && docker-php-ext-install -j$(nproc) iconv mcrypt mysqli pdo_mysql opcache \
  && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
  && docker-php-ext-install -j$(nproc) gd



# install composer

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer



# install git-flow

RUN curl -OL https://raw.github.com/nvie/gitflow/develop/contrib/gitflow-installer.sh && \
  chmod +x gitflow-installer.sh && \
  ./gitflow-installer.sh



# install XDebug

RUN pecl install xdebug
COPY xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini



# set php configuration by copying local .conf files

COPY php-fpm.conf /usr/local/etc/php-fpm.conf
COPY www.conf /usr/local/etc/php-fpm.d/www.conf
COPY php-cli.ini /usr/local/etc/php/conf.d/php-cli.ini


# continue as user vagrant

USER vagrant



# copy user profile files to userdir
# a collection of usefull scripts when working on the command line

COPY .bashrc /home/vagrant/
COPY .git-completion.bash /home/vagrant/
COPY .git-prompt.sh /home/vagrant/
COPY .gitconfig /home/vagrant/
COPY .gitignore /home/vagrant/
