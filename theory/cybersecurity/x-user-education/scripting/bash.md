# Bash

## Scripting

Start running script with **./scriptname.sh**

Start writing scripts with **#!/bin/bash**

```
#!/bin/bash
#sample code
sedcmd=""
while read -r findtxt replacetxt; do
    sedcmd+="s/$findtxt/$replacetxt/g;"
done < corrections.txt
for filename in $*; do
    echo "Correct file $filename"
    sed -i.bak "$sedcmd" $filename
done


```

Explanation:

`#!/bin/bash`

Explanation: This is called a shebang. It tells the operating system that this script should be run using the BASH shell.

Example:

`#!/usr/bin/python3`

This would tell the system to run the script with Python 3 instead.



`sedcmd=""`

Explanation: This initializes an empty string variable sedcmd. It will later store all the sed substitution commands.



