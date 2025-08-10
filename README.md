

##    My Final Homelab

### Intro

Setting up and creating a virtual network system that simulates a real-world company, including core services such as DNS, web server, NTP, authentication server, and FTP, along with Splunk and Suricata.

----------------------------------------------------------------------

### Roles and Assets List

there are 2 separate physical mchines,

 `win11` and `mate24`
 
<img width="1793" height="556" alt="diagram" src="https://github.com/user-attachments/assets/e977a6fd-8e6a-4f20-9118-1e40e8a774d3" />

 

### Network Architecture
----------------------------------------------------------------------
### Network Connections
----------------------------------------------------------------------
### Services and Confs
<details>
<summary>DNS (Bind)</summary>
  
- create zone
<img width="737" height="422" alt="image" src="https://github.com/user-attachments/assets/bd8f00e4-70ec-4565-92ab-0d1ae9f69dde" />


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
