---
layout: page
title: Infrastructure Config Archive - Install
permalink: /ica/install/
---

Requirements:

- Linux (tested on Ubuntu, Debian derivatives should be fine, CentOS/Red Hat should work but not tested)
- Expect
- Go v1.4+ (if compiling from source)

Installing from Debian Package (recommended)
--------------------------------------------

1. Download the appropiate .deb for your architecture from the [GitHub Release](https://github.com/dragonrider23/infrastructure-config-archive/releases/tag/v2.0.0)
2. Install the .deb file
3. Edit /opt/icarchive/config/configuration.toml to fit your environment
4. Restart icarchive service

Example for 64-bit:
{% highlight bash %}
wget https://github.com/dragonrider23/infrastructure-config-archive/releases/download/v2.0.0/infra-config-archive-v2.0.0-linux-x64.deb
dpkg -i infra-config-archive-v2.0.0-linux-x64.deb
vim /opt/icarchive/config/configuration.toml
service icarchive restart
{% endhighlight %}

Installing from Tarball
-----------------------

1. Download the appropiate .tar.gz for your architecture from the [GitHub Release](https://github.com/dragonrider23/infrastructure-config-archive/releases/tag/v2.0.0)
2. Untar the folder to an appropiate directory
3. Copy config/sample-configuration.toml to config/configuration.toml
3. Edit the configuration to fit your environment
4. Run the icaexec executable

Example for 64-bit:
{% highlight bash %}
mkdir ica && cd ica
wget https://github.com/dragonrider23/infrastructure-config-archive/releases/download/v2.0.0/infra-config-archive-v2.0.0-linux-x64.tar.gz
tar zvxf infra-config-archive-v2.0.0-linux-x64.tar.gz
cp config/sample-configuration.toml config/configuration.toml
vim config/configuration.toml
./icaexec
{% endhighlight %}

Installing from Source
----------------------

1. Get the [source code](http://github.com/dragonrider23/infrastructure-config-archive)
2. Compile with Go
3. Copy config/sample-configuration.toml to config/configuration.toml
3. Edit the configuration to fit your environment
4. Run the icaexec executable

{% highlight bash %}
go get github.com/dragonrider23/infrastructure-config-archive
cd $GOPATH/src/github.com/dragonrider23/infrastructure-config-archive
go build -o icaexec
cp config/sample-configuration.toml config/configuration.toml
vim config/configuration.toml
./icaexec
{% endhighlight %}

Setup Cron Job
--------------

1. Run `crontab -e -u [user to run cron]`.
2. Add `0 5 * * 1 curl http://[hostname of ICA server]:[port]/api/runnow` to the bottom of the file.
3. Now this job will run at 5am on Sunday every week.

Setup Upstart Job
-----------------

If you installed ICA with the debian package, this as already been setup for you.

1. Copy upstart.conf to /etc/init/ica.conf
2. Edit /etc/init/ica.conf and make any appropiate settings such as user to run as, the folder containing the ICA executable, and the full path of the ICA executable
3. Run `start ica` to verify the job works. The Upstart job will start on boot and can be managed with `[start, stop, status] ica`.

The source code is available at: [github.com/dragonrider23/infrastructure-config-archive](https://github.com/dragonrider23/infrastructure-config-archive)
