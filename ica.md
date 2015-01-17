---
layout: page
title: Infrastructure Config Archive
permalink: /ica/
menutitle: ICA
---

Infrastructure Config Archive (ICA) is designed to solve the problem of keeping current backups of network infrustructure configurations. In my time as an IT employee, one thing I've noticed (and really we all know) is that keeping up with current documentation, configurations, and settings can be a very tedious and time consuming task. Too often to the point where nothing gets done anymore. And then trouble strikes. A power glitch fries a switch. A router decides it has become too old to carry on. And in setting up its replacement you realize the last config you had for it was from 4 months ago. ICA can fix that. By setting up and running ICA on a scheduled basis, weekly, bi-weekly, daily if you really need to, ICA can keep a backup of the most current configurations for your infrastructure. ICA can be easily expanded to accommodate multiple types of devices since it uses Expect underneath to handle the config grabbing. The default build supports Cisco (telnet or ssh) and Juniper (ssh-only).

Requirements:

- Linux (tested on Ubuntu, Debian derivatives should be fine, CentOS/Red Hat should work but not tested)
- Expect
- Go v1.4+ (if compiling from source)

[Configuration Documentation](/ica/config)

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
