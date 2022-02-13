# SiteAdmin plugin for SvxLink

The **SiteAdmin** module is used for **EchoLink** node or repeater administration. It allows a registered and authenticated user to send predefined commands over radio to the node or repeater for predefined actions by using DTMF codes.

### Installation

Copy the following files to /etc/svxlink/svxlink.d (or the configuration folder that is defined in your SvxLink instalation):
*  **ModuleSiteAdmin.conf**

Copy the following files to /etc/svxlink/svxlink.d (or the configuration folder that is defined in your SvxLink instalation):
*  **SiteAdmin.conf**

Copy the following files to /usr/share/svxlink/events.d (or proper folder that is defined in your SvxLink instalation):
*  **SiteAdmin.tcl**

Copy the following files to /usr/share/svxlink/module.d (or proper folder that is defined in your SvxLink instalation):
*  **ModuleSiteAdmin.tcl**

Copy the SiteAdmin folder from soundfiles to /usr/share/svxlink/sounds into the proper language folder

The configuration of the allowed users and the defined commands can be found in the 
**/etc/svxlink/SiteAdmin.conf**

Users can be defined by the following format:
set users(001) "call=YO5VLZ,pass=123";
where **001** is the **user ID**, **call** is the **callsign** and the **pass** is the **password**

Commands ca be defined in the same file by the following format:
set commands(001) "description=Demo,command=/usr/bin/true";
where **001** is the **command ID** (that can be sent after loggin prefixing it with 22), **description** is the command description that will appear in logs and the **command** is the command that is linked to the defined ID.

Also if the commands need elevated privileges to be executed you need to define the proper setup in sudoers. An example can be found in the sudoers folder, example that is used for the commands included into the plugin (the file is called **70-svxlink-siteadmin**)

### Setup for sudoers for the commands that are included in the plugin

You need to copy the **70-svxlink-siteadmin** file from the sudoers folder to /etc/sudoers.d

## Commands predefined in the plugin

The following predefined commands are available:
when not logged in:
* **0** for hep and description

when logged in:
* **0** for logged in help
* **10** for powering off system
* **69** to restart SvxLink
* **73** to reboot the system
* **77** to stop SvxLink
* **87** to spell out OS, OS codename and OS version
* **88** to say local IP address

For all of sysop defined commands (that are not predefined commands by the plugin like those presented above) need to be prepend **22**.

All commands have to be ended with a #.

73, 
DE YO5VLZ
