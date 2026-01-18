<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployment and Configuration </h1>


<p>Building on the first project that set up our simulated Active Directory environment, we now move to the next step in our tutorial series. Welcome to the "Active Directory Deployment and Configuration" project, where we explore the details of deploying and refining an Active Directory system. This project is designed to impart a fundamental understanding of Active Directory services, emphasizing key aspects such as installation, forest creation, user account administration, domain integration, and customized Remote Desktop access.

</p>

<h2>Prerequisites</h2>

- <a href="https://github.com/chinhanjohnlee/ad-and-azure-setup"> Preliminary Setup for Active Directory and Network Traffic Analysis between Azure VMs </a>

<h2>Key Objectives</h2>
<h3>Active Directory Installation</h3>

-  Configure and install Active Directory services on the designated Domain Controller virtual machine.

<h3>Forest Creation</h3>

- Establish a new Active Directory forest.

<h3>Administrator Account Creation</h3>

- Create and administer user accounts with administrative privileges for effective management of the Active Directory environment.

<h3>Domain Joining</h3>

- Integrate the Client-01 virtual machine into the established domain, ensuring seamless communication with the Active Directory infrastructure.

<h3>Remote Desktop Setup</h3>

- Configure Remote Desktop access specifically tailored for non-administrative users, enhancing user accessibility while maintaining security protocols.




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)


<h2>Configuration Steps</h2>

<h3>&#9312; Install Active Directory in DC-01</h3>

- In the Server Manager dashboard, click Add roles and features and continue the setup
<img width="1174" height="831" alt="Image" src="https://github.com/user-attachments/assets/51b40cea-90fb-41d4-ad9e-823cd0564ff3" />

<p>

</p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<p><strong> Select Active Directory Domain Services and finish the installation </strong> </p>
<p>
</p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h3>&#9313; Promote DC-01 to Domain Controller </h3>

- Once the installation is done, notice the flag on the top left of the Server Manager
- Click on the flag and promote DC-01 to Domain Controller.

<img width="242" height="215" alt="Image" src="https://github.com/user-attachments/assets/53a2bd96-dab5-44e9-9597-91021b915526" />



<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

-  We will now add a new Forest and set the Root domain name to “mydomain.com”
<p>
<img width="565" height="265" alt="Image" src="https://github.com/user-attachments/assets/eca08c29-cb0c-4926-982b-6fbbad8ecbc3" />
  
- Finish setup and restart DC-01
- Log back in with “your username"@mydomain.com



<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h3>&#9314; Creating an Admin in Active Directory </h3>

- Once DC-01 has rebooted, click on tools and select Active Directory Users and Computers
- Right click on mydomain.com and select new and click on Organizational Unit
<img width="438" height="273" alt="Image" src="https://github.com/user-attachments/assets/5f0dba03-8ab4-43bf-b800-2106114dd98d" />


<br>
<br>
<br>
<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<p><strong> We will be creating an OU named _EMPLOYEES and _ADMINS </strong></p>

<img width="450" height="241" alt="Image" src="https://github.com/user-attachments/assets/dfa27277-080f-41f6-9b38-a7e6ee5c4934" />


<p><strong>.</strong></p>
<p><strong>.</strong></p>

<p><strong>Right click on Users and create a new user named Jane Doe with the username jane_admin</strong></p>

<img width="323" height="278" alt="Image" src="https://github.com/user-attachments/assets/66ceacbd-b9ec-48e8-a7b2-a71583ffc42b" />


<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<p><strong>Now we will turn Jane Doe into an admin by right clicking her name and adding her to the “Domain Admins” Security Group</strong></p>

<img width="412" height="125" alt="Image" src="https://github.com/user-attachments/assets/f76bd088-d02a-4ad2-8e65-3aefd6282155" />



<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<p><strong>Logout of DC-01 and log back in with Jane Doe’s credentials</strong></p>

<img width="337" height="231" alt="Image" src="https://github.com/user-attachments/assets/099fc039-9692-4627-b8d7-6f4cf7556036" />

<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>


<h3>&#9315; Join Client-01 to domain </h3>

<p><strong> For Client-01 to join the domain, we first have to set it’s DNS server as DC-01’s private address.</strong></p>

- In the Azure Portal, select Client-01 -> Networking -> Network interface and click on DNS servers

<img width="735" height="399" alt="Image" src="https://github.com/user-attachments/assets/c890551d-3f03-4bc3-aee6-40eca9b3f4cb" />



<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<p><strong>Select a custom DNS server and type in the private ip address of DC-01 and restart Client-01</strong></p>

<img width="356" height="163" alt="Image" src="https://github.com/user-attachments/assets/04cfcf0a-5133-4e0a-8fa5-82f200143ebe" />

<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<p><strong> Now log back in to Client-01 using your original admin credentials. Click start and go to Settings > Rename this PC (advanced) > Change and add “mydomain.com” and login with the admin credentials previously created (jane_admin) </strong></p>

<img width="476" height="599" alt="Image" src="https://github.com/user-attachments/assets/a5e8f8de-428f-4c77-a335-a68f2c5b9522" />

<br>

<p> <strong>Once Client-01 has been added, the VM will restart.</strong></p>


<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h3>&#9316; Setup Remote Desktop for non-administrative users </h3>

- Log back into Client-01 using jane_admin and open Settings > Remote Desktop> User Accounts and click “Select users that can remotely access this PC”
- Add Domain Users

<br>

<img width="343" height="191" alt="Image" src="https://github.com/user-attachments/assets/8da51086-5607-41ed-ab7f-6180a7eccccd" />
<p><strong>This will allow normal users to login to Client-01</strong></p>

<br>

<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>



<h2> Final Thoughts </h2>

<p>
We've successfully concluded the Active Directory Deployment and Configuration phase. Through configuring Active Directory on the Domain Controller, we established our infrastructure by creating a forest, administrator account, and ultimately integrating Client-01 into the domain. In the upcoming project, we'll be generating users and simulating various Active Directory scenarios. </p>

