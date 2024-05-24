FROM php:8.3-apache

ENV LANG=ja_JP.UTF-8
ENV LANGUAGE=ja_JP:ja
ENV LC_ALL=ja_JP.UTF-8

RUN mkdir -p /var/www/html/public

RUN apt update \
    && apt-get -y upgrade

RUN apt-get install -y \
    locales \
    bash-completion \
    curl \
    git \
    golang \
    libpq-dev \
    libssl-dev \
    libzip-dev \
    postgresql \
    sudo \
    vim \
    xsel \
    zip

RUN docker-php-ext-install -j$(nproc) \
    bcmath \
    opcache \
    pdo_pgsql \
    zip
RUN pecl install xdebug \
    && touch /var/log/xdebug.log \
    && chown www-data:www-data /var/log/xdebug.log
RUN curl -fsSL https://getcomposer.org/download/latest-2.x/composer.phar -o /usr/local/bin/composer \
    && chmod +x /usr/local/bin/composer \
    && composer self-update

RUN echo "ja_JP.UTF-8 UTF-8" > /etc/locale.gen && \
    locale-gen ja_JP.UTF-8

RUN a2enmod rewrite ssl
RUN ln -nfs /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-enabled/000-default.conf
RUN curl -sL https://deb.nodesource.com/setup_20.x | bash - \
    && apt install -y nodejs \
    && npm install -g npm

RUN curl https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash -o /etc/bash_completion.d/git-completion.bash -s \
    && echo . /etc/bash_completion >> /etc/bash.bashrc

RUN echo '%sudo   ALL=NOPASSWD:ALL' > /etc/sudoers.d/nopasswd
RUN echo "alias ll='ls $LS_OPTIONS -l'" > /etc/skel/.bash_aliases
RUN cp -r /etc/skel/. /root
RUN mkdir -p /home/www-data \
    && usermod -d /home/www-data www-data \
    && chsh -s /bin/bash www-data \
    && gpasswd -a www-data sudo \
    && cp -r /etc/skel/. /home/www-data \
    && chown -R www-data:www-data /home/www-data \
    && rm -rf /var/www/ \
    && mkdir -p /var/www

RUN mkdir -p /var/www/html/public \
    && chown -R www-data:www-data /var/www/html
