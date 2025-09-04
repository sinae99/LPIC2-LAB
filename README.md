




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

my lab zone name is `slab`.

`named.conf.local`:


<img width="672" height="260" alt="zones" src="https://github.com/user-attachments/assets/a5029b56-a958-4026-af78-23f1ba8ce117" />


`db.slab` for resolving IPs and `db.192` for reverse queries.

then, database files:

`db.slab`:

<img width="710" height="496" alt="dbslab" src="https://github.com/user-attachments/assets/b62343a6-22e9-4b1b-b0ed-875df60ec407" />

`db.192`:

<img width="765" height="532" alt="db192" src="https://github.com/user-attachments/assets/321069fc-fa8e-45a9-b924-cb49f8ca8939" />

and now, a check for config and db files:

<img width="1106" height="320" alt="check" src="https://github.com/user-attachments/assets/9d1108b7-3163-4032-993f-03afc39e26d8" />


now a test from other machines, for example from 192.168.1.10:

<img width="665" height="775" alt="test1" src="https://github.com/user-attachments/assets/c5e39727-7ac4-428b-9ddf-ecce5ce35624" />

or with a basic script to test them all at once: 

<img width="737" height="502" alt="test3" src="https://github.com/user-attachments/assets/a61f1011-1522-447a-9186-f27c60a04aed" />

or from win11:


<img width="942" height="390" alt="test2" src="https://github.com/user-attachments/assets/fabf8f50-3642-40b1-b395-f42cfa8d8391" />

Name Server is ready.


</details> 

### ubuntu3auth (192.168.1.30)


<details> 
 
<summary> LDAP </summary>

</details> 



----------------------------------------------------------------------
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

and another check from another machine:

<img width="1216" height="402" alt="test2 linux side" src="https://github.com/user-attachments/assets/5cf0dc4a-164b-4462-bd6f-88d6b07f2d79" />

File Server is ready.


</details>



<details> 
 
<summary> Suricata </summary>

</details> 

<details> 
 
<summary> NTP </summary>

</details> 






