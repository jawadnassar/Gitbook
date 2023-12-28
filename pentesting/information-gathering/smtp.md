# SMTP

Using `nc` to interact with an SMTP server:

```shell-session
kali@kali:~$ nc -vz example.com 25
```

* Replace `example.com` with the domain or IP address of the SMTP server.
* Use port `25` for SMTP communication.

This command checks if the SMTP server on `example.com` is reachable on port 25. The `-v` flag provides verbose output, and the `-z` flag makes `nc` operate in scanning mode, checking for an open port without sending any data.



**Using VRFY:**

* Issue the `VRFY` command to verify the existence of a user or mailbox. Replace "user" with the actual username you want to check.

```shell-session
VRFY user
```





**Resources**

* [https://en.wikipedia.org/wiki/Simple\_Mail\_Transfer\_Protocol](https://en.wikipedia.org/wiki/Simple\_Mail\_Transfer\_Protocol)
