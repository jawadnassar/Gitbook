# SmbShare

`impacket` is a collection of Python classes for working with network protocols, and it's a popular toolset among penetration testers and security professionals for tasks such as creating and sending packets, transferring files, and executing commands remotely. Here’s a concise guide on how to use `impacket` on Kali Linux, focusing on a commonly used script like `smbserver.py` which is part of the Impacket suite.

#### Step-by-Step Guide to Use `impacket` on Kali Linux

**Step 1: Installation**

First, ensure that `impacket` is installed on your Kali Linux. If it's not installed, you can install it using the following command:

```bash
sudo apt-get update
sudo apt-get install impacket-scripts python3-impacket
```

**Step 2: Setting Up a SMB Server**

One of the common tools in `impacket` is `smbserver.py`, which allows you to quickly set up an SMB server that can be used to share files or execute commands. Here’s how to set it up:

1. **Create a Share Directory:** Create a directory that will be shared via SMB

{% hint style="info" %}
In some scenarios, it might be necessary to decrease the permissions of an SMB (Server Message Block) share directory. This can be achieved using the `chmod` command in a Linux or Unix-like operating system.
{% endhint %}

```bash
mkdir /tmp/smbshare
```

**Start the SMB Server:** Use `smbserver.py` to share the directory. This command will start an SMB server with the share name `SHARENAME` and the shared directory `/tmp/smbshare`.

```bash
sudo smbserver.py SHARENAME /tmp/smbshare
```

Optionally, you can add `-smb2support` to enable SMB2 support:

```bash
sudo smbserver.py -smb2support SHARENAME /tmp/smbshare
```

On Kali Linux, the command below should work immediately, saving you from the above steps.

```bash
sudo impacket-smbserver SHARENAME -smb2support /tmp/smbshare
```

{% hint style="info" %}
In instances where authentication is required, utilize the `-user` and `-password` parameters&#x20;
{% endhint %}

**Step 3: Accessing the Share**

From a Windows machine or another Linux system, you can now access the SMB share using the server’s IP address and the share name. For example, from a Windows Run dialog (`Win + R`), you can type:

```
\\<IP_OF_KALI_MACHINE>\SHARENAME
```

Replace `<IP_OF_KALI_MACHINE>` with the actual IP address of your Kali Linux machine.

**Step 4: Using Other Impacket Tools**

Impacket comes with a variety of other scripts and tools for different purposes, such as `psexec.py` for executing processes remotely, `getTGT.py` for Kerberos ticket operations, etc. Each tool has specific parameters and usage, which can generally be viewed by running the tool with the `-h` or `--help` flag to see its usage instructions.

#### Example of Running `psexec.py`

This example demonstrates running a command on a remote system using the `psexec.py` tool from Impacket:

```bash
psexec.py domain/username:password@<TARGET_IP> cmd.exe
```

This command will open a `cmd.exe` shell on the target machine if the credentials and network settings permit.

**Step 5: Clean Up**

After your testing or operations, make sure to stop any services you started and clean up any files or configurations if necessary, to maintain security and cleanliness of your testing environment.

Impacket's scripts are powerful tools for network interaction and testing. Always ensure you have proper authorization before using these tools in any network environment other than your own lab.
