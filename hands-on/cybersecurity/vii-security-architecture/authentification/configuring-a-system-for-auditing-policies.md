# Configuring a System for Auditing Policies

### Scenario <a href="#scenario" id="scenario"></a>

In this activity, you will display processes running on the server, confirm applied Group Policy Objects, and then use Group Policy Objects to configure auditing.





### Browse running processes <a href="#browse-running-processes" id="browse-running-processes"></a>

There are many ways of viewing security-oriented information on the system. One aspect of malicious software mitigation is process management. Use the Sysinternals Process Explorer tool ([docs.microsoft.com](https://docs.microsoft.com/en-us/sysinternals)) to view which accounts are running processes.

1. &#x20;On the [DC1](https://labclient.labondemand.com/Instructions/dc54fe91-38fb-42ea-a5e0-c8e39331b5e2?rc=10) VM, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/dc54fe91-38fb-42ea-a5e0-c8e39331b5e2?rc=10) and sign in as 515support\Administrator with the password Pa\$$w0rd.
2. &#x20;Open File Explorer and browse to C:\LABFILES\Sysinternals.
3.  &#x20;Right-click **procexp64.exe** and select **Run as administrator**. Select **Yes** at the UAC prompt.

    In the output, you can see the hierarchy of processes and the various containers for user-mode processes. Kernel processes and critical services are run by SYSTEM whereas less-privileged services are run by either the LOCAL SERVICE or NETWORK SERVICE accounts. User-initiated processes and services are run by the named account (515support\Administrator in the example).

    > Try to spend time observing Process Explorer on different Windows systems with different applications and servers running. Understanding what should be running is critical to identifying what shouldn't.
4.  &#x20;Close the Process Explorer window. Minimize the File Explorer window.

    One of the key points to understand is that any malware that gets executed on this machine will run with at least the privileges of the logged-on user, and as the current user is a domain administrator, that's quite a lot of privileges.
5. &#x20;From the **Start** menu, right-click **Windows PowerShell**, and then select **Run as Administrator**. Select **Yes** to confirm the UAC prompt.
6.  &#x20;Enter the following command to generate similar information:

    ```
    tasklist
    ```

    As most systems run a large number of processes, it is common to run tasklist with filters.
7.  &#x20;Run the tasklist command again, and this time filter for running services. Redirect the output of the command to a text file named C:\services-running.txt.

    ```
    tasklist /SVC /FI "STATUS eq RUNNING" > C:\services-running.txt
    ```
8.  Does the C:\services-running.txt file exist?

    Correct

* > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
* &#x20;Minimize the PowerShell window.



### Auditing effective permissions <a href="#auditing-effective-permissions" id="auditing-effective-permissions"></a>

In this activity, you will use the existing user account **Bobby** to configure and audit NTFS permissions.

1. &#x20;In Server Manager, select **Tools**, and then select **Active Directory Users and Computers**.
2. &#x20;Select the **Users** container, right-click the **Bobby** account, and select **Add to a group**.
3. &#x20;Enter Sales and then select **Check Names**.
4. &#x20;Select **OK** to confirm both dialog boxes.
5.  Confirm that the Bobby user account is a member of the Sales group.

    Correct
6. &#x20;Minimize **Active Directory Users and Computers** open.
7. &#x20;In File Explorer, right-click C:\ and create a folder named data1.
8. &#x20;Select the data1 folder. Right-click within the folder and select **New > Text Document**. Enter the name fileA and press **ENTER**.
9. &#x20;Right-click the **C:\data1** folder, and then select **Properties**.
10. &#x20;Select the **Security** tab to configure NTFS permissions.
11. &#x20;On the Security tab, select the **Edit** button. In the Permissions for data1 dialog box, select the **Add** button.
12. &#x20;Type Sales, and then select the **Check Names** button. Select **OK**.
13. &#x20;With the **Sales** group highlighted in the Permissions for data1 dialog box, select the **Modify** check box in the Allow column. Select **OK** to confirm each dialog box.
14. &#x20;In C:\data1, right-click **fileA.txt**, and then select **Properties**.
15. &#x20;On the **Security** tab, observe that the **Sales** group is listed.
16. Does the Sales group have the Modify permission to fileA.txt?

    YesNo
17. Correct
18. What causes the permissions to be configured this way on fileA.txt?

    Group Policy has configured the permissions this way.You manually configured the Sales group to have the Modify permissions on fileA.The permissions of the parent object C:\data1 were automatically inherited by the fileA child object.These settings are the normal Windows default permissions for new files.
19. Correct
20. &#x20;Select **Cancel** to close the fileA.txt Properties box.
21. &#x20;In File Explorer, right-click the **C:\data1** folder, select **Properties**, select the **Security** tab, and then select the **Advanced** button.
22. &#x20;Select the **Effective Access** tab.
23. &#x20;In the **Select a user** interface, enter Bobby, select **Check Names**, and then select **OK**.
24. &#x20;Select **View effective access** and note the permissions.
25. Assuming this group membership, does Bobby have Full Control access?

    YesNoImpossible to determine
26. Correct

    access Bobby is a member of the Authenticated Users group, and that group does not have Full Control access to the folder.
27. &#x20;In the interface, at **Include group membership**, select **Add items**.
28. &#x20;Enter Administrators, select **Check Names**, and then select **OK**.
29. &#x20;Select **View effective access** again.

    You are simulating the effective permissions on C:\data1 if Bobby were a member of the **Administrators** group.
30. Assuming this group membership, does Bobby have Full Control access?

    YesNoImpossible to determine
31. Correct
32. &#x20;Select **Cancel** to exit each dialog box. Close File Explorer.
33. &#x20;Run the following PowerShell cmdlet to display permissions information for **fileA.txt**:

    ```
    get-acl C:\data1\fileA.txt | format-list | out-file C:\permissions.txt
    ```
34. Confirm that the C:\permissions.txt file exists.

    Correct
35.
36. &#x20;Minimize the PowerShell window.



### Create file system audit policy <a href="#create-file-system-audit-policy" id="create-file-system-audit-policy"></a>

Create a GPO to enforce a file system audit policy.

1. &#x20;In Server Manager, select **Tools**, and then select the **Group Policy Management** console.
2. &#x20;In the Group Policy Management console, select the **Domain Controllers** organizational unit. Right-click it and select **Create a GPO in this domain, and Link it here**.
3.  &#x20;In the Name box, enter Audit Policy and select **OK**.

    > We need to attach the policy to the Domain Controllers OU because this VM is the DC. You would attach the policy to a different OU to configure audit settings for other types of computer object.
4. &#x20;Right-click **Audit Policy** and select **Edit**.
5. &#x20;In the Group Policy Management Editor console, expand **Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > Security Options**.
6. &#x20;Select **Audit: Force audit policy subcategory settings**. Check the **Define this policy setting** check box and select the **Enabled** option button. Select **OK**.
7. &#x20;In the Group Policy Management Editor console, expand **Computer Configuration > Policies > Windows Settings > Security Settings > Advanced Audit Policy Configuration > Audit Policies > Object Access**.
8. &#x20;Double-click **Audit File System**. Check the **Configure the following audit events** check box, and then check the boxes for both **Success** and **Failure**.
9.  &#x20;Select **OK** to close the interface.

    > As you can see, there is a huge number of potentially auditable events. Tuning the audit policy effectively is a critical security administration challenge.
10. &#x20;In the elevated PowerShell console, run the following command to immediately apply the new GPO to the Domain Controllers Organizational Unit:

    ```
    gpupdate /force
    ```
11. &#x20;Leave the PowerShell window open.



### GPO reporting <a href="#gpo-reporting" id="gpo-reporting"></a>

Use the gpresult command to generate a file containing the Group Policy settings that are applied to DC1.

1.  &#x20;Run the following command to create an HTML file containing the applied Group Policy settings:

    ```
    gpresult /H C:\audit.html
    ```
2.  Confirm that the Audit Policy has been configured

    Correct



### Displaying audit policy results by using Event Viewer <a href="#displaying-audit-policy-results-by-using-event-viewer" id="displaying-audit-policy-results-by-using-event-viewer"></a>

You will generate log file entries based on the auditing policy, and then confirm the entries are displayed in Event Viewer.

1. &#x20;In File Explorer, right-click the **C:\data1** folder and select **Properties**.
2. &#x20;In the data1 Properties dialog box, select the **Security** tab, and then select the **Advanced** button.
3. &#x20;On the **Auditing** tab, select **Continue**, and then select **Add**.
4. &#x20;Select the **Select a principal** link, and then in the dialog box, type Authenticated Users and select **OK**.
5. &#x20;Set the **Type** of audit at **All** from the pull-down menu.
6. &#x20;Select all six available check boxes under **Basic permissions**.
7.  &#x20;Select **OK** to confirm each dialog box.

    > Access to file system objects will be recorded in the Security log of Event Viewer.
8. &#x20;Open **C:\data1\fileA.txt**, add today's date to the file, and then save and close it.
9. &#x20;From Server Manager, select **Tools**, and then select **Event Viewer**.
10. &#x20;Expand the **Windows Logs** node, and then select the **Security** log.
11. &#x20;Select the event at the top of the list.

    The event should read "An attempt was made to access an object."
12. Confirm that the file access audit log entry exists for event ID 4663.

    Correct

*
*   Was the event logged as a success or a failure?

    SuccessFailureUndetermined

Correct

