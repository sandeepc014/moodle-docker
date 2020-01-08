FROM ubuntu

MAINTAINER itadmin@linkstreet.in

RUN apt-get update -y\
    && apt-get dist-upgrade -y --no-install-recommends -o Dpkg::Options::="--force-confold" \
    && apt-get install --no-install-recommends --no-install-suggests -y \
        apt-utils locales software-properties-common \
    && locale-gen en_US.UTF-8 \
    && update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8 \
    && LC_ALL=C.UTF-8 add-apt-repository -y ppa:ondrej/php \
    && apt-get update --fix-missing \
    && apt-get update -y \ 
    && apt-get update --fix-missing \
    && apt-get update -y \
    && DEBIAN_FRONTEND=noninteractive apt install --no-install-recommends --no-install-suggests -y \
        curl git unzip ntp imagemagick file libfile-mimeinfo-perl \
        php7.3-fpm php7.3-cli php7.3-gd php7.3-curl php7.3-dev php7.3-mbstring php7.3-readline \
        php7.3-xml php7.3-json php7.3-zip php7.3-intl php7.3-bcmath php7.3-mysql php7.3-soap php7.3-xmlrpc \
        php-imagick git ssh vim \
    && mkdir -p /run/php \
    && apt remove -y apt-utils locales software-properties-common \
    && apt -y --purge autoremove \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && rm -rf /usr/lib/x86_64-linux-gnu/perl /usr/share/perl /usr/lib/x86_64-linux-gnu/libperl.* \
    && rm -rf /usr/share/{man,doc}

RUN sed -i "s/error_reporting = .*/error_reporting = E_ALL/" /etc/php/7.3/cli/php.ini \
    && sed -i "s/display_errors = .*/display_errors = On/" /etc/php/7.3/cli/php.ini \
    && sed -i "s/memory_limit = .*/memory_limit = 128M/" /etc/php/7.3/cli/php.ini \
    && sed -i "s/;date.timezone.*/date.timezone = UTC/" /etc/php/7.3/cli/php.ini \
    && sed -i "s/error_reporting = .*/error_reporting = E_ALL/" /etc/php/7.3/fpm/php.ini \
    && sed -i "s/display_errors = .*/display_errors = On/" /etc/php/7.3/fpm/php.ini \
    && sed -i "s/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/" /etc/php/7.3/fpm/php.ini \
    && sed -i "s/memory_limit = .*/memory_limit = 64M/" /etc/php/7.3/fpm/php.ini \
    && sed -i "s/upload_max_filesize = .*/upload_max_filesize = 100M/" /etc/php/7.3/fpm/php.ini \
    && sed -i "s/post_max_size = .*/post_max_size = 100M/" /etc/php/7.3/fpm/php.ini \
    && sed -i "s/;date.timezone.*/date.timezone = UTC/" /etc/php/7.3/fpm/php.ini \
    && sed -i "s/error_log = .*/error_log = \/proc\/self\/fd\/2/" /etc/php/7.3/fpm/php-fpm.conf \
    && sed -i "s/;daemonize = yes/daemonize = no/" /etc/php/7.3/fpm/php-fpm.conf \
    && sed -i "s/listen = .*/listen = [::]:9000/" /etc/php/7.3/fpm/pool.d/www.conf \
    && sed -i "s/;catch_workers_output = .*/catch_workers_output = yes/" /etc/php/7.3/fpm/pool.d/www.conf \
    && echo 'extension=mysqli' >> /etc/php/7.3/fpm/php.ini  \
    && echo 'xdebug.remote_port=9001' >> /etc/php/7.3/mods-available/xdebug.ini \
    && echo 'xdebug.remote_enable=1' >> /etc/php/7.3/mods-available/xdebug.ini \
    && echo 'xdebug.remote_connect_back=1' >> /etc/php/7.3/mods-available/xdebug.ini


WORKDIR /var/www/html

EXPOSE 9000

CMD ["php-fpm7.3"]
