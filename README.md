;<p align="center">
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

- Proceed to rename the **upload** we just copied into wwwroot folder to **osTicket**
- Reload/restart IIS Manager
- On IIS Manager on the left pane where it says **Connections** under it youre going to expand **sites** then expand **Default Web Sites**  then click on osTicket. On the far right pane you are going to click **Browse *:80**
- ![image](https://github.com/Andrea-Decasenave/osticket-prereqs/assets/150068516/f0c60d80-72bf-4062-89f0-9746b5a1de6c)

- The OsTicket Installer page should come up
- ![image](https://github.com/Andrea-Decasenave/osticket-prereqs/assets/150068516/8f4d8ece-5dc6-443e-b668-116805182e7f)
- Back on IIS Manager open **PHP Manager** scroll down and click on **enable or disable extension**

  -Enable:  
  - php_imap.dll
  -  php_intl.dll
  -   php_opcache.dll
- go back to your browser and resfresh to verify that there is a check mark next to the extansions we just enabled if there is the extesions havebeen succesfully enbaled
- Navigate to c drice----> inetpub----->wwwroot---->osTicket---->include and rename ost-sampleconfig.php to **ost-config.php**
- Right click **ost-config.php** then go to propertiesthen click on **security** then click on on **Advanced** and finally click **disable inheritance** then remove all inheritance 
- Back on **Advanced Security settings** add a new premission and click on Select principle on the top then on "Enter a new object name" just put **everyone** then click check nsme and ok. Then check the **Full Control box** then clikc ok and apply
- Head back to your browser and hit continue at the bottom of the page. Setup system settings and admin user and stop once you get to database settings. In data base setings fro your log in you can use "yourname@gmail.com" password: Password1 ( I recomend writting this down on notepad so you dont forget)
- Dowload  and install **HeidiSQL** from the installation files HeidiSQL will pop up make sure "Launch HeidiSql is checked and click finish. Heidi will open up and you will create a new session use the user name :**root**  and the password: Password1 (we set these up earlier)
- Once it connects it should look like this:
- ![image](https://github.com/Andrea-Decasenave/osticket-prereqs/assets/150068516/152b1f80-e97b-4246-a16a-fdeb3e6986fb)
- 


  

</p>
<p>

<br />
