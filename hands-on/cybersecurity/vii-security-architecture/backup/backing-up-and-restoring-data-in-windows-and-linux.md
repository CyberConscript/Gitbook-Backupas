# Backing Up and Restoring Data in Windows and Linux

### Scenario <a href="#scenario" id="scenario"></a>

Data availability is a key component of security. Hard disk drives fail, data is corrupted or accidentally-deleted, or changed in an unplanned manner. In this activity, you will back up data on a Windows server and a Linux server. You'll store the backup jobs on remote servers, which helps protect the data in case of drive failure on the original server. You'll delete the backed up data to simulate its loss, and then restore it from the remote servers to a different location on the original servers.



### Backup files on Windows <a href="#backup-files-on-windows" id="backup-files-on-windows"></a>

You will back up files on the Windows server and store the backup job on a remote server.

1. &#x20;On the [DC1](https://labclient.labondemand.com/Instructions/94b8698d-b237-4f70-9e60-bb1ce8d34316?rc=10), send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/94b8698d-b237-4f70-9e60-bb1ce8d34316?rc=10), and then sign on using 515support\Administrator and Pa\$$w0rd as the password.
2. &#x20;Open **File Explorer**, browse to the **C:** drive, and then create a new folder named Backups.
3. &#x20;To share the **C:\Backups** folder, right-click it, select **Properties**, select the **Sharing** tab, select **Advanced Sharing**, and check the box for **Share this folder**.
4.  &#x20;Select the **Permissions** button. Share the folder with the **Everyone** group at **Full Control**.

    > The folder is only being left open for the purposes of this activity. You would normally apply NTFS permissions to restrict access to a backup operator account.
5. &#x20;Select **Apply** and then confirm each dialog box.
6. &#x20;Switch to the [MS1](https://labclient.labondemand.com/Instructions/94b8698d-b237-4f70-9e60-bb1ce8d34316?rc=10) VM and send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/94b8698d-b237-4f70-9e60-bb1ce8d34316?rc=10). Sign in by using 515support\Administrator and Pa\$$w0rd.
7.  &#x20;From Server Manager, select **Tools > Windows Server Backup**.

    Most backup operations would run to a schedule, but for this activity you will configure a manual backup on the **MS1** server.
8.  &#x20;From the wbadmin console, select the **Local Backup** node.

    It takes about one minute for the backup program to check the server's configuration.
9. &#x20;From the Actions pane, select **Backup Once**, then select **Next**.
10. &#x20;Select **Custom**, then select **Next**.
11. &#x20;Select **Add Items** and browse to drive **C: > LABFILES**, and then check the box next to **Sysinternals** to back up the entire folder. Select **OK**, and then select **Next**.
12. &#x20;Select **Remote Shared Folder**, and then **Next**.
13. &#x20;Enter \\\DC1\Backups, select **Next**, and then select **Backup**.

    The backup job takes about three minutes to complete.
14. Confirm the contents of the C:\Backups folder on DC1 contains the WindowsImageBackup file.



### Restore files on Windows <a href="#restore-files-on-windows" id="restore-files-on-windows"></a>

In this activity, you will restore the files you "accidentally" deleted in the previous task.

1. &#x20;On the [MS1](https://labclient.labondemand.com/Instructions/94b8698d-b237-4f70-9e60-bb1ce8d34316?rc=10) VM, in the wbadmin console, select **Recover** from the Actions menu to begin the restore process.
2. &#x20;Select **A backup stored on another location**, and then select **Next**.
3. &#x20;Select **Remote shared folder** and then select **Next**.
4. &#x20;Enter \\\DC1\Backups, and then select **Next**.
5. &#x20;Ensure the current date is selected, and then select **Next**.
6. &#x20;Choose to restore **Files and folders**, and then select **Next**.
7.  &#x20;In the **Select Items to Recover** window, browse to **MS1 > Local disk (C:) > LABFILES > Sysinternals**, and then select **Next**.

    You will recover the entire folder, but you can also restore individual files.
8. &#x20;In the Specify Recovery Options window, select the **Browse** button, and then select **This PC > Local Disk (C:)**, and select **Make New Folder**.
9. &#x20;Name the new folder RecoveredData and then select **OK**.
10. &#x20;In the Specify Recovery Options window, select **Next**.
11. &#x20;Select **Recover**.

    The recovery process takes about two minutes. You may proceed to the next step, however.
12. &#x20;Close the Windows Server Backup utility.
13. &#x20;Browse to C:\RecoveredData and display the restored files to confirm the recovery process worked correctly.
14. Confirm that the C:\RecoveredData folder exists.



### Backup files on Linux <a href="#backup-files-on-linux" id="backup-files-on-linux"></a>

In this activity, you will create a few resources, and then perform a basic backup by using the tar command. You will store the backup job on a remote Linux server. Finally, you will delete the resources to simulate lost or corrupted data.

1. &#x20;Sign on to the [PT1-Kali](https://labclient.labondemand.com/Instructions/94b8698d-b237-4f70-9e60-bb1ce8d34316?rc=10) VM as root using Pa\$$w0rd.
2. &#x20;From the top bar, open the **Terminal Emulator** icon.
3.  &#x20;Run the following commands to create a directory and several files:

    ```bash-notab-nocopy
    mkdir /inventory
    ```

    ```bash-notab-nocopy
    touch /inventory/hardware.txt /inventory/software.txt
    ```
4.  &#x20;Run the following command to display the contents of the _/inventory_ directory:

    ```bash-notab-nocopy
    ls /inventory
    ```
5. &#x20;Enter cd /inventory to change to the inventory directory.
6.  &#x20;Run the following command to create a backup job named _inventory.tar_:

    ```bash-notab-nocopy
    tar -cf inventory.tar /inventory
    ```
7.  &#x20;Run the following command to display the contents of the _inventory_ tarball:

    ```bash-notab-nocopy
    tar -tf inventory.tar
    ```
8.  Confirm that the /inventory/inventory.tar exists.

    Correct
9. >
   >
   >
   >
   >
   >
   > Don’t forget to use exactly the same names as specified in the instructions.
10. &#x20;Create a new file named devices.txt in the _/inventory_ directory:

    ```bash-notab-nocopy
    touch /inventory/devices.txt
    ```
11. &#x20;Append the new _devices.txt_ file to the existing _inventory.tar_ tarball:

    ```bash-notab-nocopy
    tar -rf inventory.tar /inventory/devices.txt
    ```
12. &#x20;Display the contents of the _inventory.tar_ tarball again by using the -tf option, as you did a few steps above to confirm that the _devices.txt_ file has been added.
13. &#x20;Run the following command to generate a hash of the _inventory.tar_ backup job:

    ```bash-notab-nocopy
    md5sum inventory.tar
    ```

    The hash is displayed on the screen. This value uniquely identifies the state of the file. Any changes to the file, such as corruption during the network transfer, would cause the md5sum hash command to generate a different hash value. In this step, you have generated a hash based on the original file condition. In a later step you will generate a second hash and confirm that they are identical. Hashing helps to guarantee file integrity.
14. &#x20;Run the md5sum has command a second time, and redirect the results into a file named backuphash.

    ```bash-notab-nocopy
    md5sum inventory.tar > /root/backuphash
    ```
15. &#x20;Run the following command to copy the backup job to the LX1 VM by using scp:

    ```bash-notab-nocopy
    scp inventory.tar root@10.1.0.10:/root/inventory.tar
    ```
16. &#x20;Enter yes and Pa\$$w0rd when prompted.

    > The scp command provides a secure copy function across a network. It is an easy way of transferring files. You have now stored your backup job on a remote server.
17. &#x20;Run the following commands to delete the _/inventory_ directory to simulate a mistake or corrupted files.

    ```bash-notab-nocopy
    cd
    ```

    ```bash-notab-nocopy
    rm -fR /inventory
    ```

    > If you type the cd command with no arguments, the system automatically returns you to your home directory. In this case, that is /root.
18. &#x20;Run the ls / to confirm the _/inventory_ directory has been deleted. This simulates an accidentally-deleted directory or corrupted files.

### Restore files on Linux <a href="#restore-files-on-linux" id="restore-files-on-linux"></a>

In this activity, you will restore your "accidentally" deleted files from the remote server.

1.  &#x20;On the [PT1-Kali](https://labclient.labondemand.com/Instructions/94b8698d-b237-4f70-9e60-bb1ce8d34316?rc=10) VM, run the scp command to copy the backup job from the LX1 VM.

    ```bash-notab-nocopy
    scp root@10.1.0.10:/root/inventory.tar /root
    ```
2. &#x20;Enter Pa\$$w0rd when prompted.
3.  &#x20;Check the _inventory.tar_ file on the Kali VM by using the md5sum command to ensure there was no corruption during transfer. Append it to the _backuphash_ file.

    ```bash-notab-nocopy
    md5sum inventory.tar >> backuphash
    ```

    > For this step, you must use >> to _append_ the hash to the existing /root/backuphash file. If you only use >, it will overwrite the existing file contents.
4.  &#x20;Run the cat backuphash command to display the two hashes. They should be the same.

    Because the two hash values are the same, you can be confident that the backup file did not change. The content you are restoring is identical to the content you backed up.
5.  &#x20;Run the following commands to extract the _inventory.tar_ tarball to a directory named _/Inventory_:

    ```bash-notab-nocopy
    mkdir /Inventory
    ```

    > Recall that the Linux CLI is case-sensitive. The above command calls for an uppercase **I** character.

    ```bash-notab-nocopy
    tar -xf inventory.tar -C /Inventory
    ```
6.  Confirm whether the /Inventory/inventory/hardware.txt file exists.

    ls: cannot access '/Inventory/inventory': No such file or directory

*
*   &#x20;Display the _/Inventory/inventory_ directory to confirm that the restore process was successful.

    You should see the devices.txt, hardware.txt, and software.txt files.
