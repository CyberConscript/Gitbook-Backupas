# Physical



## Mounting encrypted drive

Unlock the image, mount it, and then look inside.

Here’s how you can approach the task of accessing the **`secretvault.img`** file encrypted with **cryptsetup**. You'll unlock the image, mount it, and then look inside to find the flag.

#### Steps:

1.  **Create a Directory to Mount the Encrypted Image**: You need an empty directory to mount the unlocked image. You can create a directory named `myvault`.

    ```bash
    mkdir ~/myvault
    ```
2.  **Open the Encrypted Image Using `cryptsetup`**: Use `cryptsetup` to unlock the `secretvault.img` file. The password for the encryption is **`2N9EdZYNkszEE3Ad`**.

    ```bash
    sudo cryptsetup luksOpen /home/tryhackme/secretvault.img secretvault
    ```

    This command will map the encrypted image to a device, accessible at `/dev/mapper/secretvault`.
3.  **Mount the Unlocked Image**: Now, mount the unlocked image to the directory you just created (`myvault`).

    ```bash
    sudo mount /dev/mapper/secretvault ~/myvault
    ```
4.  **Check the Contents of the Vault**: Once mounted, navigate into the `myvault` directory to see the files inside and look for the flag.

    ```bash
    cd ~/myvault
    ls
    ```

    Look for any text files or flag files (like `flag.txt`). To view the contents of a file:

    ```bash
    cat <filename>
    ```
5.  **Unmount and Close the Encrypted Image**: After retrieving the flag, unmount the image and close the encrypted mapping.

    ```bash
    sudo umount ~/myvault
    sudo cryptsetup luksClose secretvault
    ```

#### Summary of Commands:

```bash
mkdir ~/myvault
sudo cryptsetup luksOpen /home/tryhackme/secretvault.img secretvault
sudo mount /dev/mapper/secretvault ~/myvault
cd ~/myvault
ls
cat <flag_filename>
sudo umount ~/myvault
sudo cryptsetup luksClose secretvault
```

The **flag** will be located inside the mounted `myvault` directory. Use `cat` to view the flag.





Here’s a breakdown of how the **`cryptsetup luksOpen`** command works and the process behind unlocking the **`secretvault.img`** file:

#### What Happens During the Process:

1. **Cryptsetup**:
   * **`cryptsetup`** is a command-line utility used for managing disk encryption on Linux, primarily with LUKS (Linux Unified Key Setup).
   * It handles the setup and management of encrypted filesystems by providing commands to open, close, create, and modify encrypted partitions or files.
2. **LUKS (Linux Unified Key Setup)**:
   * The file **`/home/tryhackme/secretvault.img`** is a LUKS-encrypted file. LUKS manages the encryption and decryption of data stored on disks.
   * LUKS creates a header (partition header) in the encrypted image that contains information like the UUID, cipher, cipher mode, and key slots (where the encrypted master keys are stored).
3.  **Command Breakdown**:

    ```bash
    sudo cryptsetup luksOpen /home/tryhackme/secretvault.img secretvault
    ```

    Here's what happens step-by-step:

    * **`sudo`**: Superuser privileges are required because the operation involves low-level access to storage and encryption functions.
    * **`cryptsetup`**: Invokes the `cryptsetup` utility, which handles the LUKS encryption operations.
    * **`luksOpen`**: This command tells `cryptsetup` to open (unlock) a LUKS-encrypted file or partition.
    * **`/home/tryhackme/secretvault.img`**: The file path to the encrypted image. This is where the encrypted data resides.
    * **`secretvault`**: This is the name that will be given to the device mapper entry, which will appear in `/dev/mapper/secretvault`. This entry will represent the unlocked version of the encrypted image.
4. **What Happens Internally**:
   * **Password Prompt**: When the command is executed, you’ll be prompted to enter the decryption password (in this case, **`2N9EdZYNkszEE3Ad`**). This password is used to unlock one of the **key slots** in the LUKS header.
   * **PBKDF2 Key Derivation**: LUKS uses the password along with a salt stored in the LUKS header to derive the decryption key using **PBKDF2** (Password-Based Key Derivation Function 2). This process makes brute-force attacks harder by iterating the hashing process.
   * **Master Key Decryption**: LUKS will use the derived key to decrypt the **master key** stored in the key material (KM) slot. The master key is what is used to actually encrypt and decrypt the data in the partition or file.
   * **Device Mapper**: Once unlocked, the encrypted image is mapped to a virtual device under `/dev/mapper/secretvault`. The `luksOpen` command essentially makes the encrypted content available in an unencrypted form, allowing you to access it like any regular storage device.
5. **Virtual Device**:
   * Once the image is unlocked, the operating system treats the unlocked data as if it were a new block device (like a virtual hard drive). This device will be accessible via `/dev/mapper/secretvault`.
   * You can now mount this device to a directory and interact with it as if it were a regular filesystem.
6. **Mounting**:
   * After unlocking, you can mount the `/dev/mapper/secretvault` device to any directory (e.g., `myvault`), and you’ll be able to browse and access the files stored in the encrypted image.
   * The data remains encrypted on disk, but it is transparently decrypted when you access it through the mounted directory.

#### Summary:

* **`luksOpen`** opens (unlocks) a LUKS-encrypted file or partition using the provided password.
* **Cryptsetup** uses the password to decrypt the master key stored in a LUKS key slot.
* The unlocked content is made available via a device mapper entry (e.g., `/dev/mapper/secretvault`).
* Once unlocked, the image can be mounted and accessed like any regular filesystem.

This process allows secure storage of data in an encrypted form while providing access through decryption when authorized (i.e., when the correct password is provided).&#x20;
