FROM php:7-fpm

RUN useradd -ms /bin/bash vagrant

# install Git
RUN apt-get update && apt-get install -y \
  curl \
  git \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libmcrypt-dev \
  libpng12-dev \
  unzip \
  zip \
  mysql-client \
  && docker-php-ext-install -j$(nproc) iconv mcrypt mysqli pdo_mysql opcache \
  && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
  && docker-php-ext-install -j$(nproc) gd

# Install composer
RUN apt-get update &&\
  curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install git-flow
RUN curl -OL https://raw.github.com/nvie/gitflow/develop/contrib/gitflow-installer.sh && \
  chmod +x gitflow-installer.sh && \
  ./gitflow-installer.sh

USER vagrant

WORKDIR /app/vdsmh.nl/

COPY php-fpm.conf /etc/php-fpm.conf


# Copy all user profile files to user-dir

COPY .bashrc /home/vagrant/
COPY .git-completion.bash /home/vagrant/
COPY .git-prompt.sh /home/vagrant/
COPY .gitconfig /home/vagrant/
COPY .gitignore /home/vagrant/



# Add new user with homedir and set a default shell
#RUN useradd --create-home --shell /bin/bash $user
# RUN echo $user:$passwd | chpasswd
