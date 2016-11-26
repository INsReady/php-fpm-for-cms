# php-fpm-for-cms
Standalone PHP-FPM container with extensions installed for Drupal, Wordpress and Joomla

The reason to have this container image is because:

1. The offical PHP docker image doesn't have enough extensions for Drupal or WordPress
2. The offical Drupal or WordPress images are all-in-one style (Web server, PHP and CMS), which is not scalable.

This image contains:

* gd
* mbstring
* pdo
* pdo_mysql
* pdo_pgsql
* zip
* opcache
* imagemagick
* bcmath (required by Address or Commerce)
* phpredis
