Docker Machine - Xampp - MariaDB - PHP 7

MariaDB/phpmyadmin - User: root - Password: 102030

Autor: Enio Marcelo Buzaneli - Email: eniomarcelo@gmail.com

Dockerfile

version: '2'

services:

  web:

  image: ebuzaneli/xampp_mysql_php7
    
    hostname: xampp-buzza
    container_name: xampp-buzza
    ports: 
      - "8080:80" 
      - "4443:443" 
      - "33306:3306" 
    volumes:
      - /Users/eniomarcelobuzaneli/Documents/Docker/xampp/www:/opt/lampp/htdocs
      - /Users/eniomarcelobuzaneli/Documents/Docker/xampp/php/php.ini:/opt/lampp/etc/php.ini
      - /Users/eniomarcelobuzaneli/Documents/Docker/xampp/phpmyadmin/config.inc.php:/opt/lampp/phpmyadmin/config.inc.php
      - /Users/eniomarcelobuzaneli/Documents/Docker/xampp/mysql:/opt/lampp/var/mysql
      - /Users/eniomarcelobuzaneli/Documents/Docker/xampp/apache2/conf/httpd.conf:/opt/lampp/apache2/conf/httpd.conf
      
      
    environment:
      - TZ=America/Curacao
    #links:
    #  - db
    #depends_on:
    #  - db
    restart: always
    networks:
      - buzza-xampp-network
      
      
networks:
  buzza-xampp-network:
    driver: bridge
