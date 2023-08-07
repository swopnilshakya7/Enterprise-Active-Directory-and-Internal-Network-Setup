<h2>Description</h2>
This project is a complete demonstration of Internal Network Setup in an enterprise with Active Directory Domain Services in a virtual lab setup. Where everything is described in detail to create versatile department and users within an organization based on its requriement and can be controlled via main domain server. With this setup, the machines in internal network can only visit the public internet via main domain controller of the organization which can be only governed by the admins based on their authorities and superadmin.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 


<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)
- <b>Windows Server 2019</b> (21H2)

<h2>Setup Walk Through</h2>

<p align="left">
Step 1: Virtual Box setup <br/>
First of all, for the required environment and number of devices and system we need to have, we need a virtual box where we will be able to setup our devices in the network. For that we are going to use virtual box Vmware.
Oracle VirtualBox: https://www.virtualbox.org/wiki/Downl…
<br />

<br />
Step 2: Getting things ready (Windows Server 2019) <br/>
So now we need to install a operating system of server, here we are going to use the windows server 2019 to setup our domain controller. 
For that, server can be found via this link: https://www.microsoft.com/en-us/evalc…
<br />

<br />
Step 3: Getting Machine ready for Windows Server 2019 <br/>
Now we should get our virtual box ready with a machine where we are going to install the windows server 2019 Operating System.
For that we need to go to the menu machine>new.
Put name of the machine: Domain Controller or DC.
Do not select your ISO yet. Just choose Other Windows (64-bit) in the version tab and click next.
<img src="https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/c9568fc9-a4db-4804-8913-0319c8d6955f"

<br />

Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
