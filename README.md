**Project: Active Directory - Emulate a Corporate Network**
------------------------------------------------------------------------------------------------------------------
Summary of Activities:

**Network Diagram**: Created a network diagram outlining the infrastructure for the network environment.

**Server Setup**: Installed and configured Windows Server 2019 on VirtualBox, establishing the initial network setup to support Active Directory services.

**Active Directory Deployment**: Installed and configured Active Directory Domain Services (AD DS) on the designated Domain Controller.

**Forest Creation**: Added and deployed a new forest within the Active Directory environment.

**Organizational Unit and Domain Admin Setu**p: Created a new Organizational Unit (OU), established a designated folder, and configured the first Domain Admin account with appropriate administrative roles.

**NAT Configuration**: Implemented Network Address Translation (NAT) to facilitate external network communication for the simulated corporate network.

**DHCP Installation and Configuration**: Installed and configured DHCP services, defining IP address ranges and lease durations for dynamic network assignment.

**Client Virtual Machine Setup**: Deployed a client computer as a Virtual Machine (VM) to test the functionality of the DHCP service within the network environment.

**Domain Join via PowerShell**: Utilized PowerShell scripts to join a Windows 10 client computer to the Active Directory domain seamlessly.

**Network Testing**: Conducted comprehensive testing to ensure both the server and client machines within the network environment were operational and functioning correctly.

These activities were undertaken to emulate and simulate key functionalities of a corporate network environment
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Creatd network diagram outlining the infrastructure for the network environment.
I Will conduct the lab to achieve the goal of establishing the below network architecture as per my design.
 

![image](https://github.com/nahid7474/AD/assets/170605912/d12fdf65-2f65-4c02-acae-1211030ec6c3)

**Server Installation**: 
First, I have downloaded the windows server 2019 standard version and added that as a new VM it on my Oracle Virtual box.


![image](https://github.com/nahid7474/AD/assets/170605912/34207793-f849-4f5a-8d7e-7109a15665f3)

System: 8 GB RAM, 3 CPU and 2 Network Adapters.


![image](https://github.com/nahid7474/AD/assets/170605912/583e74ec-6c43-4bf0-a4e0-03ccf4f7ab51)

Adapter 1 is attached to NAT and 2 as internal network. 

![image](https://github.com/nahid7474/AD/assets/170605912/4a1421b3-93fd-485a-a665-3121fe583ff3)


Click on finish and start the VM, this will take some time to copy all the necessary files and install the server.
I will then create first admin account and log into my server. 

**Active Directory Deployment**: Installed and configured Active Directory Domain Services (AD DS) on the designated Domain Controller.
The server manager pops up immediately I am logged in, from there I will now add Active Directory Domain Services and click next.

![image](https://github.com/nahid7474/AD/assets/170605912/6c4a62d2-de23-4b69-9fc1-3f3d2e6092db)

Will follow the on screen prompt and finish/close the wizard once done

![image](https://github.com/nahid7474/AD/assets/170605912/2440e6c0-9eb0-46f6-bc78-18238ffd23d6)
![image](https://github.com/nahid7474/AD/assets/170605912/9792d2a8-f008-4c63-930d-5da0af4ed059)


**Forest Creation**: 

I will now promote this server as a domain controller by adding a new forest from the window that pops up.

![image](https://github.com/nahid7474/AD/assets/170605912/da10390e-9826-4beb-8a69-833e9741255d)


I will name the forest as "NahidHomeLab.com" and click Next.

![image](https://github.com/nahid7474/AD/assets/170605912/cd651703-66e3-4bb1-ace5-106a6301173f)


