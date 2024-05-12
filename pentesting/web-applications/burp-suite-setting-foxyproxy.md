# Burp Suite: Setting Foxyproxy

&#x20;To begin, download Burp Suite Community Edition and ensure that the Proxy listener is enabled.

![](https://jawad.ca/images/sqli-lab01/sqli-lab1-6.png)

Download the FoxyProxy extension and add the Burp Suite proxy address and port.

{% hint style="info" %}
Newer versions of Burp Suite has an embedded browser,, but I still find FoxyProxy easier to debug web apps.
{% endhint %}

![](https://jawad.ca/images/sqli-lab01/sqli-lab1-5.png)

![](https://jawad.ca/images/sqli-lab01/sqli-lab1-7.png)

Enable the Burp proxy and navigate to the interface where Burp is running (`127.0.0.1:8080`). Save the CA certificate when prompted.&#x20;

<figure><img src="https://jawad.ca/images/sqli-lab01/sqli-lab1-10.png" alt=""><figcaption></figcaption></figure>

To prevent Firefox SSL errors when using Burp, import the certificate we just downloaded by going to `about:preferences#privacy` in Firefox.

![](https://jawad.ca/images/sqli-lab01/sqli-lab1-11.png)

