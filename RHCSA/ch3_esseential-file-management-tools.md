## Ch 3 - Essential File Management Tools
### Question

how to correctly install man pages 
can I use links with git hub files/dir
 
### Quiz 
 - add FHS table from other doc
  - Mounts
    - A mount is a connection between a device and
a directory, the process of mount also gives acess to files.
    - `mount` shows all mounts from `/proc/mounts` and kernel interfaces 
    - `df -Th` shows all mounts in humand readable format with thier files system
    - `findmnt` does the same thing as `mount` but looks better
  - Files
    - Wildcards
      - |wildcard|use|
        |----|----|
        |\*|unlimited number of any character|
        |?|refer to one of any character|
        |\[auo \]|refers to one character in ramge ls c[auo]t would match *cat*, *cut*, and *cot*| 
    - directories
      - use `mkdir -p` to create directories further in the path 
        -        bash-4.2$ mkdir parent/child
                 mkdir: cannot create directory ‘parent/child’: No such file or directory
                 bash-4.2$ mkdir -p  parent/child   
    - absolute and relative file names
      - **absolute path** full path
        - `/home/user/Documents/file1`  
      - **relative path** to the path that you are working in
    - listing files and directories
      - |Command|Use|
        |---|---|
        |ls -l| Shows a long listing, which includes information about file properties, such as creation date and permissions.|
        |ls -a|Shows all files, including hidden files.|
        |ls -lrt | The -t option shows commands sorted based on modification date. You’ll see the most recently modified files last in the list because of the -r option. This is a very useful command. | 
        |ls -d  | Shows the names of directories, not the contents of all directories that match the wildcards that have been used with the ls command.<br>`bash-4.2$ ls -d maintenance\* <br> maintenance  maintenance-filters`<br>|
        |ls -R|Shows the contents of the current directory, in addition to all of its subdirectories; that is, it Recursively descends all subdirectories.|
    - copying files and directories 
      - |Command|Uses|
        |----|----|
        | `cp /<path to file> /<path todestination>`| basic  copy command useage|
        |`cp -R` | copy entire subdirectory|
        |`cp /somedir/.* /tmp`|
        |`cp -a`| keep current permissions \(archive mode\)|
        |cp -a /somedir/ . | copy the contents of the directory to itself|
        |cp -a /somedir/. . | |
    - moving files and directories 
      - |Command|Use|
        |------|------|
        |mv myfile| /tmp Moves the file myfile from the current directory to /tmp.
        |mkdir somefiles; mv somefiles /tmp| First creates a directory with the name somefiles and then moves this directory to /tmp. Notice that this also works if the directory contains files|
        |mv myfile mynewfile| Renames the file myfile to a new file with the name mynewfile.|
    - deleting files and directories  
      - RHEL 9, if you use the rm command as root, it prompts for confirmation. The reason is that through /root/.bashrc, rm is defined as an alias to rm -i. If you do not like that, you can use the -f option or remove the alias from /root/.bashrc
      _ `rm` command to remove files with `-r` for resurcive, to delete subfolders 
  - links
    - ![Hard Links and Soft Links](https://miro.medium.com/v2/resize:fit:1248/1*3qbmVwFQhnpbXPyXlUTqOQ.jpeg)
    - inodes 
      - name of the file is not stored in inode
      - stores how many names, **hard link**, associated with inodie 
      - Every file on Linux has an inode
        - The data block where the file contents are stored
        - The creation, access, and modification date
        - Permissions
        - File owners
    - Hard Links
      - one use case of hard links are to have the same file in multiple locations
      - Hard links must exist all on the same device (partition, logical volume, etc).	
      - You cannot create hard links to directories.
      - When the last name (hard link) to a file is removed, access to the file’s data is
also removed.
       if the first hard link
that ever existed for a file is removed, that does not impact the other hard links that
still exist.
    - Symbolic Link
       - A **symbolic link** links the name of the file not the inode 
      - The advantage of symbolic links is that they can link to files on other
devices, as well as on directories. 
      - The major disadvantage is that when the original file is
removed, the symbolic link becomes invalid and does not work any longer.
    - Creating Links 
      |Command|Explanation|
      |----|----|
      |`ln /etc/hosts .`| Create hard link in the current directoy |
      |`ln /etc/hosts /home/user1/host-list` | Create hard link in `/home/user1/host-list`|
      |`ln -s /etc/hosts .` | Create symbolic link in current directory|
      |`ln -s /home /tmp | Create a symbolic link in `/tmp`|       
    - Removing Links 
  - Working w/ Archives and Compressed Files 
    - Inital notes
      - Tape ARchiver (tar)
      - most important task for exam
        - Create archive
          - `tar -cf nameofarchive.tar filestoarchive` 
        - list contents of archive
          -  `tar -tf nameofarchive`
        - extract archive
          - `tar -xf nameofarchive`
        - compress and uncompress archive
    - Notes 
       - 
        ```
        office715 ~/tar-testing $ tar -cvfj  numbers1.tgz file{6..11} <-the position of the option matter ie the *f* is not preceedeing the filename
        tar: numbers1.tgz: Cannot stat: No such file or directory
        file6
        file7
        file8
        file9
        file10
        file11
        tar: Exiting with failure status due to previous errors
        [1366 03:17:33] bbyers  ---
        office715 ~/tar-testing $ tar -cvjf  numbers1.tgz file{6..11}
        file6
        file7
        file8
        file9
        file10
        file11
        ```
         - Only the last option in such a set is allowed to have an
argument(1). 

       - common options 
           |Option|Use|
           |---|---| 
           |-c |Create| 
           |-f | Filename|
           |-v |Verbose|
           |-u |Update|
           |-t |show conTents|
           |-x |Extract|
           |-C | Change DireCtory|
           |-z | compress using gzip|
           |-J | compress using xz|
           |-j | compress using j|
   
   
   
   
   
   
    
