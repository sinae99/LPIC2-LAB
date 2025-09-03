




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

### win11 (192.168.1.100)

<details> 
 
<summary> Control Node </summary>

</details>


### ubuntu1web (192.168.1.10)

<details> 
 
<summary> Nginx </summary>


</details> 


### ubuntu2dns (192.168.1.20)

<details> 
 
<summary> BIND </summary>

</details> 

### ubuntu3auth (192.168.1.30)

<details> 
 
<summary> LDAP </summary>

</details> 




### mate24 (192.168.1.200)

<details> 
 
<summary> SAMBA  </summary>

`/etc/samba/smb.conf` :

<img width="415" height="182" alt="smb conf" src="https://github.com/user-attachments/assets/5292c9fc-2a62-44cb-9ce5-9880fb4c7ec3" />

after modifying the share object, its time to create the `smbuser` and set password for that with `smbpasswd` command, 

and then a test file and permission and user check:

<img width="555" height="145" alt="smbuser" src="https://github.com/user-attachments/assets/ed8d7b17-b983-4458-a64a-68d66daab143" />


<img width="638" height="206" alt="tree -pug" src="https://github.com/user-attachments/assets/12077199-3cd8-486d-a16f-cdd1e082a0b6" />

now verify connection and do some change from windows side:

<img width="638" height="458" alt="win check" src="https://github.com/user-attachments/assets/5d80d717-68cb-40fe-ad13-855d5a449afe" />

and after entering the credential for smbuser:

<img width="872" height="438" alt="test windows side" src="https://github.com/user-attachments/assets/c91e8880-4e11-4dfb-943f-fead6e7d3428" />

and now once again to check the upload from windows side:

<img width="1550" height="467" alt="test linux side" src="https://github.com/user-attachments/assets/cabe2325-03b6-440d-a892-d0e3457c2663" />

now, file server is ready.


</details>



<details> 
 
<summary> Suricata </summary>

</details> 

<details> 
 
<summary> NTP </summary>

</details> 





----------------------------------------------------------------------
