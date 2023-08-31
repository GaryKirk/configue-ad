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

- Create two virtual machines in Microsoft Azure: Client-1 (Windows 10), DC-1 (Windows Server 2022)
- Set DC-1 to a static IP address
- Test the connection from Client-1 to DC-1
- Install Active Directory
- Create an Admin account and multiple other user accounts
- Join Client-1 to DC-1
- Setup Remote Desktop for non-admin users on Client-1

<h2>Deployment and Configuration</h2>
<p>1. In Microsoft Azure, create a new Resource group. After this, in the new resource group, create a new virtual machine (VM) with 2-4 virtual CPUs. Make sure to also create a new virtual network. Connect to the VM using a Remote Desktop program and the public IP addess of your new VM. <br /></p>
<img src="https://github.com/GaryKirk/osticket-prereqs/assets/137613637/afdf7df5-0b36-4ca7-8142-f95dbb57b113" alt="Create VM"/><br /><br />
