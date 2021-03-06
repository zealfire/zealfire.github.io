---
layout: post
title: Encounter with VPN
---

<style>
.emoji-wrapper .emoji {
	display:inline;
	width:2%;
}
</style>
The reason behind developing <a href="https://github.com/zealfire/openconnect">this</a> project was to ease the process of connecting to VPN. In my daily work I constantly required a VPN connection, Cisco AnyConnect client was the obvious choice but because I was facing some issues installing the same in Ubuntu so instead I choose openconnect. After following below-mentioned step, I am now able to get connected to a VPN using few mouse clicks.

## System Requirements ##

Currently I have tested this only on ubuntu 16.04, hopefully, in coming days I will be adding installation instruction for other OS too.

## Installation ##

<p>Install expect using this command: <code>sudo apt-get install expect</code> </p>
<p>Steps for installing openconnect: <br>
	&nbsp;&nbsp;First run command below to active th TUN module: <code>sudo /sbin/modprobe tun</code> <br>
	&nbsp;&nbsp;Install OpenConnect: <code>sudo apt-get install openconnect</code>
</p>
<p>Download <a href="https://github.com/zealfire/openconnect">this</a> module and make openconnect script executable like this:
   <code>chmod +x /path/to/openconnect.sh</code>
</p>
<p>Change these variables: <i>GATEWAY</i>, <i>UBUNTUPASSWORD</i>, <i>USERNAME</i>, <i>PASSWORD</i> present in script (openconnect.sh) as per your environment. </p>
<p>Run the script like this:
	<code>./openconnect.sh</code>, this is when you are in the root directory of the module otherwise add path to your module.
</p>
<p>Now we have to install Nautilus-Actions Configuration Tool, type this in the terminal:
	<code>sudo apt-get install nautilus-actions</code>
</p>
<p>Launch the Nautilus-Actions Configuration Tool from the Dash after installing it.</p>
![dash_nautilus](https://user-images.githubusercontent.com/5805013/27996398-f211eb8c-64fe-11e7-808a-2d617d1ebecd.png)
<p>First, click the New Action button on the toolbar and type the name of your action into the Context Label box, may be something like this: <i>Connect to VPN</i></p>
![nautilus_action](https://user-images.githubusercontent.com/5805013/27996413-2dbe33c0-64ff-11e7-8c10-dc481a462898.png)
<p>Click the Command tab and in Label box enter any suitable name like <i>VPN</i> and in Path box this: <i>/usr/local/bin/vpn</i></p>
![nautilus_command](https://user-images.githubusercontent.com/5805013/27996416-3f203ab4-64ff-11e7-8907-8fc1f3fd7ffa.png)
<p>Since we would need terminal for executing our newly created vpn command, in nautilus-actions tool, go to Edit > Preferences > Runtime Execution. In the "command pattern" field, enter: <i>gnome-terminal -x sh -c COMMAND</i></p>
![nautilus_preference](https://user-images.githubusercontent.com/5805013/27996420-4bf8911e-64ff-11e7-931d-9a3188cf2364.png)
<p>Now we need to restart nautilus typing this command in the terminal: <code>nautilus -q</code></p>
<p>After this you can access your newly created vpn command on right clicking under Nautilus-Actions actions.</p>
![click_nautilus](https://user-images.githubusercontent.com/5805013/27996495-a177e27e-6500-11e7-8c80-23decaaf7619.png)

<a href="https://github.com/zealfire/openconnect">Link</a> to repo.
<strong>Happy browsing</strong> <span class="emoji-wrapper">:smiley:</span>