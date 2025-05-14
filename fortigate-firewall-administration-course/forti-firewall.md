# Fortigate_Firewall_Adminstration_Course

## 1.Initial Setup.
 ### **Fortigate Access**
- We have 3 options to connect to our fortigate unite:
     1) Via Web
     2) Via Cli (Ssh)
     3) Via console

- The appliance come from the factory with the port1 already configured with the IP@ "192.168.1.99"

### LOGIN
- the login is "admin" for user and the password is empty  
 ####
![image](https://github.com/user-attachments/assets/c2744b5c-aa88-4069-957e-17279159129d)

### Change Hostname 

- FortiGate-VM64-KVM # config system global
- FortiGate-VM64-KVM (global) # set hostname FGT1
- FortiGate-VM64-KVM (global) # end
####
![image](https://github.com/user-attachments/assets/cd7951a4-cbb5-4427-bb30-8aa6713158e3)

### Interfaces Configuration

- FGT1 # config system interface
- FGT1 (interface) # edit port1
- FGT1 (port1) # set mode static
- FGT1 (port1) # set ip 192.168.1.99/24
- FGT1 (port1) # set allowaccess http ping ssh
- FGT1 (port1) # set alias LAN1
- FGT1 (port1) # set role lan
- FGT1 (port1) # end
#### 
![image](https://github.com/user-attachments/assets/ff642601-e8e6-4d1c-a555-d58daabc3b86)

### Ping From Cli ###
- Execute Ping

![image](https://github.com/user-attachments/assets/467fc169-4f60-431d-bcd8-39af51552eed)

---
---
---

## 2. How to Enable Intenet Access in Foritgate.
![image](https://github.com/user-attachments/assets/b7b4c83e-8609-4c34-9738-05bd82bfd898)
- Configure the dhcp mode and set role wan for port2 , allowacess for http,https,ssh,telnet
  ![image](https://github.com/user-attachments/assets/54c85a1c-6d71-4c23-8de1-45953218b717)
- Fortigate-firewall # config system interface
- Fortigate-firewall (port2) # set alias WAN-port2
- Fortigate-firewall (port2) # set allowaccess ping ssh telnet https 
- Fortigate-firewall (port2) # set role wan
- Fortigate-firewall (port2) # end
### Aceess via web now.
![image](https://github.com/user-attachments/assets/a4a9b635-daa6-4872-99cf-1b88d101fd9d)
![image](https://github.com/user-attachments/assets/b9351e90-1ef6-4a0e-9276-471e37f3fc4d)
 #### Configure such that the lan network can access the internet.
  - Cretaing Firewall Policy for Lan network to Access internet.
  - Policy & Objects >> Firewall Policy >>  
![image](https://github.com/user-attachments/assets/2a11697b-f7fb-4861-8b68-121c45187169)

![image](https://github.com/user-attachments/assets/e7da11da-73fb-48c4-a108-5287121c2045)
vpcs:ip 192.168.1.100/24 192.168.1.99 
vpcs: ip dns 8.8.8.8
vpcs: Save
![image](https://github.com/user-attachments/assets/ee7b6353-cf34-438b-9b41-ea74072725f1)


## 3.Fotigate Menu [ Kind of Inbuilt Monitor tools for Fortigate]
- Dashborad > FortiView Source.
  
![image](https://github.com/user-attachments/assets/69c5a893-9bfa-44ce-9d55-e536652656af)

## 4.Feature Visibilty [ Some features are not enabled by default , we need to explictily enable it]
- System > Feature Visibility.
###
![image](https://github.com/user-attachments/assets/80cfc94f-8748-46f4-bb76-6bdced2b7e09) 
- You can see that Email filter is disable by default, if we need it we need to enable it.
####
![image](https://github.com/user-attachments/assets/ebdfb33d-9d2c-4ffe-81ee-d6de8031667c)
- After enableing it we can see it in , **Security Profile** ( ***By Clicking in **+** icon we can have more clear details.
####
![image](https://github.com/user-attachments/assets/7cd5a5d2-0f99-45cc-b1e0-7b45976c4c1b)


## 5.How to Create Admin Users?
 - By default we have two admin Profiles.
   ####
   ![image](https://github.com/user-attachments/assets/d5ec2b0b-6ed9-46c2-a787-73a607eea02b)
- We can Create New Profile , where we can limit what shall be given with read access only, what with read/write and what should not be given
- **SYSTEM > ADMIN PROFILES > CREATE NEW >....**
####
![image](https://github.com/user-attachments/assets/dafcef0b-0287-482d-a39c-b6ff2e70fc72)

### Create user with full access.
- **SYSTEM > ADMINISTRATION > CREATE NEW >** ***HERE WE CAN BIND THE ADMIN PROFILE WE CREATED OR USE THE DEFAULT ONES***
####
![image](https://github.com/user-attachments/assets/d80b21ed-1914-48ed-bcc3-2dc2a6cb8e91)


### Create user with limited access.
 - **WE CAN CREATE USER WITH LIMITED ACCESS BY EDITING THE PROFILES**

### Create Admin Users From CLI ##

- FGT # config system admin
- FGT (admin) # edit user
  - new entry 'user' added
- FGT (user) # set vdom root
- FGT (user) # set password superpassword
- FGT (user) # set accprofile super_admin
- FGT (user) # end
- FGT #

![image](https://github.com/user-attachments/assets/97c71073-995c-453d-b9b8-290b5313d075)


## 6.Secure Access
 ### 1) Change the User Password.
   ![image](https://github.com/user-attachments/assets/5c80efa3-a755-4980-95d9-e67be1312b78)
####
![image](https://github.com/user-attachments/assets/f1e1caab-642f-43f8-aa04-33fcc5b7049f)
### 2) Allow only specific IP to access the device.
 - **SYSTEM > Administrator > EDIT > Restrict login to trusted hosts**
![image](https://github.com/user-attachments/assets/e2b2ccf2-3daf-4b12-99a1-c66f2c97577e)
####
![image](https://github.com/user-attachments/assets/458f123e-876b-44fe-88b1-5535b6700397)
####
![image](https://github.com/user-attachments/assets/16c73665-1416-4a45-b5a3-a77da0e3d543)
####
 - **Lets Change the IP address and try again to login***
####
![image](https://github.com/user-attachments/assets/5900f0eb-8a2b-4f91-bc92-e0a0ebe8c633)

- ***Now i can't acccess the device with user rajeev as only 172.16.210.233 is allowed to access***

## 7.Password Recovery.
- **Requirement**
  1) Physical Access
  2) Access via Console
  3) Serial number of Fortigate (***Back of Fortigate or will display when logging via console).
  4) Power off/on the device and access via Console.
-  LOGIN to the fortigate with username: **maintainer**
-  password will be : bcpb"serial number" i.e "bcpbFGVMEV5LDLXJ9907" 
####
- Fortigate-firewall # config system admin
- Fortigate-firewall (admin) # edit admin
- Fortigate-firewall (admin) # set password newpassword@123
- Fortigate-firewall (admin) # end
       
     
## 8. Address Objects.
 - **192.168.10.0/24** is my DMZ network alllow it to be access via internet.
 - We can Create the address object and use that in firewall policy.
#### 
- Config PORT-4 as DMZ 
![image](https://github.com/user-attachments/assets/588941ed-d55e-46f8-a46f-34923ca63f65)
####
- Config Address [ **POLICY&OBJECTS > ADDRESS > CREATE NEW** ]
  ![image](https://github.com/user-attachments/assets/e0eda05a-25ef-46e2-b07e-a19cc8cbc0b7)
####
- Config firewall policy [ **POLICY & OBJECTS > FIREWALL POLICY > CREATE NEW** ]
![image](https://github.com/user-attachments/assets/c416f591-ef05-430b-a7b5-14a0104f299a)



   
