<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation steps of the open-source help desk ticketing system osTicket.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Create an Azure Virtual Machine (Windows 10 , 4 vCPUs 16 GiB)
-<li><a href= "https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">osTicket Instalation Files</a> (Download these files on the Virtual Machine)
  
- Enable IIS 
- Install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
- Install Rewrite Module (rewrite_amd64_en-US.msi)
- Install PHP 7.38 (php-7.3.8-nts-Win32-VC15-x86.zip)
- Install MYSQL 5.562 (mysql-5.5.62-win32.msi)
 

<h2>Installation Steps</h2>

- On your virtual machine got to the **Control Panel** then click on **Programs**
- Under **Programs and Features** click on **Turn windows features on or off**
- Go throught the list and check **Internet Information Services** and expand its list then head to **World Wide Web services** and expand its list and check **Application Development Features** expand that and check **CGI**
- Finaly make sure all of the boxes under **Common HTTP Features** are checked and click ok 
  ![image](https://github.com/Andrea-Decasenave/osticket-prereqs/assets/150068516/b951a5cc-cb35-4202-8381-156a9b803aa3)

- To make sure everything was done correctly got to the browser on you Virtual machine and type **127.0.0.1** and the page to Internet Infromation Services should come up 
</p>
<br />


<p>
  
  ![image](https://github.com/Andrea-Decasenave/osticket-prereqs/assets/150068516/8d00c9bd-60e7-45d6-9f3f-da41a015620e)

</p>
<p>
<h2>File Installation for OsTicket</h2>
  

- From the Instalation files dowaload **PHP Manager** (PHPManagerForIIS_V1.5.0.msi) as well as **Rewrite Module** (rewrite_amd64_en-US.msi)
- Create a new folder in your Virtual Machines C drive and name it **PHP**
- Next dowload **PHP 7.3.8** (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip it into the **C:/PHP** file we just created

    -**WARNING**: You might get a a messsage when dowloading **PHP 7.3.8** if this happpens just right click the message and click **Keep**

  _![image](https://github.com/Andrea-Decasenave/osticket-prereqs/assets/150068516/aa38ec3d-0d64-435a-b1a0-238c3fa36213)

- From the instalation files download **VC_redist.x86.exe.** 
-From the installation files  download **MySQL 5.5.62** (mysql-5.5.62-win32.msi) make sure you choose typical set up whne installing
  - After Install launch **Configuration Wizard**
  - Check **Install Windows As A Service** (leave serviec name as ""MySQl"" only for this project)
  - Check **Modify Security Settings** and set the root password as **Password1** ( just for this project)

- Open **(IIS) INternet Infomation Manager** and run it as and Administrator
  - You should see PHP Manager and URL Rewrite since we installed it previously
  -![image](https://github.com/Andrea-Decasenave/osticket-prereqs/assets/150068516/e3de2411-5014-462a-88ef-3b7678607057)
- Click on **PHP Manager** then click on **Register New PHP version**
    - Then navigate to c drive---- PHP Folder---- Finally open php-cgi.
    - ![image](https://github.com/Andrea-Decasenave/osticket-prereqs/assets/150068516/073352b9-9742-42cb-be66-0c3fa033392e)

  - Back on **IIS** click **Restart** on the far right pane to refresh the IIS Manager

<h2>Installing OsTicket</h2>

- From the installation files dowload OsTicket (osTicket v1.15.8)
- Extract the **Upload** folder from the zip file and copy (drag and drop) it into the c:\inetpub\wwwroot folder
  -![image](https://github.com/Andrea-Decasenave/osticket-prereqs/assets/150068516/42048aad-e7f4-4812-ae23-c77e28921fea)


  

</p>
<p>

<br />
