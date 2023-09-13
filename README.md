<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
Active Directory is used throughout the business world to manage high numbers of user accounts and services. I completed this lab to build my knowledge of using Active Directory and other related services.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

<ul>
  <li>Create two virtual machines in Microsoft Azure: Client-1 (Windows 10), DC-1 (Windows Server 2022)</li>
  <li>Set DC-1 to a static IP address</li>
  <li>Test the connection from Client-1 to DC-1</li>
  <li>Install Active Directory</li>
  <li>Create an Admin account and a User account in Active Directory</li>
  <li>Join Client-1 to mydomain.com</li>
  <li>Setup Remote Desktop for non-administrative users on Client-1</li>
  <li>Create a additional users and attempt to log into Client-1 with one of the users</li>
</ul>

<h2>Deployment and Configuration</h2>
<p>1. Create a new virtual machine in Microsoft Azure. Name this "DC-1". Be sure to put all resources in the same region. Choose Windows Server 2022 as the Image and apply two VCPUs. Add an Admin username and password. Click to create the virtul machine. Once created, create another new virtual machine in the same resource group. Name this "Client-1". Choose Windows 10 as the image and make sure it has two VCPUs. Add a username and password for this virtual machine. Also, add it to the same virtual network as DC-1. Click to create the new virtual machine. <br /></p>
<img src="https://github.com/GaryKirk/configure-ad/assets/137613637/d8f57357-0f53-4d4d-8b78-ee93e25741ed" alt="Create two VMs"/><br /><br />

<p>2. In Microsoft Azure go to DC-1 --> Networking --> Network Interface --> IP-configuations --> ipconfig1 and set the IP address to 'Static'. Click to save the changes. This means that the IP address of DC-1 will stay the same. <br /></p>
<img src="https://github.com/GaryKirk/configure-ad/assets/137613637/a0b69eb4-04ae-436a-adcc-da063205d7e4" alt="Static IP" width="500" length="500"/><br /><br />

<p>3. In order to test the connection between Client-1 and DC-1, first login to Client-1 using Remote Desktop, Client-1's public IP address and the correct login credentials. After this, in Microsoft Azure, open DC-1 and copy the private IP address. On Client-1, open a Command Prompt windows and type "ping -t (DC-1 private IP address). You will notice that this will continue to time out.<br /></p>
<img src="https://github.com/GaryKirk/configure-ad/assets/137613637/0792bcb0-e087-471b-a1dd-e5375e593569" alt="Ping Time Out" width="500" length="500"/><br /><br />

<p>4. Next, using Remote Desktop, login to DC-1. You will need DC-1's public IP address and login information to do this. Once the desktop loads, type "wf.msc" in the search bar. This will take you to Windows Firewall. Click Inbound Rules --> Sort the table by 'Protocol' --> Find 'ICMPv4' and enable all of these rules. Finally, go back to your instance of Client-1 and you should now see that the ping comand is successful.<br /></p>
<img src="https://github.com/GaryKirk/configure-ad/assets/137613637/7a1ecef7-5005-408c-98f2-dd5a39bef5f7" alt="Ping Successful" width="500" length="500"/><br /><br />

<p>5. To continue, log back in to DC-1 and install Active Directory Domain Services. Click Start --> Server Manger --> Add Roles and Features. Go through the installation wizard. Select DC-1 as the destination server and 'Active Directory Domain Services' as what you want to install. Once installation is complete, you will notice a yellow triangle in the top-right toolbar. Click this to complete the post-installation steps. It will turn the server in to a domain controller. Click to add a new forest and choose a domain name such as mydomain.com". Choose a username and password and click through the wizard to complete the tutorial. Once the installation completes, you will lose connection the virtual machine. Log back in to DC-1 using the fully qualified domain name, 'mydomain.com\username and corresponding password. <br /></p>
<img src="https://github.com/GaryKirk/configure-ad/assets/137613637/e8057bac-3e74-4efc-868a-003cac206031" alt="Install AD" width="500" length="500"/><br /><br />

<p>6. To ensure that Active Driectory installed correctly, click start and search for 'Active Directory Users and Computers'. To create an Organizational Unit, which is like a folder,  right-click the domain nam eon the left menu. Click 'New' and then Organizational Unit. Use the name "_EMPLOYEES" and click 'OK'. Complete the process again to create an organizational unit called "_ADMINS". <br /></p>
<img src="https://github.com/GaryKirk/configure-ad/assets/137613637/8068207e-b605-4599-a805-28d21bb9ea73" alt="Add OUs" width="500" length="500"/><br /><br />

<p>7. In the _Admins Organizational Unit, right-click ---> New ---> User. Add a first and last name. Also, add a User login name. Click 'Next' and create a password for the account. Because this is a tutorial, uncheck 'User must change password at next login'. Click 'OK' to create the user account. This will take you back to Active Driectory dashboard. Find the account in '_ADMINS' and riht-click on the username. Select Properties ---> Member Of ---> Add ---> type "domain" ---> Check Names ---> click 'Domain Admins' ---> click Apply and OK.<br /></p>
<img src="https://github.com/GaryKirk/configure-ad/assets/137613637/246d847e-6680-4575-8254-3baf89dd6159" alt="Add OUs" width="500" length="500"/><br /><br />

<p>8.<br /></p>
<img src="https://github.com/GaryKirk/configure-ad/assets/137613637/246d847e-6680-4575-8254-3baf89dd6159" alt="Add OUs" width="500" length="500"/><br /><br />
