# **Assigning Static IP and Renaming 'DC01' Server**
## **Assign a **Static IP** to `DC01`**  
1. Start the yet to be configured DC01 and log in with your local administrator account.
2. In the Server manager, click on ‘Local Server’ --> “Ethernet IPv4 address assigned by DHCP, IPv6 enabled”.  
<p align="center">
  <img src="https://github.com/user-attachments/assets/0422d893-a225-4fc8-898f-df44e6482acf" alt="">
</p>  
  
3. Double-click /right click on the Network Adapter and select ‘Properties’.  
4.	In the pop-up window, scroll and look for ‘Internet Protocol Version 4 (TCP/IPv4) and double-click on it.  
5.	As displayed in the image below, select the checkboxes and fill the spaces [IP address, Subnet mask, and Preferred DNS Server.  
6.	Click the ‘OK’ button.  
  - IP: `192.168.50.1`, Subnet: `255.255.255.0`, DNS: `127.0.0.1`.
<p align="center">
  <img src="https://github.com/user-attachments/assets/77e05696-682d-4634-a2ad-1c9580760cd3" alt="">
</p>  
7.	In the server manager, click on the Refresh button to see the change take place, 
as seen in the image below.  
<p align="center">
  <img src="https://github.com/user-attachments/assets/63b7ba3f-8409-42d1-bdb4-4007dcafdcf3" alt="">
</p>

     
## **Renaming Server to `DC01`**  

As indicated in the image below:  
1.	In the Server manager, click on the computer name.
2.	In the Pop-up box, click on ‘Change’
3.	Enter the name of the server, DC01 and click on ‘OK’.
4.	You will be prompted to restart, so go ahead and restart the VM.


<p align="center">
  <img src="https://github.com/user-attachments/assets/91f54da2-f395-4449-b326-69c7164c0804" alt="">
</p>
