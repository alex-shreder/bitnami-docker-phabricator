FROM bitnami/oraclelinux-extras:7-r53
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages bzip2-libs cyrus-sasl-lib expat freetds freetype glibc gmp gnutls keyutils-libs krb5-libs libcom_err libcurl libffi libgcc libgcrypt libgpg-error libicu libidn libjpeg-turbo libmcrypt libpng libselinux libssh2 libstdc++ libtasn1 libtidy libxml2 libxslt ncurses-libs nettle nspr nss nss-softokn-freebl nss-util openldap openssl-libs p11-kit pcre postgresql-libs readline sqlite xz-libs zlib
RUN bitnami-pkg unpack apache-2.4.34-1 --checksum d06af72741b365147c39bb30ca9e1df1501d97c3c6a44b200e64c3c4eb7878f6
RUN bitnami-pkg unpack php-7.1.20-1 --checksum 453099c5c33e2d3f011ab61b7dc27e68e77063a80e6ce166a2ef26f73434ef62
RUN bitnami-pkg install mysql-client-10.1.34-0 --checksum 012f1f222898565b55f7d4522514c7c130d2bfe4c988754eed658ef6dafa980c
RUN bitnami-pkg install libphp-7.1.20-0 --checksum e6de4d5e2fc165cfa2c71c70826ca71bf60ed2816c2d1708fe0a4bd974d9e9cf
RUN bitnami-pkg install git-2.18.0-1 --checksum e09020e93542133c5f61daaa5a47bdcb94ec5303dd336ae05fa561729786284c
RUN bitnami-pkg unpack phabricator-2018.30.0-0 --checksum f486a0e11f917a558da62f30b62281da71b4314fd303c4bc42936e9e44af3b24

COPY rootfs /
ENV APACHE_HTTPS_PORT_NUMBER="443" \
    APACHE_HTTP_PORT_NUMBER="80" \
    BITNAMI_APP_NAME="phabricator" \
    BITNAMI_IMAGE_VERSION="2018.30.0-ol-7-r1" \
    MARIADB_HOST="mariadb" \
    MARIADB_PASSWORD="" \
    MARIADB_PORT_NUMBER="3306" \
    MARIADB_USER="root" \
    PATH="/opt/bitnami/apache/bin:/opt/bitnami/php/bin:/opt/bitnami/php/sbin:/opt/bitnami/mysql/bin:/opt/bitnami/git/bin:/opt/bitnami/arcanist/bin:/opt/bitnami/phabricator/bin:$PATH" \
    PHABRICATOR_ALTERNATE_FILE_DOMAIN="" \
    PHABRICATOR_EMAIL="user@example.com" \
    PHABRICATOR_FIRSTNAME="FirstName" \
    PHABRICATOR_HOST="127.0.0.1" \
    PHABRICATOR_LASTNAME="LastName" \
    PHABRICATOR_PASSWORD="bitnami1" \
    PHABRICATOR_USERNAME="user" \
    SMTP_HOST="" \
    SMTP_PASSWORD="" \
    SMTP_PORT="" \
    SMTP_PROTOCOL="" \
    SMTP_USER=""

EXPOSE 80 443

ENTRYPOINT ["/app-entrypoint.sh"]
CMD ["/run.sh"]
