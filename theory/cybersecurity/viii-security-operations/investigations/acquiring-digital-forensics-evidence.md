# Acquiring Digital Forensics Evidence

### Scenario <a href="#scenario" id="scenario"></a>

As a digital forensics analyst, you should never work directly on the suspect hard disk drive. In this activity, you will use a built-in Linux command to duplicate the suspect disk. You will also use hashing to ensure data integrity. Next, on a Windows computer, you will use the file carving tools provided with the open source forensics suite Autopsy ([sleuthkit.org](https://www.sleuthkit.org)) to investigate a disk image. You will open a pre-built case file and probe the information extracted to identify a malware installation event.

### Use Linux to create a disk image <a href="#use-linux-to-create-a-disk-image" id="use-linux-to-create-a-disk-image"></a>

A virtual hard disk drive containing possible evidence has already been attached to the PT1-Kali Linux virtual machine. You need to create a disk image, and then prove whether there have been unexpected changes to the file during the investigation. Linux contains a built-in tool named dd that can easily create copies of disks for forensics professionals. You will use dd to create an image. Next, you will use MD5 hashes to discover whether a file has changed unexpectedly.

1.  &#x20;Log in to the [PT1-Kali](https://labclient.labondemand.com/Instructions/c9af2577-4d63-4cc2-9f71-7a6b72c85c4a?rc=10) VM with root and Pa\$$w0rd

    > The suspect 1 GB disk is already attached to the PT1-Kali VM.
2. &#x20;From the top bar, select **Terminal Emulator**.
3. &#x20;Run lsblk and use the output to record the name of the 1G disk:
4.  &#x20;Run the following commands to display disk information. Make sure you have input the name of the drive (such as sdb) in the text box:

    ```bash-notab-nocopy
    cat /proc/partitions
    ```

    ```bash-notab-nocopy
    df -h /dev/sdb
    ```
5.  &#x20;Use the following command to create a copy of the suspect disk. Make sure you have input the name of the drive (such as sdb) in the text box:

    ```bash-notab-nocopy
    dd if=/dev/sdb of=/root/suspect.img
    ```

    > The image creation process will take several seconds. If the /dev/sdb drive were larger, the process would take much longer.
6.  Confirm that that /root/suspect.img disk image file exists.

    Correct
7. &#x20;Run the md5sum command to generate a checksum and redirect it into a file named suspect.img-hash.
8. d5sum suspect.img > suspect.img-hash
9. ```bash-notab-nocopy
   cat suspect.img-hash
   ```
10. Confirm that the /root/suspect.img-hash file exists.
11.
12. &#x20;To mark the image with today's date, run the following command:

    ```bash-notab-nocopy
    echo "Today is $(date)" > suspect.img
    ```

    > This command might not seem like a good idea, but run it anyway!
13. &#x20;Use the md5sum command from the previous steps to hash the suspect.img file again, but this time, _append_ the hash results to the existing suspect.img-hash file.

    > You must enter the following command carefully, or you will destroy the hash generated for the original suspect.img file. Note the use of **>>** instead of **>**. The double greater-than signs append data to the file without over-writing existing data.

    ```bash-notab-nocopy
    md5sum suspect.img >> suspect.img-hash
    ```
14. &#x20;Use the cat command from earlier steps to display the contents of the suspect.img-hash file.
15. Are the hash values the same?

    YesNo
16.
17. &#x20;Run the following command to display the contents of the suspect.img file:

    ```bash-notab-nocopy
    cat suspect.img
    ```

    > It appears that you accidentally overwrote the entire file, hence the hashes are different. This is an extreme example of the risks of working directly with evidence. Because you still have the original content, located at /dev/sdb, you could use dd to create another image file. Had you been working directly with the disk content, the evidence would have been destroyed.



### Browse forensics case file <a href="#browse-forensics-case-file" id="browse-forensics-case-file"></a>

Open the "Forensics – Marketing" case in Autopsy, and browse the disk image that has been seized as evidence.

1. &#x20;Select the [MS1](https://labclient.labondemand.com/Instructions/c9af2577-4d63-4cc2-9f71-7a6b72c85c4a?rc=10) VM, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/c9af2577-4d63-4cc2-9f71-7a6b72c85c4a?rc=10), and then log in with the username 515support\Administrator and password Pa\$$w0rd.
2. &#x20;Close Server Manager.
3. &#x20;Use the desktop shortcut to start **Autopsy**. The program takes 1-2 minutes to open.
4. &#x20;From the Welcome dialog box, select the **Open Case** icon.
5. &#x20;In the Open dialog box, browse to the **Forensics - Marketing** folder on the Desktop, select **Forensics - Marketing.aut** and select **Open**.
6. &#x20;Autopsy identifies many critical portions of the storage media for you. You may briefly examine the following components:
   *   Expand the **Data Sources** node then select the **marketing.vhd** disk in the main pane. In the lower pane, select the **Hex** tab.

       This is the Master Boot Record, residing in the first 512-byte sector on the disk.
   *   Expand the **marketing.vhd**, and then select **vol2**. This is the system volume and is normally hidden from view.

       Observe that the initial string of hex characters identifies the partition type as NTFS.
7.  &#x20;Select **vol3**. This is the boot volume, hosting the OS files and applications plus user data. Expand the folders to **Users > Viral > Downloads**. Observe what is shown.

    You can see the symbolic links for the current directory and parent directory, plus the default view settings configuration file, but there are no download files present.
8. &#x20;Autopsy also displays drive contents. You may briefly examine the following results:
   * Under the **Results** node, select the **EXIF Metadata** node. Criminal investigations might need to locate images of illegal activity. This search has only located the default Windows backgrounds, though.
   * Under the **Encryption Detected** and the **Encryption Suspected** nodes. The presence of encrypted files in suspect locations could be a red flag.
   * Under the **Installed Programs** node. Sort by the **Date/Time** column to display what has been installed recently.
   * Under the **Operating System Information** and **Operating System User Account** nodes. Select **Viral's** user account for more information on a per-user basis.
9. What are the last four digits of Viral's Security Identifier (SID)?

* Correct
* &#x20;Continue examining the results from automated analysis of the drive:
  * Under the **Web History** node. You could display information about web browsing habits in this node.
  * Under **E-Mail Messages**. You might find some valuable information here.
  * Under **Interesting Items**. There are numerous references to an "atypical" compression file format (not native to Windows, that is) within the **carved files** area (that is, typically files that have been deleted).

### Browse activity timeline <a href="#browse-activity-timeline" id="browse-activity-timeline"></a>

Viewing the timeline of file activity might also help to reconstruct the pattern of events.

1.  &#x20;Select the **Timeline** button from the menu at the top of the Autopsy user interface.

    Once the database has been repopulated (this will take a few minutes), a high-level chart of file activity will be displayed in a new window.
2. &#x20;Maximize the window.
3. &#x20;From the Display times in panel, select **GMT/UTC**.
4.  &#x20;Right-click the long bar for **2017** and select **Zoom into Time Range**. Repeat to zoom into **April** and then the **29th**. Finally, repeat **Zoom into Time Range** again for the **14** hour (2pm).

    > There is a **History - Back** button in the upper left of the interface. If you select a setting in error, use that to return to an earlier time setting.
5. &#x20;From the View Mode panel, select the **List** button. Scroll down to locate the section containing the email message at **14:48:00** (it is near the bottom of the list).
6. &#x20;You can read the content of the email from Viral and examine the other operating system activities at this time.
7.  Which of the following answers best describes what security incident occurred, based on the information from Viral at 14:48:00?

    Viral was tricked into installing malware from an untrusted web site.Viral installed malware from an untrusted DVD.Viral was tricked into installing malware from an email attachment.Viral tricked CRM Admin into installing malware.

*   Correct

    > The lab interface makes it difficult to adjust column widths in this application. Use the **Full Screen** feature of the lab environment to maximize window space. Also, you can show the full text in a column by pointing to a field to show its tooltip.
* &#x20;Select the email message from Viral at 14:48:00 that reads _I've installed the update but it didn't seem to do anything?_. Right-click the message, choose **Extract File(s)**, and then save it to the **Desktop** with the default file name **Sent-1**.
*   Confirm that the Sent-1 file exists on the Administrators desktop.

    Correct
*
* &#x20;Close the **Timeline** window.
* &#x20;Close **Autopsy**.
