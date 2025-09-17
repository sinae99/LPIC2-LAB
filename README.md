


# LPIC2 LAB

## Intro

Setting up and creating a virtual network system that simulates a real-world company, including core services such as DNS, web server, NTP, authentication server, and FTP, along with Suricata .

----------------------------------------------------------------------

## Roles and Assets List

there are 2 separate physical machines,

 `win11` and `mate24`
 


<img width="1540" height="615" alt="assest list2" src="https://github.com/user-attachments/assets/1adff12c-fd72-4c39-b202-de872447f8f3" />



 
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


This is my main machine, serving as the central control node for my lab and also running my virtual servers.

im using WSL to have better connectivity with my machines.

WSL, by default, is in a private network created by Windows, but I need it to be in the same network as my nodes, so I set it to **Mirrored**:

for this i must change (or add) `.wslconfig` file:



<img width="585" height="258" alt="wslconfi" src="https://github.com/user-attachments/assets/934cd872-c7d7-4008-a116-ac0ab6e7b8fe" />



now WSL has the same ip address as my Windows 11:



<img width="1380" height="692" alt="ip" src="https://github.com/user-attachments/assets/b72f269a-2dbc-47e3-9696-c6af24fc8e96" />




I use **MobaXterm** to access all of my nodes by establishing SSH connections:



<img width="1679" height="896" alt="mobaxterm" src="https://github.com/user-attachments/assets/612f13fc-c335-4167-8c2a-9c3c67d4826b" />









</details>


### ubuntu1web (192.168.1.10)


<details> 
 
<summary> Nginx </summary>

i have 3 sample websites to test and configure:

1 - sina-personal-page.slab

2 - webtest.slab

3 - nginx-default.slab

html files at `/var/www`:

<img width="472" height="170" alt="varwww" src="https://github.com/user-attachments/assets/56ffcc47-5c0a-4afc-8add-ab8a16e78dc1" />



config files at `/etc/nginx/sites-available`:

<img width="853" height="176" alt="availabe" src="https://github.com/user-attachments/assets/03cbdea3-9f2f-491f-b596-35241c2daa3b" />


server blocks for each virtual host:


<img width="702" height="330" alt="sinaconf" src="https://github.com/user-attachments/assets/aab52327-7123-40a7-8013-d2a79e19a2e1" />

and like this for other ones.

i used `server_name` directive to get help from my DNS server because all hosts are serving at 192.168.1.10.

`access_log` and `error_log` for logging and to be used by syslog in next phases.

and location block for matching specific URIs. (in case of not found URI it will return 404)


creating sym link for sites and enabling them:

<img width="1448" height="222" alt="enable" src="https://github.com/user-attachments/assets/010d9b01-e919-4289-ac73-5addf3c05d56" />

now final conf check:

<img width="827" height="151" alt="check" src="https://github.com/user-attachments/assets/9c9b6c87-5e68-4840-9f69-0e086e7ea1e2" />

configs looks good, now time to check the sites.

because im using ubuntu server i dont have GUI so i use `lynx` to view my sites in terminal:

<img width="616" height="125" alt="lynx" src="https://github.com/user-attachments/assets/3573e729-50cb-47cc-9669-22411baf2b97" />

`sina-personal-page.slab`
 
<img width="1290" height="935" alt="sina" src="https://github.com/user-attachments/assets/4c2efaad-6d1d-4487-ac23-dc37cf1b688b" />

`nginx-default.slab`

<img width="1595" height="528" alt="nginx" src="https://github.com/user-attachments/assets/253c9348-1c9f-440c-8d6c-29871439d477" />


`webtest.slab`

<img width="1577" height="508" alt="webtest" src="https://github.com/user-attachments/assets/4f3c8acf-828b-4598-a043-89d8b69fe641" />


now a check from my other machine with GUI:



<img width="1140" height="542" alt="sinaa" src="https://github.com/user-attachments/assets/659395dc-358a-4fb0-8728-9c919b49f99a" />


<img width="1352" height="430" alt="nginx" src="https://github.com/user-attachments/assets/01e3828b-0028-4cef-8344-5907e6491745" />


<img width="781" height="280" alt="webtest" src="https://github.com/user-attachments/assets/2c10f6b2-8be6-4a57-a35d-c81ff19d9e3a" />


Web Server is ready.




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




### server side
----------------------------------------------------------------------------------------------------------

after installing the OpenLDAP packages, `slapd` & `ldap-utils`, i run  `dpkg-reconfigure slapd` command to renew the configs.

then defining my hierarchy:

**Key LDAP Values:**

DNS Domain Name ---> `slab`

Organization Name ---> `SLAB`

Database Backend ---> `MDB` (Modern Database)


**Organizational Units (OU):**

i must create a logical structure for organizing users and groups, so i need a LDIF (LDAP Data Interchange Format) file:

`base.ldif`:

<img width="502" height="220" alt="base" src="https://github.com/user-attachments/assets/0aa1b0b6-433e-472a-bc53-cb45c5ee2f0c" />

and now :

```
ldapadd -x -D "cn=admin,dc=slab" -W -f base.ldif
```

`-x`: to enable simple auth instead of other ways

`-D "cn=admin,dc=slab"` : to specify the DN (Distinguished Name) and the name of the user who is performing the command

`-W` : ask password for DN

`-f base.ldif` : read from base.ldif file

now my directory is set up.



**Users and Groups:**

i have 4 groups and 5 users for my lab:

**groups** ---> webadmins, itadmins, fileusers, devs



**users** ---> sina, jay, s-admin, user1, user2



each of users and groups has its own .ldif file:


<img width="561" height="463" alt="treegu" src="https://github.com/user-attachments/assets/5e58f8cb-4e71-415f-8056-4911c1f58ae4" />



<img width="697" height="365" alt="groups" src="https://github.com/user-attachments/assets/a55bad7e-938d-40d1-a12c-5fae605f15b7" />



<img width="723" height="677" alt="users" src="https://github.com/user-attachments/assets/16c40ec9-83cd-4c0d-945c-24b8818d29a2" />


object classes that i used:

`inetOrgPerson` : a fundamental object class for representing people within an organization

`cn` : Common Name, user full name

`sn` : Surname, user last name

----------


`posixAccount` : for integrating LDAP users with Linux based systems

`uid` :  user login name

`uidNumber` : unique numerical ID for the user 

`gidNumber` : primary group number for the user

`homeDirectory` : path to the user home directory

`loginShell` : default shell for the user

----------


`shadowAccount` : for more advanced password management

`shadowLastChange` : date of the last password change

`shadowMax` : maximum number of days a password is valid before it expires

----------






other `.ldif` files to add users to groups:



<img width="900" height="527" alt="add" src="https://github.com/user-attachments/assets/fa288e40-74ed-4f86-b7ab-7b358761b94c" />





**Verifying the Directory:**


using the `ldapsearch` command to search and retrieve information from LDAP server and final check:

```
ldapsearch -x -W -D "cn=admin,dc=slab" -b "dc=slab"
```

<img width="772" height="670" alt="check1" src="https://github.com/user-attachments/assets/f14fd9fb-2a77-4914-8abf-f20b17f9c74c" />


<img width="731" height="688" alt="check2" src="https://github.com/user-attachments/assets/9ff91540-b921-4ed3-b38e-5e179d7dd482" />


Server side is ready.


### Client side
----------------------------------------------------------------------------------------------------------






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






