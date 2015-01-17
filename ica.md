---
layout: page
title: Infrastructure Config Archive
permalink: /ica/
menutitle: ICA
---

Infrastructure Config Archive (ICA) is designed to solve the problem of keeping current backups of network infrustructure configurations. In my time as an IT employee, one thing I've noticed (and really we all know) is that keeping up with current documentation, configurations, and settings can be a very tedious and time consuming task. Too often to the point where nothing gets done anymore. And then trouble strikes. A power glitch fries a switch. A router decides it has become too old to carry on. And in setting up its replacement you realize the last config you had for it was from 4 months ago. ICA can fix that. By setting up and running ICA on a scheduled basis, weekly, bi-weekly, daily if you really need to, ICA can keep a backup of the most current configurations for your infrastructure. ICA can be easily expanded to accommodate multiple types of devices since it uses Expect underneath to handle the config grabbing. The default build supports Cisco (telnet or ssh) and Juniper (ssh-only).

* [Installation Instructions](/ica/install)
* [Configuration Documentation](/ica/config)
* [Using ICA](/ica/using)
