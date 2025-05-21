# **Configuring Active Directory Domain Services (AD DS)**  


## **Installing **AD DS Role**
1. 1.	As indicated in the snapshot below, in the Server Manager, click on ‘Manage’ and select ‘Add Role and Features’.
   	A pop-up window will appear. Click on the Next button.
<p align="center">
  <img src="https://github.com/user-attachments/assets/25fd3d55-c19c-417a-9ca4-9138247c9c6a" alt="">
</p>
2.	 In your next screen, go by the default as seen in the snapshot below. Continue to click on next.

<p align="center">
  <img src="https://github.com/user-attachments/assets/885d25a7-d20c-40a7-900a-0014c495f2a8" alt="">
</p>

3.	As shown below, Select the ‘Active Directory Domain Services’. A pop-up window appears. Click on the ‘Add Features’.
<p align="center">
  <img src="https://github.com/user-attachments/assets/9c7dddcd-1668-4b7e-84d8-bbd678c89f0f" alt="">
</p>
4.	Continue to click on ‘Next’ until you get to the ‘Confirmation’ page, as indicated in the
snapshot below. Check the ‘Restart the destination server automatically if required’.
Checkbox and click the ‘Yes’ on the pop-up dialog box.
<p align="center">
  <img src="https://github.com/user-attachments/assets/f19031e6-48c8-4ffd-9c24-83bb484fff76" alt="">
</p>
5.	Click on Install.

## **Promoting DC01 as Domain Controller**  

4. Promote server:  
   - Select **Add a new forest** → Define root domain (e.g., `enterpriselab.local`).  
   - Set **Directory Services Restore Mode (DSRM)** password.  

<p align="center">
  <img src="" alt="">
</p>



<p align="center">
  <img src="" alt="">
</p>

<p align="center">
  <img src="" alt="">
</p>

<p align="center">
  <img src="" alt="">
</p>
