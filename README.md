<h1>Active Directory Home Lab Project - Setting up a basic home lab with Windows, Windows Server 2016 and Active Directory Services</h1>

<h2>Description</h2>
This project(s) shows users how to start hands-on with Active Directory using virtualbox and installing Windows Server 2016. Knowing the basics of Active Directory is an important service within any IT environment to help simplify user profiles, data, assets and providing enhanced security within a Windows domained network. This is just the downloads initialization/start, with downloading the environments and configuring the virtual DC. More to follow after these steps below.

<br/>
<img src="https://imgur.com/yibftVW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<h2>Download the following:</h2>

- <b>https://www.virtualbox.org/wiki/Downloads (Download the VirtualBox 7.0.18 Oracle VM VirtualBox Extension Pack as well)
- <b>https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019
- <b>https://www.microsoft.com/en-us/software-download/windows10

<br />

<h2>Languages and Utilities Used</h2>

- <b>None yet but next project will incorporate PowerShell and scripts.
  
<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)
- <b>Windows Server 2016</b>
- <b>Oracle VirtualBox</b>
- <b>Windows 10 Image/ISO disc image file to load onto the virtualbox environment (https://www.microsoft.com/en-us/software-download/windows10)

<h2>Lab walk-through/details:</h2>

<p align="center">
Download all of the necessary environments for the lab listed above. <br/>

Launch virtualbox and create the VM for the Server 2019 computer for the domain controller (DC):  <br/>
<img src="https://imgur.com/J23hbye.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Set the RAM to 2048MB (2GB), keep it simple: <br/>
<img src="https://imgur.com/dxnBgr8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Keep the disc steps at the defaults:  <br/>
<img src="https://imgur.com/dG4IJk2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Continue and hit Finish. Your DC should have been created and will be ready to power on virtualbox, after making some more tweaks:  <br/>
<img src="https://imgur.com/OcDKlEw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Find Settings on the virtualbox, and make the changes below. Bidirectional will allow you to "drag and drop and copy and paste" between your virtual environment and your live environment, making it easier without the awkward pauses or barriers when working.  <br/>
<img src="https://imgur.com/Qgvk1Eo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Find System on your virtualbox panel and update your CPU cores as necessary. If you don't know/unsure, set it to 1 or 2 to be safe:  <br/>
<img src="https://imgur.com/5G997c9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Find Network on your virtualbox panel. We are wanting to create two NICs later, so setting up the network adapter is necessary. Set adapter 1 as NAT (your home/whatever internet you are using). Set adapter 2 as Internal network (the VM environment's network). Example of adapter tabs (pick and 1 and 2, set 1 as NAT and 2 and Internal network).  <br/>
<img src="https://imgur.com/vhG19OK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Start up the server and mount the Windows 10 ISO disc file that you downloaded from Microsoft. Afterwards, you should be here and select Standard Desktop Experience. If you pick the datacenter option, it'll be just CLI and not GUI which will be a little inconvenient to work with. <br/>
<img src="https://imgur.com/Jp4reyq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
After picking desktop, hit next accept the licensing agreement and select Drive 0 Partition 2, to start and install from scratch. Afterwards, the installation might take a minute so you'll need to wait a bit. <br/>
<img src="https://imgur.com/xA3WQOV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once the installation finishes, you'll be a familiar black screen. DO NOT PRESS ANYTHING. Let the VM do its thing on its own; otherwise if you press any key it'll revert you to redo the process again. <br/>
<img src="https://imgur.com/KDICfLz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
You'll appear at Customize settings page for the admin credentials for the server. Set it to any password you want and can remember. <br/>
<img src="https://imgur.com/yPcLT3Q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
After setting up your admin credentials, you'll now be on the homepage. To login, the screenshot below has input keys shown as typically your live keyboard isn't connected to the VM and has specific ways to send inputs to the VM. Select "Send Ctrl+Alt+Del" on the input selections to unlock the page to enter your login info. <br/>
<img src="https://imgur.com/mhBcF6y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Login and find Devices at the top of the Window page of the VM (Not in the VM, outside of it, as shown in the screenshot) and select "Insert Guests Addition CD image" <br/>
<img src="https://imgur.com/qm0ee3F.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Afterwards, go to File Explorer (yellow folder), This PC, and you'll see the Guests Addition program next to the local disk. Select it, find "VBox Windows Additions amd64." Run it, and hit next for everything. Install it, then at the last page, select "I want to reboot manuall later" and then SHUTDOWN your VM (bottom left of the desktop, Windows icon, select Shut down). Then power it back up. You will notice that there is last lag and the VM running can have it's windows adjusted and auto adjusted with the resolution. <br/>
<img src="https://imgur.com/AGCOYrw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now we will setup the IP addressing and identify which is which (internal vs. the actual internet we're using). Check each details of the adapter. Rename the one that has 169.x.x.x as Internal and rename the other one as Internet. <br/>
<img src="https://imgur.com/VITft3r.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Next, we will need to rename the PC. You can do so under Settings and About, shown below as reference. Name it DC so we know it as the domain controller. Then restart now, continue with unplanned. <br/>
<img src="https://imgur.com/dv34xwn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Earlier I forgot to point to assign the internal network a static IP address. Use the diagram (very top of the page) and assign the internal network a static ipv4 address. Reference below of how to navigate there. 
IP: 172.16.0.1
Mask: 255.255.255.0
Default: empty
DNS: 127.0.0.1 <br/>
<img src="https://imgur.com/AMa095m.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Next, we will install Active Directory Domain Services and setup a domain. <br/>
<img src="https://imgur.com/lt3aOtw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Hit Next for all selections/preset defaults. On Server Roles, check Active Directory Domain Services, then next all the way and install. <br/>
<img src="https://imgur.com/yv4dgs7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once done, go to the yellow flag, and hit promote. Add new Forest, name it whatever you want but mydomain.com helps for training/tutorials. <br/>
<img src="https://imgur.com/PyBBdwX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
After setting the Forest for your Domain, add your password on Domain Controller options. Then hit next all the way and hit Install once there.
<img src="https://imgur.com/xQFLxb7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
