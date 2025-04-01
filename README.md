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
1.) First you are going to create a virtual machine by going to https://portal.azure.com/. Set up your virtual machine with Windows 10 Pro, version 22H2. Note, create a virtual machine with atleast 2 vcpus and 8 GBs of memory.
</p>
<br />

<p>
2.) Once you have created your virtual machine you will want to connect to it by using the public IP address of the VM. You will connect using the remote desktop protocol connection app (Windows App on Mac).
</p>
<p>
<img src="install-shot1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
3.) Now connected to your VM, you will want to go to your control panel. From the control panel open up programs. Select, Turn Windows features on and off.
</p>
<p>
<img src="install-image3.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="install-image33.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
  4.) Now install and enable <strong>IIS</strong> in Windows with <strong>CGI</strong> and <strong>Common HTTP Features</strong>.<br><br>

  Navigate to:<br>
  <strong>World Wide Web Services → Application Development Features</strong><br>
  Then check:<br>
  <strong>[✔] CGI</strong><br>
  <strong>[✔] Common HTTP Features</strong>
</p>
<img src="install-image4.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

To make sure the IIS is installed/enabled go to a browser and search 127.0.0.1 (loopback). It should look something like this.
</p>
  <p>
<img src="install-image5.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
5.) Now that the IIS is enabled, from the installation files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0). Go through the install wizard and complete the install.
</p>
<br />

<p>
6.) Next from the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)
</p>
<br />

<p>
7.) Create a folder in the C drive called PHP.
</p>
<br />

<p>
8.) From the installation files, download PHP 7.3.8 (php-7.3.88-nts-Win32-VC15-x866.zip) and unzip the contents into C:\PHP
</p>
<br />

<p>
9.) Once you have downloaded and extracted the zip file into the PHP folder on the C drive, download and install the VC_redist.x86.exe from the installation files. Go through the setup wizard to finish setting up and installing the VC_redist.x86.exe.
</p>
<br />

<p>
10.) Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) Run the setup wizard: Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration 
Make the new root password: root
  <p>
<img src="install-image6.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Execute the process on the next page.
  <p>
<img src="install-image7.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
<br />

<p>
11.) Now that the files are downloaded and installed, search for IIS in the windows search bar. Open IIS as an administrator. The program should like this.
</p>
<p>
<img src="install-image8.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
12.) Register PHP from within IIS. Click on PHP Manager.
<p>
<img src="install-image9.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Register new PHP version.
</p>
<p>
<img src="install-image10.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Provide a new path to the PHP executable file (php-cgi.exe). C Drive -> PHP -> php-cgi file.
<p>
<img src="install-image11.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Restart the IIS server.
</p>
<p>
<img src="install-image12.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
  13.)Install osTicket v1.15.8 -Download osTicket from the Installation Files Folder -Extract and copy "upload" folder to c:\inetpub\wwwroot -Within c:\inetpub\root, Rename "upload" to "osTicket"

Reload IIS again.
</p>
<br />

<p>
  14.) On IIS go to sites -> Default -> osTicket -> Browse *:80
</p>
<p>
<img src="install-image13.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Enable extensions on the osTicket browser. Navigate back to IIS, Sites -> Default -> osTicket -> PHP manager -> "Enable or disble an extension"
</p>
<p>
  <img src="install-image14.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <img src="install-image15.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
  <p>
  Enable the following three PHP extensions:
</p>
<ol>
  <li><code>php_imap.dll</code></li>
  <li><code>php_intl.dll</code></li>
  <li><code>php_opcache.dll</code></li>
</ol>
  <p>
  <img src="install-image16.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

15.) Once we have those extensions enabled in IIS, we are going to want to rename one of the files in our osTicket folder.
  Go into the file explorer and search for C;\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  
  We are going to rename the ost-sampleconfig.php to ost-config.php
  
  Now that we have renamed the files, right click on the file and go to properties.
  From there click security, click on advance, and disable the inheritance.
  We will select Remove all inherited permissions from this object.
  
  Now we will add new permissions.
  
  Click Add
  
<p>
<img src="install-image17.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
Select a principal
  
<p>
<img src="install-image18.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  
 Type "Everyone" in the box.
  
<p>
<img src="install-image19.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Make sure Full Control and all the other boxes are checked.
  
<p>
<img src="install-image20.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Click Apply and Ok.
  
<p>
<img src="install-image21.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Once that is done we will continue to setup osTicket in the browser. Click Continue on the osTicket browser page.
  Fill out the page as required except the Database Settings at the bottom of the page. We will get to that. 
  
  We will want to download and install HeidiSQL from the Installation Files. 
  
<p>
<img src="install-image22.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  When the program is open we will create a new session in it.
  
<p>
<img src="install-image23.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  We want to make sure the username is root and the password is root.
  
<p>
<img src="install-image24.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Once we are connected to the session we will go back to the browser to finish setting everything up. Under the Database Settings in the browser the username will be root and the password will be Password1.
  
  We will now create a new database within HeidiSQL. In Heidi right click on the left side where is says "Unnamed", select "create new", and then select "database". Name the new database osTicket. Once we have the new database setup go back to the osTicket browser and under MySQL Database type in osTicket.
  
<p>
<img src="install-image25.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  The last step after that is to login to osTicket on the browser.
  
<p>
<img src="https://imgur.com/uHVdDsx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  You have now successfully installed and setup osTicket!
