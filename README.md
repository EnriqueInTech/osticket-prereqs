<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

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
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<ul>
  <li>Create a Virtual Machine:</li>
  <ul>
    <li>Start by visiting Azure Portal.</li>
    <li>Set up a new virtual machine with Windows 10 Pro (version 22H2). Be sure to choose a VM size with at least 2 vCPUs and 16 GB of RAM to meet the requirements.</li>
  </ul>
  
  <li>Connect to Your Virtual Machine:</li>
  <ul>
    <li>After setting up the VM, find the public IP address assigned to it in the Azure portal.</li>
    <li>Use the Remote Desktop Connection app to connect to your VM by entering the public IP address.</li>
  </ul>
</ul>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<ul>
  <li>Access Windows Features:</li>
  <ul>
    <li>After connecting to your virtual machine, open the Control Panel.</li>
    <li>In the Control Panel, go to Programs and then click on Turn Windows features on or off.</li>
  </ul>

  <li>Enable IIS and Required Features:</li>
  <ul>
    <li>In the Windows Features menu, navigate to World Wide Web Services.</li>
    <li>Under Application Development Features, check the boxes for CGI and Common HTTP Features.</li>
  </ul>
</ul>
<br />
<ul>
  <li>Verify IIS Installation:</li>
  <ul>
    <li>To confirm IIS is properly installed, open your web browser and type 127.0.0.1 in the address bar. You should see the default IIS landing page.</li>
  </ul>

  <li>Install PHP Manager for IIS:</li>
  <ul>
    <li>Download PHP Manager for IIS from the installation files (look for PHPManagerForIIS_V1.5.0.msi).</li>
    <li>Run the installer and follow the setup wizard to complete the installation.</li>
  </ul>
</ul>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<ul>
  <li>Install the Rewrite Module:</li>
  <ul>
    <li>Download the Rewrite Module from the installation files (look for rewrite_amd64_en-US.msi).</li>
    <li>Run the installer to complete the installation.</li>
  </ul>

  <li>Set Up PHP:</li>
  <ul>
    <li>Create a folder named PHP in the *C:* drive.</li>
    <li>From the installation files, download PHP 7.3.8 (look for php-7.3.8-nts-Win32-VC15-x866.zip), and extract the contents into C:\PHP.</li>
  </ul>
</ul>
<br />
<ul>
  <li>Install Visual C++ Redistributable:</li>
  <ul>
    <li>After extracting the PHP files into the C:\PHP folder, download VC_redist.x86.exe from the installation files.</li>
    <li>Run the installer and follow the setup wizard to complete the installation of the Visual C++ Redistributable.</li>
  </ul>

  <li>Install MySQL:</li>
  <ul>
    <li>Download MySQL 5.5.62 (look for mysql-5.5.62-win32.msi) and run the installer.</li>
    <li>In the setup wizard, select Typical Setup and click Launch Configuration Wizard after installation.</li>
    <li>Choose Standard Configuration and set the root password to Password1.</li>
  </ul>
</ul>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<ul>
  <li>Open IIS Manager:</li>
  <ul>
    <li>After installing the necessary files, search for IIS in the Windows search bar and open Internet Information Services (IIS) Manager as an administrator. The program interface should appear like this.</li>
  </ul>

  <li>Register PHP with IIS:</li>
  <ul>
    <li>In IIS Manager, locate and click on PHP Manager.</li>
    <li>Select Register new PHP version.</li>
    <li>When prompted, provide the path to the PHP executable file (php-cgi.exe). Navigate to C:\PHP, and select the php-cgi.exe file.</li>
    <li>Finally, restart the IIS server to apply the changes.</li>
  </ul>
</ul>
<br />
<ul>
  <li>Install osTicket v1.15.8:</li>
  <ul>
    <li>Download osTicket v1.15.8 from the Installation Files folder.</li>
    <li>Extract the contents and copy the upload folder to C:\inetpub\wwwroot.</li>
    <li>Inside C:\inetpub\wwwroot, rename the upload folder to osTicket.</li>
    <li>Reload IIS for the changes to take effect.</li>
  </ul>

  <li>Access osTicket through IIS:</li>
  <ul>
    <li>In IIS Manager, navigate to Sites -> Default -> osTicket.</li>
    <li>On the right, click *Browse :80 to access osTicket in your web browser.</li>
  </ul>

  <li>Enable Required PHP Extensions:</li>
  <ul>
    <li>Go back to IIS Manager and navigate to Sites -> Default -> osTicket.</li>
    <li>Double-click on PHP Manager.</li>
    <li>Select Enable or Disable an Extension.</li>
    <li>Enable the following extensions:</li>
    <ul>
      <li>php_imap.dll</li>
      <li>php_intl.dll</li>
      <li>php_opcache.dll</li>
    </ul>
  </ul>
</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<ul>
  <li>Rename the Configuration File and Set Permissions:</li>
  <ul>
    <li>Open File Explorer and navigate to the following directory: C:\inetpub\wwwroot\osTicket\include.</li>
    <li>Locate the file ost-sampleconfig.php and rename it to ost-config.php.</li>
    <li>After renaming the file, right-click on it and select Properties. In the Properties window, go to the Security tab and click on Advanced.</li>
    <li>Disable Inheritance by selecting Remove all inherited permissions from this object.</li>
    <li>Next, we’ll add new permissions:</li>
    <ul>
      <li>Click Add.</li>
      <li>In the dialog box, click Select a principal.</li>
      <li>Type Everyone in the box and click Check Names.</li>
      <li>Make sure Full Control is selected, and all other checkboxes are ticked.</li>
      <li>Click Apply and then OK.</li>
    </ul>
  </ul>
</ul>
<br />
<ul>
  <li>Complete osTicket Setup in the Browser:</li>
  <ul>
    <li>In the browser, click Continue on the osTicket setup page.</li>
    <li>Fill out the required fields on the page, but leave the Database Settings section blank for now; we'll address that shortly.</li>
    <li>Download and install HeidiSQL from the Installation Files.</li>
    <li>Once HeidiSQL is installed, open the program and create a new session.</li>
    <li>Make sure the Username is set to root and the Password is Password1.</li>
    <li>After establishing the connection in HeidiSQL, return to the browser to complete the osTicket setup. Under the Database Settings section, enter root as the username and Password1 as the password.</li>
  </ul>
</ul>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<ul>
  <li>Create a New Database in HeidiSQL:</li>
  <ul>
    <li>In HeidiSQL, right-click on Unnamed on the left panel, select Create New, and then choose Database.</li>
    <li>Name the new database osTicket.</li>
    <li>Once the database is created, go back to the osTicket browser setup and enter osTicket as the database name under the MySQL Database section.</li>
  </ul>

  <li>Cleanup and Final Permissions:</li>
  <ul>
    <li>To complete the setup, we need to delete the setup folder:</li>
    <ul>
      <li>Navigate to C:\inetpub\wwwroot\osTicket\setup and delete the setup folder. Be sure to delete only this folder and not any other files or directories.</li>
    </ul>
    <li>Finally, we’ll adjust permissions for the following folders:</li>
    <ul>
      <li>C:\inetpub\wwwroot\osTicket\attachments</li>
      <li>C:\inetpub\wwwroot\osTicket\include</li>
    </ul>
    <li>Grant full control for these folders as well to ensure osTicket operates smoothly.</li>
  </ul>
</ul>
<br />
<ul>
  <li>Complete the osTicket Installation:</li>
  <ul>
    <li>Return to your browser and finalize the osTicket installation by clicking Finish.</li>
    <li>Congratulations! osTicket is now successfully installed and ready to use.</li>
  </ul>
</ul>

</p>


