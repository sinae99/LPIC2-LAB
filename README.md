

##    My Final Homelab

### Intro

Setting up and creating a virtual network system that simulates a real-world company, including core services such as DNS, web server, NTP, authentication server, and FTP, along with Splunk and Suricata.

----------------------------------------------------------------------

### Roles and Assets List

there are 2 separate physical mchines,

 `win11` and `mate24`
 
<img width="1638" height="502" alt="diagram1" src="https://github.com/user-attachments/assets/baafdc4d-90fb-4eca-8175-9636c51e1c2b" />


 
----------------------------------------------------------------------
### Network Architecture

2 main machines are connected to each other via a home router and get their IP addresses from it.

all VMs are in NAT mode and they can communicate with others via statis routes and port forwarding.

this is a basic visual diagram of the lab:


<img width="1722" height="766" alt="diagram2" src="https://github.com/user-attachments/assets/d1c219a1-c9ab-48c9-b07d-a8ddcaa397a5" />


----------------------------------------------------------------------
### Network Connections
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
