# Managing Access Controls in Linux

### Scenario <a href="#scenario" id="scenario"></a>

In this activity, you will manage access controls on a Linux server. First, you will configure local users and groups on the system. Next, you will create directories and files to represent resources that need to be controlled. Next, you will configure the ownership of these directories and files. Finally, you'll configure standard Linux permissions to manage for the users and groups to access the directories and files.

### Create users and groups <a href="#create-users-and-groups" id="create-users-and-groups"></a>

You need to create two test users and two groups on the Linux virtual machine. You'll configure passwords for the two users, too.

1. &#x20;Sign in to the [PT1-Kali](https://labclient.labondemand.com/Instructions/7af67893-2ef7-4060-a0f6-9424737b9a13?rc=10) VM as root using Pa\$$w0rd as the password.
2.  &#x20;From the toolbar at the top of the Desktop, open the Terminal.

    > You should get used to managing Linux servers from the command line.
3.  &#x20;Run the following command to create a new user named user01:

    ```bash-notab-nocopy
    useradd user01
    ```
4.  &#x20;Run the following command to set a password for user01:

    ```bash-notab-nocopy
    passwd user01
    ```
5.  &#x20;When prompted, enter and confirm the password Pa\$$w0rd

    > Creating a user in Linux is two steps: 1) create the user by using the useradd command, and 2) set the password by using the passwd command.
6. &#x20;Repeat the above steps to create user02, and then set Pa\$$w0rd as password.
7.  Confirm that user01 and user02 exist.

    Correct
8. > &#x20;Run the following command to create a new group named admins:

```bash-notab-nocopy
groupadd admins
```

1.  &#x20;Create a second group named devs.

    Confirm that the devs group exists.

    Correct
2.
3.  &#x20;Add **user01** to the **admins** group:

    ```bash-notab-nocopy
    usermod -aG admins user01
    ```

    > Adding a user to a group is a modification of the user object, hence the use of usermod.
4.  &#x20;Run these commands to verify the group memberships:

    ```bash-notab-nocopy
    id user01
    ```

    ```bash-notab-nocopy
    tail /etc/group
    ```

    > The tail command in Linux displays the last 10 lines of a file. In this case, it displays the most recently-created groups.
5. &#x20;Add **user02** to the **devs** group.
6.  Confirm that user02 is a member of the devs group.

    Correct





### Create directories and files <a href="#create-directories-and-files" id="create-directories-and-files"></a>

Use the mkdir and touch commands to create directories and files to simulate resources that need to have permissions applied to them.

1.  &#x20;Run the following commands to create three directories:

    ```bash-notab-nocopy
    mkdir /projects
    ```

    ```bash-notab-nocopy
    mkdir /projects/ITprojects
    ```

    ```bash-notab-nocopy
    mkdir /projects/devprojects
    ```

    > You could create all three directories (/projects, /projects/ITprojects, /projects/devprojects) by issuing one command: mkdir /projects /projects/ITprojects /projects/devprojects

    > Don’t forget to use exactly the same names as specified in the instructions.
2.  Confirm that the /projects/ITprojects directory exists.

    Correc
3.  Confirm that the /projects/devprojects directory exists.

    Correct
4.
5.  &#x20;Run the following commands to create two files:

    ```bash-notab-nocopy
    touch /projects/ITprojects/servers.txt
    ```

    ```bash-notab-nocopy
    touch /projects/devprojects/programming.txt
    ```

    > The touch command updates the timestamp on an existing file. If the specified file does not exist, touch creates it.
6.  Confirm that the servers.txt file exists.

    Correct
7.
8.  Confirm that the /projects/devprojects/programming.txt file exists.

    Correct



### Configure ownership <a href="#configure-ownership" id="configure-ownership"></a>

By default, the creator of a resource owns the resource. Because you used to the root user account to create the directories and files in the previous activity, the root user controls access. You need to permit users and groups to own the directories and files so that they can configure permissions..

1.  &#x20;Run the following commands to display the current default permissions on the contents of the /labs directory:

    ```bash-notab-nocopy
    ls -ld /projects
    ```

    > Whoever creates the object, owns the object. Hence, root owns these objects.
2.  &#x20;Run the following commands to change ownership from root to the specified users and groups:

    ```bash-notab-nocopy
    chown -R user01:admins /projects/ITprojects
    ```

    ```bash-notab-nocopy
    chown -R user02:devs /projects/devprojects
    ```

    > The -R option makes the chown recursive. This applies the ownership and groups settings to the directory and everything in it.
3.  &#x20;Run the following command to display the user and group associations for the **/projects/ITprojects** directory itself:

    ```bash-notab-nocopy
    ls -ld /projects/ITprojects
    ```
4.  &#x20;Run the following command to display the user and group associations for the _contents_ of the **/projects/ITprojects** directory:

    ```bash-notab-nocopy
    ls -l /projects/ITprojects
    ```
5.  Who is the owner and what group is associated with the /projects/ITprojects directory?

    The user01 account and the admins group.The user01 account and the devs group.The user02 account and the devs group.The user02 account and the admins group.

*   Correct

    > The purpose behind Assisted Labs is to confirm your knowledge and guide you through the given configurations. If you get a scored question incorrect, you may repeat the question and achieve the correct answer. You do not need a correct answer to move forward through the lab.
* &#x20;Optionally, use ls to view the same information for the **devprojects** directory.

### Configure permissions <a href="#configure-permissions" id="configure-permissions"></a>

You will use the chmod command in symbolic mode to configure permissions for the resource owner, the associated group, and all others.

1.  &#x20;Run the following command to display the current permissions for the **/projects/ITprojects** directory:

    ```bash-notab-nocopy
    ls -ld /projects/ITprojects
    ```
2.  &#x20;Configure the permissions according to the table below. You may select the _Set the permissions_ section below if you need a reminder on how to configure permissions:

    | Resource:             | User/Group:   | Access Level: |
    | --------------------- | ------------- | ------------- |
    | /projects/ITprojects  | user01/admins | rwxrwxr-x     |
    | /projects/devprojects | user02/devs   | rwxrwxr-x     |
3.  Confirm that permissions are set correctly for the /projects/ITprojects directory.

    Correct





### Comprehensive questions <a href="#comprehensive-questions" id="comprehensive-questions"></a>

Answer the following final comprehensive questions to ensure that you recognize the importance of the activity steps and the uses for the information you have learned.

1.  Which command below adds userA to groupZ?

    useradd userA groupzuseradd userAgroupmod -aG userA groupZusermod -aG groupZ userA

* Correct
* Enter the command to create a file named "fileA" in a directory named "/test".\

* Correct
* Enter the command to set "admin" as the user and "IT" as the group for a directory named /infrastructure and all of its contents.
* chown -R admin:IT /infrastructure
* Correct
*   Which of the following best describes the steps you took in this activity?

    Configured users and passwords, removed unnecessary users, created computer accounts, managed permissions.Created users and groups and set permissions on files and directories.Created users and groups, added users to groups, created directories and files, configured ownership, configured permissions.Configured file and directory ownership.





