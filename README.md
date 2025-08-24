

##    My Final Homelab

### Intro

Setting up and creating a virtual network system that simulates a real-world company, including core services such as DNS, web server, NTP, authentication server, and FTP, along with Suricata (and Splunk in next phases).

----------------------------------------------------------------------

### Roles and Assets List

there are 2 separate physical mchines,

 `win11` and `mate24`
 
<img width="1677" height="567" alt="diagram" src="https://github.com/user-attachments/assets/466cb22d-f021-44b3-89ac-5b12473c3dfa" />



 
----------------------------------------------------------------------
### Network Architecture

2 main machines are connected to each other via a home router and get their IP addresses from it.

all VMs are in NAT mode and they can communicate with others via statis routes and port forwarding.

this is a basic visual diagram of the lab:





----------------------------------------------------------------------
### Services and Confs
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
