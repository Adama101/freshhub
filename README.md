# <p align="center"> Fresh Hub MARKETPLACE</p> 

> ### Fresh Hub is a fully open-source eCommerce platform that is customizable and configurable to your needs.

> ##### This repository is functionality complete. Pull requests and issues are welcome!
----------

- [ Fresh Hub MARKETPLACE](#-Fresh Hub-marketplace)
- [About](#about)
- [Features](#features)
- [Requirements](#requirements)
- [ Easy Installation ](#-easy-installation-)
  - [Install Project using Git](#install-project-using-git)
  - [laragon user configuration](#laragon-user-configuration)
    - [Site URL Shoud Be Like](#site-url-shoud-be-like)
    - [Default Users](#default-users)
- [ Server Setup ](#-server-setup-)
  - [Linux Server Setup For Production Deployment](#linux-server-setup-for-production-deployment)
      - [install apache server](#install-apache-server)
      - [checking your Apache configuration for syntax errors:](#checking-your-apache-configuration-for-syntax-errors)
    - [Install MySQL](#install-mysql)
    - [PHP 8 Install](#php-8-install)
    - [Restart Apache](#restart-apache)
    - [Composer Install](#composer-install)
    - [Apache Config and  virtual hosts](#apache-config-and--virtual-hosts)
    - [copy the virtual config](#copy-the-virtual-config)
  - [Windows Server Setup For Local Deployment](#windows-server-setup-for-local-deployment)
    - [Composer Install](#composer-install-1)
  - [ Compatibility and Upgrade Information ](#-compatibility-and-upgrade-information-)
    - [Upgrading to Laravel 8 \& PHP 8](#upgrading-to-laravel-8--php-8)
    - [System Requirements](#system-requirements)
    - [Required PHP Extensions](#required-php-extensions)
          - [Ensure the following PHP extensions are installed and enabled:](#ensure-the-following-php-extensions-are-installed-and-enabled)
    - [Licensing \& Copyright](#licensing--copyright)


# About
Fresh Hub is a fully open-source eCommerce platform that is customizable and configurable to your needs. It is completely free, adaptable and open to be supported by a worldwide community of volunteers and contributors. It’s free and open source nature allows users to maintain complete control of the data content and modify it as they wish and according to their needs. Our intended goal is to allow any potential entrepreneur to quickly get up and running with an online platform to sell goods online. 
Some key features of Marketplace include:


-   Showcase digital and physical goods in categories, sorting by brands
-   Multi-vendor support with management tools and configuration
-   Modular product blocks allow you to customize pages in minutes.
-   Built in campaign tools to allow for promotions and sales
-   SEO configuration input simplified to boost page rank in search results
-   Admin dashboard to import and export items in bulk
-   Inventory management
-   Multi-user access
-   Ticket based support system
-   Social media integration
-   Multiple payment integration supported
-   Privacy preserving with limited or no 3rd party data tracking

Our platform is open to modifications by developers by its open source nature. With this in mid, the platform is built with the best standards and practices to ensure ease with expanding the code base and making it scalable. Learn more by exploring the documentation or seeing the code in the Github repository.  


# Features
- [Merchant Features](https://github.com/a2i-dpg/Fresh Hub-doc/blob/master/merchant/MerchantFeatures.md)
- [Admin Features](https://github.com/a2i-dpg/Fresh Hub-doc/blob/master/admin/AdminFeature.md)
- [Marketing Features](https://github.com/a2i-dpg/Fresh Hub-doc/blob/master/admin/MarketingFeature.md)
- [Product Features](https://github.com/a2i-dpg/Fresh Hub-doc//blob/masteradmin/ProductFeature.md)
- [Checkout Process](https://github.com/a2i-dpg/Fresh Hub-doc/blob/master/marketplace/CheckoutProcess.md)


# Requirements
- Ubuntu Server
- Apache
- PHP 8
- Laravel 8.0
- MySQL 
or  
- MariaDB


# <p align="center"> Easy Installation </p>

## Install Project using Git

```shell
    #1st need to update composer itself
    composer self-update
    
    git clone https://github.com/a2i-dpg/Fresh Hub.git

    import database (find DB in database folder)
    cp .env.example .env
    
    composer install
    php artisan storage:link
    php artisan key:generate
    php artisan passport:install --force
```

## laragon user configuration
- right click on the laragon window:
    - go to Apache > sites-enabled >  {eksho-dpg.test}.conf =>
    - remove '/public' from "define ROOT "D:/laragon/www/Fresh Hub-dpg-latest/public"
    - *Resstart Laragon

### Site URL Shoud Be Like
- http://localhost/project_folder  
or
- http://www.dummy-host.com (FOr Real Domain Address)
or
- http://Fresh Hub-dpg.test (For Laragon User)




### Default Users

#Login as an Admin
Username: admin@admin.com
Password: 123456

#Login as a Customer
Username: customer@example.com
Password: 123456

#Login as a Seller
Username: seller@example.com
Password: 123456




# <p align="center"> Server Setup </p>

## Linux Server Setup For Production Deployment

<hr /> <br />

```shell
sudo apt-get update
```

#### install apache server
```shell
sudo apt-get install apache2
```

#### checking your Apache configuration for syntax errors:
```shell
sudo apache2ctl configtest
```

<!-- ### Install Db
```shell
sudo apt install mariadb-server
mysql_secure_installation
GRANT ALL ON *.* TO 'admin'@'localhost' IDENTIFIED BY 'password' WITH GRANT OPTION;
``` -->

### Install MySQL
```shell
sudo apt update
sudo apt install mysql-client mysql-server
sudo mysql_secure_installation

CREATE DATABASE laravel;
mysql -u root -p
CREATE USER 'laravel'@'localhost' IDENTIFIED BY 'secret';
GRANT ALL ON laravel.* to 'laravel'@'localhost';
FLUSH PRIVILEGES;
quit
```

### PHP 8 Install
```shell
sudo apt -y install php8

sudo apt-get install -y php8-cli php8-json php8-common php8-mysql php8-zip php8-gd php8-mbstring php8-curl php8-xml php8-bcmath

sudo apt-get install php8-mysqli

php -v
```

### Restart Apache
```shell
sudo service apache2 restart
```

### Composer Install 

Once php installed, need to install composer if not installed on machine. To install composer please follow following steps. [Reference link](https://getcomposer.org/download/)

```shell
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === '55ce33d7678c5a611085589f1f3ddf8b3c52d662cd01d4ba75c0ee0459970c2200a51f492d557530c71c15d8dba01eae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"

sudo mv composer.phar /usr/local/bin/composer

composer -v
```

### Apache Config and  virtual hosts
```shell
    <Directory "/var/www/html">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
```

### copy the virtual config
```shell
vi [Real Domain Address or Dummy Domain Address Like (www.dummy-host.com)].conf
```

```shell
    <VirtualHost *:80>
        ServerName [Real Domain Address or Dummy Domain Address Like (www.dummy-host.com)]
        ServerAdmin webmaster@[Real Domain Address or Dummy Domain Address Like (www.dummy-host.com)]
        DocumentRoot /var/www/html

        <Directory /var/www/html>
            AllowOverride All
        </Directory>

        ErrorLog /var/www/html/error.log
        CustomLog /var/www/html/access.log combined
    </VirtualHost>
```

```shell
sudo a2dissite 000-default.conf
sudo a2ensite [Real Domain Address or Dummy Domain Address Like (www.dummy-host.com)]
sudo a2enmod rewrite
sudo systemctl restart apache2
```


## Windows Server Setup For Local Deployment
<hr /> <br />


Use XAMPP or WAMP, if use XAMPP (PHP development environment) for installing php and Mysql or MariaDB server in windows local machine, for this case download xampp version (7.3 / PHP 7.3) in c drive.

Once installed xapmm, update configure apache server if needed, in this case go to C:\xampp\php\php.ini and extend limit max_execution_time = 10000 , max_input_time = 10000, memory_limit = 2048M, post_max_size = 2048M, upload_max_filesize = 2048M .


### Composer Install
Once XAMPP installed successfully, need to install composer if not installed on machine. To install composer please follow following steps. [Download link](https://getcomposer.org/download/)

Download and run Composer-Setup.exe - it will install the latest composer version whenever it is executed.
Once downloaded composer.exe, install this file and use command line path (C:\xampp\php\php.exe)

Now open the xampp server then run Apache and MySQL service.

Project folder path should be C:\xampp\htdocs 

To check composer version run this command into cli

```shell
composer -v
```


## <p align="center"> Compatibility and Upgrade Information </p>

### Upgrading to Laravel 8 & PHP 8
This version of Fresh Hub has been upgraded to utilize the features and improvements offered by Laravel 8 and PHP 8. Below are key considerations and steps to ensure compatibility and optimal functionality:

### System Requirements
- PHP: Version 8.0 or greater.
- Web Server: Apache or Nginx with PHP 8 support.
- Database: MySQL 8.0 or MariaDB 10.4.22.
- Composer: Ensure you have the latest version installed.

### Required PHP Extensions
###### Ensure the following PHP extensions are installed and enabled:

- json
- pdo_mysql
- mbstring
- curl
- xml
- bcmath
- gd
- zip

These can typically be installed via your operating system’s package manager. For Ubuntu, you would use:

```shell
    sudo apt-get install php8.0-json php8.0-mbstring php8.0-curl php8.0-xml php8.0-bcmath php8.0-gd php8.0-zip
```


### Licensing & Copyright
Copyright 2024 @a2i, Bangladesh

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
