<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> 

<h2>List of Prerequisites</h2>

- [PHP for Windows (Non Thread Safe Version Recommended)](https://windows.php.net/download#php-8.3) 
- [HeidiSQL](https://www.heidisql.com/download.php) 
- [MySQL](https://dev.mysql.com/downloads/installer/) 
- [osTicket](https://osticket.com/download/)
- [PHP Manager 2](https://github.com/phpmanager/phpmanager/releases)
- [Rewrite Module](https://www.iis.net/downloads/microsoft/url-rewrite)
- [Latest Visual C++ Redistributable](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170)

<h2>Installation Steps</h2>

<h3>Part 1 - Create and Access Azure Virtual Machine (Optional) </h3>

<p>
If needed, create a Virtual Machine with Microsoft Azure, otherwise, move on to Part 2.
  
> - Create a Resource Group
> - Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs
> - When creating the VM, allow it to create a new Virtual Network (Vnet)
> - Note the username and password for your virtual machine
> - Note the Public IP of your Virtual Machine

Access your Virtual Machine via Remote Desktop 
> - On your local Windows PC: In the search box on the taskbar, type Remote Desktop Connection
> - Select Remote Desktop Connection
> - In Remote Desktop Connection, type the IP Address of the PC you want to connect to, and then select Connect.
</p>

<h3>Part 2 - Installation </h3>

<p>
  
Install / Enable IIS in Windows with CGI and Common HTTP Features
> - Open the Start menu.
> - Type "features" and select Turn Windows features on or off.
> - Tick the Internet Information Services checkbox
> - Enable CGI and Common HTTP Features via World Wide Web Services -> Application Development Features ->
> - Tick CGI
> - Tick Common HTTP Features

AND IIS Management Console
> - Internet Information Services -> Web Management Tools -> IIS Management Console
> - Tick IIS Management Console

Download and Install [PHP Manager 2](https://github.com/phpmanager/phpmanager/releases)

Download and Install [Rewrite Module](https://www.iis.net/downloads/microsoft/url-rewrite)

Create the directory C:\PHP

Download [PHP for Windows (Non Thread Safe Version Recommended)](https://windows.php.net/download#php-8.3) and Unzip contents into C:\PHP

Download and Install [Latest Visual C++ Redistributable](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170)

Download and Install [MySQL](https://dev.mysql.com/downloads/installer/) 
> - Launch Configuration Wizard (after install) -> Standard Configuration -> Create Password

Open IIS Manager as Admin

Register PHP from within IIS

Reload IIS (Open IIS, Stop and Start the server)

Download and Install [osTicket](https://osticket.com/download/)
> - Extract and copy “upload” folder to c:\inetpub\wwwroot
> - Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”

Reload IIS (Open IIS, Stop and Start the server)

Go to sites -> Default -> osTicket
> - On the right, click “Browse *:80”

Note that some extensions are not enabled
> - Go back to IIS, sites -> Default -> osTicket
> - Double-click PHP Manager
> - Click “Enable or disable an extension”
> - Enable: php_imap.dll
> - Enable: php_intl.dll
> - Enable: php_opcache.dll
> - Refresh the osTicket site in your browser, observe the changes

Rename: **ost-sampleconfig.php** to **ost-config.php**
> - Location: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php

Assign Permissions: ost-config.php
> - Right Click file, go to Properties
> - Security Tab
> - Advanced Button
> - Disable inheritance Button -> Remove All
> - New Permissions -> Everyone -> All

Continue Setting up osTicket in the browser (click Continue)
> - Name Helpdesk
> - Default email (receives email from customers)

From the Installation Files, download and install HeidiSQL.

Open Heidi SQL
> - Create a new session, root/Password1
> - Connect to the session
> - Create a database called “osTicket”

Continue Setting up osticket in the browser
> - Name MySQL Database
> - Create MySQL Username
> - Create MySQL Password
> - Click “Install Now!"

Verify installation
> - Browse to your help desk login page: http://localhost/osTicket/scp/login.php
> - Check End Users osTicket URL: http://localhost/osTicket/ 
>> - This is the site that users would go to in order to create tickets and ask for assistance.

Installation is now complete.

</p>

