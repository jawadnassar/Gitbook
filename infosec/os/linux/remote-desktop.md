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

# Remote Desktop

rdesktop

<pre class="language-shell-session"><code class="lang-shell-session"><strong>kali@kali:~$ rdesktop 192.168.111.222
</strong></code></pre>

xfreerdp

```shell-session
kali@kali:~$ xfreerdp /u:username /p:password /v:192.168.111.222 /drive:shared,/tmp /cert:ignore
```

