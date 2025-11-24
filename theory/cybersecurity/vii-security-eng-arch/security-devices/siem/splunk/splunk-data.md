# Splunk: Data

## Parsing

Splunk needs to be properly configured to parse and transform the logs appropriately. Some of the issues being highlighted are:

* Event Breaking:
  * Configure Splunk to break the events properly.<br>
* Multi-line Events:
  * Configure Splunk to configure multi-line events properly.<br>
* Masking:
  * Some logs contain sensitive data. To comply with the PCI DSS (Payment Card Industry Data Security Standard) standard, information like credit card numbers must be masked to avoid any violation.<br>
* Extracting custom fields:<br>
  * In the weblogs, some fields are redundant and need to be removed.



## Data process in splunk

### Step 1: Understand the Data Format

First, you need to understand the data format you want to parse. Splunk supports various data formats, such as CSV, JSON, XML, syslog, and more. Determine the format of your data source and the relevant fields you want to extract.

### Step 2: Identify the Sourcetype<br>

In Splunk, the sourcetype represents the format of the data being indexed. It helps Splunk apply the appropriate parsing rules. If your data source does not have a pre-defined sourcetype, you can create a custom one in Splunk.

### Step 3: Configure `props.conf`<br>

The `props.conf` file defines data parsing settings for specific sourcetypes or data sources. It resides in the `$SPLUNK_HOME/etc/system/local` directory. Here’s an example of how you can configure `props.conf`:

```c
[source::/path/to/your/data] 
sourcetype = your_sourcetype
```

In this example, `/path/to/your/data` is the path to your data source, and `your_sourcetype` is the name of the sourcetype you want to assign to that data.

### Step 4: Define Field Extractions<br>

You can define regular expressions or use pre-built extraction techniques to parse fields from the data. Here’s an example of defining field extractions in `props.conf`:

```c
[your_sourcetype] 
EXTRACT-fieldname1 = regular_expression1 
EXTRACT-fieldname2 = regular_expression2
```

Replace `your_sourcetype` with the actual sourcetype name you defined. `fieldname1` and `fieldname2` represent the names of the fields you want to extract, while `regular_expression1` and `regular_expression2` are the regular expressions used to match and extract the desired values.

### Step 5: Save and Restart Splunk<br>

After making changes to `props.conf`, save the file, and restart Splunk to apply the new configurations. You can do this using the Splunk web interface or by using the command line.

## Step 6: Verify and Search the Data

\
Once Splunk restarts, you can search and verify that the data is being parsed correctly. You can use the extracted fields to filter and analyze the data effectively.

In the next task, we will explore important configuration files.
