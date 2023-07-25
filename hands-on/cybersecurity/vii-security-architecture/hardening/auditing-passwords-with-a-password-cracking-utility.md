# Auditing Passwords with a Password Cracking Utility

### Scenario <a href="#scenario" id="scenario"></a>

You are auditing password quality to better teach your fellow employees the importance of strong passwords. First, you sent out an employee survey, asking seemingly harmless questions. The results are in the following table. Next, you will add the results to a wordlist to be used as a source for password cracking utilities such as John the Ripper. Finally, you will crack the passwords to demonstrate whether they expose the organization to authentication vulnerabilities.



### Create the necessary accounts and passwords <a href="#create-the-necessary-accounts-and-passwords" id="create-the-necessary-accounts-and-passwords"></a>

You will create six user accounts with passwords related to the above survey.

1. &#x20;Sign in as root using Pa\$$w0rd as the password.
2. &#x20;Launch the **Terminal** application from the toolbar on the top of the Kali desktop.
3.  &#x20;Run the following command to create the first user:

    ```bash-notab-nocopy
    adduser --gecos "" user01
    ```

    When prompted, set 06101988 as the password (you'll type it in twice).

    > As a Debian-based Linux distribution, Kali Linux prefers the adduser command to create users. Red Hat-derived distributions, such as CentOS, typically use useradd.
4.  &#x20;Create the following additional accounts by using the adduser command, and set the specified passwords when prompted:

    | Username: | Password:     |
    | --------- | ------------- |
    | user02    | Password      |
    | user03    | Duke          |
    | user04    | george        |
    | user05    | $p0T          |
    | user06    | G00dPa\$$w0rd |

    > Don't forget about using Bash's history feature. After creating **user01**, press the **UP ARROW** key one time, backspace over the **1** character and then enter the **2** character. This should allow you to create the accounts quickly.

    > Recall that Linux does not display any indication on the screen that the password is being entered. It is accepting your keystrokes, however.
5.  Confirm that the six specified users exist.

    Correct

> Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.

### Add probable passwords to the word list file <a href="#add-probable-passwords-to-the-word-list-file" id="add-probable-passwords-to-the-word-list-file"></a>

John the Ripper uses word list files as the basis for its password cracking attempts. The employee survey results above include many probable passwords. You will extract the compressed wordlist file, and then add the probable passwords to the list.

1.  &#x20;Run the following command to extract the **/usr/share/wordlists/rockyou.txt.gz** word list file:

    ```bash-notab-nocopy
    gunzip /usr/share/wordlists/rockyou.txt.gz
    ```

    > This word list is used as the source for the password cracking attempt.

    > The rockyou.txt wordlist contains entries with language that some may find offensive. If you are offended by bad language, please do not examine the file contents.
2.  &#x20;Enter the following command to open the **rockyou.txt** wordlist file for editing:

    ```bash-notab-nocopy
    vim /usr/share/wordlists/rockyou.txt
    ```
3.  &#x20;Select the **i** key to enter Vim's Insert mode, and then add the following passwords, each on a separate line, at the _top_ of the file:

    06101988\
    Password\
    Duke\
    george\
    $p0T

    > You would normally enter every survey response for each user (birthday, spouse name, anniversary, favorite color, favorite band, pet name). In order to better manage time, you will only enter the passwords John needs to guess. Note that you cannot enter a possible password for user06, because that user declined to fill out the survey.
4.  &#x20;In Vim, press **ESC**, and then type :wq and press **ENTER** to save your changes and exit the file.

    You are returned to the command prompt.



### Run John to crack passwords <a href="#run-john-to-crack-passwords" id="run-john-to-crack-passwords"></a>

You need to combine the /etc/passwd and /etc/shadow files, and then use John the Ripper to audit the employee passwords.

1.  &#x20;Run the following command to create a text file of usernames and password hashes:

    ```bash-notab-nocopy
    unshadow /etc/passwd /etc/shadow > crack-this-file
    ```
2.  &#x20;Run the following command to crack passwords:

    ```bash-notab-nocopy
    john --wordlist=/usr/share/wordlists/rockyou.txt crack-this-file
    ```
3.  &#x20;Open a second tab in the Terminal, and then run the following command to view the status of the audit:

    ```bash-notab-nocopy
    john --show crack-this-file
    ```

    > Don’t forget to use exactly the same names as specified in the instructions.
4.  Confirm that the crack-this-file file exists.

    Correct

*
* &#x20;Type top to display system utilization information. Observe that John is consuming most of the system's processing power.
*   &#x20;Select **q** to exit top.

    > John will eventually break the root user password Pa\$$w0rd, because it is in the word list, too. It may take as much as 10 minutes.
* &#x20;Switch to the Terminal tab where John the Ripper is running, and then type **q** to interrupt the cracking attempt.
*   &#x20;Redirect the results of the john --show crack-this-file to a text file:

    ```bash-notab-nocopy
    john --show crack-this-file > results.txt
    ```
*   &#x20;Display the results.txt file contents by using the cat command.

    Confirm that the results.txt file exists.

    Correct
