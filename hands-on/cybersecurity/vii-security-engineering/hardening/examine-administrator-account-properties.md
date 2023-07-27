# Examine Administrator account properties

### Examine Administrator account properties <a href="#examine-administrator-account-properties" id="examine-administrator-account-properties"></a>

Implement some Microsoft best practices for securing administrative accounts and learn how not-such-best-practice can compromise organizational security. First, examine the properties of the current Administrator account.

1. &#x20;On the [DC1](https://labclient.labondemand.com/Instructions/8a598b88-49f2-4992-92e2-f23f8689fd80?rc=10) VM, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/8a598b88-49f2-4992-92e2-f23f8689fd80?rc=10) and then sign in as 515support\Administrator using Pa\$$w0rd as the password.
2. &#x20;Select the **Start** menu, right-click **Windows Powershell**, and then select **Run as Administrator**. Confirm the UAC prompt by selecting **Yes**
3.  &#x20;Run the following command to display the Security ID (SID) and other information for the current user:

    ```
    whoami /user
    ```

    > User accounts are actually identified to the system by number, not by name. In Windows, this number is the Security Identifier (SID). In Linux, it is the User Identifier (UID).
4. What are the final three digits of the administrator's SID?

*   Correct

    > The purpose behind Assisted Labs is to confirm your knowledge and guide you through the given configurations. If you get a scored question incorrect, you may repeat the question and achieve the correct answer. You do not need a correct answer to move forward through the lab.

    > You can use the **/all** switch with **whoami** to display additional group and privilege information.
*   &#x20;Run the **get-aduser** cmdlet to display account information:

    ```
    get-aduser -identity administrator -properties *
    ```
*   Which of the following is the DistinguishedName for the Administrator account? (You may have to scroll up in PowerShell to display this information)

    administratorCN=Administrator,CN=Users,DC=corp,DC=515support,DC=comadministrator@corp.515support.comroot500515support\Administratoradministrator.corp.515support.com
* Correct
* &#x20;Minimize the **Administrator: Windows PowerShell** window.



### Manage user, group, and computer objects <a href="#manage-user-group-and-computer-objects" id="manage-user-group-and-computer-objects"></a>

Active Directory stores and manages objects that represent common entities, such as user accounts or computers. You will manage users, groups, and computer objects in this activity.

1. &#x20;In **Server Manager**, from the **Tools** menu, open the **Active Directory Users and Computers** console.
2. &#x20;Expand the **corp.515support.com** domain node.
3.  &#x20;Right-click the **corp.515support.com** domain node, select **New**, and then select **Organizational Unit**. Name the new OU ITAdmins.

    > Microsoft differentiates between the terms _container_ and _organizational unit_. An OU can have a Group Policy Object linked to it, which results in it being easier and more flexible to manage. Containers cannot have linked GPOs and are not typically used for day-to-day AD administration. Observe the difference in the icons between the _Computers_ container and the _ComputersOU_ organizational unit.

    [...less](https://labclient.labondemand.com/Instructions/8a598b88-49f2-4992-92e2-f23f8689fd80?rc=10)
4.  Confirm that the ITAdmins organizational unit account exists

    Correct

* > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
*   &#x20;Right-click the **ITAdmins** OU, select **New**, and select **User**. Create a new user named `IT_Consultant`.

    * First name: Temp
    * Last name: Contractor
    * User login name: IT\_Consultant
    * Password: Pa\$$w0rd

    Confirm that the IT\_Consultant account exists.

    Correct
*
* &#x20;Create a global security group within the **ITAdmins** OU and name it DesktopSupport.
* &#x20;Add the **IT\_Consultant** account to the **DesktopSupport** group.
* &#x20;From the **corp.515support.com** domain object, browse to the **ComputersOU** Organizational Unit, right-click it, select **New** and then create a new computer account named laptop01.
*   &#x20;Run the following PowerShell cmdlet to generate a report of all computer objects in the domain.

    ```
    get-adcomputer -filter * | out-file C:\computers.txt
    ```
*   Confirm that the C:\computers.txt file exists.

    Correct
* > You have created several types of Active Directory objects: users, groups, and computer accounts. You have also stored these objects in the appropriate Organizational Units so that Group Policy Object configurations can be easily applied to the correct OUs and impact the correct users and computers.
* &#x20;Minimize the **Administrator: Windows PowerShell** window.



### Modify an existing GPO to match password requirements <a href="#modify-an-existing-gpo-to-match-password-requirements" id="modify-an-existing-gpo-to-match-password-requirements"></a>

Group Policy is a powerful tool enabling custom user and computer settings to be deployed to objects across Active Directory. Use the Group Policy Management console to examine the 515 Support Local Admin Policy.

1. &#x20;In **Server Manager**, select **Tools > Group Policy Management**.
2.  &#x20;In the Group Policy Management console, expand **Forest > Domains > corp.515support.com** and select the **Default Domain Policy**.

    > The Default Domain Policy defines a single password policy for all members of the entire domain. Microsoft recommends that password management is the only use of the Default Domain Policy.
3. &#x20;Right-click the **Default Domain Policy**, and then select **Edit**.
4. &#x20;Browse to the **Password Policy** node by following this path: **Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies**.
5.  &#x20;You have reviewed your company's written security policy regarding passwords. You must now configure the **Default Domain Policy** to match the following requirements. Double-click each **Policy** value to edit the settings.

    | Setting                       | Value         | Explanation                                                                                                         |
    | ----------------------------- | ------------- | ------------------------------------------------------------------------------------------------------------------- |
    | Minimum Password Length       | 14 characters | All passwords must contain at least 14 characters                                                                   |
    | Complexity Requirements       | Enabled       | Passwords must contain at least three of the following four characteristics: uppercase, lowercase, letters, numbers |
    | Maximum Password Age          | 90 days       | Passwords must be changed every 90 days                                                                             |
    | Minimum Password Age          | 1 day         | Passwords can only be changed once daily                                                                            |
    | Enforce Password History      | 20            | Unique passwords that must be used before an old password may be repeated                                           |
    | Enforce Reversible Encyrption | Disabled      | Makes it possible to decrypt passwords (not recommended)                                                            |
6.  &#x20;In the Administrator: Windows PowerShell window, run the following command to produce a report of the password policy settings to updating configuration documentation:

    ```
    gpresult /H C:\passwords-gpresults.html
    ```
7.  Confirm that the C:\passwords-gpresults.html file exists.

    Correct

<details>

<summary>The C:\passwords-gpresult.html file.</summary>

If the file does not exist, ensure that you saved it to the correct location and with the specified name. Rerun the gpresult command, if necessary.

</details>

> The Default Domain Policy (DDP) applies to ALL domain members, offering no flexibility to have different password polices for different kinds of users (stricter for high-privilege administrators but looser for non-privileged standard users, for instance). Fine grained password policies provide flexibility by enforcing different password requirements for specific users and groups. You will work with fine grained password policies in a later activity.





