---
layout: post
title: Encounter with VPN
---


The reason behind developing this tool was to automate the process of connecting to VPN. My daily work required me to connect to a VPN, Cisco AnyConnect client was the obvious choice but I was facing some issues installing the same in ubuntu so instead I choosed openconnect. Using this I am able to connect to vpn via few mouse clicks.

## System Requirements ##

Currently I have tested this only on ubuntu 16.04, hopefully in coming days I will be adding installation instruction for other OS too.

## Installation ##

1. Install expect using this command: <code>sudo apt-get install expect</code>

2. Steps for installing openconnect: <br>
	1. First run command below to active th TUN module: <code>sudo /sbin/modprobe tun</code>
	2. Install OpenConnect: <code>sudo apt-get install openconnect</code>

3. Download this module and make openconnect script executable like this:
   <code>chmod +x /path/to/openconnect.sh</code>

4. Change these variables: *GATEWAY*, *UBUNTUPASSWORD*, *USERNAME*, *PASSWORD* present in script as per your environment.

5. Run the script like this:
	<code>./openconnect.sh</code>, this is when you are in the root directory of the module otherwise add path to your module.

6. Now we have to install Nautilus-Actions Configuration Tool, type this in the terminal:
	<code>sudo apt-get install nautilus-actions</code>

7. Launch the Nautilus-Actions Configuration Tool from the Dash after installing it.
![dash_nautilus](https://user-images.githubusercontent.com/5805013/27996398-f211eb8c-64fe-11e7-808a-2d617d1ebecd.png)

8. First, click the New Action button on the toolbar and type the name of your action into the Context Label box, may be something like this: *Connect to VPN*
![nautilus_action](https://user-images.githubusercontent.com/5805013/27996413-2dbe33c0-64ff-11e7-8c10-dc481a462898.png)

9. Click the Command tab and in Label box enter any suitable name like *VPN* and in Path box this: */usr/local/bin/vpn*
![nautilus_command](https://user-images.githubusercontent.com/5805013/27996416-3f203ab4-64ff-11e7-8907-8fc1f3fd7ffa.png)

10. Since we would need terminal for executing our newly created vpn command, in nautilus-actions tool, go to Edit > Preferences > Runtime Execution. In the "command pattern" field, enter: *gnome-terminal -x sh -c COMMAND*
![nautilus_preference](https://user-images.githubusercontent.com/5805013/27996420-4bf8911e-64ff-11e7-931d-9a3188cf2364.png)

11. Now we need to restart nautilus typing this command in the terminal: <code>nautilus -q</code>

12. After this you can access your newly created vpn command on right clicking under Nautilus-Actions actions.
![click_nautilus](https://user-images.githubusercontent.com/5805013/27996495-a177e27e-6500-11e7-8c80-23decaaf7619.png)

Happy browsing :smiley: