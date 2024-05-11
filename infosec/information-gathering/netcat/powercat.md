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

# Powercat

**Powercat** is a PowerShell tool that mimics the functionality of Netcat, providing network connectivity for reading, writing, and relaying data across network connections. It's a versatile tool for network testing and debugging, particularly useful in Windows environments where traditional Unix tools may not be available.

**Key Features:**

* Capable of setting up both TCP and UDP connections.
* Supports file transfers, port forwarding, and shell interactions.
* Can be used as a client or a server for network communications.
* Allows for easy data transfer between machines in a PowerShell environment.

**Command-Line Examples:**

*   **Create a TCP listener on a specific port**:

    ```powershell
    powercat -l -p 1234
    ```
*   **Connect to a TCP server**:

    ```powershell
    powercat -c 192.168.1.5 -p 1234
    ```
*   **Send a file over TCP**:

    ```powershell
    powercat -c 192.168.1.5 -p 1234 -i C:\path\to\file.txt
    ```
*   **Receive a file over TCP**:

    ```powershell
    powercat -l -p 1234 -o C:\path\to\output.txt
    ```
*   **Create an encrypted connection using SSL**:

    ```powershell
    powercat -c 192.168.1.5 -p 1234 -ssl
    ```

**Installation:**

Powercat is a script that can be easily imported into any PowerShell session. It can be sourced from GitHub and loaded directly into PowerShell:

```powershell
IEX (New-Object Net.WebClient).DownloadString('https://github.com/path/to/powercat.ps1')
```

