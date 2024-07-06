**Project: Active Directory - Emulate a Corporate Network**
------------------------------------------------------------------------------------------------------------------
Summary of Activities:

**Network Diagram**: Created a network diagram outlining the infrastructure for the network environment.

**Server Setup**: Installed and configured Windows Server 2019 on VirtualBox, establishing the initial network setup to support Active Directory services.

**Active Directory Deployment**: Installed and configured Active Directory Domain Services (AD DS) and DNS on the Domain Controller.

**Forest Creation**: Added and deployed a new forest within the Active Directory environment.

**Organizational Unit and Domain Admin Setup**: Created a new Organizational Unit (OU) for domain admin users, and configured the first Domain Admin account with appropriate administrative roles/group membership.

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

![image](https://github.com/nahid7474/AD/assets/170605912/76e47127-c9f2-4c86-82c8-6365f624507e)

Also, checked that I have two network adapters are present as defined previously.

![image](https://github.com/nahid7474/AD/assets/170605912/4a030a71-831c-429d-b056-a74b0f57b52f)

Also, as per my network diagram, I'll assign the internal NIC an IP of 172.16.0.1 with a subnet mask of 24.

![image](https://github.com/nahid7474/AD/assets/170605912/805f0314-0d09-4a09-8f53-71ee53200223)


**ADDS Deployment**: 
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

On the next window, will add the Directory Services Restore Mode password and click Next.

![image](https://github.com/nahid7474/AD/assets/170605912/e9c832ed-ae9c-4399-a1f4-7771b7fa81e8)


Will follow the promppt to finish this installation and restart our server.
Now that I have my ADDS set up successfully, it comes up with the option to log in as a domain admin as expected.


![image](https://github.com/nahid7474/AD/assets/170605912/a14b9a10-86c5-46a4-97ef-43182a37dfea)

Now that I am logged in with the default Administrator account, first thing I'll now do is, create an organization unit named _ADMINS within my Active Directory Users and COmputers

![image](https://github.com/nahid7474/AD/assets/170605912/16879a09-29ff-46b2-b5e7-282d99679ac4)
![image](https://github.com/nahid7474/AD/assets/170605912/e6b50a28-b7de-413c-8da6-576f65396d6d)

Will create my first domain admin account in this newly created OU.

![image](https://github.com/nahid7474/AD/assets/170605912/9336fdef-b928-4941-b437-68e1983da5cc)


Will check the password never expired for this admin account and leave other boxes unchecked.

![image](https://github.com/nahid7474/AD/assets/170605912/a0faa120-84cf-4d16-80b0-3c1b5f8e7a35)

Click Next and finish the prompt to save the user details.

![image](https://github.com/nahid7474/AD/assets/170605912/f83078d6-eaf3-45d2-b8b0-b65caa79a07b)


Will make this account a member of Domain Admins group to give it the priviledged access it requires to be a domain admin. 

![image](https://github.com/nahid7474/AD/assets/170605912/05acf83e-dff2-4a65-858d-06eaf886307b)


I’ll now sign out and log in as a domain admin with my newly created domain admin account.

![image](https://github.com/nahid7474/AD/assets/170605912/e266f531-d7ec-4c79-8086-18099e91ee84)


My DC is now ready with AD DS, DNS and File and Storage Services.

![image](https://github.com/nahid7474/AD/assets/170605912/4effd426-4830-4c53-992a-c99a0f0cf5ba)


**NAT Configuration**: 
Will now facilitate external network communication for this network. For routing purpose, to facilitate this I'll now add/configure NAT so that all my machines within this domain can have internet using one public IP.
From the roles and features, I'll choose Remote Access this time, click Next.

![image](https://github.com/nahid7474/AD/assets/170605912/c2404094-afae-4062-aa01-5f535c777068)


On the Role Services I'll keep the RAS and Routing boxes checked. Click Next, and Install by following the on screen prompts

![image](https://github.com/nahid7474/AD/assets/170605912/61335985-c786-4c9f-8efd-1a12216339da)


Features installation is now complete, will close this window.

![image](https://github.com/nahid7474/AD/assets/170605912/b06b08cc-d643-4f6d-9504-230660fe2f6b)


This requires additional configuration to work. 
From the Tools menu at the top right, I'll select "ROuting and Remote Access" to bring up the consol to configure this. 
RIght click DC and select COnfigure and EnableROuting and Remote Access.

![image](https://github.com/nahid7474/AD/assets/170605912/b261dade-c098-4b1b-b6e4-6bc63302889a)


THe setup wizard will appear and select NAT, click Next

![image](https://github.com/nahid7474/AD/assets/170605912/eb020150-06c6-4304-b5f6-2226275eb904)

Choose the network interface that is external, has internet and click Next

![image](https://github.com/nahid7474/AD/assets/170605912/a2d6414a-0c5c-4c9e-9742-b7eb8bc7f4a9)


Finish the wizarz and refresh the DC.
It appears with green Icons, up arrows etc indicating I have configured it successfully.

![image](https://github.com/nahid7474/AD/assets/170605912/bfdb46a5-e5e5-48e3-a1e7-95bbfe0e40a3)


**DHCP Installation and Configuration**:
From server manager, I will now add DHCP Services using the Add Roles and Features wizard.
Follow along with the on screen prompt, Click next and then Install to finish the installation process.

![image](https://github.com/nahid7474/AD/assets/170605912/3c9e3ab6-e07f-4298-8c68-54bcadaa05f4)


Installed successfully, will now set up my scope so any new computer gets their IP address automatically from this DHCP server.
From Tools menu, choose DHCP at te top right, and then right click on IPv4, Click New Scope

![image](https://github.com/nahid7474/AD/assets/170605912/6d4bc694-ab6d-483e-af66-868f0a3abb24)


Will keep the lease duration as 28 days, click Next

![image](https://github.com/nahid7474/AD/assets/170605912/29be6b0d-c199-46f7-b121-175d8a87b699)

Because NAT is configured on domain controller, I will add my domain controller's IP as router's default gateway in the next winsow and click Next.

![image](https://github.com/nahid7474/AD/assets/170605912/0ed1bf22-1b67-470f-ab6d-ec3889e32967)

Our DC will act as a DNS server as this feature is already installed. 
So again, I'll select the domain controller IP as DNS Server and click next. 

 ![image](https://github.com/nahid7474/AD/assets/170605912/1924806e-ee18-4b1f-9c63-bd991a4d32e5)

 
Activate the scope, Click Next. 

![image](https://github.com/nahid7474/AD/assets/170605912/4e763846-d399-4f6b-81f4-a79a011b3075)

Now, right click on the DHCP server dc.nahidhomelab.com and then click “authorize” and refresh the domain. 
Both IPv4 and IPv6 came with green ticks which represents that I have configured my DHCP Server successfully. 

![image](https://github.com/nahid7474/AD/assets/170605912/780d10a9-c436-42c2-9397-60c72277de83)


**Client Virtual Machine Setup and Domain Join via PowerShell**
Next step is to onboard a machine/a client computer to test the functionality of the DHCP, DNS and Routing and other services within the environment.

Will now spin up an Windows 10 pro 64 bit VM in my virtual box and condider that as my client computer.

![image](https://github.com/nahid7474/AD/assets/170605912/dc68ae2c-7771-49ab-a908-5fe873960879)


VM has spun up with the local user name of CLient1.
Will now check it's network information to see if it has picked up my DHCP server that I configured earlier. 

