# Working on Local Consoles

## Logging in to a local console 

- `sudo -i` will open a root shell, for the commands you only need the paswword of the user configured for sudo use. 
- `su` can also open a roor shell 

## Switching bewween terminal in a graphical enviroment 
- when using a graphical terminal and starting a terminal other terminals started are stated as subshells, meaning you have the same access 

## Working with multiple terminals in a nongraphical environment 
- virtual terminals can be changed with **ALT-Functions** Key sequences  
  - F1 gnome display manager graphical login 
  - F2 aceess to graphical console 
  - F3 gives back access to grapical session?
  - F4-F6 access to graphical consoles 
- chvt is alernative 
- device files
  - /dev/tty  
  - virtual console uses directory
    - /dev/tty1
- 
 


## Understanding psuedo terminal devices 
- terminals started in graphical environments spawn pseudo terminals 
  - 1st one started is `/dev/pts/1 
  - subsequesnt terminals are identified as `/dev/pts/N`
- Exersize 5-2 has good way of showing graphical logins and `/dev/tty` device 
## Booting, rebooting, and shutting down systems 
- proper shutdown ensures that all processes have any data that is stored in memory buffers written to disk
- *Systemd* is the process that manages the reboot 
  - it is the first process that startrs and manaages all other process 
- commands 
  - reboot
  - halt
    - powers system down immediately  
  - poweroff
    - uses power management services to corrdinate shutdown  
- more details on halt vs poweroff

# Using SSH and related utilties 


## Accessing remote systems using SSH
 - default port is 22
  - use `-p` option to specify different port 
- `ssh user@server
  - use `-v` option for verbose mode 
- `~/.ssh/known_hosts` file is used to store public key fingerprints for host that have been accessed with ssh
  - ![1st-ssh-connect-fingerprint](https://www.simplified.guide/_media/ssh/fix-remote-host-identification-has-changed-error/confirm-ssh-key-fingerprint.png?w=700&tok=79cd77) 
  - this fingerprint is checked for future connections to the same server 
  - when the fingerprint matches no message will be displayed
  - if the fingerprint does not match a message will be displayed
    - ![ssh-mismatch](https://www.simplified.guide/_media/ssh/fix-remote-host-identification-has-changed-error/remote-host-identification-has-changed.png?w=700&tok=0ee1b3)
    - use `sed -i -e '25d' ~/.ssh/known_hosts
     - 25 repreents the line number to be deleted 

## Using graphical application in an SSH environment
- use `-Y` to allow graphical applictions on a per session basis
- use `ForwardX11 yes` on the server to allow graphical application by default 
  - see more on the video exersise ![exercise-notes](/Users/bbyers/Documents/local-filevideo-lab-module7-lesson24_managing-ssh.md)   

## Securly transferring files beween systems 
- scp used to copy files and folders 
- rsync used to sync files 
- sftp secure ftp

### scp to copy files 
- similar to `cp` command   
- local > remote(using current user) 
  - `scp /local/file remotehost:/remotefolder`
- remote (different user)  > local 
  - `scp user@remotehost:/remotefile /localhome/home
-use `-r` option to copy recursively 
-use `-P` option to specify different port   
### Using sftp to securely transfer files 
- uses FTP style interface 
- FTP server needs to be running sshd and then sftp can be used?
  - is this true would like to test 
- use command **get** to download and **put** to upload  

### Using rsync to sync files 
- use to sync local and remote dir
- there is no exerice on the command so we should definitly spend some time with this 

Option Use
-r    Synchronizes the entire directory tree
-l    Copies symbolic links as symbolic links
-p    Preserves permissions
-n    Performs only a dry run, not actually synchronizing anything
-a   Uses archive mode, thus ensuring that entire subdirectory trees and all
file properties will be synchronized
-A   Uses archive mode, and in addition synchronizes ACLs
-X   Synchronizes SELinux context as well

## configuring key based authentication for ssh  
- public/privte key authentication is enbaled by default 
  - more secure than passwords 
  - passwords may be used as fail-back
- use `ssh-keygen` to create key pair 
- ![pub/pri-auth-process](https://rayka-co.com/wp-content/uploads/2022/05/14.-Junos-SSH-Public-Key-Authentication-Process.png)  
- public keys are stored in *.ssh/authorized_keys*

## Using passphrases or not
- passphrases can be used for maximum security 
- do the exercise a few more times and set ip up of all users and all hosts in lab  

