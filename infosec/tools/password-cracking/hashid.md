# hashID

HashID is a command-line tool designed to identify the type of a given hash or list of hashes. It supports a wide range of hash algorithms and provides a quick and efficient way for security professionals to determine which hash cracking techniques and tools to use.

**Key Features**

1. **Broad Hash Algorithm Support**: Recognizes over 220 unique hash types.
2. **Ease of Use**: Simple command-line interface that allows for both single hash and bulk hash identification.
3. **Accurate Detection**: High accuracy in identifying hash types, which is crucial for effective password cracking.

**Usage and Examples**

**Basic Syntax**:

```bash
hashid [options] <hash>
```

**Example 1: Identifying a Single Hash** To identify the type of a single hash, simply run `hashid` followed by the hash:

```bash
kali@kali:~$ hashid -m 5d41402abc4b2a76b9719d911017c592
```

Output:

```
Analyzing '5d41402abc4b2a76b9719d911017c592'
[+] MD2
[+] MD5
[+] Domain Cached Credentials
[+] NTLM
```

**Example 2: Identifying Hashes from a File** HashID can also process a file containing multiple hashes:

```bash
kali@kali:~$ hashid -f hashes.txt
```

Output:

```
Analyzing 'hashes.txt'
[+] Hash 1: 5d41402abc4b2a76b9719d911017c592
   [+] MD2
   [+] MD5
   [+] Domain Cached Credentials
   [+] NTLM
[+] Hash 2: e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
   [+] SHA-256
```

**Options and Tips**

1.  **Verbose Mode**: Use `-v` to get more detailed output.

    ```bash
    hashid -v -m 5d41402abc4b2a76b9719d911017c592
    ```
2.  **Extended Hash Types**: Use `--extended` to include less common hash types in the identification process.

    ```bash
    hashid --extended -m 5d41402abc4b2a76b9719d911017c592
    ```
3.  **Including Salts**: If you have a hash with a known salt, use the `--salt` option.

    ```bash
    hashid --salt mySalt -m 5d41402abc4b2a76b9719d911017c592
    ```

**Practical Examples**

1.  **Identifying SHA-1 Hash**

    ```bash
    hashid -m da39a3ee5e6b4b0d3255bfef95601890afd80709
    ```

    Output:

    ```
    [+] SHA-1
    ```
2.  **Identifying Multiple Hashes** Create a file `hashes.txt` with the following content:

    ```
    5d41402abc4b2a76b9719d911017c592
    da39a3ee5e6b4b0d3255bfef95601890afd80709
    ```

    Run:

    ```bash
    hashid -f hashes.txt
    ```

####

{% hint style="info" %}
Ensure no spaces or lines are added mistakenly when copy/pasting hashes, as they can completely alter the value.
{% endhint %}
