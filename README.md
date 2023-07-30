# install-k8s
install-k8s


# 1) Set hostname on Each Node
    root@master:~/.aws# hostnamectl set-hostname "k8smaster.jy6.shop"
    root@master:~/.aws# hostnamectl
     Static hostname: k8smaster.jy6.shop
           Icon name: computer
          Machine ID: f13d61e1b9eb4977bb8fdadeacdd00a9
             Boot ID: cb109f273d7a461db8e10cad64eeb73c
    Operating System: Ubuntu 22.10
              Kernel: Linux 5.19.0-46-generic
        Architecture: x86-64
     Hardware Vendor: Hewlett-Packard
      Hardware Model: HP EliteBook 840 G2
    Firmware Version: M71 Ver. 01.31
    root@master:~/.aws# exec bash
    root@k8smaster:~/.aws# 
  
    
    
    
    root@worker2:~# sudo hostnamectl set-hostname "k8sworker1.example.net"
    root@worker2:~# hostnamectl
     Static hostname: k8sworker1.example.net
           Icon name: computer
          Machine ID: d58313246ca34fc6bdb115c74932ad50
             Boot ID: 792b794fe7a44d9ca203f2555384ea7c
    Operating System: Ubuntu 22.10
              Kernel: Linux 5.19.0-45-generic
        Architecture: x86-64
     Hardware Vendor: Hewlett-Packard
      Hardware Model: HP EliteBook 8470p
    Firmware Version: 68ICF Ver. F.74
    root@worker2:~# exec bash
    root@k8sworker1:~#
    
  
    
    sangbinlee9@worker4:~$ sudo hostnamectl set-hostname "k8sworker2.example.net"
    [sudo] password for sangbinlee9:
    sangbinlee9@worker4:~$ exec bash
    sangbinlee9@k8sworker2:~$
    root@k8sworker2:/home/sangbinlee9# hostnamectl
     Static hostname: k8sworker2.example.net
           Icon name: computer
          Machine ID: d4d1aba42a2c412292cf1eea1e10fdc4
             Boot ID: d2c72ad6d529455e9f5ab304de0d2463
    Operating System: Ubuntu 22.10
              Kernel: Linux 5.19.0-42-generic
        Architecture: x86-64
     Hardware Vendor: Dell Inc.
      Hardware Model: Inspiron N7010
    Firmware Version: A11
    root@k8sworker2:/home/sangbinlee9#
    
    
    
  
  




  
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
