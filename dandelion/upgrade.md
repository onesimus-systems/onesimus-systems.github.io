---
layout: page-no-title
title: Dandelion - Upgrade
permalink: /dandelion/upgrade/
---

NOTICE
------

Upgrades are only possible starting with Dandelion version 6.0.0. Any patch update is simply extracting and replacing the files. Any minor/major version may require database upgrades.

Upgrading Dandelion
--------------------

Before upgrading, be sure to read all release notes for any new configuration options or requirement changes. If you're need to update between multiple minor or major versions, e.g. from 6.0 to 6.2 or 6.0 to 8.0, you MUST apply database changes in the correct order. If they are not applied correctly, the database could be put in an unusable state.

1. Move your existing Dandelion installation to a different directory. For example, rename it to `dandelion.bak`.
2. Extract the built release package to your preferred directory. There should now be a directory named `dandelion`.
3. Copy your configuration file from the old version to the new.
4. Make a backup of your Dandelion database. Seriously, do it.
5. Merge in the schema changes for the new version. SQL files are located under `app/install/upgrades`. Make sure to apply the updates in the correct order. If you're upgrading from 6.0 to 6.3, the updates for 6.1 and 6.2 must be applied first. Each update file assumes the last minor version was applied. Not all versions will have database changes. Just apply the available SQL files in their respective version order.
6. Assuming the database upgrades were successful, the upgrade is now complete.

Example
-------

{% highlight bash %}
$ cd /var/www
$ mv dandelion dandelion.old
$ wget [download url]
$ tar zvxf [downloaded file]
$ cp ./dandelion.old/app/config/config.php ./dandelion/app/config/config.php
$ cd ./dandelion/app/install/upgrades
$ mysqldump -u [username] -p [database] > dandelion-backup.sql
$ mysql -u [username] -p [database] < db_upgrade_mysql_[version].sql
{% endhighlight %}
