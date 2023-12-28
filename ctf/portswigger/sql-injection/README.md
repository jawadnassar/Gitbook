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

# SQL Injection

I came across this funny post [on r/ProgrammerHumor](https://www.reddit.com/r/ProgrammerHumor/comments/k0r22a/sql\_injections\_are\_still\_a\_problem\_in\_2255/). I still remember the first time in 2007 (Yes! I know, I wish I had continued focusing on this stuff back then) when I was reading about SQL Injections as part of my PHP journey. The [documentation](https://www.php.net/manual/en/function.mysql-real-escape-string.php) said to simply wrap your query within `mysql_real_escape_string()` to mitigate all SQLi risks (LOL); Little did I know that this attack vector would remain relevant in 2023.

![](https://jawad.ca/images/2255sqli.png)
