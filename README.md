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
1. Create a Virtual Machine:
- Start by visiting Azure Portal.
- Set up a new virtual machine with Windows 10 Pro (version 22H2). Be sure to choose a VM size with at least 2 vCPUs and 16 GB of RAM to meet the requirements.
  
2. Connect to Your Virtual Machine:
- After setting up the VM, find the public IP address assigned to it in the Azure portal.
- Use the Remote Desktop Connection app to connect to your VM by entering the public IP address.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
3. Access Windows Features:
- After connecting to your virtual machine, open the Control Panel.
- In the Control Panel, go to Programs and then click on Turn Windows features on or off.

4. Enable IIS and Required Features:
- In the Windows Features menu, navigate to World Wide Web Services.
- Under Application Development Features, check the boxes for CGI and Common HTTP Features.
</p>
<br />
5. Verify IIS Installation:
- To confirm IIS is properly installed, open your web browser and type 127.0.0.1 in the address bar. You should see the default IIS landing page.

6. Install PHP Manager for IIS:
- Download PHP Manager for IIS from the installation files (look for PHPManagerForIIS_V1.5.0.msi).
- Run the installer and follow the setup wizard to complete the installation.
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
7. Install the Rewrite Module:
- Download the Rewrite Module from the installation files (look for rewrite_amd64_en-US.msi).
- Run the installer to complete the installation.
  
8. Set Up PHP:
- Create a folder named PHP in the *C:* drive.
- From the installation files, download PHP 7.3.8 (look for php-7.3.8-nts-Win32-VC15-x866.zip), and extract the contents into C:\PHP.
</p>
<br />
9. Install Visual C++ Redistributable:
- After extracting the PHP files into the C:\PHP folder, download VC_redist.x86.exe from the installation files.
- Run the installer and follow the setup wizard to complete the installation of the Visual C++ Redistributable.

10. Install MySQL:
- Download MySQL 5.5.62 (look for mysql-5.5.62-win32.msi) and run the installer.
- In the setup wizard, select Typical Setup and click Launch Configuration Wizard after installation.
- Choose Standard Configuration and set the root password to Password1.
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
11. Open IIS Manager:
- After installing the necessary files, search for IIS in the Windows search bar and open Internet Information Services (IIS) Manager as an administrator. The program interface should appear like this.
  
12. Register PHP with IIS:
- In IIS Manager, locate and click on PHP Manager.
- Select Register new PHP version.
- When prompted, provide the path to the PHP executable file (php-cgi.exe). Navigate to C:\PHP, and select the php-cgi.exe file.
- Finally, restart the IIS server to apply the changes.
</p>
<br />
13. Install osTicket v1.15.8:
- Download osTicket v1.15.8 from the Installation Files folder.
- Extract the contents and copy the upload folder to C:\inetpub\wwwroot.
- Inside C:\inetpub\wwwroot, rename the upload folder to osTicket.
- Reload IIS for the changes to take effect.

14. Access osTicket through IIS:
- In IIS Manager, navigate to Sites -> Default -> osTicket.
- On the right, click *Browse :80 to access osTicket in your web browser.
Enable Required PHP Extensions:
    1. Go back to IIS Manager and navigate to Sites -> Default -> osTicket.
    2. Double-click on PHP Manager.
    3. Select Enable or Disable an Extension.
Enable the following extensions:
    1. php_imap.dll
    2. php_intl.dll
    3. php_opcache.dll
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
15. Rename the Configuration File and Set Permissions:
- Open File Explorer and navigate to the following directory: C:\inetpub\wwwroot\osTicket\include.
- Locate the file ost-sampleconfig.php and rename it to ost-config.php.
- After renaming the file, right-click on it and select Properties. In the Properties window, go to the Security tab and click on Advanced.
- Disable Inheritance by selecting Remove all inherited permissions from this object.
- Next, we’ll add new permissions:
    1. Click Add.
    2. In the dialog box, click Select a principal.
    3. Type Everyone in the box and click Check Names.
    4. Make sure Full Control is selected, and all other checkboxes are ticked.
    5. Click Apply and then OK.
</p>
<br />
16. Complete osTicket Setup in the Browser:
- In the browser, click Continue on the osTicket setup page.
- Fill out the required fields on the page, but leave the Database Settings section blank for now; we'll address that shortly.
- Download and install HeidiSQL from the Installation Files.
- Once HeidiSQL is installed, open the program and create a new session.
- Make sure the Username is set to root and the Password is Password1.
- After establishing the connection in HeidiSQL, return to the browser to complete the osTicket setup. Under the Database Settings section, enter root as the username and Password1 as the password.
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
17. Create a New Database in HeidiSQL:
- In HeidiSQL, right-click on Unnamed on the left panel, select Create New, and then choose Database.
- Name the new database osTicket.
- Once the database is created, go back to the osTicket browser setup and enter osTicket as the database name under the MySQL Database section.
Cleanup and Final Permissions:
- To complete the setup, we need to delete the setup folder:
- Navigate to C:\inetpub\wwwroot\osTicket\setup and delete the setup folder. Be sure to delete only this folder and not any other files or directories.
- After the cleanup, set the permissions of the ost-config.php file back to Read-only.
</p>
<br />
18. Complete the osTicket Setup:
- The final step is to log in to osTicket via your browser.
- Congratulations! You have successfully installed and set up osTicket!
</p>
<br />
