Lab assignment 
  - setup ssh server with the following config options 
    - offers services on port 22
      - this is the default port for sshd
        ```
        [root@vm1 ~]# netstat -tulpn | grep ssh
        tcp        0      0 127.0.0.1:6010          0.0.0.0:*               LISTEN      40745/sshd: user1@n
        tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      39583/sshd: /usr/sb
        tcp6       0      0 ::1:6010                :::*                    LISTEN      40745/sshd: user1@n
        tcp6       0      0 :::22                   :::*                    LISTEN      39583/sshd: /usr/sb
        ``` 
      - not sure why this does not need to be uncommented  
    - allow root login 
      -  it the **Authenitcation** section add the line `PermitRootLogin yes` 
    - grphical sessions can be forwarded 
        
  - verify the X forwarding works from the SSH client
    - so after some testing and setting up a new vm i think i understand how this works
you have to kinda flip the client/server architecture around 

|\\\\\\\\\\\\\\\\\\\\\\\|                          |\\\\\\\\\\\\\\\\\\\\\\\|     
|    ssh client ---------------------------------------> ssh server        |
|_ _ _ _ _ _ _ _ _ _ _ _|                          |_ _ _ _ _ _ _ _ _ _ _ _|
|  |                  | |                          |  |                    |
|  | x-windows server | |                          |  |  x-windows client  |
|  |                  | |                          |  |                  | |
|  |  grapical        | |                          |  | graphical app    | |
|  | application <------------------------------------  application      | |
|  | displayed here   | |                          |     installed       | |
|  |                  | |                          |  |  and executed    | |
|  |                  | |                          |  |      here        | |
|  |                  | |                          |  |                  | |
|  |                  | |                          |  |                  | |
|  |                  | |                          |  |                  | |
|  |                  | |                          |  |                  | |
|  | _ _ _ _ _ _ _ _ _| |                          |  | _ _ _ _ _ _ _ _ _| |
|\\\\\\\\\\\\\\\\\\\\\\\|                          |\\\\\\\\\\\\\\\\\\\\\\\|


  - it is also very important to note on the x
