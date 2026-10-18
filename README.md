# Ancora-Education-Ucertify-Lab30
# Configuring IP and Management Access

Configuring IP involves assigning an IP address and subnet mask to a network interface on a networking device, enabling communication within the network. Management access involves setting up protocols (e.g., SSH, Telnet) and access control methods to remotely manage and configure the device, ensuring secure administration.

> **Original Lab Source**
> 
> This lab was available through:
>
> [https://ancoraeducation.ucertify.com/app/?func=navigate_items&item_sequence=3]

## Instructions
The PuTTY SSH Client is used in this lab. It is a popular SSH and Telnet Client that provides a secure way to access remote systems. You are provided with the Linux virtual machine.

**Topology**

Topology refers to the arrangement or configuration of the virtual network connections within the virtual machine (VM) environment. It defines how the virtual network interfaces and components are interconnected and organized.

## Objective of the Lab
This lab session demonstrates the steps involved in configuring IP and management access. Upon completion of this lab, you will be able to:
* Understand the concept of assigning IP and management.
* Configure IP and management access.
## PART A: Accessing the R1 Terminal
Access the PuTTY console with IP address as 192.168.116.128, Port as 5017, and Connection type as Other.
### STEP 1
From the left sidebar, click the PuTTY SSH Client icon. The PuTTY Configuration dialog box will appear on the screen.
### STEP 2
Type Host Name (or IP address) as 192.168.116.128
### STEP 3
Type Port as 5017
### STEP 4
Select the Other radio button.
### STEP 5
Click Open to connect the R1 terminal window.
### STEP 6
If you don't get a command line prompt in the terminal window, then press Enter.
## PART B: Assigning the IP Address
Enter into configuration mode and execute commands to assign the 172.16.55.123 255.255.255.0 IP address to e0/3 interface.
### STEP 1
Execute the following commands to enter into configuration mode and assign the IP address to the selected VLAN (Note: Execute one command at a time.):
```bash
configure terminal
```
```bash
int e0/3
```
```bash
ip address 172.16.55.123 255.255.255.0
```
```bash
exit
```
### NOTE
* The configure terminal (conf t) command allows users to enter global mode/configuration commands
* The int e0/3 command selects the Ethernet 0/3 interface.
* The ip address 172.16.55.123 255.255.255.0 command assigns the ip address 172.16.55.123 255.255.255.0 to Ethernet 0/3 interface.
## PART C: Configuring the Domain Name and Enabling SSH
### STEP 1
Execute the following commands to configure the domain name and enable SSH (Note: Execute one command at a time.):
```bash
ip domain name cisco.com
```
```bash
crypto key generate rsa
```
### NOTE
* The ip domain name cisco.com command is used to configure a domain name required for creating the keys used for SSH cryptography.
* The crypto key generate rsa command is used to configure a network device (such as a router or switch) to synchronize its time with the NTP server located at the IP address 192.168.0.1.
### STEP 2
When asked How many bits in the modulus [512], type 1024 and press Enter. 
### Caution 
It may take a few minutes to execute the command.
### STEP 3
Execute the following commands to enable ssh version 2, and configure the username and password, respectively (Note: Execute one command at a time.):
```bash
ip ssh version 2
```
```bash
username root privilege 15 secret ucertify
```
### NOTE
* The ip ssh version 2 command specifies the version of SSH to allow.
* The username root privilege 15 secret ucertify command is used to create a user account on the local switch.
### STEP 4 
Execute the following commands into configuration mode to configure ssh at line mode (Note: Execute one command at a time.):
```bash
line vty 0 4
```
```bash
transport input ssh
```
```bash
login local
```
```bash
exit
```
```bash
line console 0
```
```bash
login local
```
### NOTE
* The line vty 0 4 command specifies the logical VTY (Virtual Terminal) lines used for SSH access.
* The transport input ssh command is used to allow only SSH on the logical range 5 VTY lines (0 - 4).
* The login local command tells the switch to authenticate all incoming virtual terminal sessions via the local username database.
* The line console 0 command is used to move to the console port of the switch.
### STEP 5 
Close all windows. At the PuTTY Exit Confirmation prompt, click Yes. 
### Lab Summary
This lab session provides you with a straightforward and practical understanding of configuring IP and management access. Here's a summary of what you have learned: 
* How to assign the IP address to any VLAN.
* How to configure IP and management access.

Now, you are equipped with the knowledge and skills to configure IP and management access and enhance the efficiency and scalability of your network infrastructure.

## Disclaimer

This repository is for **educational and personal learning purposes only**.  

The original lab content belongs to **uCertify / Ancora Education** and remains their copyrighted material.  
This repository is not affiliated with, endorsed by, or sponsored by uCertify or Ancora Education.  

No copyright infringement is intended.  
Use of any tools or techniques mentioned here should only be performed in authorized, legal environments.
