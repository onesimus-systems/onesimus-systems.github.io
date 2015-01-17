---
layout: page
title: Infrastructure Config Archive - Configure
permalink: /ica/config/
---

Configuring Infrastructure Config Archive (ICA) is simple. All configuration files are located in the config directory. Using the debian package installer the location would be `/opt/icarchive/config`.

Main Application Configuration
------------------------------

The main application configuration is named `configuration.toml`. Here's the sample configuration:

<pre>
RemoteUsername = ""
RemotePassword = ""
EnablePassword = ""
DeviceListFile = "config/device-definitions.conf"
DeviceTypeFile = "config/device-types.conf"
FullConfDir    = "latest"
MaxSimultaneousConn = 100

[server]
BindAddress = ""
BindPort = 8080
</pre>

Fields:

- **RemoteUsername** - The username used to login to remote devices.
- **RemotePassword** - The password for the account used to login to remote devices.
- **EnablePassword** - This is used for Cisco network devices if the RemoteUsername doesn't automatically go to Enable mode
- **DeviceListFile** - The filename for the device definitions file relative to the root application folder.
- **DeviceTypeFile** - The filename for the device type definitions file relative to the root application folder.
- **FullConfDir**    - The directory where the latest configurations should be stored.
- **MaxSimultaneousConn** - The maximum number of configurations to run in parallel. If this number is set too low, it will take considerably longer for a full run to finish. If you have a lot of devices it may be wise to set this such that the server doesn't use too many connections at the same time.

**[server]** - Configuration for the HTTP server

- **BindAddress** - The network address the HTTP server should bind to. If left blank, it will be accessable on all IP addresses assigned to the server.
- **BindPort** - The port that the HTTP server will be available. If you set this to the common HTTP port 80, you will need to run ICA as root or give the running user permission to bind to common ports.

Device Definitions File
-----------------------

Located in `device-definitions.conf`. Example:

<pre>
# This is a comment
Foo::192.168.0.1::cisco::telnet
Bar::192.168.0.2::cisco::ssh
FooBar::192.168.0.3::juniper::ssh
</pre>

The device definitions file (DTF) is used to define the devices that will be managed with ICA. The fields are separated by a double colon `::` and consist of `device name::hostname::device type::method`. Comments may be added by starting a line with a "#". Comments MUST be on a new line.

Fields:

- **device name** - Name of the device
- **hostname** - Hostname or IP address of device
- **device type** - Device type
- **method** - Device type method used

Device Type Definitions File
----------------------------

Located in `device-types.conf`. Default file:

<pre>
# This is a comment
cisco::ssh::cisco-ssh-config-grab.exp::$address,$username,$password,$logfile,$enablepw
cisco::telnet::cisco-telnet-config-grab.exp::$address,$username,$password,$logfile,$enablepw
juniper::ssh::juniper-ssh-config-grab.exp::$address,$username,$password,$logfile
</pre>

The device type definitions file (DTTF) is used to define the device types, methods, and the script file to run for them. Default types are cisco (methods ssh, telnet) and juniper (method ssh). The method does not need to be the actual protocol used to communicate with the device. It's simply used to distinguish one device type from another within the same family (cisco). The fields are separated by a double colon `::` and consist of `type name::method::script filename::arguments to script`. Comments may be added by starting a line with a "#". Comments MUST be on a new line.

Fields:

- **type name** - The name for the device type family (cisco, juniper)
- **method** - The name for the method, subdividing type families for organization (ssh, telnet)
- **script filename** - The name of the script to run. All scripts must be located under the `scripts` directory. From the debian installer this would be `/opt/icarchive/scripts`. The script file must be executable. It may use any shell available on the system.
- **arguments** - Arguments are comma separated fields that will be passed to the script as command line arguments in order.

Available Arguments:

- **$address** - The address of the device as defined in config.DeviceListFile.
- **$username** - The username as defined in the application configuration.
- **$password** - The password as defined in the application configuration.
- **$logfile** - The file that the script to write to. The script is responsible for outputting stdout to a file.
- **$enablepw** - The enable password for Cisco devices as defined in the application configuration
