---
layout: page-no-title
title: Infrastructure Config Archive - How to Use
permalink: /ica/using/
---

Using ICA
---------

The First Run
-------------

Before you can fully utilize ICA you need to define you devices. In the web interface click on `Device List`. The default list is completely commented out. What you will need to do is delete the default lines and add your own devices. The format for the file is one device per line and the fields are separated by a double colon `::`. A device line consists of `device name::hostname::device type::method`. For full documentation on the device list file please see the [Configuration Documentation](/ica/config).

After you've added your devices click the save button. You will see an alert letting you know if the save was successful or not. Once you've saved the definitions, go to the `Status` page and click `Run Archive Job`. This will get the config of your entire device list.

Once the job is done (the progress bar will be green and the status will be Idle), click on `Archive` to see the latest configs from your devices. And that's it!

Getting Configs
---------------

There are three ways to get a config from a device.

1. **A full run job.** This is where you click `Run Archive Job` on the status page. It will collect the configs for all your devices.
2. **Single config for existing device.** If your device's config was updated and is already in the archive list, you can click the New Config button next to the device on the Archive page to download that single device's config.
3. **Manually run a device.** On the Status page there's a form where you can input the details of a device and run the config manually. You can do this after adding it to the device list but don't want to run a full job.
