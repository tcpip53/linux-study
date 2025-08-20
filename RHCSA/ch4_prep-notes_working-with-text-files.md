```
1. which command was developed to show only the first ten lines in a text file? <br> 
a. head [x]<br>
b. top []<br> 
c. first []<br> 
d. cat [] <br> 

NAME
       head - output the first part of files
SYNOPSIS
       head [OPTION]... [FILE]...
DESCRIPTION
       Print the first 10 lines of each FILE to standard output.  With more than one FILE, precede each with a header giving the file name.

NAME
       top - display Linux processes
SYNOPSIS
       top [options]
DESCRIPTION
       The  top  program  provides a dynamic real-time view of a running system.  It can display system summary information as well as a list of
       processes or threads currently being managed by the Linux kernel
  
c. first
no comand 
d. cat
NAME
       cat - concatenate files and print on the standard output
SYNOPSIS
       cat [OPTION]... [FILE]...
DESCRIPTION
       Concatenate FILE(s) to standard output.
       With no FILE, or when FILE is -, read standard input.
```
---       

```       
2. Which command enables you to count the number of words in a text file?
a. count []
b. list  []
c. ls -l [] 
d. wc    [x]

a. count is not a command 
b. list is not a command 
c. ls is used to list files
d. wc 
NAME
       wc - print newline, word, and byte counts for each file

SYNOPSIS
       wc [OPTION]... [FILE]...
       wc [OPTION]... --files0-from=F
```

---

```
3. Which key on your keyboard do you use in less to go to the last line of the
current text file?
a. End        [x]
b. Page Down  []
c. q          []
d. G          []


less is a pager program 
a. End single key to move to end of file 
b. Page Down single key to move 
c. q quits less 
d. G will also move to end of file but not single key 

```

---

```
4. Which option is missing (…) from the following command, assuming that you
want to filter the first field out of the /etc/passwd file and assuming that the
character that is used as the field delimiter is a :?
cut ... : -f 1 /etc/passwd
a. -d [x]
b. -c []
c. -t []
d. -x []

a. -d
Set the field delimiter to the character delim. The default is the <tab>. this option is correct and needed because the colon is used as trhe delimiter in 
b. -c
this option is used to cut a certian number of characters from a file 
c. -t
this is not a valid option 
d. -x
this is not a valid oprion
```
---

```
5. Which option is missing (…) if you want to sort the third column of the out-
put of the command ps aux?
ps aux | sort ...
a. -k3     [x]
b. -s3     []
c. -k f 3  []
d. -f 3    []
```
---

```
6. Which of the following commands would only show lines in the file
/etc/passwd that start with the text anna?
a. grep anna /etc/passwd    []
b. grep -v anna /etc/passwd []
c. grep $anna /etc/passwd   []
d. grep ^anna /etc/passwd   [x]

a.
this would list all return all instances of anna 
b.
this would select all the lines not match anna 
c.
the $ sign is an anchor matching at the end of the line 
d.
the ^ sign is an anchor matching at the start of the line 
```
---

```
7. Which regular expression do you use to make the the previous character optional? 
a. ? [x]
b. . []
c. * []
d. & []

a.
*?* would be used to mark characters ad optional 
b. 
_._ used to match any character 
c. 
_*_ used to match character zero or more times
d. 
_&_ is not a standard metacharacter 

```

``` 
8. Which regular expression do you if you want the preceding character to occur at least one time? 

a. ? []
b. . []
c. * [x]
d. + []


a.
*?* would be used to mark characters ad optional 
b. 
_._ used to match any character 
c. 
_*_ used to match character zero or more times
d. 
_+_ matches one or more characters of the preceding element 
```

```
9. Assuming that the field delimiter : is used, which command prints the fourth field of a line in the /etc/passwd if the text *user* occurs in that line  

a. awk '/user/ { print $4 }' /etc/passwd        []
b. awk -d : '/user/ { print $4 }' /etc/passwd   [] 
c. awk -F : '/user/ $4' /etc/passwd             []
d. awk -F : '/user/ { print $4 }' /etc/passwd   [x]


a. awk '/user/ { print $4 }' /etc/passwd
search for pattern *user* as defined in `/` and prints the fouth column
  
b. awk -d : '/user/ { print $4 }' /etc/passwd 
this will result in an error. `-d` must be use in conjuction w/ a file name  

c. awk -F : '/user/ $4' /etc/passwd
this is half correct; $4 should be used with a `PRINT` statement 

d. awk -F : '/user/ { print $4 }' /etc/passwd 
correct answer *-F* is the feild seperator option *:* is the delimiter ` { print $4 } ` is the awk commnad to print the fourth column

*notes on awk, havent seen it explanined in the chapter but the default delimiter is " " (whitespace)[https://labex.io/tutorials/linux-how-to-use-delimiters-in-awk-parsing-426190] which can cause results that are not intended for patteren matching 
```

```
10. Which option would you use with grep to show only lines that do not contain
the regular expression that was used?
a. -x []
b. -v [x]
c. -u []
d. -q [] 

a. -x 
force PATTERN to maych only whole lines 
b. -v
select non-matching lines
c. -u
report offsets as if CRs were not there ˘\(`_`)/˘
d. -q
suppress all normal output
```

