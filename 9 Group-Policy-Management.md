# 9 Group Policy Management

## 9.1 Disabling Control Panel for Marketing/Research
1. Open Group Policy Management Console (GPMC) from DC01
2. Expand ‘Forest..’ Domains enterpriselab.local
3. Right click Group Policy Object and select New

<p align="center">
  <img src="https://github.com/user-attachments/assets/d81fdf9e-595c-46ea-a546-31fe172d5242" alt="">
</p>
  
4.	In the ‘New GPO’ pop-up window, type the name of the GPO. 
Eg ‘DisableControlPanel_Marketing’ as seen below  

<p align="center">
  <img src="https://github.com/user-attachments/assets/c6f1473c-32e2-4d4c-9cd1-0451673be788" alt="">
</p>

5.	Right-click the new GPO and click on ‘Edit’ to open Group Policy Management Editor  
6.	Navigate to: User Configuration → Policies → Administrative Templates → Control Panel  
7.	Double-click “Prohibit access to Control Panel and PC settings” → Enable → OK  
<p align="center">
  <img src="![image](https://github.com/user-attachments/assets/780ef3b1-8a14-4ec3-99b2-ee1bc1a9d6b2)
" alt="">
</p>

## 9.1.1 Linking GPO for ‘DisableCtrlPanel_Marketing&Research’  to OU ( Marketing & Research)  
1.	In GPMC, right-click the OU (e.g., Marketing, Research) that has been created and
   click on ‘Link an Existing GPO’.
<p align="center">
  <img src="https://github.com/user-attachments/assets/7d6aca67-8e81-4da4-a806-2226bb8fbe6b" alt="">
</p>
2.	Select the GPO ‘DisableCtrlPanel_Marketing&Research’  
<p align="center">
  <img src="https://github.com/user-attachments/assets/54e2a41a-ff93-45a5-aadf-5537c2f97449" alt="">
</p>

3.	That policy will now apply to users in the Marketing and Research OU the next time they log in.
As shown below, I logged in with a user from the marketing OU and when I try to access control panel, it tells me,
‘ The operation has been cancelled due to restriction in effect on this computer.
 Please contact your system administrator.’
<p align="center">
  <img src="https://github.com/user-attachments/assets/2926e014-2219-465e-bbde-fe0e7b0f9736" alt="">
</p>


## 9.2 GPO to Deploy Different Desktop Wallpaper for Users in Various OU’s
1.	From ‘Tools’ on the Server manager, open the ‘Group Policy Management’.
Expand the Forest, Domains and right-click on the ‘Group Policy Object’ and select ‘New’.
Enter the name of the policy. Eg. ‘Wallpaper4IT ‘, ‘Wallpaper4Managers’,’ Wallpaper4Marketing’, and ’Wallpaper4Reseach’.  
2.	Under the ‘Group Policy Object’, right click on the jus created policy and select ‘Edit’.  
3.	Follow the path below to User Config → Policies → Admin Templates → Desktop → Desktop Wallpaper (Double click)  
4.	Set it to Enable and give the path to each wallpaper. (I used paint to create the wallpapers)  
5.	Within the same ‘Group Management Policy’, locate the various OU’s and right click, go to ‘Link to an Existing GPO’.  
6.	Select the right policy associated to the OUs’ and click on ‘OK’.  
7.	Force the policy to be applied using the command in CMD: gpupdate /force.  
8.	After logging in with the right credentials associated with the OUs will display something like below:
   
<p align="center">
  <img src="https://github.com/user-attachments/assets/ed968c9e-d597-4b56-9dbc-80824931cabb" alt="">
</p>

## 9.3 GPO to Disable Users [Managers, Marketing & Research] in OU from Using the USB Storage/Port
1.	From ‘Tools’ on the Server manager, open the ‘Group Policy Management’.
Expand the Forest, Domains and right-click on the ‘Group Policy Object’ and select ‘New’.
Enter the name of the policy. Eg. ‘DisableUSBStorage4Managers_Market&Reseach’.  
2.	Under the ‘Group Policy Object’, right click on the jus created policy and select ‘Edit’.  
3.	Under Computer Config, go through Policies → Admin Templates → System → Removable Storage Access.
4.	Double-click on the ‘All Removable Storage classes: Deny all access’ and select ‘Enable’.
   Click on ‘OK’ as shown below:

<p align="center">
  <img src="https://github.com/user-attachments/assets/d151bee2-59a7-4524-8bf0-3e2973a5e47b" alt="">
</p>

## 9.4 Creating GPO to Map a Network Drive Containing Shared Folders on DC01
### 9.4.1 Step 1: Create a Shared Folder on DC01
NB: You may not want to use your C: Drive to create this for security reasons.
Also, I have already created security groups within the various OUs’ AND added the respective users to these groups.  
1.	Create a folder in the desired location.  
2.	Right-click on the Shared folder and click on ‘Properties’, ‘Advanced Sharing’, check the ‘Share the folder’ checkbox.  
3.	Below it is a ‘Permission’, click on it and add the necessary permission and Group needed to access that folder. Allow Full Control to IT team  (or a more restricted group like Domain Users or Marketing,etc.)  

<p align="center">
  <img src="https://github.com/user-attachments/assets/36b087b8-5a17-4ec9-b988-24d156b80ebd" alt="">
</p>
  
4.	To be able to access the different folders from the network, use the path eg:
\\dc01\MarketingShares

<p align="center">
  <img src="https://github.com/user-attachments/assets/4f2e935a-7c02-4344-90f5-5513a24fd89b" alt="">
</p>

5.	Since the IT team  group has access to al folders, lets log in with an IT user. 

<p align="center">
  <img src="https://github.com/user-attachments/assets/d42b26ba-7e65-44a6-9902-c60626ac559" alt="">
</p>

I am able to access with the IT User

<p align="center">
  <img src="https://github.com/user-attachments/assets/1de167eb-25bb-46ed-b02c-c1c16fa565b6" alt="">
</p>

If you login with another user belonging to a particular group, you are only able to see what was shared to that group of users.
As an example, I can’t access the IT Team folder as I have logged in with a marketing group use
![image](https://github.com/user-attachments/assets/d45cb750-da2e-4de9-a31c-362054c5ea40)


### 9.4.2 Step 2: Creating GPOs to Map the Various Network Drives.
1.	Open Group Policy Management (gpmc.msc)  
2.	 Right-click the individual OUs (e.g., IT Team, Marketing, etc.) and  select ‘Create a GPO in this domain, and Link it here…..’. Enter the name,eg. MapDrive_Marketing.  
3.	Go to ‘Group Policy Object’ and edit the new GPOs created. Navigate to ‘User Configuration → Preferences → Windows Settings → Drive Maps’.  
4.	Right-click on the “Mapped Drive’, select ‘New’, ‘Mapped Drive’  

<p align="center">
  <img src="https://github.com/user-attachments/assets/288b233c-2ae5-4430-bae0-315059e7fa34" alt="">
</p>
5.	Configure /fill the necessary portions as indicated in the below snapshot.

<p align="center">
  <img src="https://github.com/user-attachments/assets/f4fbc188-c866-4d1a-b7bf-6603563045d2" alt="">
</p>
6.	We can test it by first logging in with each individual OU or Group user, running the ‘gpupdate /force’.  
7.	Log out and log back in, open File explorer and you should be able to see the mapped drive for each user group as below. Eg. For Marketing  

<p align="center">
  <img src="https://github.com/user-attachments/assets/5ee4f256-dad5-4561-a2bb-dc6927a91c6f" alt="">
</p>

For managers:
<p align="center">
  <img src="https://github.com/user-attachments/assets/2b66449f-6a40-4be2-b21f-7b2bc1d862cf" alt="">
</p>

