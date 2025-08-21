1. What should you do with the root user account to enhance system
security?
a. Don’t set a password.                 []
b. Allow password-less sudo.             []  
c. Delete the root user.                 []
d. Disable SSH login for the root user.  [x]

2. On a default installation of an RHEL 9 server, which group does the user typi-
cally need to be a member of to be able to use sudo to run all administration
commands?

a. admin []  
b. root  []
c. sys   []
d. wheel [x]

3. Which of the following sudo configurations allows user amy to change
passwords for all users, but not root?

a. amy ALL=! /usr/bin/passwd root, /usr/bin/passwd
b. amy ALL=/usr/bin/passwd, ! /usr/bin/passwd root
c. amy ALL=passwd, ! passwd root
d. amy ALL=! passwd root, passwd

4. Which of the following commands shows correct syntax for using a command
with a pipe in a sudo environment?

a. sudo -c "cat /etc/passwd | grep root"     []   
b. sudo "cat /etc/passwd | grep root"        []
c. sudo sh -c "cat /etc/passwd | grep root"  []
d. sudo cat /etc/passwd | grep root          [x]


5. Which configuration file should you change to set the default location for all
new user home directories?
a. /etc/login.defaults     []     
b. /etc/login.defs         []
c. /etc/default/useradd    [x] 
d. /etc/default/login.defs []


6. Which command enables you to get information about password properties
such as password expiry?
a. chage -l        [x] 
b. usermod --show  [] can be used to set expire date with **-e** option
c. passwd -l       [] can be user to set expire date with **-e** option 
d. chage --show    [] there is no *show* option for the **chage** command 

7. Which of the following files is not processed when a user starts a login shell?
a. /etc/profile    []  for system wide environment changes 
b. /etc/.profile   [x] does not exist
c. ~/.bashrc       [] for user logins 
d. ~/.bash_profile [] for user logins 

8. Which of the following offers the best option to modify user group
membership?
a. vigr      [] 
b. vipw      []
c. vipasswd  []
d. usermod   [x]

9. Which command can be used to list all the groups a user is a member of?
a. userlist  []
b. grouplist []
c. id        [x]
d. groups    [x]

What can you do to ensure that no users, except for the user root, can log in
temporarily?
a. Set the default shell to /usr/sbin/nologin.   []
b. Set the default shell to /bin/false.          []
c. Create a file with the name /etc/nologin.     [x]
d. Create a file with the name /etc/nologin.txt. []

