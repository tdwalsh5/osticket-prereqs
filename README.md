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

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- Rewrite Module
- MySQL
- HeidiSQL
- osTicket
- Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  1
First you are going to create a virtual machine by going to https://portal.azure.com/. Set up your virtual machine with Windows 10 Pro, version 22H2. Note, create a virtual machine with atleast 2 vcpus and 8 GBs of memory.
</p>
<br />

<p>
  2
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once you have created your virtual machine you will want to connect to it by using the public IP address of the VM. You will connect using the remote desktop protocol connection app (Windows App on Mac).
</p>

<p>
  image 3 and 33
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now connected to your VM, you will want to go to your control panel. From the control panel open up programs. Select, Turn Windows features on and off.
</p>
<br />

<p>
  image 4 and 44
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now you want to install / enable IIS in Windows with CGI and Common HTTP features.
  World Wide Web Services -> Application Development Features -> [X]CGI[X] Common HTTP Features
To make sure the IIS is installed/enabled go to a browser and search 127.0.0.1 (loopback). It should look something like this. (Image 5)
</p>
<br />

<p>
Now that the IIS is enabled, from the installation files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0). Go through the install wizard and complete the install.
</p>
<br />

<p>
Next from the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)
</p>
<br />

<p>
Create a folder in the C drive called PHP.
</p>
<br />

<p>
From the installation files, download PHP 7.3.8 (php-7.3.88-nts-Win32-VC15-x866.zip) and unzip the contents into C:\PHP
</p>
<br />

<p>
Once you have downloaded and extracted the zip file into the PHP folder on the C drive, download and install the VC_redist.x86.exe from the installation files. Go through the setup wizard to finish setting up and installing the VC_redist.x86.exe.
</p>
<br />

<p>
  image 6 &7
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) Run the setup wizard: Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration ->
Make the new root password: Password1
Execute the process on the next page.

</p>
<br />

<p>
  image 8
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
11.) Now that the files are downloaded and installed, search for IIS in the windows search bar. Open IIS as an administrator. The program should like this.
</p>
<br />

<p>
  step 12
  (image 9 & 10)
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
12.) Register PHP from within IIS. Click on PHP Manager -> register new PHP version.
(image 11)
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
Provide a new path to the PHP executable file (php-cgi.exe). C Drive -> PHP -> php-cgi file.
(image 12)
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
Restart the IIS server.
</p>
<br />

<p>
  image 13
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  13.)Install osTicket v1.15.8 -Download osTicket from the Installation Files Folder -Extract and copy "upload" folder to c:\inetpub\wwwroot -Within c:\inetpub\root, Rename "upload" to "osTicket"

Reload IIS again.
</p>
<br />

<p>
  14.) On IIS go to sites -> Default -> osTicket -> Browse *:80
</p>
<p>
  image 14
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Enable extensions on the osTicket browser. Navigate back to IIS, Sites -> Default -> osTicket -> PHP manager -> "Enable or disble an extension"
Enable three extensions
  1.) php_imap.dll
  2.) php_intl.dll
  3.) php_opcache.dll
</p>
<p>
  image15
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
