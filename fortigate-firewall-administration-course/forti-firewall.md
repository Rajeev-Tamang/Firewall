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

### Change Hostname 

- FortiGate-VM64-KVM # config system global
- FortiGate-VM64-KVM (global) # set hostname FGT1
- FortiGate-VM64-KVM (global) # end

### Interfaces Configuration

- FGT1 # config system interface
- FGT1 (interface) # edit port1
- FGT1 (port1) # set mode static
- FGT1 (port1) # set ip 192.168.1.99/24
- FGT1 (port1) # set allowaccess http ping ssh
- FGT1 (port1) # set alias LAN1
- FGT1 (port1) # set role lan
- FGT1 (port1) # end

### Ping From Cli ###
- Execute Ping
---
---
---

## 2. How to Enable Intenet Access in Foritgate.

## 3.Fotigate Menu [ Kind of Inbuilt Monitor tools for Fortigate]

## 4.Feature Visibilty [ Some features are not enabled by default , we need to explictily enable it]
 - System > Feature Visibility.

## 5.How to Create Admin Users?

## 6.Secure Access

## Password Recovery.

