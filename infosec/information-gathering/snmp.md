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

# SNMP

1. **SNMP (Simple Network Management Protocol):**
   * **What it does:** SNMP is a protocol used for managing and monitoring devices on a network.
   * **How it works:** It allows devices (like routers, servers, printers) to communicate their status and information to a central management system.
   * **Key idea:** Think of it like a language that devices use to report their health and status to a network manager.
2. **MIB (Management Information Base):**
   * **What it is:** MIB is like a dictionary that defines the structure and content of the information SNMP-enabled devices can provide.
   * **How it works:** It specifies what kind of information can be retrieved from a device and how to interpret that information.
   * **Key idea:** Imagine MIB as a guide that tells you what each device is capable of telling you and how to understand the information it provides.

| MIB Value              | Description      |
| ---------------------- | ---------------- |
| 1.3.6.1.2.1.25.1.6.0   | System Processes |
| 1.3.6.1.2.1.25.4.2.1.2 | Running Programs |
| 1.3.6.1.2.1.25.4.2.1.4 | Processes Path   |
| 1.3.6.1.2.1.25.2.3.1.4 | Storage Units    |
| 1.3.6.1.2.1.25.6.3.1.2 | Software Name    |
| 1.3.6.1.4.1.77.1.2.25  | User Accounts    |
| 1.3.6.1.2.1.6.13.1.3   | TCP Local Ports  |

SNMP can be leveraged to gather information about a target network and its devices.&#x20;



**nmap**

To scan for open SNMP ports (161), using **-sU** option to perform UDP scanning and the **--open** option to limit the output and display only open ports

<pre class="language-shell-session"><code class="lang-shell-session"><strong>kali@kali:~$ sudo nmap -sU --open -p 161 192.168.100.1-254 -oG open-snmp.txt
</strong></code></pre>

**onesixtyone**

onesixtyone brute forces an attack against a list of ips.

Check if the default community string "public" is valid on a target:

```shell-session
kali@kali:~$ onesixtyone -c public target_ip
```

&#x20;**snmpwalk**&#x20;

snmpwalk \[APPLICATION OPTIONS] \[COMMON OPTIONS] \[OID]

Here's an example of using `snmpwalk` with a specific OID:

<pre class="language-shell-session"><code class="lang-shell-session"><strong>kali@kali:~$ snmpwalk -v 2c -c community_string target_ip 1.3.6.1.2.1.1
</strong></code></pre>

* Replace `community_string` with a valid SNMP community string.
* Replace `target_ip` with the IP address or hostname of the SNMP-enabled device.
* The OID `1.3.6.1.2.1.1` corresponds to the SNMP MIB-II system group, which includes information about the system.

This command will perform an SNMP walk on the specified OID, displaying information related to the system group. You can replace the OID with any other valid OID to explore different parts of the SNMP tree and retrieve specific information.



**Resources:**

* [https://book.hacktricks.xyz/network-services-pentesting/pentesting-snmp](https://book.hacktricks.xyz/network-services-pentesting/pentesting-snmp)
* [https://www.kali.org/tools/onesixtyone/](https://www.kali.org/tools/onesixtyone/)
* [https://www.kali.org/tools/snmpcheck/](https://www.kali.org/tools/snmpcheck/)
* [https://linux.die.net/man/1/snmpwalk](https://linux.die.net/man/1/snmpwalk)
