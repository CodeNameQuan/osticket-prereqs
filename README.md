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
- osTicket Installation files
- Heidi SQL

<h2>Installation Steps</h2>

<p>
</p>
<p>
Hello all! This is my first tutorial! To begin we will have to create a Virtual machine using the Microsoft Azure portal. We will be using a Virtual Machine a.k.a VM which is a remote computer. We will be using a VM to protect our physical machine just in case something breaks. In order to create the VM we need to first create a resource group and title it "osTicket-lab". Afterwards create a VM with 2-4 CPUs. In this example I will be using 2 CPUs.
  
 <img src="https://i.imgur.com/dlVokFd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
<p>
</p>
<p>Next simply connect to your newly created VM using RDP using the public IPv4 address. If you are a Mac user you will have to download Microsoft RDP. As you can see in this example I am a mac user. 
</p>
<img src="https://i.imgur.com/FXpfunz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
</p>
<p>
So now that you are connected to your VM you will have to enable IIS. Simply access the control panel then select uninstall a program. On the left you will see "Turn windows features on or off", click on that. A list will appear then you will enable Internet Information Services. After enabling IIS, go to world wide web services, then application development and enable CGI.
</p>  
<img src="https://i.imgur.com/qtEnuWu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/W2JkJZw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
</p>
<p>
Now that you have enabled IIS we need to install the PHP Manager for IIS, and then after that install the Rewrite module
</p>
<img src="https://imgur.com/x3JOQPA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/b7gQiPG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next after that is completed lets create a C file and name it PHP, and from there go to the installation files and download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents of that into the C file, C:\PHP
</p>
<img src="https://imgur.com/IkOqZjZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<p>
Now you will want to download MySQL 5.5.62, open it as Typical setup, launch the configuration wizard, set up standard configuration and set the password as "Password1" After thats completed, open IIS as adminastrator, and register PHP from inside IIS, once done re-open IIS and stop, start the server.
</p>
<img src="https://imgur.com/6gA3Rur.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  
</p>
<br />
<p>
</p>
<p>  
Next you want to download osTicket. Then extract and copy the "upload" folder into c:\inetpub\wwwroot. Afterwards rename the folder to osTicket
</P>
<img src="https://i.imgur.com/TUGiSKi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
<p>
</p>
<p>
Open IIS Manager and restart the server. Once inside IIS manager go to Sites->Default->osTicket on the right, click "Browse*.80" from there your default browser should open osTicket webserver.
</p>
<img src="https://i.imgur.com/4AkTkV0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
</p>
<p>
Go back into IIS manager and enable some extensions. To do this, go to Sites->Default->osTicket
Double click on PHP manager. Click on "Disable or enable an extension" Enable "php_intl.dll" & "php_opcache.dll" then refresh the osTicket webserver and obsereve the changes "Intl Extension" should now be enabled. 
</p>
<img src="https://i.imgur.com/APZgUTT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
</p>
<p>
Go back into c:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php rename the file to c:\inetpub\wwwroot\osTicket\include\ost-config.php
Assign permissions to ost-config.php Disable inheritance->Removeall
New Permissions->Everyone->all
</p>
<img src="https://i.imgur.com/1nYaYGe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
</p>
<p>
Finish setting up osTicket in the browser (click continue) then you will name the Helpdesk to your liking. Select a default email that will receive emails from customers who submit tickets. Then from the installation files install HeidiSQL, open HeidiSQL, create a new session user us root, password is Password1, connect to the session, and create a database called "osTicket"
</p>
<img src="https://i.imgur.com/RmVk3q5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
<p>Continue Setting up osticket in the browser MySQL Database: osTicket MySQL Username: root MySQL Password: Password1 Click “Install Now!”
Congrats! osTicket should be installed with hopefully no errors!
Clean up
Delete: C:\inetpub\wwwroot\osTicket\setup
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php
Login to the osTicket Admin Panel (http://localhost/osTicket/scp/login.php)
