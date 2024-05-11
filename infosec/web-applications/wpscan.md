---
cover: >-
  https://images.unsplash.com/photo-1560472354-0088b5dc9d8d?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw0fHx3b3JkcHJlc3N8ZW58MHx8fHwxNzE1NDQ2MjQ5fDA&ixlib=rb-4.0.3&q=85
coverY: 0
layout:
  cover:
    visible: true
    size: full
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

# WPScan

**WPScan** is a free, open-source security tool designed for WordPress, used primarily to identify security vulnerabilities. It is well-suited for black box testing and offers comprehensive scanning capabilities.

**Key Features:**

* Scans for vulnerabilities in WordPress core, plugins, and themes.
* Enumerates users, plugins, themes, and weak passwords.
* Integrates with the WPScan Vulnerability Database.

**Command-Line Examples:**

*   **Scan for Vulnerabilities**:

    ```sh
    wpscan --url example.com
    ```
*   **Enumerate Users**:

    ```sh
    wpscan --url example.com --enumerate u
    ```
*   **Brute Force Password Attack**:

    ```sh
    wpscan --url example.com --passwords /path/to/passwords.txt --usernames admin
    ```
*   **Check for Vulnerable Plugins**:

    ```sh
    wpscan --url example.com --enumerate vp
    ```



Regular scanning with WPScan is recommended as part of a robust WordPress security strategy.
