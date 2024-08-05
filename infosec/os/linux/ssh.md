# SSH

#### Connecting via SSH using a Key

1.  Ensure the key file has the correct permissions:

    ```bash
    chmod 600 id_rsa
    ```
2.  Connect via SSH using the key:

    ```bash
    ssh -i id_rsa -p [PORT] [user]@[IP_ADDRESS]
    ```
