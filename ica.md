---
layout: page
title: Infrastructure Config Archive
permalink: /ica/
menutitle: ICA
---

Infrastructure Config Archive (ICA) is to solve the problem of keeping current backups of network infrustructure configurations. In my time as an IT employee, one thing I've noticed (and really we all know) is that keeping up with current documentation, configurations, and settings can be a very tedious and time consuming task. Too often to the point where nothing gets done anymore. And then trouble strikes. A power glitch fries a switch. A router decides it has become too old to carry on. And in setting up its replacement you realize the last config you had for it was from 4 months ago. ICA can fix that. By setting up and running ICA on a scheduled basis, weekly, bi-weekly, daily if you really need to, ICA can keep a backup of the most current configurations for your infrastructure. ICA can be easily expanded to accommodate multiple types of devices since it uses Expect underneath to handle the config grabbing. The default build supports Cisco (telnet or ssh) and Juniper (ssh-only). Just setup the application configuration, give it a device list, setup the cron job, and let it go.

Requirements:

- Ubuntu (or another Debian-based OS, may work with CentOS and derivatives but not tested)
- Expect
- TFTP Server
- Go v1.4+ (if compiling from source)

Installing From Precompiled Binaries (recommended):

1. Download the [gzipped archive](/content/ica/infra-config-archive-v1.2.0.tar.gz) (Ubuntu x64)
2. Unzip the archive
3. Run scripts/setup.sh as root. This will install expect and setup a TFTP server and icauser user account.
4. Copy sample-configuration.toml to configuration.toml
5. Edit the file with the appropiate settings
6. Run icaexec

{% highlight bash %}
wget http://onesimussystems.com/content/ica/infra-config-archive-v1.2.0.tar.gz
tar -xvfz infra-config-archive-v1.2.0.tar.gz
sudo ./scripts/setup.sh
cp sample-configuration.toml configuration.toml
vim configuration.toml
./icaexec
{% endhighlight %}

Installing From Source:

1. Get the source code
2. Compile with Go
3. Run scripts/setup.sh as root. This will install expect and setup a TFTP server and icauser user account.
4. Copy sample-configuration.toml to configuration.toml
5. Edit the file with the appropiate settings
6. Run executable from directory where you pulled/extracted the application

{% highlight bash %}
go get github.com/dragonrider23/infrastructure-config-archive
cd $GOPATH/src/github.com/dragonrider23/infrastructure-config-archive
go build
sudo ./scrips/setup.sh
cp sample-configuration.toml configuration.toml
vim configuration.toml
./infrastructure-config-archive
{% endhighlight %}

Setup Cron Job (to backup configs on a regular basis):

1. Run `crontab -e -u [user to run cron]`.
2. Add `0 5 * * 1 curl http://[hostname of ICA server]:[port]/api/runnow` to the bottom of the file.
3. Now this job will run at 5am on Sunday every week.

Setup Upstart Job (to manage frontend server as a service):

1. Copy upstart.conf to /etc/init/ica.conf
2. Edit /etc/init/ica.conf and make any appropiate settings such as user to run as, the folder containing the ICA executable, and the full path of the ICA executable
3. Run `start ica` to verify the job works. The Upstart job will start on boot and can be managed with `[start, stop, status] ica`.

The source code is available at: [github.com/dragonrider23/infrastructure-config-archive](https://github.com/dragonrider23/infrastructure-config-archive)
