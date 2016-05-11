---
layout: page-no-title
title: Dandelion - Install
permalink: /dandelion/install/
---

Installing Dandelion
--------------------

Requirements
------------

* Apache or Nginx web server
    - mod_rewrite must be enabled for Apache
* PHP >= 5.4.0
* MySQL/Maria DB

Dandelion has only been tested on Ubuntu with Apache and Nginx. Other combos may work but YMMV.

Install From Build - Easiest
----------------------------

Installing Dandelion is an easy and simple task. Just follow these steps and you'll be up and running in no time.

1. Download the latest version from the [Releases](https://github.com/onesimus-systems/dandelion/releases) page.
2. Extract the archive where ever you like
3. Create a database in MySQL/MariaDB to house Dandelion.
4. Setup your web server to use the public directory under Dandelion as its root. Under the app/install directory is a sample configuration for Nginx and Apache2. For apache, you will need to enable mod_rewrite and install the apache2 PHP5 module. For Nginx, you will need to install the php-fpm package.
5. Browse to ```http://[dandelion server]/install.php```.
6. Fill out the information, asterisks mark required fields.
7. Click Finish Install
8. If it was successful, you'll be redirected to the login page of Dandelion. Login with:

   ```
   Username: admin
   Password: admin
   ```

    and change the password when prompted.
9. Congratulations! You've now installed Dandelion. Go and make your first log.

Example (Ubuntu, Nginx):
------------------------

{% highlight bash %}
$ mkdir -p /var/www
$ cd /var/www
$ wget https://github.com/onesimus-systems/dandelion/releases/download/v6.0.3/dandelion-v6.0.3.tar.gz
$ tar zvxf dandelion-v6.0.3.tar.gz
$ [configure web server to serve the public directory]
{% endhighlight %}

Now browse to ```http://[dandelion hostname]/install.php``` to finish the installation.


Install From Source - Installer Page
------------------------------------

Installing Dandelion is an easy and simple task. Just follow these steps and you'll be up and running in no time.

1. Grab a copy of Dandelion of Github.
2. Run ```composer install --no-dev``` from the root Dandelion directory. If you don't have Composer installed please see the [Getting Started](https://getcomposer.org/doc/00-intro.md#locally) guide. This will install PHP dependencies.
3. Run ```npm install && ./node_modules/.bin/gulp```. This will compile the TypeScript and stylesheets.
4. Create a database in MySQL/MariaDB to house Dandelion.
5. Setup your web server to use the public directory under Dandelion as its root. Under the app/install directory is a sample configuration for Nginx and Apache2. For apache, you will need to enable mod_rewrite and install the apache2 PHP5 module. For Nginx, you will need to install the php-fpm package.
6. Browse to ```http://[dandelion server]/install.php```.
7. Fill out the information, astericks mark required fields.
8. Click Finish Install
9. If it was successful, you'll be redirected to the login page of Dandelion. Login with:

   ```
   Username: admin
   Password: admin
   ```

    and change the password when prompted.
10. Congratulations! You've now installed Dandelion. Go and make your first log.

Example (Ubuntu, Nginx):
------------------------

{% highlight bash %}
$ mkdir -p /var/www
$ cd /var/www
$ git clone https://github.com/onesimus-systems/dandelion
$ cd dandelion
$ git checkout tags/v6.0.3
$ composer install --no-dev
$ npm install && ./node_modules/.bin/gulp
$ cp app/install/Nginx-sample-config.conf /etc/nginx/sites-available/default
$ service nginx restart
{% endhighlight %}

Now browse to ```http://[dandelion hostname]/install.php``` to finish the installation.


Install From Source - Completely Manually
-----------------------------------------

Sometimes we just want to do things ourselves. And that's fine! Here's the verbose way of installing Dandelion without using our install page.

1. Grab a copy of Dandelion off GitHub. Either via a source download from the web UI or from the git command.
2. Import the file ```mysql_schema.sql``` located under the app/install directory into a database table. Dandelion currently only supports MySQL/MariaDB. Supporting other databases is in the works.
3. Copy ```config.sample.php``` under app/config to ```config.php``` under the same folder. Use your favorite text editor (ie. Vim) and edit the configuration to fit your environment. The comments in the file explain what each setting is. Also look at the ```config.defaults.php``` to see all available options. Don't change the defaults file, make any changes in your own config file.
4. Run ```composer install --no-dev``` from the root Dandelion directory. If you don't have Composer installed please see the [Getting Started](https://getcomposer.org/doc/00-intro.md) guide.
5. Run ```npm install && ./node_modules/.bin/gulp```. This will compile the javascript and stylesheets.
6. Setup your web server to use the public directory under Dandelion as its root. Under the app/install directory is a sample configuration for Nginx and Apache2. For apache, you will need to enable mod_rewrite and install the apache2 PHP5 module. For Nginx, you will need to install the php-fpm package.
7. Browse to your Dandelion install in a web browser and login with:

   ```
   Username: admin
   Password: admin
   ```

8. Dandelion will prompt you to change the password, change it to something you'll remember then login again.
9. Congratulations! You've now installed Dandelion. Go and make your first log.

Example (Ubuntu, Nginx):
------------------------

{% highlight bash %}
$ mkdir -p /var/www
$ cd /var/www
$ git clone https://github.com/onesimus-systems/dandelion
$ cd dandelion
$ git checkout tags/v6.0.3
$ mysql -u [username] -p
mysql> CREATE DATABASE [some name];
mysql> exit;
$ mysql -u [username] -p [some name] < app/install/mysql_schema.sql
$ cp app/config/config.sample.php app/config/config.php
$ vim app/config/config.php
$ composer install --no-dev
$ npm install && ./node_modules/.bin/gulp
$ cp app/install/Nginx-sample-config.conf /etc/nginx/sites-available/default
$ service nginx restart
{% endhighlight %}
