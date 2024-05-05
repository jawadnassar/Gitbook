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

# Gobuster

`gobuster` is a command-line tool used for directory and file brute-forcing in web applications. It helps in uncovering hidden paths by systematically testing a web server for existing directories and files. For example, running the below command will search for common directories on the specified website.

```shell-session
kali@kali:~$ gobuster dir -u https://example.com -w common.txt
```

{% hint style="info" %}
You can find wordlists on kali linux under `/usr/share/wordlists/dirb/*`
{% endhint %}



A file containing the below pattern, can be used to discover potential APIs

```
{GOBUSTER}/v1
{GOBUSTER}/v2
{GOBUSTER}/v3
{GOBUSTER}/v4
{GOBUSTER}/v5
{GOBUSTER}/v6
{GOBUSTER}/v7
{GOBUSTER}/v8
```

{% hint style="info" %}
When developers update APIs, they may create a new version, annotated as v2, v3, etc., to ensure that backward compatibility is maintained for some clients. However, vulnerabilities fixed in newer versions can sometimes be reproducible in older ones.
{% endhint %}

Enumerating using the above pattern

```shell-session
kali@kali:~$ gobuster dir -u http://example.com -w dictionnary.txt -p pattern
```



You can use `-w` to specify an extension if searching for specific file types.
