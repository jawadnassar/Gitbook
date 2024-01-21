# PHP Wrappers

**PHP Wrappers** are powerful tools in PHP that modify how file operations are handled, often exploited in LFI attacks to execute or disclose code.

**How PHP Wrappers Work in LFI**

* Serve as a layer that interprets file streams in various ways, allowing attackers to manipulate file handling in PHP.
* Exploited in file inclusion functions (`include`, `require`) to fetch or transform file data in malicious ways.

**Common PHP Wrappers and Usage Examples**

* **php://filter**: Converts file data through filters. Attackers use it to read PHP files in base64 encoding.
  * Example: `include('php://filter/read=convert.base64-encode/resource=index.php');`
* **php://input**: Reads raw data from the request body, used to execute code by including `php://input` and sending code in the request body.
  * Example: `include('php://input');` and POSTing PHP code.
* **php://memory** and **php://temp**: Allow access to read/write temporary data streams. Can be used to execute transient code that doesn't leave traces on the disk.
* **data://**: Allows inclusion of inline data. Can be exploited to execute arbitrary data as code.
  * Example: `include('data://text/plain;base64,SGVsbG8sIFdvcmxkIQ==');`

**Mitigation Strategies**

* **Disable Dangerous Wrappers**: Configure `php.ini` to disallow certain wrappers (e.g., `php://filter`, `php://input`) if they are not required.
* **Input Validation**: Implement rigorous input validation to reject wrapper syntax or unexpected patterns.
* **Use of `allow_url_include`**: Set `allow_url_include` to `Off` in `php.ini` to prevent the inclusion of files from remote locations.
