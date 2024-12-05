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
  <strong>1. Create a Virtual Machine:</strong><br>
  - Start by visiting Azure Portal: https://portal.azure.com<br>
  - Set up a new virtual machine with Windows 10 Pro (version 22H2). Choose a VM size with at least 2 vCPUs and 16 GB of RAM.
</p>

<p>
  <img src="[https://i.imgur.com/DJmEXEB.png](https://i.imgur.com/RByMLDt.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
  <strong>2. Connect to Your Virtual Machine:</strong><br>
  - After setting up the VM, find the public IP address assigned to it in the Azure portal.<br>
  - Use the Remote Desktop Connection app to connect to your VM by entering the public IP address.
</p>

<br>

<p>
  <img src="https://i.imgur.com/RByMLDt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
  <strong>3. Access Windows Features:</strong><br>
  - After connecting to your virtual machine, open the Control Panel.<br>
  - In the Control Panel, go to Programs and then click on Turn Windows features on or off.
</p>

<p>
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
  <strong>4. Enable IIS and Required Features:</strong><br>
  - In the Windows Features menu, navigate to World Wide Web Services.<br>
  - Under Application Development Features, check the boxes for CGI and Common HTTP Features.
</p>

<p>
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
  <strong>5. Verify IIS Installation:</strong><br>
  - To confirm IIS is properly installed, open your web browser and type 127.0.0.1 in the address bar. You should see the default IIS landing page.
</p>

<p>
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
  <strong>6. Install PHP Manager for IIS:</strong><br>
  - Download PHP Manager for IIS from the installation files (look for PHPManagerForIIS_V1.5.0.msi).<br>
  - Run the installer and follow the setup wizard to complete the installation.
</p>

<p>
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
  <strong>7. Install the Rewrite Module:</strong><br>
  - Download the Rewrite Module from the installation files (look for rewrite_amd64_en-US.msi).<br>
  - Run the installer to complete the installation.
</p>

<p>
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
  <strong>8. Set Up PHP:</strong><br>
  - Create a folder named PHP in the *C:* drive.<br>
  - From the installation files, download PHP 7.3.8 (look for php-7.3.8-nts-Win32-VC15-x866.zip), and extract the contents into C:\PHP.
</p>

<p>
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br>

<p>
  <strong>9. Install Visual C++ Redistributable:</strong><br>
  - After extracting the PHP files into the C:\PHP folder, download VC_redist.x86.exe from the installation files.<br>
  - Run the installer and follow the setup wizard to complete the installation of the Visual C++ Redistributable.
</p>

<p>
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
  <strong>10. Install MySQL:</strong><br>
  - Download MySQL 5.5.62 (look for mysql-5.5.62-win32.msi) and run the installer.<br>
  - In the setup wizard, select Typical Setup and click Launch Configuration Wizard after installation.<br>
  - Choose Standard Configuration and set the root password to Password1.
</p>

<p>
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
  <strong>11. Open IIS Manager:</strong><br>
  - After installing the necessary files, search for IIS in the Windows search bar and open Internet Information Services (IIS) Manager as an administrator. The program interface should appear like this.
</p>

<p>
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
  <strong>12. Register PHP with IIS:</strong><br>
  - In IIS Manager, locate and click on PHP Manager.<br>
  - Select Register new PHP version.<br>
  - When prompted, provide the path to the PHP executable file (php-cgi.exe). Navigate to C:\PHP, and select the php-cgi.exe file.<br>
  - Finally, restart the IIS server to apply the changes.
</p>

<p>
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br>

<p>
  <strong>13. Install osTicket v1.15.8:</strong><br>
  - Download osTicket v1.15.8 from the Installation Files folder.<br>
  - Extract the contents and copy the upload folder to C:\inetpub\wwwroot.<br>
  - Inside C:\inetpub\wwwroot, rename the upload folder to osTicket.<br>
  - Reload IIS for the changes to take effect.
</p>

<p>
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
  <strong>14. Access osTicket through IIS:</strong><br>
  - In IIS Manager, navigate to Sites -> Default -> osTicket.<br>
  - On the right, click *Browse :80* to access osTicket in your web browser.<br>
  - <strong>Enable Required PHP Extensions:</strong><br>
    1. Go back to IIS Manager and navigate to Sites -> Default -> osTicket.<br>
    2. Double-click on PHP Manager.<br>
    3. Select Enable or Disable an Extension.<br>
    Enable the following extensions:<br>
    1. php_imap.dll<br>
    2. php_intl.dll<br>
    3. php_opcache.dll
</p>

<p>
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
  <strong>15. Rename the Configuration File and Set Permissions:</strong><br>
  - Open File Explorer and navigate to the following directory: C:\inetpub\wwwroot\osTicket\include.<br>
  - Locate the file ost-sampleconfig.php and rename it to ost-config.php.<br>
  - After renaming the file, right-click on it and select Properties. In the Properties window, go to the Security tab and click on Advanced.<br>
  - Disable Inheritance by selecting Remove all inherited permissions from this object.<br>
  - Next, we’ll add new permissions:<br>
    1. Click Add.<br>
    2. In the dialog box, click Select a principal.<br>
    3. Type Everyone in the box and click Check Names.<br>
    4. Make sure Full Control is selected, and all other checkboxes are ticked.<br>
    5. Click Apply and then OK.
</p>

<p>
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br>

<p>
  <strong>16. Complete osTicket Setup in the Browser:</strong><br>
  - In the browser, click Continue on the osTicket setup page.<br>
  - Fill out the required fields on the page, but leave the Database Settings section blank for now; we'll address that shortly.<br>
  - Download and install HeidiSQL from the Installation Files.<br>
  - Once HeidiSQL is installed, open the program and create a new session.<br>
  - Make sure the Username is set to root and the Password is Password1.<br>
  - After establishing the connection in HeidiSQL, return to the browser to complete the osTicket setup. Under the Database Settings section, enter root as the username and Password1 as the password.
</p>

<p>
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
  <strong>17. Create a New Database in HeidiSQL:</strong><br>
  - In HeidiSQL, right-click on Unnamed on the left panel, select Create New, and then choose Database.<br>
  - Name the new database osTicket.<br>
  - Once the database is created, go back to the osTicket browser setup and enter osTicket as the database name under the MySQL Database section.<br>
  <strong>Cleanup and Final Permissions:</strong><br>
  - To complete the setup, we need to delete the setup folder:<br>
  - Navigate to C:\inetpub\wwwroot\osTicket\setup and delete the setup folder. Be sure to delete only this folder and not any other files or directories.<br>
  - After the cleanup, set the permissions of the ost-config.php file back to Read-only.
</p>

<p>
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br>

<p>
  <strong>18. Complete the osTicket Setup:</strong><br>
  - The final step is to log in to osTicket via your browser.<br>
  - Congratulations! You have successfully installed and set up osTicket!
</p>

<p>
  <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

