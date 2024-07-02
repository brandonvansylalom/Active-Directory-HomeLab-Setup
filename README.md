<h1>Active Directory Home Lab Project - Setting up a basic home lab and adding users with PowerShell/h1>

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
After picking desktop, hit next accept the licensing agreement and select Drive 0 Partition 2, to start and install from scratch. Afterwards, the installation might take a minute so you'll need to wait a bit. 
<img src="https://imgur.com/xA3WQOV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once the installation finishes, you'll be a familiar black screen. DO NOT PRESS ANYTHING. Let the VM do its thing on its own; otherwise if you press any key it'll revert you to redo the process again.
<img src="https://imgur.com/KDICfLz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
You'll appear at Customize settings page for the admin credentials for the server. Set it to any password you want and can remember.
<img src="https://imgur.com/yPcLT3Q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
After setting up your admin credentials, you'll now be on the homepage. To login, the screenshot below has input keys shown as typically your live keyboard isn't connected to the VM and has specific ways to send inputs to the VM. Select "Send Ctrl+Alt+Del" on the input selections to unlock the page to enter your login info.
<img src="https://imgur.com/mhBcF6y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
