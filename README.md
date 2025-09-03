




## Intro

Setting up and creating a virtual network system that simulates a real-world company, including core services such as DNS, web server, NTP, authentication server, and FTP, along with Suricata .

----------------------------------------------------------------------

## Roles and Assets List

there are 2 separate physical mchines,

 `win11` and `mate24`
 

<img width="1390" height="567" alt="assest list" src="https://github.com/user-attachments/assets/d6e9776d-7bc1-4b5b-a198-0b1061191809" />



 
----------------------------------------------------------------------
## Network Architecture

2 main machines are connected to each other via a home router and get their IP addresses from it.

all VMs are in Bridged mode (home router is acting as DHCP server) and they can communicate with each other in `192.168.1.x` .

this is a basic visual diagram of the lab:

<img width="1782" height="713" alt="diagram" src="https://github.com/user-attachments/assets/0cda909a-a3c1-4b52-9b24-6f4b5ac85714" />

(Blue lines: Virtual Machines)

(Red lines: Physical Hosts)


----------------------------------------------------------------------
## Services and Confs

just only a brief summary of configs and settings and test for each machine and service:

### MATE24 (192.168.1.200)

#### SAMBA Server 

`/etc/samba/smb.conf` :

<img width="415" height="182" alt="smb conf" src="https://github.com/user-attachments/assets/5292c9fc-2a62-44cb-9ce5-9880fb4c7ec3" />

after modifying the share object, its time to create the `smbuser` and set password for that with `smbpasswd` command, 

and then a test file and permission and user check:

<img width="555" height="145" alt="smbuser" src="https://github.com/user-attachments/assets/ed8d7b17-b983-4458-a64a-68d66daab143" />


<img width="638" height="206" alt="tree -pug" src="https://github.com/user-attachments/assets/12077199-3cd8-486d-a16f-cdd1e082a0b6" />



----------------------------------------------------------------------
