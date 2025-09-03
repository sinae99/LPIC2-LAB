




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
<details>
<summary>DNS (Bind)</summary>
  
- create zone


</details>

<details>
<summary>shared files (Samba)</summary>
  
- Configure `/etc/samba/smb.conf` to create a shared directory.

- Set up user accounts and permissions for accessing the shared folder.

- Ensure the Samba service is running and enabled to start on boot.


  
- create zone

- create db files

</details>

<details>
  
<summary>web server (Nginx)</summary>
  
- create zone

- create db files

</details>

<details>
  
<summary>NTP</summary>
  
- create zone

- create db files

</details>

<details>
  
<summary>Authentication server (LDAP)</summary>
  
- create zone

- create db files

</details>


----------------------------------------------------------------------
