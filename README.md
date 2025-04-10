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
  <strong>1.)</strong> Begin by creating a virtual machine at <a href="https://portal.azure.com/" target="_blank">https://portal.azure.com/</a>.<br>
  Set up the VM using <strong>Windows 10 Pro, version 22H2</strong>.<br>
  <strong>Note:</strong> Be sure to select a virtual machine size with at least <strong>2 vCPUs</strong> and <strong>8 GB</strong> of memory to meet the system requirements.
</p>

<p>
  <strong>2.)</strong> Once your virtual machine is created, connect to it using its <strong>public IP address</strong>.<br>
  Use the <strong>Remote Desktop Protocol (RDP)</strong> connection app, this is the <strong>Microsoft Remote Desktop</strong> app available in the App Store (Mac users it's called Windows App).
</p>
<p>
<img src="install-shot1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br></br>

<p>
  <strong>3.)</strong> Once connected to your VM, open the <strong>Control Panel</strong>.<br>
  Navigate to <strong>Programs</strong>, then click on <strong>Turn Windows features on or off</strong>.
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
<br></br>

<p>
  To verify that <strong>IIS</strong> is installed and running, open a browser on the VM and navigate to <code>127.0.0.1</code> (the loopback address).<br>
  If IIS is enabled, you should see the default IIS welcome page.
</p>
</p>
  <p>
<img src="install-image5.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
  <strong>5.)</strong> Now that <strong>IIS</strong> is enabled, download and install <strong>PHP Manager for IIS</strong> from the installation files (<code>PHPManagerForIIS_V1.5.0</code>).<br>
  Run the installer and follow the installation wizard to complete the setup.
</p>
<br />

<p>
  <strong>6.)</strong> Next, from the installation files, download and install the <strong>URL Rewrite Module</strong> (<code>rewrite_amd64_en-US.msi</code>).
</p>
<br />

<p>
  <strong>7.)</strong> Create a new folder on the <strong>C:\</strong> drive named <strong>PHP</strong>.
</p>
<br />

<p>
  <strong>8.)</strong> From the installation files, download <strong>PHP 7.3.8</strong> (<code>php-7.3.8-nts-Win32-VC15-x86.zip</code>) and extract the contents into the <strong>C:\PHP</strong> directory.
</p>
<br />

<p>
  <strong>9.)</strong> After extracting the PHP zip file into the <strong>C:\PHP</strong> folder, download and install <code>VC_redist.x86.exe</code> from the installation files.<br>
  Follow the setup wizard to complete the installation.
</p>
<br />

<p>
  <strong>10.)</strong> Download and install <strong>MySQL 5.5.62</strong> (<code>mysql-5.5.62-win32.msi</code>) from the installation files.<br>
  Run the setup wizard and choose: <strong>Typical Setup</strong> → after installation, launch the <strong>Configuration Wizard</strong> → select <strong>Standard Configuration</strong>.<br>
  When prompted, set the new root password to: <code>root</code>.
</p>
<img src="install-image6.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br></br>

Execute the process on the next page.
  <p>
<img src="install-image7.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
<br />

<p>
  <strong>11.)</strong> Now that all necessary files are downloaded and installed, search for <strong>IIS</strong> in the Windows search bar.<br>
  Right-click and open it as an administrator. The <strong>Internet Information Services (IIS) Manager</strong> should launch and appear similar to the image shown.
</p>
<p>
<img src="install-image8.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
  <strong>12.)</strong> Register PHP within <strong>IIS</strong> by opening <strong>PHP Manager</strong> from the IIS Manager interface.
</p>
<img src="install-image9.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br></br>

<p>
  Register new PHP version.
</p>
<p>
<img src="install-image10.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br></br>

<p>
  After opening <strong>PHP Manager</strong>, provide the path to the PHP executable file:<br>
  <strong>C:\PHP\php-cgi.exe</strong><br>
  This will register PHP with IIS.
</p>
<p>
<img src="install-image11.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br></br>

<p>
Restart the IIS server.
</p>
<p>
<img src="install-image12.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
  <strong>13.)</strong> Install <strong>osTicket v1.15.8</strong>:<br>
  – Download the osTicket archive from the <strong>Installation Files</strong> folder.<br>
  – Extract the archive and copy the <strong>upload</strong> folder to <strong>C:\inetpub\wwwroot</strong>.<br>
  – Within <strong>C:\inetpub\wwwroot</strong>, rename the <strong>upload</strong> folder to <strong>osTicket</strong>.<br><br>

  Once done, reload <strong>IIS</strong> to reflect the changes.
</p>
<br />

<p>
  <strong>14.)</strong> In <strong>IIS Manager</strong>, navigate to:<br>
  <strong>Sites → Default Web Site → osTicket</strong>, then click on <strong>Browse *:80</strong> to launch osTicket in your browser.
</p>
<p>
<img src="install-image13.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br></br>

<p>
  To enable necessary PHP extensions for osTicket, return to <strong>IIS Manager</strong>.<br>
  Navigate to: <strong>Sites → Default Web Site → osTicket → PHP Manager</strong>, then click on <strong>"Enable or disable an extension"</strong>.
</p>
<p>
  <img src="install-image14.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <img src="install-image15.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br></br>

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
<br></br>

<p>
  <strong>15.)</strong> After enabling the required extensions in IIS, you'll need to rename a configuration file in your osTicket directory.<br><br>

  Open <strong>File Explorer</strong> and navigate to:<br>
  <code>C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php</code><br><br>

  Rename the file from <strong>ost-sampleconfig.php</strong> to <strong>ost-config.php</strong>.<br><br>

  Once renamed, right-click the file and select <strong>Properties</strong> → go to the <strong>Security</strong> tab → click <strong>Advanced</strong> → click <strong>Disable inheritance</strong>.<br>
  When prompted, select <strong>Remove all inherited permissions from this object</strong>.<br><br>

  Then, click <strong>Add</strong> to assign new permissions.
</p>
  
<p>
<img src="install-image17.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br></br>

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
<br></br>

<p>
  Once the file permissions are set, return to the osTicket setup page in your browser and click <strong>Continue</strong> to begin the installation process.<br><br>

  Fill out the form with the required information, but leave the <strong>Database Settings</strong> section at the bottom for now — we’ll come back to it shortly.<br><br>

  Next, download and install <strong>HeidiSQL</strong> from the <strong>Installation Files</strong> folder. This tool will be used to create and manage the osTicket database.
</p>
<p>
<img src="install-image22.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br></br>

<p>
  Once <strong>HeidiSQL</strong> is open, create a new session to begin configuring your database connection.
</p>
<p>
<img src="install-image23.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br></br>

<p>
  Make sure to set the <strong>Username</strong> to <code>root</code> and the <strong>Password</strong> to <code>root</code> when creating the new session in HeidiSQL.
</p>
<p>
<img src="install-image24.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br></br>

<p>
  Once connected to the session in <strong>HeidiSQL</strong>, return to the osTicket setup page in your browser to complete the configuration.<br><br>

  Under the <strong>Database Settings</strong> section, enter the following:<br>
  <strong>Username:</strong> <code>root</code><br>
  <strong>Password:</strong> <code>Password1</code><br><br>

  Now go back to <strong>HeidiSQL</strong> to create the database.<br>
  On the left panel, right-click where it says <strong>"Unnamed"</strong> → select <strong>Create New</strong> → then choose <strong>Database</strong>.<br>
  Name the new database: <code>osTicket</code>.<br><br>

  Once the database is created, return to the osTicket browser setup page and, under <strong>MySQL Database</strong>, enter: <code>osTicket</code>.
</p>
<p>
<img src="install-image25.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br></br>

<p>
  The final step is to log in to <strong>osTicket</strong> through your browser.<br>
  Use the admin credentials you created during setup to access the osTicket dashboard and begin managing your help desk system.
</p>
<p>
<img src="https://imgur.com/uHVdDsx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br></br>

<p>
  🎉 You have now successfully installed and set up <strong>osTicket</strong>!
</p>
