# APT

In this scenario, reports of the below graphic come in from your user community when they visit the Wayne Enterprises website, and some of the reports reference "P01s0n1vy." In case you are unaware, P01s0n1vy is an APT group that has targeted Wayne Enterprises. Your goal, as Alice, is to investigate the defacement, with an eye towards reconstructing the attack via the Lockheed Martin Kill Chain.

## Question 1. Source IP of scanner

In this example, we're trying to understand the different sourcetypes that are scanning the website imreallynotbatman.com. From there we can drill down and further iterate on the search to find the IP address that is performing the scanning.

### Solution

```
index=botsv1 imreallynotbatman.com
```

| **Values of src\_ip** | Count  | %       |   |
| --------------------- | ------ | ------- | - |
| 40.80.148.42          | 38,416 | 72.767% |   |
| 192.168.250.70        | 11,493 | 21.77%  |   |
| 23.22.63.114          | 2,884  | 5.463%  |   |

| **Values of src** | Count  | %       |   |
| ----------------- | ------ | ------- | - |
| 40.80.148.42      | 51,130 | 76.607% |   |
| 192.168.250.70    | 11,493 | 17.22%  |   |
| 23.22.63.114      | 4,120  | 6.173%  |   |

Because now we know IP addresses, we can drill down to check ones with http. Adding sourcetype narrows down results:

```
index=botsv1 imreallynotbatman.com sourcetype=stream:http
```

| **Values**   | Count  | %       |   |
| ------------ | ------ | ------- | - |
| 40.80.148.42 | 20,964 | 94.432% |   |
| 23.22.63.114 | 1,236  | 5.568%  |   |

Two possible IP addresses were left.

## Question 2. Evaluating IPs

Now we need validate the results and check what is what.

By utilizing the IP address obtained from our stream data and modifying the sourcetype to Suricata (an IDS tool), we gain access to a variety of logged events originating from that specific IP address.

#### Kill Chain Phase

* Reconnaissance

#### Sourcetypes

* suricata

### Solution

```
index=botsv1 imreallynotbatman.com sourcetype=suricata
```

After receiving results to see interesting fields we add extra ones with suricata signatures after receiving results. Fields are addedd when clicking on "X more fields" after each search:

If we check each IP separately, we can decide if it was detected by suricata. If IP was not malicious, it should not have triggered many signatures:

```
index=botsv1 imreallynotbatman.com src=<IP> sourcetype=suricata
```

23.22.63.114 does not return IDS signatures. Or at least it was not detected using intrusive means.

40.80.148.42 return many suricata signatures detected

## Question 3. Web scanner origins

What company created the web vulnerability scanner used by P01s0n1vy?

#### Kill Chain Phase

* Reconnaissance

#### Sourcetypes

* stream:http

## Solution

Search for the details with that IP in http stream because http might have registered requestor client in http request headers

```
index=botsv1 src=40.80.148.42 sourcetype=stream:http 
```

From dest\_headers field we see that acunetix was used:

POST /joomla/index.php/component/search/ HTTP/1.1 Content-Length: 124 Content-Type: application/x-www-form-urlencoded Cookie: ae72c62a4936b238523950a4f26f67d0=v7ikb3m59romokqmbiet3vphv3 Host: imreallynotbatman.com Connection: Keep-alive Accept-Encoding: gzip,deflate User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.21 (KHTML, like Gecko) Chrome/41.0.2228.0 Safari/537.21 Acunetix-Product: WVS/10.0 (Acunetix Web Vulnerability Scanner - Free Edition) Acunetix-Scanning-agreement: Third Party Scanning PROHIBITED Acunetix-User-agreement: http://www.acunetix.com/wvs/disc.htm Accept: \*/\*

Similar result can be achieved with http\_user\_agent.

## Question 4. Which Web Server is the Target

What content management system is imreallynotbatman.com likely using

#### Kill Chain Phase

* Reconnaissance

#### Sourcetypes

* stream:http, iis

### Solution

From previous search joomla was found. But also we can do different search just for that to confirm. From destination IPs we see

| 192.168.250.70 | 20,999 | 99.995% |   |
| -------------- | ------ | ------- | - |
| 192.168.250.40 | 1      | 0.005%  |   |

192.168.250.70 possible host of web site. So we edit our seach to

```
index=botsv1 dest=192.168.250.70 sourcetype=stream:http
```

With easy search we find in results which confirm joomla:

| http://imreallynotbatman.com:80/                                                                  | 11,575 | 94.916% |
| ------------------------------------------------------------------------------------------------- | ------ | ------- |
| http://imreallynotbatman.com/joomla/index.php/component/search                                    | 45     | 0.369%  |
| http://imreallynotbatman.com/joomla/administrator/index.php?option=com\_extplorer\&tmpl=component | 44     |         |

Smart search would also include succesful http response 200 value. Later check by uri.

```
index=botsv1 dest=192.168.250.70 sourcetype=stream:http status=200
```

```
index=botsv1 sourcetype=iis sc_status=200 | stats values(cs_uri_stem)
```

## Question 5. Which Web Server is the Target

Currently what we know:

#### Kill Chain Phase

* Exploitation

#### Sourcetypes

* stream:http

Lets determine how our site was exploited. HTTP POST method use to send data to web server, so we can check that.

## Solution

```
index=botsv1 sourcetype=stream:http dest="192.168.250.70" http_method=POST
```

We are now still seeing two IP addresses. Even though it has been confirmed that one IP address was used for vulnerability scanning, we should not forget about other IP addresses. Who actually logged in? Who pass'ed?

<pre><code><strong>index=botsv1 sourcetype=stream:http dest="192.168.250.70" http_method=POST pass
</strong></code></pre>

Luckly, we see session token was given to the 23.22.63.114

\<anything>username\<anything>passwd\<anything> is string sent for login. To check how many logins were attempted from each source we check HTTP form data with this query:

```
index=botsv1 sourcetype=stream:http dest="192.168.250.70" http_method=POST form_data=*username*passwd* | table form_data
```

## Question 6. What is the admin pass

Solution

Need to count which password was used more times than other. We already know how form data is sent so we need to see statistics for each password.

Using ChatGPT:

To extract the "passwd" string from the "form\_data" field in your Splunk search, you can use the `rex` command. Here's the modified search query:

```plaintext
index=botsv1 sourcetype=stream:http dest="192.168.250.70" http_method=POST
| rex field=form_data "(?:^|&|\?)passwd=(?<passwd>[^&]+)"
| stats count by passwd
```

In this updated query, the `rex` command is applied to extract the value of "passwd" from the "form\_data" field. The regular expression pattern `(?:^|&|\?)passwd=(?<passwd>[^&]+)` is used to capture the value following the "passwd=" string.

The extracted "passwd" values are then used in the `stats` command to calculate the count of occurrences for each unique password value.

Please note that the regular expression pattern assumes that the "form\_data" field follows the format you provided in your previous message. Adjust the regular expression accordingly if the format varies.

Feel free to modify the search query as needed to include additional fields or criteria based on your specific requirements.

Only batman was used twice:

How these two were apart?

```
index=botsv1 sourcetype=stream:http  
| rex field=form_data "passwd=(?<userpassword>\w+)" 
| search userpassword=batman  
| transaction userpassword 
 | table duration
```

The provided Splunk search query performs several operations to extract and analyze data related to the "form\_data" field. Here's a breakdown of each step:

1. `index=botsv1 sourcetype=stream:http`: This specifies the index and sourcetype to search within. It filters the events based on the sourcetype "stream:http" within the "botsv1" index.
2. `| rex field=form_data "passwd=(?<userpassword>\w+)"`: The `rex` command extracts the value of the "userpassword" field from the "form\_data" field. It uses a regular expression pattern to match and capture the alphanumeric characters following "passwd=".
3. `| search userpassword=batman`: The `search` command filters the events to include only those where the "userpassword" field is equal to "batman". This narrows down the events to those where the password used is "batman".
4. `| transaction userpassword`: The `transaction` command groups events based on the "userpassword" field value. It combines consecutive events with the same "userpassword" into transactions, treating them as a single logical unit. This step helps to determine the duration of each transaction.
5. `| table duration`: The `table` command displays the "duration" field, which represents the duration of each transaction. This provides the time taken for each occurrence of the "userpassword" value "batman".

By running this search query, you can obtain a table displaying the duration of each transaction where the password used is "batman".

## Question 7. What file was uploaded?

What is the name of the executable uploaded by P01s0n1vy?

### Solution

#### Kill Chain Phase

* Installation

#### Sourcetypes

* stream:http, suricata

Files are marked in part\_filename{} field, so we can create a search for exe file and view results:

```
index=botsv1 sourcetype=stream:http dest="192.168.250.70" *.exe part_filename{}=* | table part_filename{}
```

Fields can be searched with phrases like upload. {'action':'upload','message':'Upload successful!','error':'Upload successful!','success':true}

Two files:

If we know the file, we can check more detailed logs for it:

```
index=botsv1 3791.exe
```

From logs we there is too much info, so we can check for known OSINT. Probably start with md5 or other hash.

```
index=botsv1 3791.exe md5
```

Returns aprox 67 results. Lets dig deeper by checking what cmd executed, because it only has 4 logs:

One of these 4 resuls has 3791 executed by cmd. Exacution provides very valuable info: md5, hostname (computer) and so on.

MD5=AAE3F5A29935E6ABCC2C2754D12A9AF0

Searching in virus total auto gives new hash and filename:

## Question 7. What image used for defacement

Because the site was defaced, we want to better understand what ended up on our website to cause the defacement.

#### Kill Chain Phase

* Actions on Objective

#### Resources

* Web Defacement Data Flow

#### Sourcetypes

* suricata, stream:http

Lets check what files our web server dowloaded from the interned after it was compromised:

I bet this one poisonivy-is-coming-for-you-batman.jpeg is interesting.

Just basic search of file in splunk returns 10 results. To check what security tools know about this we can select different source type:\\

From fgt\_utm we see FQDN of the site which stored image file:

Filling in all data:

## Summary

### Background

Here are the Splunk commands that should have been used according training material. The stats and eval commands have a number of additional function beyond the ones listed in case you are curious.

* metadata
* stats – distinct count, count, values, average, AS
* lookup
* eval – lower, length, round
* fields
* table
* AND OR NOT
* sort
* reverse
* transaction
* rex
* search
* inputlookup
* outputlookup
