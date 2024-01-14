# LFI

**Local File Inclusion (LFI)** allows attackers to include and execute files on a server via a web application. This vulnerability can expose sensitive data or lead to remote code execution.

**How LFI Works**

* Results from improper validation of user-supplied input in file inclusion operations.
* Attackers manipulate parameters to access files on the server, such as using `?page=../../etc/passwd` in a URL.

**Typical Vulnerable Code Patterns**

* Common in PHP with `include()` or `require()` functions.
*   Example of vulnerable PHP code:

    ```php
    $file = $_GET['file'];
    include($file);
    ```

**Exploitation Techniques**

* **Basic LFI**: Direct file referencing, e.g., `?file=../../../../etc/passwd`.
* **Null Byte Injection**: Using `%00` or null byte in older PHP versions to bypass checks.
* **PHP Wrappers**: Utilizing PHP streams like `php://filter` for code execution or file disclosure.
* **Log Poisoning**: Injecting code into logs and including the log file to execute code.

**Mitigation Strategies**

* **Input Validation**: Implement whitelisting for acceptable inputs, avoiding dynamic file inclusion.
* **Limit File Access**: Restrict accessible files with server-side controls.
* **Update and Patch**: Regularly update PHP and server software.
* **Error Handling**: Robust error handling to prevent information leakage.

**Impact**

* Potential unauthorized access to sensitive files, credential leakage, source code disclosure, and remote **code execution capabilities**.



{% hint style="info" %}
We should remember that on Windows, directory structures might differ, and log files are located in application-specific paths.
{% endhint %}

**Resources**

* [https://owasp.org/www-community/attacks/Log\_Injection](https://owasp.org/www-community/attacks/Log\_Injection)
