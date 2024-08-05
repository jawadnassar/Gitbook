---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Server Message Block (SMB)

Server Message Block (SMB) is a [communication protocol](https://en.wikipedia.org/wiki/Communication\_protocol)[\[1\]](https://en.wikipedia.org/wiki/Server\_Message\_Block#cite\_note-1) mainly used by [Microsoft Windows](https://en.wikipedia.org/wiki/Microsoft\_Windows) equipped computers normally used to share files, printers, serial ports, and miscellaneous communications between [nodes](https://en.wikipedia.org/wiki/Node\_\(networking\)) on a [network](https://en.wikipedia.org/wiki/Computer\_network)

* **Definition**: Server Message Block (SMB) is a network protocol used for sharing files, printers, and other resources between computers on a network.
* **Functionality**: SMB facilitates communication between devices for file and printer sharing, as well as providing access to shared resources on a network.
* **Versions**: Various versions of SMB exist, with SMB1 being the oldest and less secure, and newer versions (SMB2, SMB3) offering improved security features and performance enhancements.
* **Port**: SMB typically operates over TCP ports 139 and 445, and it allows users to access shared files and resources on a remote server.
* **Authentication**: SMB supports multiple authentication mechanisms, including user names and passwords, making it essential for securing shared network resources.
* **Vulnerabilities**: Historically, SMB has been susceptible to security vulnerabilities, such as the infamous WannaCry ransomware exploiting a flaw in SMB to spread across networks.
* **Security Features**: Newer versions of SMB include enhanced security features, like message signing and encryption, to mitigate vulnerabilities and protect against unauthorized access.
* **Common Usage**: SMB is commonly used in Windows environments for seamless file and printer sharing, but it is also implemented in other operating systems.
* **Integration**: Many network-attached storage (NAS) devices and file servers use SMB to enable easy access and sharing of files within a local network.

\
Server Message Block (SMB) uses the following ports:

* **SMB over NetBIOS (Legacy):**
  * Port 137 (UDP) - NetBIOS name service
  * Port 138 (UDP) - NetBIOS datagram service
  * Port 139 (TCP) - NetBIOS session service
* **SMB over TCP/IP:**
  * Port 445 (TCP) - Used for SMB over TCP without NetBIOS.

Enumeration SMB shares within a windows enviroment via net view.

```powershell
C:\Users\tester> net view \\computername /all
```

`/all` Displays detailed information about shared resources, including hidden ones, on the local computer. Administrative shares ends with `$`.



**Enumerate via Nmap**

```shell-session
kali@kali:~$ nmap -v -p 139,445 -oG output-file.txt 192.168.100.1-254
```

**NMAP NSE Scripts**

```shell-session
kali@kali:~$ ls -1 /usr/share/nmap/scripts/smb*
/usr/share/nmap/scripts/smb2-capabilities.nse
/usr/share/nmap/scripts/smb2-security-mode.nse
/usr/share/nmap/scripts/smb2-time.nse
/usr/share/nmap/scripts/smb2-vuln-uptime.nse
/usr/share/nmap/scripts/smb-brute.nse
/usr/share/nmap/scripts/smb-double-pulsar-backdoor.nse
/usr/share/nmap/scripts/smb-enum-domains.nse
/usr/share/nmap/scripts/smb-enum-groups.nse
/usr/share/nmap/scripts/smb-enum-processes.nse
/usr/share/nmap/scripts/smb-enum-sessions.nse
/usr/share/nmap/scripts/smb-enum-shares.nse
/usr/share/nmap/scripts/smb-enum-users.nse
/usr/share/nmap/scripts/smb-os-discovery.nse
...
```

#### nbtscan <a href="#nbtscan" id="nbtscan"></a>

NBTscan is a program for scanning IP networks for NetBIOS name information. It sends NetBIOS status query to each address in supplied range and lists received information in human readable form. For each responded host it lists IP address, NetBIOS computer name, logged-in user name and MAC address (such as Ethernet).

```shell-session
kali@kali:~$ sudo nbtscan -r 192.168.100.0/24
Doing NBT name scan for addresses from 192.168.50.0/24

IP address       NetBIOS Name     Server    User             MAC address
------------------------------------------------------------------------------
192.168.100.22   SAMBAWEB        <server>  SAMBAWEB          00:00:00:00:00:00
192.168.100.33   SAMBA           <server>  SAMBA             00:00:00:00:00:00
...
```



**enum4linux**

&#x20;`enum4linux` will interact with the target SMB server and attempt to extract information such as user names, group names, shares, policies, and other details.

```bash
enum4linux -a target_ip
```

* `enum4linux`: The command name.
* `-a`: An option that tells `enum4linux` to perform all possible enumeration tasks.
* `target_ip`: The IP address of the target Windows machine with SMB services.





**Resources:**

* [https://en.wikipedia.org/wiki/Server\_Message\_Block](https://en.wikipedia.org/wiki/Server\_Message\_Block)
* [https://www.kali.org/tools/nbtscan/](https://www.kali.org/tools/nbtscan/)
