---
coverY: 0
layout:
  cover:
    visible: false
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Hydra

Hydra is a fast and flexible password-cracking tool used to perform brute force attacks against various network services.&#x20;

**Key Features**

1. **Multi-threading**: Hydra supports multi-threading, which allows it to perform attacks much faster than single-threaded tools.
2. **Protocol Support**: Hydra supports a wide range of protocols, including but not limited to SSH, FTP, HTTP, HTTPS, SMB, and more.
3. **Customizable**: Users can specify custom parameters for different protocols and services, making Hydra highly adaptable to various scenarios.
4. **Efficient**: Hydra can resume interrupted attacks, saving time and resources.

**Usage and Examples**

**Basic Syntax**:

```bash
hydra [options] target service
```

**Example 1: Brute Force SSH Login**

```bash
hydra -l username -P passwords.txt ssh://192.168.1.100
```

* `-l username`: Specifies the username to use in the attack.
* `-P passwords.txt`: Specifies the file containing the list of passwords.
* `ssh://192.168.1.100`: Specifies the target SSH service.

**Example 2: Brute Force HTTP Login**

```bash
hydra -l admin -P passwords.txt http-post-form "/login.php:username=^USER^&password=^PASS^:F=incorrect"
```

* `-l admin`: Specifies the username to use in the attack.
* `-P passwords.txt`: Specifies the file containing the list of passwords.
* `http-post-form`: Specifies the method and form parameters for the HTTP POST request.
* `"/login.php:username=^USER^&password=^PASS^:F=incorrect"`: Defines the form parameters and the failure condition.

**Example 3: Brute Force FTP Login**

```bash
hydra -l anonymous -P passwords.txt ftp://192.168.1.100
```

* `-l anonymous`: Specifies the username to use in the attack.
* `-P passwords.txt`: Specifies the file containing the list of passwords.
* `ftp://192.168.1.100`: Specifies the target FTP service.

**Tips and Tricks**

1.  **Threading**: Use the `-t` option to specify the number of threads. More threads can speed up the attack but might cause network congestion.

    ```bash
    hydra -t 16 -l admin -P passwords.txt ssh://192.168.1.100
    ```
2.  **Verbose Mode**: Use the `-v` option to get detailed output about the progress of the attack.

    ```bash
    hydra -v -l admin -P passwords.txt ftp://192.168.1.100
    ```
3.  **Resume Attack**: If an attack is interrupted, use the `-R` option to resume it.

    ```bash
    hydra -R
    ```

**Practical Considerations**

* **Targeting**: Ensure you have permission to perform brute force attacks on the target systems to avoid legal issues.
* **Dictionary Files**: Use comprehensive password lists to increase the chances of successful brute force attacks.
* **Network Impact**: Be mindful of the potential impact on the network and target services when running high-thread count attacks.

