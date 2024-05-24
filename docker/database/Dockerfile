FROM postgres:latest

RUN apt update \
    && apt -y upgrade \
    && apt -y install \
    libonig-dev \
    libpq-dev \
    procps

RUN echo "alias ll='ls $LS_OPTIONS -l'" > /etc/skel/.bash_aliases
RUN localedef -i ja_JP -c -f UTF-8 -A /usr/share/locale/locale.alias ja_JP.UTF-8
