# Commands

## Commands and examples

* Searching with locate. The locate command is not perfect, however. Sometimes the results of  \
  locate can be overwhelming, giving you too much information. Also, locate  \
  uses a database that is usually only updated once a day, so if you just created  \
  a file a few minutes or a few hours ago, it might not appear in this list until  \
  the next day

```
locate <something>
```



* Finding Binaries with whereis. whereis returns just the binaries and man page

```
whereis <something>
```

*   Finding Binaries in the PATH Variable with which. able to find a binary file in the directories listed    \
    in the PATH variable

    ```
    which <something>
    ```
* Powerful Searches with find

```
find <directory> -type <type> -name <something>
```





* Wildcards

```
? - single char
[xyz] - chars in brackets
* - any
```



* To copy files, we use the cp command. This creates a duplicate of the file in  \
  the new location and leaves the old one in place

```
cp old_file location/copy_file
```







* Powerful Searches with find

```
find <directory> -type <type> <something>
```

* To copy files, we use the cp command. This creates a duplicate of the file in  \
  the new location and leaves the old one in place

```
cp old_file location/copy_file
```

* The mv command can be used to move a file or directory to a new location or simply to give an existing file a new name.

```
mv old_file_name new_name
```

* The mv command can be used to move a file or directory to a new location or simply to give an existing file a new name.

```
mv old_file_name new_name
```

* To remove a file, you can simply use the rm command,

```
rm filename
```

* The command for removing a directory is similar to the rm command for  \
  removing files but with dir (for directory) appended

```
rmdir dirname    
rm -r newdirectory
```

* If you just want to view the beginning of a file, you can use the head command

```
head -20 /etc/snort/snort.conf
```

* If you just want to view the end of a file, you can use the tail command

```
tail-20 /etc/snort/snort.conf
```

* To display a file with line numbers, we use the nl (number lines) command.

```
nl /etc/snort/snort.conf    
```

* To display a file with line numbers, we use the nl (number lines) command.

```
nl /etc/snort/snort.conf   
```

* The sed command lets you search for occurrences of a word or a text pattern and then perform some action on it.

```
sed s/what_to_find/how_to_change/ source_file > destination_file
sed s/what_to_find/how_to_change/g source_file > destination_file
sed s/what_to_find/how_to_change/2 source_file > destination_file
```

##

## Analyzing and managing Networks



