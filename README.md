# osTicket-Prerequisites-and-Installation
installing open source help desk ticketing system osTicket
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket. We will be installing all the necessary piece of software to be able to use osTicket. Which is an open source ticketing system for an IT job.<br />


<h2>Video Demonstration</h2>

-<h3>Check out <a href="https://www.youtube.com/watch?v=umu79gT9cIU" target="_blank">YouTube: How To Install osTicket with Prerequisites</a>.</h3>

<h2>Environments and Technologies Used</h2>

<ul>
	<li>Microsoft Azure (Virtual Machines/Compute)</li>
	<li>Remote Desktop</li>
	<li>Internet Information Services (IIS)</li>
	<li>osTicket (open source Ticketing System)</li>
</ul>

<p>&nbsp;</p>

<p><u>Part 1 (Create Virtual Machine in Azure)</u></p>

<p>Create a Resource Group Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs When creating the VM, allow it to create a new Virtual Network (Vnet)</p>

<p>&nbsp;</p>

<p><u>Part 2 (Installation) </u></p>

<p>Please go to Google to download some of the files listed below as you follow the instructions. All the files below and require to install osTicket. Without the files the software will not work.&nbsp;</p>

<p>Create an Azure Virtual Machine Windows 10, 4 vCPUs Name: Vm-osticket Username: labuser (for example/whatever you chose) Password: osTicket Password1! (for example/whatever you chose)&nbsp;</p>

<p><u>Open this: Installation Files</u></p>

<p>We will use these files to install osTicket and some of the dependencies. I&rsquo;m using this offline version to make sure everyone is using the same version of all the files :)</p>

<p>First thing to do is to&nbsp; <u>Install / Enable IIS in your Windows computer WITH CGI and Common HTTP Features</u></p>

<p>Go to your windows <strong>Control Panel</strong>&nbsp; Then click on <strong>programs </strong>then click below <strong>Programs and Features</strong> where is says <strong>&quot;turn windows features on and off&quot;</strong></p>

<p>World Wide Web Services -&gt; Application Development Features -&gt; select the following</p>

<p>[X] CGI</p>

<p>[X] Common HTTP Features</p>

<p><u>AND IIS Management Console</u></p>

<p>Internet Information Services -&gt; Web Management Tools -&gt; IIS Management Console</p>

<p>[X] IIS Management Console</p>

<p>Now install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) (Google it and download it)</p>

<p>Download and install the Rewrite Module (rewrite_amd64_en-US.msi)&nbsp;(Google it and download it)</p>

<p><strong>In your windows computer go to &quot;This PC&quot; or&nbsp; &quot;My Computer&quot; then to the C driver (C:\\) and Create the directory (create a folder and name it PHP) C:\PHP </strong></p>

<p><strong>Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP </strong></p>

<p><strong>Download and install VC_redist.x86.exe. </strong></p>

<p><strong>Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) please select and do the following</strong></p>

<ol>
	<li>Typical Setup</li>
	<li>Launch Configuration Wizard (after install)&nbsp;&nbsp;</li>
	<li>Standard Configuration&nbsp;</li>
	<li>Enter a password &quot;Password1&quot;</li>
</ol>

<p>Open IIS as an Admin</p>

<p>Click on PHP Manager then click Register PHP from within IIS</p>

<p>Reload IIS (Open IIS, Stop and Start the server)</p>

<p><strong>Install osTicket v1.15.8 (Google It)</strong></p>

<p>Download osTicket then Extract and copy &ldquo;upload&rdquo; folder to c:\inetpub\wwwroot Within c:\inetpub\wwwroot,</p>

<p>Rename &ldquo;upload&rdquo; to &ldquo;osTicket&rdquo;</p>

<p><strong><u>Reload IIS (Open IIS, Stop and Start the server)</u></strong></p>

<ol>
	<li>Go to sites</li>
	<li>Default&nbsp;</li>
	<li>osTicket On the right, click &ldquo;Browse *:80&rdquo;</li>
</ol>

<p>Note that some extensions are not enabled</p>

<p>Go back to IIS, sites -&gt; Default -&gt; osTicket</p>

<p>Double-click PHP Manager</p>

<p><strong>Click &ldquo;Enable or disable an extension&rdquo; Enable the following:</strong></p>

<ol>
	<li>php_imap.dll</li>
	<li>php_intl.dll</li>
	<li>php_opcache.dll</li>
	<li>Refresh the osTicket site in your browse, observe the changes</li>
</ol>

<p>Rename: ost-config.php From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php&nbsp; &nbsp;&nbsp;<strong>To</strong>:&nbsp; C:\inetpub\wwwroot\osTicket\include\ost-config.php</p>

<p><u><strong>Assign Permissions: ost-config.php</strong></u></p>

<ol>
	<li>right click on ost-config.php&nbsp;</li>
	<li>click on properties</li>
	<li>then click on the security tab</li>
	<li>then click on&nbsp; Disable inheritance</li>
	<li>Then click on Add. T</li>
	<li>hen Click on &quot;select a principal&quot;</li>
	<li>In the field named &quot;enter the object name to select&quot; enter the word everyone then click on &quot;check names&quot; then click OK.</li>
	<li>&nbsp;On Basic permissions select permissions -&gt; Remove All New Permissions -&gt; Everyone -&gt; All</li>
</ol>

<p><strong><u>Continue Setting up osTicket in the browser (click Continue) </u></strong></p>

<ol>
	<li>Name Helpdesk</li>
	<li>Default email (receives email from customers)</li>
</ol>

<p><strong>From the Installation Files, download and install HeidiSQL. </strong></p>

<ol>
	<li>Open Heidi SQL</li>
	<li>Create a new session, root/Password1</li>
	<li>Connect to the session</li>
	<li>Create a database called &ldquo;osTicket&rdquo;</li>
</ol>

<p><strong>Continue Setting up osticket in the browser </strong></p>

<ol>
	<li>MySQL Database: osTicket</li>
	<li>MySQL Username: root</li>
	<li>MySQL Password: Password1</li>
	<li>Click &ldquo;Install Now!&rdquo;</li>
</ol>

<p>Congratulations, hopefully it is installed with no errors! Browse to your help desk login page: http://localhost/osTicket/scp/login.php</p>

<p>End Users osTicket URL: http://localhost/osTicket/</p>

<p>Clean up Delete: C:\inetpub\wwwroot\osTicket\setup</p>

<p>Set Permissions to &ldquo;Read&rdquo; only: C:\inetpub\wwwroot\osTicket\include\ost-config.php</p>

<p>Notes: Browse to your help desk login page: <a href="http://localhost/osTicket/scp/login.php">http://localhost/osTicket/scp/login.php</a></p>

<p>End Users osTicket URL: http://localhost/osTicket/</p>

<p>

</p>
<br />
