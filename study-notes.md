# 20250301
- man 7 file-hierarchy

|directory   |use                                |
|------------|-----------------------------------|
|/ 	     | stasrt of file system 	         |
|/boot       |files needed to boot kernel  	 |
|/dev        |                                   |  
|/etc        |                                   |
|/home       |                                   |
|/media,/mt  |                                   |
|/opt        |                                   |
|/proc       |                                   |
|/root       |                                   |
|/run        |                                   | 
|/src        |                                   |
|/sys        |                                   |
|/tmp        |                                   |
|/usr        |                                   | 
|/var        |                                   


#  20240118
dmesg --color=always | less -R
Error message on boot: "piix4_smbus 0000:00:01.3: SMBus base address uninitialized - upgrade BIOS or use force_addr=0xaddr"


# 20240107
wanted to write journal entries for the last session 
quick notes 
installing guest additions
kernel headers 
uname -r 
just update the the vm software
ipv6 continuing issues saw this log entry on /var/log/messages 
Jan  7 22:33:59 vm4 NetworkManager[918]: <warn>  [1704663239.1483] ipv6ll[4f3d5f689e0c6aa4,ifindex=2]: changed: no IPv6 link local address to retry after Duplicate Address Detection failures (back off)
dont forget mkdir -p

20231115
not 100% sure about how to configure the interface using the nmcli command. it seem that the network device is automatically added and also a connection is added 
20231109
objectives for tonight 
setup/confirm static ip config for all vms on ‘internet’ interface
setup local and automatic name resolution for all vms 
setup keyfile ssh  authentication for all vms 
setup ‘mgmt’ interface on all vms 
20231105
cant get dhcp working on rocky linux 9 used the following command to try and set interface manually, even     
# nmcli connection modify Example-Connection ipv4.addresses 192.0.2.1/24
20230814
there is an option in MobaXtertm to save the terminal output o a central location, this is hold be thought about and included in the overvall setp of the lab 
20230810
Instead of using terminal on the windows host machine mobaxterm will be used as the main terminal emulator 
First step is to setup ssh 
Second step is 
20230410
using UTM as a hypervisor seems to be a bit limiting in that we can on use 1 NIC 
20230407
its seems better to use nmcli to turn off ipv6
20230405
configuring network interfaces 
switched VM NIC from “shared network” to “bridged mode”. Using bridge mode uses DHCP which changes the IP address so we need to change the interface from DHCP to static. tried to use the network scripts method but the interfaces are not in this folder. 
need to set hostname for machine(s)
completed using nmcli 
20230401
input-output direction
> : this will overwrite information in a file 
>>: this will append information 


20230309
tar 
 Initially, 'tar' archives were used to store files conveniently on
magnetic tape.  The name 'tar' comes from this use; it stands for 't'ape
'ar'chiver.  

The 'tar' program is used to create and manipulate 'tar' archives.  An
"archive" is a single file which contains the contents of many files,
while still identifying the names of the files, their owner(s), and so
forth



20230307 session 2
dnf is the “new yum” and that is what is recommended from the redhat documentation  
install vbox guest additions 
$ dnf install gcc kernel-devel kernel-headers make bzip2 perl
change hostname
# hostnamectl set-hostname your-new-hostname
restart network service
sudo systemctl start NetworkManager.service
sudo systemctl stop NetworkManager.service
sudo systemctl restart NetworkManager.service

turn off IPV6   (source 1)(source 2 )
and the following line GRUB config
# cat /etc/default/grub
GRUB_TIMEOUT=5
GRUB_DEFAULT=saved
GRUB_DISABLE_SUBMENU=true
GRUB_TERMINAL_OUTPUT="console"
GRUB_CMDLINE_LINUX="ipv6.disable=1 crashkernel=auto rhgb quiet"
GRUB_DISABLE_RECOVERY="true"

20230307 session 1 
created a new VM(s)
redhat-1 
had kernel panic on boot initially 
can reuse this vm if if we add command from 
redhat-2
used the following command to bring VM up (source)
VBoxManage setextradata "RHEL9" "VBoxInternal/CPUM/IsaExts/POPCNT" "1"
REF
https://gist.github.com/tsangwpx/414eac56a0e14119bbfca5ef133d357
https://vaibhavsagar.com/blog/2019/09/08/popcount/
https://docs.oracle.com/en/virtualization/virtualbox/6.0/admin/sse412passthrough.html
https://www.virtualbox.org/manual/ch08.html#vboxmanage-setextradata
https://en.wikipedia.org/wiki/SSE4
https://forums.virtualbox.org/viewtopic.php?f=3&t=106666


VM was installed as workstation on many “packages” ie 
TODO (add all packages )
