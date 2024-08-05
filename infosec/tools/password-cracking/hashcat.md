---
cover: >-
  https://images.unsplash.com/photo-1514888286974-6c03e2ca1dba?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw2fHxjYXR8ZW58MHx8fHwxNzIyODI1NTk2fDA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Hashcat

**Key Usages:**

1.  **Dictionary Attack**: Utilizes a wordlist to try potential passwords.

    ```bash
    hashcat -a 0 -m 0 hashes.txt wordlist.txt
    ```
2.  **Brute Force Attack**: Tries all possible combinations of characters.

    ```bash
    hashcat -a 3 -m 0 hashes.txt ?a?a?a?a
    ```
3.  **Combinator Attack**: Combines words from two wordlists.

    ```bash
    hashcat -a 1 -m 0 hashes.txt wordlist1.txt wordlist2.txt
    ```
4.  **Mask Attack**: Uses patterns to reduce the search space.

    ```bash
    hashcat -a 3 -m 0 hashes.txt ?u?l?l?l?d?d
    ```
5.  **Hybrid Attack**: Combines dictionary and mask attacks.

    ```bash
    hashcat -a 6 -m 0 hashes.txt wordlist.txt ?d?d
    ```

**Tips and Tricks:**

1. **Optimize Performance**:
   * Use `--force` to bypass warnings.
   * Utilize GPU acceleration with appropriate drivers.
   * Adjust workload tuning with `-w` (e.g., `-w 3` for high).
2. **Efficient Mask Usage**:
   * Use masks to focus on probable patterns (e.g., `?l?l?l?d?d` for three letters followed by two digits).
3.  **Rule-Based Attacks**:

    * Enhance dictionary attacks with rules to generate variations.

    ```bash
    hashcat -a 0 -m 0 hashes.txt wordlist.txt -r rules/best64.rule
    ```
4.  **Session Management**:

    * Save and restore sessions to manage long-running tasks.

    ```bash
    hashcat -m 0 -a 3 hashes.txt ?a?a?a?a --session=mySession
    hashcat --restore mySession
    ```
5. **Hash Modes**:
   * Specify the correct hash mode (`-m`) for your target hash type (e.g., `-m 1000` for NTLM).
6.  **Output Management**:

    * Save cracked passwords to a file.

    ```bash
    hashcat -m 0 -a 0 hashes.txt wordlist.txt -o found.txt
    ```

By understanding and applying these usages, tips, and tricks, you can leverage Hashcat effectively for password cracking in various scenarios.
