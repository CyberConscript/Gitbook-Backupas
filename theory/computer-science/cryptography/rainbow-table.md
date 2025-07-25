# Rainbow Table

A **Rainbow Table** is a lookup table of hashes to plaintexts, so you can quickly find out what password a user had just from the hash. A rainbow table trades the time to crack a hash for hard disk space, but it takes time to create. Here’s a quick example to get an idea of what a rainbow table looks like.



| Hash                             | Password       |
| -------------------------------- | -------------- |
| 02c75fb22c75b23dc963c7eb91a062cc | zxcvbnm        |
| b0baee9d279d34fa1dfd71aadb908c3f | 11111          |
| c44a471bd78cc6c2fea32b9fe028d30a | asdfghjkl      |
| d0199f51d2728db6011945145a1b607a | basketball     |
| dcddb75469b4b4875094e14561e573d8 | 000000         |
| e10adc3949ba59abbe56e057f20f883e | 123456         |
| e19d5cd5af0378da05f63f891c7467af | abcd1234       |
| e99a18c428cb38d5f260853678922e03 | abc123         |
| fcea920f7412b5da7be0cf42b8c93759 | 1234567        |
| 4c5923b6a6fac7b7355f53bfe2b8f8c1 | inS3CyourP4\$$ |



#### Protecting Against Rainbow Tables

To protect against rainbow tables, we add a salt to the passwords. The salt is a randomly generated value stored in the database and should be unique to each user. In theory, you could use the same salt for all users, but duplicate passwords would still have the same hash and a rainbow table could still be created for passwords with that salt.

The salt is added to either the start or the end of the password before it’s hashed, and this means that every user will have a different password hash even if they have the same password. Hash functions like Bcrypt and Scrypt handle this automatically. Salts don’t need to be kept private.



#### Example of Securely Storing Passwords

You can find many good guides online that promote best security practices when storing passwords. Please check if there are any standards you need to follow when storing passwords before adopting one. Consider this example following good security practices when storing user passwords:

1. We select a secure hashing function, such as Argon2, Scrypt, Bcrypt, or PBKDF2.
2. We add a unique salt to the password, such as `Y4UV*^(=go_!`
3. Concatenate the password with the unique salt. For example, if the password is `AL4RMc10k`, the result string would be `AL4RMc10kY4UV*^(=go_!`
4. Calculate the hash value of the combined password and salt. In this example, using the chosen algorithm, you need to calculate the hash value of `AL4RMc10kY4UV*^(=go_!`.
5. Store the hash value and the unique salt used (`Y4UV*^(=go_!`).

{% embed url="https://hashes.com" %}

{% embed url="https://crackstation.net/" %}

If you want to run [Hashcat](https://hashcat.net/hashcat/), it’s best to run it on your host to make the most of your GPU, if available. If you prefer MS Windows, you are in luck; MS Windows builds are available on the website, and you can run it from PowerShell. You can get Hashcat working with OpenCL in a VM, but the speeds will likely be worse than cracking on your host.

[John the Ripper](https://www.openwall.com/john/) uses CPU by default and works in a VM out of the box, although you may get better speeds running it on the host OS to avoid any virtualisation overhead and make the most of your CPU cores and threads.

#### Practical



Hashcat uses the following basic syntax: `hashcat -m <hash_type> -a <attack_mode> hashfile wordlist`, where:

* `-m <hash_type>` specifies the hash-type in numeric format. For example, `-m 1000` is for NTLM. Check the official documentation (`man hashcat`) and [example page](https://hashcat.net/wiki/doku.php?id=example_hashes) to find the hash type code to use.
* `-a <attack_mode>` specifies the attack-mode. For example, `-a 0` is for straight, i.e., trying one password from the wordlist after the other.
* `hashfile` is the file containing the hash you want to crack.
* `wordlist` is the security word list you want to use in your attack.

For example, `hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt` will treat the hash as Bcrypt and try the passwords in the `rockyou.txt` file.



hashcat -m
