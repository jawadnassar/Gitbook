# Dirb

**Dirb** is a web content scanner and an essential tool in the arsenal of penetration testers and security researchers. It's designed to brute-force discover interesting directories and files on web servers. Using wordlists, Dirb will systematically check for the existence of specific paths, revealing hidden directories, vulnerable scripts, and potential points of entry that are not typically found through traditional browsing.

#### Basic Usage of Dirb

To start using Dirb, you enter the command followed by the URL of the target website. Here are a few command examples to demonstrate how Dirb can be utilized effectively:

**Basic Directory Scanning:** To scan a website for common directories:

```bash
dirb http://example.com
```

This command uses the default wordlist to search for directories on `http://example.com`.

**Using a Specific Wordlist:** If you have a specific set of paths you want to check, you can specify a custom wordlist:

```bash
dirb http://example.com /usr/share/dirb/wordlists/common.txt
```

Here, `common.txt` is the wordlist file that contains the paths Dirb will check.

**Ignoring Errors:** Sometimes you may want to ignore error messages from the server:

```bash
dirb http://example.com -z
```

The `-z` option tells Dirb to proceed without pausing for error messages.

**Saving Output to a File:** For better analysis, you might want to save the scan results to a file:

```bash
dirb http://example.com -o results.txt
```

This command saves the output of the scan into `results.txt`, allowing for easy review and record-keeping.

**Scanning with HTTPS:** To scan a secure website that uses HTTPS:

```bash
dirb https://securewebsite.com
```

This ensures that Dirb checks the site using the HTTPS protocol.

**Adjusting Connection Settings:** You can modify the connection settings for timeouts and retries:

```bash
dirb http://example.com -t 20 -r 3
```

The `-t` option sets the timeout for each test to 20 seconds, and `-r` sets the number of retries to 3.

These examples highlight how Dirb can systematically uncover hidden web resources that could be leveraged for deeper penetration testing or security assessments. By effectively mapping web applications, security professionals can identify and secure potentially vulnerable endpoints and scripts.
