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

# curl

`curl` is a versatile command-line tool used for making HTTP requests to transfer data between a client and a server. It supports various protocols, including HTTP, HTTPS, FTP, FTPS, SCP, SFTP, LDAP, and more. With a simple syntax, it enables users to retrieve, upload, and interact with data on the web, making it a powerful utility for web developers, system administrators, and security professionals. `curl` supports a wide range of options, allowing customization of requests and handling various authentication methods, making it a go-to tool for tasks like downloading files, testing APIs, and debugging network-related issues.





```shell-session
curl -i https://example.com

```

the `-i` will display both the headers and the body of the HTTP response.



Here's an example of a `curl` command for making a POST request with an Authorization header:

```bash
curl -X POST \
     -H "Authorization: Bearer YourAccessToken" \
     -H "Content-Type: application/json" \
     -d '{"key1": "value1", "key2": "value2"}' \
     https://api.example.com/endpoint
```

Explanation of the options used:

* `-X POST`: Specifies the HTTP method as POST.
* `-H "Authorization: Bearer YourAccessToken"`: Adds an Authorization header with a Bearer token. Replace `YourAccessToken` with the actual access token.
* `-H "Content-Type: application/json"`: Sets the Content-Type header to indicate that the data being sent is in JSON format.
* `-d '{"key1": "value1", "key2": "value2"}'`: Provides the data payload for the POST request in JSON format.
* `https://api.example.com/endpoint`: Specifies the URL endpoint where the POST request should be sent.



We can retrieve the **`robots.txt`** file from **`www.example.com`** with **`curl`;** `robots.txt` is a file used by websites to communicate with web crawlers or spiders, providing directives on which parts of the site should not be crawled or indexed; we can explore these paths to identify potentially hidden or forgotten content

```shell-session
kali@kali:~$ curl https://www.example.com/robots.txt
```
