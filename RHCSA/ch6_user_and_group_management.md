##Reading Notes
##sudo
###configure user for sudo 
  - changes must be made in the visudo file/tool
    - for user configuration find the "User Privilige Specification" 
      - line number 80? 
  - Make the administrative user account a member of the group wheel by using usermod -aG wheel user. 
  - Type visudo and make sure the line %wheel ALL=(ALL) ALL is included.
  - to allow a user to run specific commands 
    - `linda ALL=/usr/bin/useradd, /usr/bin/passwd` 
    -  username ALL=command1, command2

  - user a user has entered thier password for sudo the default timeout is 5 minutes and the the password will need to be re-entrered. to extened the time the sudo password token is valid add the following line to the visudo file `Defaults timestamp_timeout=240` 240 is the number of minutes 
  -  this command adds an exception fore the user linda that she is not alllowed to change the root password but can change passwords for other users and add users. note the placement of the `!` `linda ALL=/usr/ bin/useradd, /usr/bin/passwd, ! /usr/bin/passwd root.`  
  - according to the reading it is a best practice to create a copy of the /etc/sudoers file it think or create and alias to the orginal file not 100% what a "drop in file" is 
  - when working on ish on the ipad there is no `useradd` command and working by default with the root user 

- 

##Creating and Managing User Accounts
###

  - sample of /etc/passwd 
ntp:x:38:38::/etc/ntp:/sbin/nologin 
chrony:x:994:993::/var/lib/chrony:/sbin/nologin 
abrt:x:173:173::/etc/abrt:/sbin/nologin 
pulse:x:171:171:PulseAudio System Daemon:/var/run/pulse:/sbin/nologin

    - username:password:UID:GID:comment:home directory:shell

    - UIDs less than 1000 are used for system accounts 

    - passwords are stored in /etc/shadow

# Understanding Different User Types

## users on linux
- privileged users
  - root is the defualt privilieged user 
- unprivileged users
- use `id` to get information abaout user account 

## Working as root 

|Method|Descripton|
|------|----------|
|su|opens subshell and commands as root only in the subshell|
|sudo|authorized users can work as administator|

## Using su 
  - `su` is used to switch users 
  - 

 

