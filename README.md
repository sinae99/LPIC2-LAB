
### Project FAILED - uncompleted repo



## Intro

Setting up and creating a virtual network system that simulates a real-world company, including core services such as DNS, web server, NTP, authentication server, and FTP, along with Suricata .

----------------------------------------------------------------------

## Roles and Assets List

there are 2 separate physical mchines,

 `win11` and `mate24`
 
<img width="1677" height="567" alt="diagram" src="https://github.com/user-attachments/assets/466cb22d-f021-44b3-89ac-5b12473c3dfa" />



 
----------------------------------------------------------------------
## Network Architecture

2 main machines are connected to each other via a home router and get their IP addresses from it.

all VMs are in NAT mode and they can communicate with others via statis routes and port forwarding.

this is a basic visual diagram of the lab:

<img width="1890" height="693" alt="diagram" src="https://github.com/user-attachments/assets/f714d68b-01de-4877-b4c9-398640ebd88b" />



### Virtual Network Layer :

virtualBox "Host-Only Network" creates the core isolated network segment for the VMs, and the host machine acts as a router and gateway, providing internet access to users.

to provide internet for my network (`10.10.100.1`), Internet Connection Sharing (ICS) in win11 is enabled and also the `IPEnableRoute` registry key is set to 1.



<img width="1025" height="215" alt="image" src="https://github.com/user-attachments/assets/02cd9b9a-51dd-4427-9602-98984388858c" />



<img width="935" height="556" alt="image" src="https://github.com/user-attachments/assets/c942ce23-607b-47a2-9937-3d8012d89964" />


The host's physical Wi-Fi adapter shares its internet connection with the VirtualBox Host-Only adapter (10.10.100.1).

so finally network traffic follows this path:

`ubuntu (10.10.100.10) → win11 Gateway (10.10.100.1) → Windows ICS Routing → Physical Wi-Fi Adapter → Home Router → Internet` 



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
