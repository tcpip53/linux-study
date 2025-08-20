# Chapter 1: Installing RHEL

## Comparison of related distros

- Red Hat 
  - To use RHEL for free you can register for a free Red Hat developer subscription at https://
  developers.redhat.com. With this subscription, you can run up to 16 unsupported
  instances of RHEL in any environment you’d like.This is an example sentence
- Fedora 
  - Fedora as the development platform for RHEL
- centos7
  -  CentOS Stream is a Linux distribution where new features that will be released in the next version of RHEL are intro-
  duced. In the RHEL development cycle, new features are introduced in Fedora.
  After testing in Fedora, some features are introduced in CentOS Stream, which
  is used as the last testing platform before the features are included in RHEL.
- Rocky Linux
- Alma Linux
## System Requirements

- Min 
  - 1 GiB of RAM
  - A 10-GiB hard disk
  - A network card
- Recomemnded
  - 64-bit platform support, either Intel based or ARM
  - 2 GiB of RAM
  - A 20-GiB hard disk
  - A DVD drive, either virtual or physical
  - A network card  
## Basic Attended Installation

- Install/Test
- Keyboard Lanuage 
- Installation Summary 
- Time & Date
- Root Password 
- Create User
- Installation Source
- Sofware Selection
- Installation Destination 
- Network & Host Name 

## Questions

# Chapter 2: Using Essential Tools

- Quiz

## Commmands

  - Understanding Commands
    - ls^1^ -l^2^ etc^3^:  1 - command 2 - options 3 - arguements 
      - commands
        - program to be excuted 
      - options
        - how the commands behaves 
        - specific type of argument
        - Options are a part of the program code, and they modify what the command is doing.[^1] 
        [^1]: Red Hat RHCSA™ 9 Cert Guide EX200.
      - arguments
        - gernral term used to describe any after the command    
        - where/how the commmand is applied ie target

  ## Executing Commands 

   - shell  "The purpose of the Linux shell is to provide an environment in which commands can be executed. The shell takes care of interpreting the command that a user has entered correctly. To do this, the shell makes a distinction between three kinds of commands"[^2] 
    [^2]: Red Hat RHCSA™ 9 Cert Guide EX200.
      - Aliases
        - user defined command 
        - issue `alias` to get overview of all aliases currently defined 
        - `alias newcommand=‘oldcommand`
        - only set temporaily if not set in user
         - always executed first 
      - Internal commands
          -  is a command that is a part of the shell itself and, as such, doesn’t have to be loaded from disk separately [^3] 
             [^3]: Red Hat RHCSA™ 9 Cert Guide EX200.
      - External commands
        - use `type` to determine which type of command
        - `$PATH` variable defines a list of directories that is searched for a matching filename when a user enters a command.
        - example value `$PATH` varible  `/export/home/bbyers/.local/bin:/export/home/bbyers/bin:/opt/imc/oracle-jdk-1.7.0_u51/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/opt/puppetlabs/bin:/export/home/bbyers/.local/bin:/export/home/bbyers/bin`
        - `.`is not included in `$PATH` The current directory (.) is sometimes included by users as well, allowing programs residing in the current working directory to be executed directly. System administrators as a rule do not include it in $PATH in order to prevent the accidental execution of scripts residing in the current directory,[^4] 
        [^4]: https://en.wikipedia.org/wiki/PATH_(variable)

## I/0 Redirection (To Review)

  - overwrite
      `echo
  - STDOUT to file
      `ls -l 1> file` 
  - overview

| Name | Default_Destination | Redirection | File_Descrtion_Number |
|-------|---------------------|--------------|---------------------|
|STDIN|Keyboard|<|0|
|STDOUT|Monitor|>|1|
|STDERR|Monitor|2>|2|
  - redirectors

|redirector|Explenation|
|------------|----------|
|>,1>|STDOUT; overwrite,if file |
|>>,1>>|STDOUT; append,if file|
|2>|STDERR|
|2>&1|STDERR to STDOUT|

|command chain| explanation|
|-----|-----|
|`echo "some text" >file`| over/write|
|`echo "some file" >>file`|append quoted text to file |
|`ls -l 1> file` |redirect command output to file|
|`lt > file 2>&1` | redirect stderr to file [^5] [^6] [^7]

[^5]: must be used w/ redirect to file  if exit code is not error, output  will be printed to STDIN  
[^6]: if exit code is not error, output
[^7]: https://tldp.org/LDP/abs/html/exitcodes.html |

## Pipe

  - use pipe `|`command to send output from one commmand to another command 

## History

|command| explanation|
|----|-----|
|`history` | list all history commands |
|`!number `|run command from number in history|
|`history -d number`| delete command from history| 
|`!startofsomecomman`| immediatly run commmand that matches, can be start of command|
|`history -w`| write to history|
| `history -c` | clear current history|

## VIM 

|vim |Command Explanation |
|----|--------|
|`Esc`| Switches from input mode to command mode. Press this key before typing any command.|
|`i`| |Switches from command mode to input mode at (i) or after (a) the current cursor position.|
|`o`| Opens a new line below the current cursor position and goes to input mode.|
|`:wq`| Writes the current file and quits.|
|`:q!`| Quits the file without applying any changes. The ! forces the command to do its work. Add the ! only if you really know what you are doing.|
|`:w` |filename Writes the current file with a new filename.|
|`dd`| Deletes the current line and places the contents of the deleted line into memory|.
|`yy`| Copies the current line.|
|`p`| Pastes the contents that have been cut or copied into memory.|
|`v`| Enters visual mode, which allows you to select a block of text using the arrow keys. Use d to cut the selection or y to copy it.
|`u`| Undoes the last command. Repeat as often as necessary.
|`Ctrl-r`|  Redoes the last undo. (Cannot be repeated more than once.)|
|`gg` |Goes to the first line in the document.|
|`G`| Goes to the last line in the document.|
|`/`| text Searches for text from the current cursor position forward.|
|`?`| text Searches for text from the current cursor position backward.|
|`^`|  Goes to the first position in the current line.|
|`$`|  Goes to the last position in the current line.|
|`!`| ls Adds the output of ls (or any other command) in the current file.|
|`:`| %s/old/new/g Replaces all occurrences of old with new. [^9] 

[^9]: red-hat | 


## Shell Enviroments

  - Enviroments
    - A shell maintains an environment that includes a set of variables defined by the login program, the system initialization file, and the user initialization files. In addition, some variables are defined by default. [^8] 
    [^8]: https://docs.oracle.com/cd/E19120-01/open.solaris/819-2379/userconcept-26/index.html

  - Varibles
    - use `env` to see all varibles set in shell environment 

  - Environment Configuration Files 

      |config file | Explanation| 
      |------|----|
      | `/etc/profile`| This is the generic file that is processed by all users upon login.|
      | `/etc/bashrc`| This file is processed when subshells are started.|
      | `~/.bash_profile`| In this file, user-specific login shell variables can be defined.|
      | `~/.bashrc`| In this user-specific file, subshell variables can be defined.|
  
  - types of shells
    - different types of shells have different types of environments 
    - A **login shell** is the first shell that is opened for a user after the user has logged in. 
    - From the login shell, a user may run scripts, which will start a **subshell** of that login shell 
## /etc/motd /etc/issue

  -  `/etc/motd` contents displayed after user logs in 
  - `/etc/issue` contents displayed before user logs in 

## getting help

  - `apropos`, `man -k`search man pages
  -  `info`, `pinfo` some commands not in man pages might have entry in info pages, pinfo has cleaner look 
  - `/usr/share/doc` infomation about well know services 

-----------

Footnotes 
