# Bash

## Scripting

Start running script with **./scriptname.sh**

To start, you need to tell your operating system which interpreter you\
want to use for the script. To do this, enter a shebang, which is a combination of a hash mark and an exclamation mark

Start writing scripts with **#!**

**For bash - #!/bin/bash**

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



## Compressing and Archiving

Tar - tape archive

```
tar -cvf HackersArise.tar hackersarise1 hackersarise2 hackersarise3
hackersarise1
```

tar -cvf HackersArise.tar hackersarise1 hackersarise2 hackersarise3\
hackersarise1













