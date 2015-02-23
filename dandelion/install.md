---
layout: page-no-title
title: Dandelion - Install
permalink: /dandelion/install/
---

Installing Dandelion
--------------------

Automatic Configuration
-----------------------

Installing Dandelion is an easy and simple task. Just follow these steps and you'll be up and running in no time.

1. Grab a copy of Dandelion of Github.
2. Run ```composer install --no-dev``` from the root Dandelion directory. If you don't have Composer installed please see the [Getting Started](https://getcomposer.org/doc/00-intro.md#locally) guide. This will install PHP dependencies.
3. Run ```npm install``` and ```gulp```. This will compile the javascript and stylesheets.
4. Create a database in MySQL/MariaDB to house Dandelion.
5. Setup your web server to serve the ```public``` directory of Dandelion.
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

Sample Auto Install Commands (Ubuntu, Nginx)
--------------------------------------------

{% highlight bash %}
$ mkdir -p /var/www
$ cd /var/www
$ git clone https://github.com/dragonrider23/dandelion
$ cd dandelion
$ composer install --no-dev
$ npm install && gulp
$ cp app/install/Nginx-sample-config.conf /etc/nginx/sites-available/default
$ service nginx restart
{% endhighlight %}

Now browse to ```http://[dandelion hostname]/install.php``` to finish the installation.


Manual Configuration
--------------------

Sometimes we just want to do things ourselves. And that's fine! Here's the verbose way of installing Dandelion without using our install page.

1. Grab a copy of Dandelion off GitHub. Either via a source download from the web UI or from the git command.
2. Import the file ```base_MySQL_DB.sql``` under the app/install directory. Dandelion currently only supports MySQL/MariaDB. Supporting other databases is in the works.
3. Copy ```config.sample.php``` under app/config to ```config.php``` under the same folder. Use your favorite text editor (ie. Vim) and edit the configuration to fit your environment. The comments in the file explain what each setting is.
4. Run ```composer install --no-dev``` from the root Dandelion directory. If you don't have Composer installed please see the [Getting Started](https://getcomposer.org/doc/00-intro.md) guide.
5. Run ```npm install``` and ```gulp```. This will compile the javascript and stylesheets.
6. Setup your web server to use the public directory under Dandelion as its root. Under the app/install directory is a sample configuration for Nginx and Apache2. For apache, you will need to enable mod_rewrite and install the apache2 PHP5 module. For Nginx, you will need to install the php-fpm package.
7. Browse to your Dandelion install in a web browser and login with:

   ```
   Username: admin
   Password: admin
   ```

8. Dandelion will prompt you to change the password, change it to something you'll remember then relogin.
9. Congratulations! You've now installed Dandelion. Go and make your first log.

Sample Install Commands (Ubuntu, Nginx)
---------------------------------------

{% highlight bash %}
$ mkdir -p /var/www
$ cd /var/www
$ git clone https://github.com/dragonrider23/dandelion
$ cd dandelion
$ mysql -u [username] -p
mysql> CREATE DATABASE [some name];
mysql> exit;
$ mysql -u [username] -p [some name] < app/install/base_MySQL_DB.sql
$ cp app/config/config.sample.php app/config/config.php
$ vim app/config/config.php
$ composer install --no-dev
$ npm install && gulp
$ cp app/install/Nginx-sample-config.conf /etc/nginx/sites-available/default
$ service nginx restart
{% endhighlight %}
