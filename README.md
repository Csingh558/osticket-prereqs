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

- Windows 10</b> (21H2)

<h2>List of Prerequisite Software</h2>

- All Download Files: https://drive.google.com/drive/folders/1mEqQ_2mQjnj1UpAKXUKOVyPW2h7206Gg?usp=sharing
- php-7.3.8-nts-Win32-VC15-x86.zip
- HeidiSQL_12.3.0.6589_Setup.exe
- mysql-5.5.62-win32.msi
- osTicket-v1.15.8.zip
- PHPManagerForIIS_V1.5.0.msi
- rewrite_amd64_en-US.msi
- VC_redist.x86.exe

<h2>Installation Steps</h2>

<p>

</p>
<p>


**Step 1: Azure Virtual Machine Setup**
1. Create a Resource Group.
2. Create a Windows 10 VM in Azure with 2-4 Virtual CPUs and a new Virtual Network (Vnet).
   - VM Configuration:
     - Name: Vm-osticket
     - Username: labuser
     - Password: osTicketPassword1!
3. Log into the VM through Remote Desktop with the Public IP address of the VM.     

**Step 2: Prerequisite Software Installation**
1. Install IIS with CGI and Common HTTP Features, along with IIS Management Console.
   - World Wide Web Services -> Application Development Features:
     - [X] CGI
     - [X] Common HTTP Features
   - Internet Information Services -> Web Management Tools:
     - [X] IIS Management Console
2. Download and install PHP Manager for IIS, Rewrite Module, VC_redist.x86.exe, and MySQL 5.5.62.
3. Set up PHP 7.3.8, creating C:\PHP and configuring IIS.
   - Download PHP 7.3.8 from Installation Files and unzip contents into C:\PHP.
   - If prompted, choose to "Keep" the file.
   - If issues persist, consider using Google Chrome for the download.

**Step 3: osTicket Installation and Configuration**
1. Install osTicket v1.15.8, configuring extensions in IIS.
   - Download osTicket from Installation Files.
   - Extract and copy "upload" folder to C:\inetpub\wwwroot.
   - Rename "upload" to "osTicket" within C:\inetpub\wwwroot.
2. Reload IIS, go to sites -> Default -> osTicket, and click "Browse *:80".
3. Enable missing extensions in IIS (php_imap.dll, php_intl.dll, php_opcache.dll).
4. Rename ost-config.php:
   - From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
   - To: C:\inetpub\wwwroot\osTicket\include\ost-config.php.
5. Assign Permissions to ost-config.php:
   - Disable inheritance -> Remove All.
   - New Permissions -> Everyone -> All.
6. Continue osTicket setup in the browser (click Continue):
   - Name: Helpdesk.
   - Default email (receives email from customers).
7. Download and install HeidiSQL.
   - Open HeidiSQL, create a session (root/Password1), and connect.
   - Create a database called "osTicket" in HeidiSQL.
8. Continue osTicket setup in the browser:
   - MySQL Database: osTicket.
   - MySQL Username: root.
   - MySQL Password: Password1.
   - Click "Install Now!" to complete the setup.
   - Log into the help desk page to see if it works: http://localhost/osTicket/scp/login.php


