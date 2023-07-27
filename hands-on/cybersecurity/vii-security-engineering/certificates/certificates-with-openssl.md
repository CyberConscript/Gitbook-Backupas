# Certificates with OpenSSL

### Scenario <a href="#scenario" id="scenario"></a>

In this activity, you will work with OpenSSL to manage certificates. You will generate certificates, generate a certificate signing request, and convert certificate formats. These are all tasks administrators are responsible for when managing web servers, email servers, and other devices.

### Use basic OpenSSL commands <a href="#use-basic-openssl-commands" id="use-basic-openssl-commands"></a>

In the first part of this activity, you will use basic OpenSSL commands to confirm the program version. You will also create a storage directory for the keys that you will generate.

1.  &#x20;Sign in to the [PT1-Kali](https://labclient.labondemand.com/Instructions/c631febe-df68-4e44-b11f-d1e30d00101f?rc=10) VM as root using Pa\$$w0rd as the password.

    > Recall that you cannot use the automatic Type Text feature with Linux virtual machines and that all commands and input in Linux are case-sensitive. Linux commands will be displayed by using the monospace font: hostname
2. &#x20;Open the **Terminal** from the menu at the top of the Desktop.
3.  &#x20;To check the OpenSSL version, type the following command, and then press **ENTER**:

    ```bash-notab-nocopy
    openssl version
    ```
4.  What version of OpenSSL is installed?

    1.12.33.16.0

*   Correct

    > The purpose behind Assisted Labs is to confirm your knowledge and guide you through the given configurations. If you get a scored question incorrect, you may repeat the question and achieve the correct answer. You do not need a correct answer to move forward through the lab.
*   &#x20;Run the following command to create a directory named **keys** in the root user's home directory:

    ```bash-notab-nocopy
    mkdir keys
    ```
* &#x20;Use the cd command to change to the **keys** directory.
*   &#x20;Generate an asymmetric encryption RSA key pair and extract the public portion to prepare to create a certificate signing request (which occurs below). Type the following command, then press **ENTER**:

    ```bash-notab-nocopy
    openssl genrsa -out corp.515support.com.key 2048
    ```
*   &#x20;Run the following command to display the private key:

    ```bash-notab-nocopy
    cat corp.515support.com.key
    ```
*   &#x20;Extract the public key file to a file for export with a CSR.

    ```bash-notab-nocopy
    openssl rsa -in corp.515support.com.key -pubout -out corp.515support.com_public.key
    ```

    > You can resize the panes by clicking and dragging the border between the Instructions pane and the VM pane. This can make it much easier to see the long commands contained in this activity.
* &#x20;Use the ls command to display the two key files that you have created so far.
*   &#x20;Display the public key file:

    ```bash-notab-nocopy
    cat corp.515support.com_public.key
    ```
*   Confirm that the corp.515support.com\_public.key file exists.

    Correct

> Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.5



### Generate a certificate signing request <a href="#generate-a-certificate-signing-request" id="generate-a-certificate-signing-request"></a>

Generate a web site certificate signing request that could be sent to a certificate authority (CA).

1.  &#x20;Generate a certificate signing request. Type the following command, then press **ENTER**:

    ```bash-notab-nocopy
    openssl req -new -key corp.515support.com.key -out corp.515support.com.csr
    ```
2. &#x20;Provide the following answers to the prompts:
   * Country Code: _your country_
   * State or Province Name: _your state or province_
   * Locality Name: _your city_
   * Organization Name: 515 Support
   * Organizational Unit Name: WebServices
   * Common Name: webserver.corp.515support.com
   * Email Address: admin@515support.com
3.  &#x20;When prompted to enter a challenge password and an optional company name, press **ENTER**.

    This OpenSSL command generates a certificate signing request on behalf of the Apache web server service for a web site.
4. &#x20;Run the ls command to display the .csr file.
5. Confirm that the corp.515support.com.csr file exists.

*
*   &#x20;Verify the certificate request. Type the following command, then press **ENTER**:

    ```bash-notab-nocopy
    openssl req -text -in corp.515support.com.csr -noout -verify
    ```

    This OpenSSL command verifies the certificate request.
*   &#x20;The certificate signing request must be sent to the certificate authority using the PEM format. Run the following command to display the CSR file in this format:

    ```bash-notab-nocopy
    cat corp.515support.com.csr
    ```

### Convert certificate format <a href="#convert-certificate-format" id="convert-certificate-format"></a>

As we don't have a CA available to sign the request, for the next part of the exercise we'll generate a self-signed certificate with a new key, overwriting the old one.

1. &#x20;Run the ls command and observe that there are three files in the directory.
2.  &#x20;Generate a self-signed certificate:

    ```bash-notab-nocopy
    openssl req -newkey rsa:2048 -nodes -keyout corp.515support.com.key -x509 -days 365 -out corp.515support.com.crt
    ```
3. &#x20;Provide the following answers to the prompts:
   * Country Code: _your country_
   * State or Province Name: _your state or province_
   * Locality Name: _your city_
   * Organization Name: 515 Support
   * Organizational Unit Name: WebServices
   * Common Name: webserver.corp.515support.com
   * Email Address: admin@515support.com
4. Confirm that the corp.515support.com.crt file exists.

* > Don’t forget to use exactly the same names as specified in the instructions.
* &#x20;Run the ls command again and observe that there are now four files in the directory. A new .crt file has been created.



### Merge the .key and .crt files (the non-Windows PEM format) into a .pfx file (the Windows PKCS#12 format) <a href="#merge-the-key-and-crt-files-the-non-windows-pem-format-into-a-pfx-file-the-windows-pkcs12-format" id="merge-the-key-and-crt-files-the-non-windows-pem-format-into-a-pfx-file-the-windows-pkcs12-format"></a>

Convert the certificate you generated to a format accepted by the Windows.

Certificates are often issued by CAs in the PEM format. Windows servers often use the PKCS#12 format, where keys are merged into a single file. The PKCS#12 format is an archival file that stores both the certificate and the private key. This format is useful for migrating certificates and keys from one system to another as it contains all the necessary files. PKCS#12 files use either the .pfx or .p12 file extension.

Use the following command to convert your PEM key and certificate into the PKCS#12 format (i.e., a single .pfx file):

1.  &#x20;Type the following command to convert the files, then press **ENTER**:

    ```bash-notab-nocopy
    openssl pkcs12 -export -name "corp.515support.com" -out corp.515support.com.pfx -inkey corp.515support.com.key -in corp.515support.com.crt
    ```
2. &#x20;When prompted select **ENTER** to skip defining an **Export Password**.
3. &#x20;Run the ls command and observe that there are now five files in the directory. A new .pfx file has been created.
4. Confirm that the corp.515support.com.pfx file exists.

<details>

<summary>The .pfx file</summary>



</details>
