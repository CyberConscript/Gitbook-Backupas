# Cryptography

## Intro

Cryptography is used to protect confidentiality, integrity, and authenticity. In this age, you use cryptography daily, and you’re almost certainly reading this over an encrypted connection. Consider the following scenarios where you would use cryptography:

* When you log in to website, your credentials are encrypted and sent to the server so that no one can retrieve them by snooping on your connection.
* When you connect over SSH, your SSH client and the server establish an encrypted tunnel so no one can eavesdrop on your session.
* When you conduct online banking, your browser checks the remote server’s certificate to confirm that you are communicating with your bank’s server and not an attacker’s.
* When you download a file, how do you check if it was downloaded correctly? Cryptography provides a solution through hash functions to confirm that your file is identical to the original one.
* **Cryptography** is the science of securing communication and data using codes and ciphers.
* **Cryptanalysis** is the study of methods to break or bypass cryptographic security systems without knowing the key.
* **Brute-Force Attack** is an attack method that involves trying every possible key or password to decrypt a message.
* **Dictionary Attack** is an attack method where the attacker tries dictionary words or combinations of them.
* **Authentication**: You want to be sure you communicate with the right person, not someone else pretending.
* **Authenticity**: You can verify that the information comes from the claimed source.
* **Integrity**: You must ensure that no one changes the data you exchange.
* **Confidentiality**: You want to prevent an unauthorised party from eavesdropping on your conversations.

## Symetrical encryption

The encryption function is part of the cipher; a cipher is an algorithm to convert a plaintext into a ciphertext and vice versa.

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Decryption<br>

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Terms;

* **Plaintext** is the original, readable message or data before it’s encrypted. It can be a document, an image, a multimedia file, or any other binary data.
* **Ciphertext** is the scrambled, unreadable version of the message after encryption. Ideally, we cannot get any information about the original plaintext except its approximate size.
* **Cipher** is an algorithm or method to convert plaintext into ciphertext and back again. A cipher is usually developed by a mathematician.
* **Key** is a string of bits the cipher uses to encrypt or decrypt data. In general, the used cipher is public knowledge; however, the key must remain secret unless it is the public key in asymmetric encryption. We will visit asymmetric encryption in a later task.
* **Encryption** is the process of converting plaintext into ciphertext using a cipher and a key. Unlike the key, the choice of the cipher is disclosed.
* **Decryption** is the reverse process of encryption, converting ciphertext back into plaintext using a cipher and a key. Although the cipher would be public knowledge, recovering the plaintext without knowledge of the key should be impossible (infeasible).

Examples of symmetric encryption are DES (Data Encryption Standard), 3DES (Triple DES) and AES (Advanced Encryption Standard).

* **DES** was adopted as a standard in 1977 and uses a 56-bit key. With the advancement in computing power, in 1999, a DES key was successfully broken in less than 24 hours, motivating the shift to 3DES.
* **3DES** is DES applied three times; consequently, the key size is 168 bits, though the effective security is 112 bits. 3DES was more of an ad-hoc solution when DES was no longer considered secure. 3DES was deprecated in 2019 and should be replaced by AES; however, it may still be found in some legacy systems.
* **AES** was adopted as a standard in 2001. Its key size can be 128, 192, or 256 bits.



### Asymmetric Encryption

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Unlike symmetric encryption, which uses the same key for encryption and decryption, **asymmetric encryption** uses a pair of keys, one to encrypt and the other to decrypt, as shown in the illustration below. To protect confidentiality, asymmetric encryption or **asymmetric cryptography** encrypts the data using the public key; hence, it is also called **public key cryptography**

Examples are RSA, Diffie-Hellman, and Elliptic Curve cryptography (ECC). The two keys involved in the process are referred to as a public key and a private key. Data encrypted with the public key can be decrypted with the private key. Your private key needs to be kept private, hence the name.

Asymmetric encryption tends to be slower, and many asymmetric encryption ciphers use larger keys than symmetric encryption. For example, RSA uses 2048-bit, 3072-bit, and 4096-bit keys; 2048-bit is the recommended minimum key size. Diffie-Hellman also has a recommended minimum key size of 2048 bits but uses 3072-bit and 4096-bit keys for enhanced security. On the other hand, ECC can achieve equivalent security with shorter keys. For example, with a 256-bit key, ECC provides a level of security comparable to a 3072-bit RSA key.

* RSA
* Diffie-Hellman
* SSH
* SSL/TLS Certificates
* PGP and GPG





## Diffie-Hellman Key Exchange&#x20;

Exchanging keys for symmetric encryption is a widespread use of asymmetric cryptography. Asymmetric encryption is relatively slow compared to symmetric encryption; therefore, we rely on asymmetric encryption to negotiate and agree on symmetric encryption ciphers and keys.

But the question is, how do you agree on a key with the server without transmitting the key for people snooping to see?



Consider the following scenario. Alice and Bob want to talk securely. They want to establish a shared key for symmetric cryptography but don’t want to use asymmetric cryptography for the key exchange. This is where the Diffie-Hellman Key Exchange comes in.

Alice and Bob generate secrets independently; let’s call these secrets A and B. They also have some public common material; let’s call this C.

We need to make some assumptions. Firstly, whenever we combine secrets, they’re practically impossible to separate. Secondly, the order in which they’re combined doesn’t matter. Alice and Bob will combine their secrets with the common material to form **AC** and **BC.** They will then send these to each other and combine the received part with their secret **to create two identical keys, both ABC**. Now, they can use this key to communicate.

#### **Public parameters**

* Prime number: p=29
* Generator: g=3

#### **Private keys**

* Alice chooses a=13
* Bob chooses b=15

#### **Ką tai reiškia Diffie–Hellman'e?**



<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

If you found the previous paragraphs too abstract, let’s investigate the exact process.

1. Alice and Bob agree on the **public variables**: a large prime number $$p$$ and a generator $$g$$, where $$0 < g < p$$. These values will be disclosed publicly over the communication channel. Although insecurely small, we will choose $$p = 29$$ and $$g = 3$$ to simplify our calculations.
2. Each party chooses a private integer. As a numerical example, Alice chooses $$a = 13$$, and Bob chooses $$b = 15$$. Each of these values represents a **private key** and must not be disclosed.
3. It is time for each party to calculate their **public key** using their private key from step 2 and the agreed-upon public variables from step 1. Alice calculates $$A = ga$$ mod $$p = 313$$ mod $$29 = 19$$ and Bob calculates $$B = gb$$ mod $$p = 315$$ mod $$29 = 26$$. These are the public keys.
4. Alice and Bob send the keys to each other. Bob receives $$A = ga$$ mod $$p = 19$$, i.e., Alice’s public key. And Alice receives $$B = gb$$ mod $$p = 26$$, i.e., Bob’s public key. This step is called the **key exchange**.
5. Alice and Bob can finally calculate the **shared secret** using the received public key and their own private key. Alice calculates $$Ba$$ mod $$p = 2613$$ mod $$29 = 10$$ and Bob calculates $$Ab$$ mod $$p = 1915$$ mod $$29 = 10$$. Both calculations yield the same result, $$gab$$ mod $$p = 10$$, the shared secret key.

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>



## Digital Signature

Digital signatures provide a way to verify the authenticity and integrity of a digital message or document. Proving the authenticity of files means we know who created or modified them. Using asymmetric cryptography, you produce a signature with your private key, which can be verified using your public key. Only you should have access to your private key, which proves you signed the file. In many modern countries, digital and physical signatures have the same legal value.

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

The simplest form of digital signature is encrypting the document with your private key. If someone wants to verify this signature, they would decrypt it with your public key and check if the files match. This process is shown in the image below.

## Certificates: Chain of trust

Certificates are an essential application of public key cryptography, and they are also linked to digital signatures. A common place where they’re used is for HTTPS. How does your web browser know that the server you’re talking to is the real tryhackme.com?

The answer lies in certificates. The web server has a certificate that says it is the real tryhackme.com. The certificates have a chain of trust, starting with a root CA (Certificate Authority). From install time, your device, operating system, and web browser automatically trust various root CAs. Certificates are trusted only when the Root CAs say they trust the organisation that signed them. In a way, it is a chain; for example, the certificate is signed by an organisation, the organisation is trusted by a CA, and the CA is trusted by your browser. Therefore, your browser trusts the certificate. In general, there are long chains of trust. You can take a look at the certificate authorities trusted by Mozilla Firefox [here](https://wiki.mozilla.org/CA/Included_Certificates) and by Google Chrome [here](https://chromium.googlesource.com/chromium/src/+/main/net/data/ssl/chrome_root_store/root_store.md).





#### PGP and GPG

**PGP** stands for Pretty Good Privacy. It’s software that implements encryption for encrypting files, performing digital signing, and more. [GnuPG or GPG](https://gnupg.org/) is an open-source implementation of the OpenPGP standard.

GPG is commonly used in email to protect the confidentiality of the email messages. Furthermore, it can be used to sign an email message and confirm its integrity.



Below is an example of generating GPG. You are asked about the purpose of using `gpg`, whether signing only or signing and encrypting. Besides selecting the cryptographic algorithm, we needed to choose an expiry date for the generated key. Finally, we provided some information about us: our name, email address, and a comment usually about the purpose of this key.



You may need to use GPG to decrypt files in CTFs. With PGP/GPG, private keys can be protected with passphrases in a similar way that we protect SSH private keys. If the key is passphrase protected, you can attempt to crack it using John the Ripper and `gpg2john`. The key provided in this task is not protected with a passphrase. The man page for GPG can be found online [here](https://www.gnupg.org/gph/de/manual/r1023.html).



Now that you have your GPG key pair, you can share the public key with your contacts. Whenever your contacts want to communicate securely, they encrypt their messages to you using your public key. To decrypt the message, you will have to use your private key. Due to the importance of the GPG keys, it is vital that you keep a backup copy in a secure location.

Let’s say you got a new computer. All you need to do is import your key, and you can start decrypting your received messages again:

* You would use `gpg --import backup.key` to import your key from backup.key
* To decrypt your messages, you need to issue `gpg --decrypt confidential_message.gpg`



### NTHash / NTLM

Windows New Technology LAN Manager (NTLM) is a suite of security protocols offered by Microsoft to authenticate users’ identity and protect the integrity and confidentiality of their activity.

