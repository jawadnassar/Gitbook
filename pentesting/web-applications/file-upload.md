# File Upload

**File Upload Vulnerabilities** arise when a web application allows users to upload files without proper validation or sanitization, potentially leading to unauthorized file execution, data breaches, or server compromise.

**How File Upload Vulnerabilities Work**

* Attackers exploit inadequate validation of uploaded files to upload and execute malicious scripts or overwrite critical files.
* Commonly targeted areas include web forms allowing image, document, or media uploads.

**Typical Vulnerable Scenarios**

* Lack of proper file type validation, allowing executable scripts to be uploaded.
* Insecure file storage, where uploaded files are accessible through web browsers.

**Exploitation Techniques**

* **Malicious File Upload**: Uploading files with scripts (PHP, JavaScript) embedded in seemingly benign files (images, PDFs).
* **Extension Tampering**: Changing the file extension to bypass validation checks (e.g., `evil.php.jpg`).
* **Path Traversal in File Names**: Using path traversal sequences (e.g., `../../`) in file names to overwrite critical files.

**Mitigation Strategies**

* **Strict Validation**: Validate file type by checking MIME types and file extensions both on client-side and server-side.
* **File Type Verification**: Implement server-side checks to verify the actual type of the uploaded file (e.g., magic numbers for images).
* **Storage and Access**: Store uploaded files in a directory outside of the webroot, with indirect access through a script.
* **File Execution Prevention**: Configure server settings to prevent execution of files in upload directories.
* **Regular Scanning**: Periodically scan upload directories for unexpected or potentially malicious files.
