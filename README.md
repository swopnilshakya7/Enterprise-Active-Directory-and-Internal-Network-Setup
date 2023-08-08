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

Now give base and processors as per your real system capabilities. For smooth operations, at least of 4 GB RAM is good (1024 MB *4 = 4096 MB) enough. With 4 processors.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/4421747c-b477-4c7b-bd6d-857b4c2a9777)


So, for good operation of the ISO, at least we need to assign 20 GB of our hard disk for the system. Now, next step is to configure the machine to install the operating system.

<br />


<br />
Right Click on the machine, go to setting then in general setting, go to advanced and make the sharing bidirectional so we will be able to interact with the OS of the machine in easier way.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/13a91be6-e1be-4d21-9201-194f4541d8e4)

<br />
And go to network, and provide two different NICs Network Interface Cards (adapters) for this machine.
Adapter 1: NAT (This is to connect the machine to public internet)
Adapter 2: Internal Network (So that this machine will be able to create a VPN inside to create an internal network).

<br />
Adapter 1: Internet

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/6c6a29ba-8c99-4577-91d7-191e4bc9d9e2)
<br/>
Adapter 2: Internal Network

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/a64ac4ab-3060-4996-b07f-fb16a7103e8c)

<br />
Step 5: Install the Windows Server 2019 Operating System in our machine.<br/>
For that, double click on the machine and then a window will popup, Select your ISO file from your computer and then install the Operating System in your virtual machine.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/43a48bfc-1ea0-4d8d-b69f-f8a5883e948c)

Press mount and retry boot, then let the system get setup with your choices of configurations. From the lists of windows server provided, select the Desktop Experience one.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/c7747282-1320-438b-82f7-03f314d80e46)

Choose custom installation, don’t go with the upgrade one.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/b53f4eae-659d-4768-ab89-cda201a7d0aa)

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/d0fbe299-271e-42cf-80a1-49a4e4ba6e6e)

Let the system do its work of installation.

Based on the choice and strength, then we need to put the password for the administrator account.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/24ffd309-5cdc-4141-92c9-e66389460c4a)

The system will get setup. Now we can login on the Operating System of Windows Server 2019

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/8d73d46d-a315-42b6-b8da-d2de19713413)

<br />

Step 6: Configuration of IP and Name of the Networks in the Windows Server <br />

So, as per the adapters present in the machine, the machine is going to have Network settings available, now here we are going to assign Ips on those adapters based on our requirement of this laboratory.

Go the network on the bottom right corner of the machine. Right click and select network and sharing. There if you are connected via Wifi you need to go the the configuration via Wifi otherwise via Ethernet based on your current setting.

Go to Related Settings and choose Change adapter options.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/aa7f28ab-9ad9-4e3b-b3ed-faba7a91fa2f)

We can see there are two network adapters where Ethernet is showing Unidentified Network and Ethernet 2 is showing Network.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/d26b09b7-41e2-47a5-8ace-e9d250e5d1ce)

Now, we should separate the duties of these adapters. One to connect to the public network and one for the internal network.
As, Ethernet 2 is showing the Network, lets see its properties and IP address. For that right click on it and click status>details.
We can see the proper home IP address there. I am not attaching the screenshot for security reasons. The main point is, Ethernet 2 adapter is connected to our main computer and getting internet network from there and its IP address has been assigned automatically.
So, we can rename these adapters for later use and flexibility as one Internet and the other is Internal Network.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/81fd1570-dc1c-4dff-9ad3-bfcd9e57de8a)

Now, we need to configure the IP address of the Internal Adapter so that we can make it the network controller for the machine in internal network. To configure its IP address, we are going to put the following setting on the _internal_ adapter.

IP: 172.16.0.1
Mask: 255.255.255.0
Gateway: <empty> (Because the Domain Controller itself is going to serve as a default gateway.)
DNS: 127.0.0.1 (this is a generic address that refers to myself.) If a machine ping this, its pinging itself. So, instead of this DNS, 172.16.0.1 is also okay. When we install the Active Directory in the system, it will automatically have the DNS so, the machine can call itself for any Domain Name System works.

For that, right click. Go to properties, double click on the ipv4 to change its setting. Choose Use the following IP address.
And put the above ones.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/10aae83c-e95b-40ce-9ae8-c4c34d3547f4)

Now save all the setting and we are going to change the name of the PC for easy usage. Right click start menu, go to system, then click on Rename this PC and write DC (Domain Controller) and restart the machine.

<br />
Step 7: Installation of Active Directory Domain Services ( AD DS) <br />

Go to the server manager dashboard, and as we are going to install the Active Directory Domain services which is a kind of feature, we need to click on the Add roles and feature option on the Dashboard.
Click Next Next and choose the server. We have named the server as DC. We can choose that where we are going to install the AD DS.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/795a2517-895c-4432-ab11-7dda301483ee)

In the next step, from the list of features that provided, choose Active Directory Domain Services and click on add feature.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/9212b7a8-6c4a-4be6-aa81-5d267115a101)

Make sure in the next step, Group Policy Management is Checked. Click next next and then install. 
So, now the Windows Server 2019 will have the feature of AD DS installed which we are going to use for the Active Directory works.

<br />
Step 8: Creating a Domain <br />

After the installation, the server dashboard will have a notification where we need to click and upgrade to the ADDS configuration wizard by creating a new domain.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/26455852-1664-473e-b886-5dda1a23b0fa)

Since, we are going to create a internal network of our devices which is a forest, we need to Add a new forest.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/cbb1cde5-2524-4cb0-8c7e-0c6286c1eb63)

Here, I gave the name of new domain as swopnildomain.com where we will be able to create users who are going to use this domain to belong to this forest of internal network. Give a good password for the creation on the next step.
I am using the password as: DomainServer7

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/bd02e96d-b6a1-4a7d-bef4-99a23d0805eb)

Click next, next and then install. We will get rebooted for the installation.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/d2568941-37f3-4a12-92b3-ad301ff637e7)



<br />

Step 9: Creating a User <br />
Creating a user (Admin : First user) of the domain.
To create a user, go to start menu> Windows Administrative Tools > Active Directory Users and Computers.

We will see our created domain. Now we can start creating a user by creating a unit or department first. For this one, we are going to create a unit/ department for admins. So, right click on the domain and then new and Organizational Unit.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/4c98414d-59cb-4242-8bd0-84ea5b879ace)

Name the unit as Admins. Then we will be able to see there will be a sub folder under Users which name is Admins.
Now simply right click on that sub folder> click new > click user.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/aec9b850-aef5-4728-864d-b6be9cd89fd6)

Now based on the naming convention, we can fill the blank form to input the information of user.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/8df64cf2-25e1-47e6-8db4-98e3f1c32ad3)

The user can be granted access for different activities based upon the company requirements. For this user password kept is: Server78

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/f0031b5a-bf1d-4d54-9a89-f766ceaff952)

After that we can see there is a user named as Ram Shakya under the Admins sub folder.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/5f50aafe-945a-4ef9-a0ca-c458c8f2bd69)

Now we need to make this user as the member of Domain Organizational department. For that right click on the user> click properties > choose member of > Click Add> write Admin Users and then click Apply. Okay.

Now we can test the account by rebooting the system to see if the user exist or not. And try logging in with the help of that created admin account. Because of our setting of changing the password on first login, we will need to change the password. For now new password that I have kept is: Server7.
So R.Shakya is the username and PW is Server7 which is an admin account and can successfully login to the server.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/1f41a4cb-bd89-4921-be59-62492cca573a)

<br/>

Step 10: Installation of RAS/ NAT />

This is for outside internet and insider internal network configuration for new machines who will be connected to the internal network and will use this server machine as a gateway to the internet.

So now, similarly as the installation of ADDS, we need to install Remote Access via the server manager dashboard to have RAS/ NAT.
RAS stands for Remote Access Services.
NAT stands for Network Address Translation.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/c46d48ab-2649-4685-a392-7d05687c2828)


Make sure to select Routing as that is the main purpose of this service installation.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/4087023b-bc3f-4f0d-9371-d579fe8c4b9b)


Carry on with next next and then install.

Now, we can see the service available. Go to Tools> Routing and remote access. Now we need to up our Domain Controller.



<br />
Step 11: Routing and Remote Access Configuration <br />

Right click on DC > configure and enable > Next Next and choose NAT (there’s written allows internal client to connect to the internet using one public IP address) .

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/b7f3e7d4-9ae5-404a-a8c0-2f3dd7bbd772)

Now here is the main part of selecting the Network Interface. We should be configuring the RAS in the Internet Network adapter that we set up on our server previously to make it functional as per our requirement.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/c2f109c8-c134-4d81-9e10-d17c57194c81)

Because we should be using the X_Internet_X to connect to the Internet. Click next and finish.


<br />

Step 12: Adding DHCP feature on the server <br />

So, as everything else is installed on the server, server also needs to have DHCP (Dynamic Host Control Protocol) , so that any machine on the internet will be able to automatically get the IP address from this server machine to connect to the internet via this gateway.

Now, to do that, just simply we need to do the installation like previously done from the Windows Server 2017 Dashboard.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/82d8108f-462e-494f-a936-241d39625d8b)


<br />
Step 13: Configuration of DHCP server (Defining the IP scope) <br />

Jus the way in remote access configuration, now we need to go to Tools, and choose DHCP.
Our settings for now:
Range 172.16.0.100-200 (creating for 100 machines)
Mask: 255.255.255.0
Gateway: 172.16.0.1 (This is the IP address of our server machine in the internal network adapter and it will server the entire machines in the internal network to connect to the internet. Such that, it is the default gateway).
DNS: 172.16.0.1 (This is also the IP address of our server where ADDS is installed so DNS is also installed. Such that all other computers in the internal network will be using this server for DNS services too.)

Mask length 24 with this addresses.

Right click on the IPv4 present under dc in DHCP> click New Scope> you can give the IP range as its name for better (we can put anything here). Start IP and End IP, length, mask as defined above.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/23967783-f5a3-48f4-92f3-f714f6b9a0a7)

Exclusion page (only if needed but our machine will have sufficient with this much of range. So click next on the next page. Lease Duration defines, how long a machine can hold the IP address. So based on the requirement of the organization, the time duration can be added.

For now, we are assuming as a 1 hour class for students, so we are giving two hours of lease of IP. So that, for another session we can free the Ips.

Now, check that admin is going to control and define the IP and DNS works for the clients. Heading to the next wizard, Now the IP address needs to be added. Here, for our internal network, the default gateway to the internet for the entire machines on internal network, it should be the server machine. So that will act as the router for everyone.

So, we need to put the IP address of the server machine which is 192.16.0.1 as the router address for the machines of internal network.


![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/edacd580-a6e4-43d8-9422-3c485d509b57)

Next> next> choose the router IP and I want to add the scope. Then finish.

Now to activate the scope and put IPv4 up, we have to right click on the dc server and authorize the DHCP and right click the IPv4 and refresh.


![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/c245fe3a-109c-4ff4-bcaa-98f291f48312)


<br />

Step 14: Creating a bunch of users using PowerShell Script and a text document with the list of names of the users. <br />


Power Shell script to create users:

# ----- Variables are editable based on requirements----- #
    $PASSWORD_FOR_USERS   = "Password1"
    $USER_FIRST_LAST_LIST = Get-Content .\namelist.txt
    # ------------------------------------------------------ #

    $password = ConvertTo-SecureString $PASSWORD_FOR_USERS -AsPlainText -Force
    New-ADOrganizationalUnit -Name _USERS -ProtectedFromAccidentalDeletion $false

    foreach ($n in $USER_FIRST_LAST_LIST) {
        $first = $n.Split(" ")[0].ToLower()
        $last = $n.Split(" ")[1].ToLower()
        $username = "$($first.Substring(0,1))$($last)".ToLower()
        Write-Host "Creating user: $($username)" -BackgroundColor Black -ForegroundColor Cyan
    
    New-AdUser -AccountPassword $password `
               -GivenName $first `
               -Surname $last `
               -DisplayName $username `
               -Name $username `
               -EmployeeID $username `
               -PasswordNeverExpires $true `
               -Path "ou=_USERS,$(([ADSI]`"").distinguishedName)" `
               -Enabled $true
    }


Here, this script is going to take name of users from the text name whose name is namelist.txt in the same folder. Everyone will have the password as “Password1” by default and the naming convention is First letter of First name followed by dot (.) and Last name/ Surname.

With the help of this script, we can create large number of users based on the requirement of an enterprise.

Now lets manually create a user with non admin privileges to login to another machine(client). So first get the machine ready with windows 10 Operating System on it.


<br />

Step 15: Getting new machine ready with Windows 10 (Client) <br />

Go to virtual box.> Machine > New then similar to before we need to create a machine with necessary setups of processor and RAM as per the capability of the system.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/3a73fcd1-ec2f-4b53-a621-e44c05854f4f)

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/cc6046be-70cd-4423-b0a2-dbed6bd75826)

Now configure the setting of the machine. Specially, for the network before the installation of Windows 10 Operating System on the machine.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/51bfd372-8ccb-430b-b16e-6ea7febe0be7)

Here, for the network adapter, Internal Network is used. Now once the machine is ready, lets install the Operating System.


<br />
Step 16: Installation of Windows 10 in client machine <br />


Double click the machine, choose the ISO file from your real machine location and go next to the setup.
Choose I don’t have a product key for now.
Choose windows 10 Pro, In home, the Domain Controller won’t work.
Let the setup to get completed.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/b8965aa5-bfbe-425b-8e3a-fedcb87cfb19)

Do not proceed with all the setups and experiences, just go with the limited experience option to not connect your online account/ outlook account for now.

After the installation of windows 10, go to cmd and type ipconfig to make sure that the client machine is in the internal network and using the ip address of our server machine as its default gateway/ router to the internet.


![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/8cfc3540-9372-4d73-b246-d6e1c6dc6f5f)


Here we can see that the DNS service has been taken from swopnildomain.com which we have setup for the internal network. Similarly, the machine got its IPv4 address automatically from the internal network which was supplied by the DHCP feature of the domain controller/ server machine as per the setup done before.


<br />

Step 17: Creating a general user in Domain Controller (Windows Server) Machine. <br />

Go to Admin account of Domain controller> click start menu > Windows Administrative Tools> Active Directory Users and Computers

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/84ab67c6-196d-4d42-b93c-5a64dbbd3912)

Then right click on the domain> New> Organizational Unit> General Users (anygroup name you want to create).
Right click on that created sub folder. Then New> User and fill the form like before we did.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/6ce455c0-ee90-4888-bd69-02998714f6e0)



<br />
Step 18: Joining the Client Machine in the work group of swopnildomain.com. <br />
This is being done, so that the windows 10 client can be logged in via the users that are created by the domain controller.

So for that, we go to rename this PC (advance). This setting is present just like before we did for the Domain Controller machine to change its name.

So go to start menu, right click on it, Go to system and then select Rename this PC (advance).

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/6d53c9d5-fdb7-42d5-b437-8db177d4987d)

Click on Change and name the windows 10 machine as Client1 and we need to make it a member of swopnildomain.com.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/bb82d84e-aba5-4714-bfe0-081cf0a7bfde)

Now after we press okay, we need to know the username and password of the admin account of swopnildomain.com.
In our case,
Username is R.shakya@swopnildomain.com
Pw is Server7

So lets use it here too.

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/322ae0b7-5d69-4262-8a5d-085a69e62b2c)


![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/a6243e3d-c99f-4449-bf7f-b208ff6b77de)


Now, we should reboot our system so that we can use the user we have created that can login even in this client computer.

Username: S.Shakya@swopnildomain.com
Password: Server7

![image](https://github.com/swopnilshakya7/Enterprise-Active-Directory-and-Internal-Network-Setup/assets/140642619/01ccc16f-6794-4206-8689-10b9afdce444)



You will be able to login. And for the first login, the windows will welcome you and will take some of time.

The whole lab is complete now.

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
