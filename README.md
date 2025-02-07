# Configure-ad
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Video Demonstration</h2>

- ### [YouTube: How To Implement An Active Directory In The Cloud Using Microsoft Azure](https://youtu.be/6om-kq9T49I)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Deployment and Configuration Steps</h2>

<p>To start this Active Directory tutorial we are going to create two Virtual Machines in Microsoft Azure.
</p>
<p>
</p>
<br />
<p>Section 1: Select the “Virtual Machines” option in Azure -> Select “Create Virtual Machine” -> Create a new Resource Group -> Name the VM “DC-1” -> Select “Windows Server 2022” as the Image -> Select “2vcpus, 16 GiB memory” for the “Size” option -> Create a username and password for the administrator account section -> Click “Review + create”</p>
<img src="https://i.gyazo.com/e6a9e290e25895dc34d4e02d354ce40b.png">
<img src="https://i.gyazo.com/d2fee5c127c16f240c64fc22addabeb3.png">
<img src="https://i.gyazo.com/30ddb13bc9a509331963818d763f0be1.png">
<img src="https://i.gyazo.com/d0aa64b7d15ae739868fcbe3c515a09f.png">
<img src="https://i.gyazo.com/142bdf7bba1856b23b5d6bc7287ff0ce.png">
<img src="https://i.gyazo.com/82b68c920f205e3635850a113b6d3ea7.png">
<p>
<p>Section 2: Once the VM is finished being created go to “Virtual Machines” -> Select “Networking” -> Select the Network Interfaces name -> Select “IP configurations” -> Select the Private IP address number -> Change the “Assignment” from “Dynamic” to “Static”</p>
<img src="https://i.gyazo.com/5189f0830049f96b8ea7a0c4355cba4e.png">
<img src="https://i.gyazo.com/086ace2f525faa3a7f8350d446a8af5f.png">
<img src="https://i.gyazo.com/4b7e95fe3c54d9c14de1beba915c441f.png">
<img src="https://i.gyazo.com/79edeede8dc27f725e7c5c4366bc94eb.png">
<img src="https://i.gyazo.com/82b2f02c71057357183691c34bb9c097.png">
<p>Section 3: Select the “Virtual Machines” option in Azure ->  Select “Create Virtual Machine” -> Select the same Resource Group you used to create the “DC-1” VM -> Name the VM “Client-1” -> Select “Windows 10 Pro” as the Image -> Select “2vcpus, 16 GiB memory” for the “Size” option -> Create a username and password for the administrator account section -> Click “Review + create” -> Review both of the VMs properties information when “Client-1” is done being created to ensure that they are in the same “Virtual network/subnet</p>
<img src="https://i.gyazo.com/42530219f21d00948f71f5b2f10e4639.png">
<img src="https://i.gyazo.com/aad925bf3119f50a3fc73bcaf1c0179a.png">
<img src="https://i.gyazo.com/c9fd3e9c824d2313dd47dadd523fb070.png">
<img src="https://i.gyazo.com/33a58fc9bda355e1392c241498ba7c69.png">
<img src="https://i.gyazo.com/925f7743bc5da56465ef21a801465dda.png">
<p>Section 4: Login to the “Client-1” VM using Remote Desktop Connection and the VMs public IP address and administrator account details -> Open command prompt in the “Client-1” Windows 10 VM -> Ping DC-1’s private IP address with the command ping -t <ip address> -> Login to the “DC-1” VM using Remote Desktop Connection and the VMs public IP address and administrator account details -> Search “Windows firewall” into the Windows 10 search bar and select the option “Windows Defender Firewall” -> Click “Advanced settings” -> Select Inbound Rules -> Sort by “Protocol” -> Enable both of the options that have “ICMP Echo Request” in its name -> Check Client-1 to see that the ping is now replying</p>
<img src="https://i.gyazo.com/e4c5cb0d06a36fdfe7ba92f475f3c8c9.png">
<img src="https://i.gyazo.com/95b326db5c13069115cd39fc63ac9bdb.png">
<img src="https://i.gyazo.com/4c957e955bd196a3e22fdff5f76616c1.png">
<img src="https://i.gyazo.com/1bc4737ed9f42402654a510e5b10ffbf.png">
<img src="https://i.gyazo.com/f23a167b54da56e650c42865ffd9f0fa.png">
<img src="https://i.gyazo.com/d7b8aa39253ad6bb9373f95fc04f9ccf.png">
<img src="https://i.gyazo.com/5836b6c5fee146d1da607f5e5d952524.png">
<img src="https://i.gyazo.com/643d195d5c376f8ab07b4cd87357a027.png">
<img src="https://i.gyazo.com/fab7aa0cbeb4d33b8af0c3e972d875d6.png">
<img src="https://i.gyazo.com/2eac7fe96eeca8178cd97d05b119856f.png">
<img src="https://i.gyazo.com/927900553ef274cf44e4c87f9ef8610d.png">
<img src="https://i.gyazo.com/2c426c65fb8632beccf55065a8649382.png">
<p>Section 5: Open the DC-1 virtual machine -> Go to Server Manager and select “Manage” and then “Add Roles and Features” -> Click next until you get to “Server Roles” -> Select only “Active Directory Domain Services and then next -> Click next until you get to “Confirmation” and then select “Install” -> Once it is done being installed select the flag at the top of the Server Manager Dashboard -> Click “Promote this server to a domain controller” -> Select “Add a new forest” -> Write “mydomain.com” as the Root domain name and select Next -> Use Password1 as the DRSM password then click next -> Continue to click next and then click install (Note: The VM will now restart to complete the installation) -> Log back into DC-1 but you must now login as username: mydomain.com\labuser and the password remains the same</p>
<img src="https://i.gyazo.com/002cce0a04acb7e5a6acb87c204f7ca9.png">
<img src="https://i.gyazo.com/7429f203fbc6e96d232e8deeacb1a6b0.png">
<img src="https://i.gyazo.com/bcb02728fb6abd8997b017e222f27564.png">
<img src="https://i.gyazo.com/2b0d4d16cd68c28a531de8cb8daf243d.png">
<img src="https://i.gyazo.com/4f1c4c9992ab8fcad64e04f8bff16408.png">
<img src="https://i.gyazo.com/bc41685accdbfdf8d9d1543264f3f2e2.png">
<img src="https://i.gyazo.com/5251ce4b4b683d7641e4d5621f67d192.png">
<img src="https://i.gyazo.com/0a6eaf91ad9611e6f276fb3f0c97e916.png">
<img src="https://i.gyazo.com/6535686817371af63bd9e08269112ccd.png">
<img src="https://i.gyazo.com/7c31f9fc22750ba9950d9373c4622e9b.png">
<img src="https://i.gyazo.com/18e067bced007e3dbc2b110157a3a2c9.png">
<img src="https://i.gyazo.com/0c9324f96fac859e4854f71d05ef3e70.png">
<img src="https://i.gyazo.com/0a7b004bb24c08d2d76d671f8609377f.png">
<img src="https://i.gyazo.com/d1121eca0c6e5236b2091507f94fff19.png">
<img src="https://i.gyazo.com/6417933072f0b01223a8b29c684f3b9a.png">
<img src="https://i.gyazo.com/7ac566fa9cc2172d7c16210b3e7775e0.png">
<p>Section 6: Open Server Manager -> Open the Active Directory Users and Computers console
From the Server Manager dashboard, select "Tools" from the top menu and then choose "Active Directory Users and Computers" -> Right-click on mydomain.com and select "New Organizational Unit" from the context menu. Name the new OU "_EMPLOYEES" and click "OK". -> Create a new OU named “_ADMINS” Repeat the last step, but name the new OU "_ADMINS" instead. -> Right-click on the "_EMPLOYEES" OU and select "New" from the context menu. -> Then, select "User" from the sub-menu to open the "New Object - User" wizard. Enter "Jane" for the first name and "Doe" for the last name, then set the "User logon name" to "jane_admin". -> Fill in any other required user information, such as the password, and click "Next" to proceed. -> Right click the Jane Doe name and select “Properties” -> Select “Member Of” and then “add” -> Enter “domain admins” as the name and select ok</p>
<img src="https://i.gyazo.com/c64dff3a2971baa69b4a52aa130c054e.png">
<img src="https://i.gyazo.com/c58b9a0574c90f044241a6d0b8d7e49c.png">
<img src="https://i.gyazo.com/68ed6f39cf2b674246ad827277e41d2f.png">
<img src="https://i.gyazo.com/70cdbd2bd7d2e47e9010c24deeb9f8af.png">
<img src="https://i.gyazo.com/e3207416b0bfc288e936372b3e7290d4.png">
<img src="https://i.gyazo.com/4ed6584a87bf20bbc825bd76141599f7.png">
<img src="https://i.gyazo.com/b6c6d539f41855f70cdd69fbfeef92eb.png">
<img src="https://i.gyazo.com/d154ea8ba76acf37da305a9b67d488eb.png">
<img src="https://i.gyazo.com/f8a68944b07ee1c639ac71fba342fb48.png">
<img src="https://i.gyazo.com/62f542526d4c69f70dba813a2317e325.png">
<img src="https://i.gyazo.com/60e628202b239b318f6d2232d6971215.png">
<img src="https://i.gyazo.com/de538fed61a7b9b596335dc82cda503b.png">
<p>Section 7: Log out or close the Remote Desktop connection to DC-1, then log back in using the "mydomain.com\jane_admin" account credentials. -> Use jane_admin as your admin account from now on use the "jane_admin" account as your admin account when accessing the Active Directory Users and Computers console or other administrative tools in Windows Server 2022</p>
<img src="https://i.gyazo.com/c979e21e87be68c7a628025332b2b9a9.png">
<p>Section 8: Now we are going to add Client-1 to the Domain Controller! In the Azure portal select the “Client-1” VM -> Click “Networking” -> Click the network interfaces name ->  Select DNS servers under “Settings” -> Select “Custom” and enter DC-1’s private IP address -> Click Save -> Once the change is completed restart Client-1 -> Login to Client-1 (Remote Desktop) using the original labuser account info -> Head to settings in Windows 10 -> Click “System” -> Click “About’ -> Click “”Rename this PC (advanced) -> Select “Change” -> Click “Domain:” and enter in mydomain.com and click OK -> Enter mydomain.com\jane_admin as the username (this is the account we made a domain admin earlier) and enter in the password you gave that account -> If it all went well a window should pop up saying “Welcome to the domain” -> Restart the Client-1 VM</p>
<img src="https://i.gyazo.com/c979e21e87be68c7a628025332b2b9a9.png">
<img src="https://i.gyazo.com/a98a7bcd9b19e4e0491fe720870c577f.png">
<img src="https://i.gyazo.com/d5cd5c3d4aba68e5c4ecdd44c538ab51.png">
<img src="https://i.gyazo.com/a065dc5877eb4cfe865d9d2f1925a3ca.png">
<img src="https://i.gyazo.com/0fca136cad3e0912f15c6e47ad14e755.png">
<img src="https://i.gyazo.com/3edaa86a9e7b51d9a349d57f736cf5d7.png">
<img src="https://i.gyazo.com/7f0c8180e5466171006c9d168413530d.png">
<img src="https://i.gyazo.com/87827edf789e906e599d43a70005f527.png">
<img src="https://i.gyazo.com/dcbb9983c3cfff76c4c29d18d7b4d53c.png">
<img src="https://i.gyazo.com/3fcd9e3541defc94d363d666e8744b04.png">
<img src="https://i.gyazo.com/a39c327c8eff1885d49a2a3dc9877ee3.png">
<img src="https://i.gyazo.com/59017ee6a5ca842ea6035576b9ac4f0c.png">
<img src="https://i.gyazo.com/d2a7ce453b03b81d62b209093a398705.png">
<img src="https://i.gyazo.com/8ea2735d809a568807a0de7f78240293.png">
<img src="https://i.gyazo.com/a1c9440445fb1c13923927f5d1aa6d62.png">
<p>Section 9: Enter into the DC-1 VM and verify that Client-1 pops up inside of the “Computers” section of Active Directory’s Users and Computers window -> Create a new organizational unit and name it “_CLIENTS” -> Drag the Client-1 computer into the “_CLIENTS” OU</p>
<img src="https://i.gyazo.com/2fc06e2dcd31240b7b1080d2a9aee8f9.png">
<img src="https://i.gyazo.com/3ce843e3d594c8036bdfd3e843023e5f.png">
<img src="https://i.gyazo.com/b8b3f13de5d4c39f907bcbfc5579b73f.png">
<img src="https://i.gyazo.com/b5e29f354edce07682946122efd0cbda.png">
<img src="https://i.gyazo.com/ff4a0964af131c29e62c247c0be81f62.png">
<img src="https://i.gyazo.com/2e903d0d68c04d5f86c2ca135cd057f7.png">
<p>Section 10: Enter into the Client-1 VM -> Search for the “Settings” app in Windows 10 and select the icon -> Click the “System” icon -> Click the “Remote Desktop” option -> Then select “Select users that can remotely access this PC” -> Select add and enter the name “domain users’ then check all names and lastly click “OK” (Note: You are now able to login into Client-1 as a normal non-administrative user)</p>
<img src="https://i.gyazo.com/765a956354cc0bc75ca17edc7cbdcf37.png">
<img src="https://i.gyazo.com/afb3acced72fe804be47bcc3fd2fce85.png">
<img src="https://i.gyazo.com/337e28bb29d8217f1587c4cc9157fd41.png">
<img src="https://i.gyazo.com/b1998e7d86a5226e0d350db32fa13564.png">
<img src="https://i.gyazo.com/bfa215aba1544192eb9e1afaf753ae9c.png">
<img src="https://i.gyazo.com/3f43bc72b307d63ce4c8923b4190980e.png">
<img src="https://i.gyazo.com/64be22dfb4f72d8570569b062124603c.png">
<img src="https://i.gyazo.com/a3352675f4155482049e8b7c6518da32.png">
<img src="https://i.gyazo.com/6ed8df86109ea18246f4ed97b798b2ed.png">
<p>Section 11: Enter into the DC-1 VM as the jane_admin account user -> Search and then open the Powershell_ise application as an administrator -> Copy the code from this url (https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1) using the copy icon above the code -> Create a new file in Powershell -> Paste the code from the script you previously copied -> Change the number of users from 10000 to 100 -> Run the script by pressing on the play button at the top of Powershell ISE (Note: This Powershell script code has automatically created 100 user accounts in the Active Directory) -> Note down a random username from the active directory -> Login into Client-1 using that random username via Remote Desktop -> Username = mydomain.com\user.name Password = Password1</p>
<img src="https://i.gyazo.com/70226bfef483bf9221209da72fbcb897.png">
<img src="https://i.gyazo.com/4d5f709e2fa6a686b91dac5f7fb554a3.png">
<img src="https://i.gyazo.com/3b5432f7fa9ac6c2183c072e8ee1af23.png">
<img src="https://i.gyazo.com/d05ef2a94eecebb7e1669842bc00378c.png">
<img src="https://i.gyazo.com/a071b4c042073d3a2fa5a92f844d4fed.png">
<img src="https://i.gyazo.com/c8f49cef1c2873a7d2f8e08e96eff35f.png">
<img src="https://i.gyazo.com/3a20ec05a91c60da04c24ec68dd8363e.png">
<img src="https://i.gyazo.com/fa94f66111d0a5ff708b656e2fae1629.png">
<img src="https://i.gyazo.com/368f9ce60e3f68646368870466b0ade7.png">
<img src="https://i.gyazo.com/351932c46b537639d4fb39da2dd43c6f.png">
<img src="https://i.gyazo.com/f5cda273e15ebce56e055ad6f454dc9d.png">
<p>Congrats you’ve just completed all of the steps for this Active Diretory configuration project tutorial!</p>
