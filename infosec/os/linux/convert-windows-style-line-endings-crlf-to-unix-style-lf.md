# Convert Windows-style line endings (CRLF) to Unix-style (LF)

When executing a downloaded shell script, you might encounter the error `syntax error: unexpected end of file (expecting "do")`. This is often due to improper line endings.

To fix this issue:

1.  Convert Windows-style line endings (CRLF) to Unix-style (LF):

    ```sh
    cat yourscript.sh | tr -d '\r' > yournewscript.sh
    ```
2.  Verify the line endings by looking for `0d 0a` sequences using the `hexdump` command:

    ```sh
    hexdump -C yourscript.sh
    ```

By removing the `0d` characters, your script should execute without syntax errors.
