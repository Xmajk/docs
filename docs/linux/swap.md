In a nutshell swap is a piece of storage (used from your harddisk) which can be used as additional RAM. If you want to change the size of your swap file (which is 1GB by default on Ploi) just follow the following steps.

Turn off all running swap processes: swapoff -a

Resize swap: fallocate -l 1G /swapfile #(change 1G to the gigabyte size you want it to be)

CHMOD swap: chmod 600 /swapfile

Make file usable as swap: mkswap /swapfile

Active the swap file: swapon /swapfile

Thats it! Some commands may take some time to be executed, just wait patiently for the commands to finish.


To verify your swap size run the following command and you will see the swap size: free -m