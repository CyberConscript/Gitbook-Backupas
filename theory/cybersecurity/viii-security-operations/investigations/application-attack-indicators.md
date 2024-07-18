# Application Attack Indicators

### Scenario <a href="#scenario" id="scenario"></a>

You are concerned about discovering application layer attacks against your Windows servers. You have decided to simulate some attacks that might consume processor or memory resources, making the server sluggish or unresponsive. First, you will use CPU Stress to simulate a heavy processor load on the server. Second, you will use testlimit to simulate a similar heavy memory load. In both cases, you will monitor the output by using CPU Explorer, Task Manager, and Performance Monitor.



### Display Process Explorer and Performance Monitor <a href="#display-process-explorer-and-performance-monitor" id="display-process-explorer-and-performance-monitor"></a>

To prepare for application attack detection, you will use Process Explorer and Performance Monitor to display current resource utilization information. You will create a custom Data Collector Set in Performance Monitor to observe a simulated deviation from the baseline.

1. &#x20;On the [DC1](https://labclient.labondemand.com/Instructions/aca6d773-e2b4-451a-9428-2174a7276bcb?rc=10) VM, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/aca6d773-e2b4-451a-9428-2174a7276bcb?rc=10), and then sign on as 515support\Administrator using Pa\$$w0rd as the password.
2. &#x20;In Server Manager, select **Tools > Performance Monitor**.
3. &#x20;Expand the **Data Collector Sets > User Defined** node. Right-click the **User Defined** node and then select **New > Data Collector Set**.
4.  &#x20;Use CPU baseline as the Name, select the radio button for **Create manually (advanced)**, and then select **Next**.

    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
5. &#x20;With **Create data logs** selected, check the box for **Performance Counter**, and then select **Next**.
6. &#x20;On the Which performance counters would you like to log? page, select **Add**.
7. &#x20;On the Available counters page, expand the **Processor** node (it is already highlighted for you). Select the following three counters, and **Add** them to the **Added Counters** column:
   * % Processor Time (this counter is a good general indicator of the processor's overall activity level)
   * % User Time (this counter provides data on time spent by the processor managing user applications)
   * Interrupts/sec (this counter measures interrupts that the processor must handle immediately)
8. &#x20;Select **OK** to complete the **Available counters** dialog box.
9. &#x20;Select **Next**.
10. Which of the following is the path displayed for the Root directory, where the Performance Monitor Data Collector Set logs will be stored?

    %systemdrive%\Performance Monitor\LogsC:\Performance Monitor\LogsC:\\%systemdrive%\PerfLogs\Admin\CPU baselineC:\User\Administrator\Desktop%systemdrive%

*   Correct

    > The purpose behind Assisted Labs is to confirm your knowledge and guide you through the given configurations. If you get a scored question incorrect, you may repeat the question and achieve the correct answer. You do not need a correct answer to move forward through the lab.
*   &#x20;Select **Finish** to complete the Data Collector Set configuration.

    You will start the Data Collector Set in a later step.
* &#x20;Minimize Performance Monitor. You will use it in later tasks.
* &#x20;From the desktop, open the **LABFILES** folder, browse to the **Sysinternals** folder, and then launch **procexp**.
* &#x20;Observe some of the key information reported by Process Explorer, including:
  * CPU Usage in the lower left corner - a percentage of processor utilization
  * The tree format of the processes and their relationships to each other
  * Reorganize data by selecting the column headers. The CPU column can be organized to display processes that are consuming the most resources, for example.
* &#x20;Leave Process Explorer open. You will use it in later tasks.
* &#x20;Right-click the **Taskbar**, and then select **Task Manager**.
* &#x20;Select the **Performance** tab.
* &#x20;Select each of the following three categories to observe the relevant performance information:
  * CPU
  * Memory
  * Ethernet
* &#x20;Leave **CPU** selected.
* &#x20;Leave Task Manager open. You will use it in later tasks.



### Create stress on the CPU <a href="#create-stress-on-the-cpu" id="create-stress-on-the-cpu"></a>

You will use CPU Stress to place a false load on the VM's processors. You'll use Performance Monitor, Task Manager, and Process Explorer to monitor the workload.

1.  &#x20;Select Performance Monitor. Under **Data Collector Sets > User Defined**, right-click the **CPU baseline** set, and then select **Start**.

    You will leave the Data Collector Set running through the next several tasks. It gathers information as you accomplish activity steps.
2.  &#x20;From the C:\LABFILES\Sysinternals folder, open **cpustres64**.

    You will see a dashboard with four pre-created threads available. The menu allows you to start and stop threads, as well as to create new threads. Right-click threads to manage their priority level. You will create and execute threads in a later step.

    > [CPUStres](https://docs.microsoft.com/en-us/sysinternals/downloads/cpustres) is a performance management utility that applies a workload to the processor by creating one or more threads. Each thread can be given a priority level (low, medium, high, maximum). This tool is part of the Windows Sysinternals suite.
3.  &#x20;Resize and reposition the Task Manager, Process Explorer, and CPU Stress windows so that you can observe them simultaneously.

    The goal is to view the effect of starting CPU Stress in Task Manager and Process Explorer.
4.  &#x20;In the CPU Stress console, select the **Create Threads** button. A thread is generated in the window.

    The new thread is currently inactive. You can select additional values, such as workload, affinity, and priority.

    There should now be five threads created. Four were created by default, and you created the fifth.
5. &#x20;Select all five threads, right-click them, and then select **Activity Level** > **Medium (50%)**.
6.  &#x20;In CPU Stress, select the five threads, right-click the selection, and then select **Activate**.

    > The system will become very slow!
7. &#x20;Switch to Task Manager. CPU Utilization should be nearly 100%.
8. &#x20;Switch to Process Explorer. In the lower left corner, CPU Usage should also be nearly 100%.
9. &#x20;In Process Explorer, open the **CPUSTRES64.exe** process to display detailed data. Select **Cancel** when you have browsed each tab.

### End the CPU Stress threads <a href="#end-the-cpu-stress-threads" id="end-the-cpu-stress-threads"></a>

You have now completed the stress test, so you will end the threads.

1.  &#x20;In the CPU Stress console, right-click each thread, and then select **Deactivate**.

    You can select several or all of the threads by holding down the **SHIFT** or **CTRL** keys.
2. &#x20;Display Process Explorer and Task Manager. CPU utlization should be well below 100%.
3. &#x20;Close Process Explorer and CPU Stress.
4. &#x20;Switch to Performance Monitor, right-click the **CPU baseline** data collector set, and select **Stop**.
5. &#x20;Right-click **CPU baseline** and select **Latest Report**. Use this log to answer the following question:
6.  Which of the following answers best describes the results of the CPU baseline data?

    Processor utilization is high, then normal, then high again.Processor utilization is high throughout the activity.Processor utilization is normal, then high, then normal again.Processor utilization is unchanged throughout the activity.

* Correct
*   Confirm that the CPU baseline report directory exists.

    Correct

### Create stress on the Memory <a href="#create-stress-on-the-memory" id="create-stress-on-the-memory"></a>

You will use the testlimit utility to create a false workload that stresses the system's memory, simulating an application attack that attempts to consume RAM. You'll use Peformance Monitor and Task Manager to observe the results.

1. &#x20;Select Performance Monitor, and then create a new Data Collector Set named Memory baseline with the following counters from the **Memory** category:
   * % Committed Bytes In Use (this counter compares committed memory bytes to the byte commit level, indicating paging utilization that may be due to memory leaks or too many open applications)
   * Available MBytes (this counter reports the quantity of memory available for new applications to startup)
   * Pages/sec (this counter reports the rate at which memory pages are written to or from the pagefile on the hard disk drive)
2. > Don’t forget to use exactly the same names as specified in the instructions.
3.  &#x20;Right-click the **Memory baseline** data collector set, and then select **Start**.

    You will leave the Data Collector Set running through the next several tasks. It gathers information as you accomplish activity steps.
4. &#x20;From the desktop, select the Windows **Start** menu, right-click **Windows PowerShell**, and then select **Run as Administrator**. Select **Yes** to confirm the UAC prompt.
5. &#x20;In the Windows PowerShell console, enter cd C:\LABFILES\Sysinternals
6. &#x20;In the Task Manager console, select the **Memory** node.
7.  &#x20;Resize the Windows PowerShell console and the Task Manager console so that you can observe them simultaneously.

    The goal is to view the effect of starting the testlimit utility in Task Manager.
8.  &#x20;Run the following command in Windows PowerShell to simulate the consumption of memory, selecting **Agree** when prompted to accept the license agreement:

    ```
    .\testlimit -d 1024 -c 1
    ```
9.  Which of the following answers best describes the purpose of the .\ characters in this command?

    The .\ characters inform Windows PowerShell that this is a script.The .\ characters inform Windows PowerShell that this is not a script.The .\ characters inform Windows PowerShell to look in the current folder for the executable.All Windows PowerShell cmdlets require .\ as the first two characters.

* Correct
*   &#x20;Switch to Task Manager, and then view the **Memory** category.

    Memory utilization should be very high.
* &#x20;In Task Manager, select the **Processes** tab.
* &#x20;Scroll down to the **Background Processes** section, right-click **Test Windows Limits**, and then select **End Task**.
* &#x20;Select Performance Monitor, and then _stop_ the **Memory baseline** Data Collector Set.
* &#x20;Right-click **Memory baseline** and then select **Latest Report**. Use this log to answer the following question:
*   Which of the following answers best describes the results of the Memory baseline data?

    Memory utilization is normal, then high, and then normal again through the activity.Memory utilization is high, then normal, and then high again through the activity.Memory utilization is high through the activity.Memory utilization is unchanged through the activity.
* Correct
* Confirm that the Memory baseline report directory exists.

<details>

<summary>Memory utilization information</summary>



</details>
