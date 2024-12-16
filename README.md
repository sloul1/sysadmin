# sysadmin

## Swappiness

Swappiness is a Linux kernel parameter that controls how aggressively the system swaps pages between memory (RAM) and swap space (hard disk) when physical memory is low. It determines the balance between using RAM and swap space, aiming to optimize system performance and memory usage. Swappiness can be set between 0 and 100. The higher the number, the more aggressively the VM swaps data to disk. More in depth in Ubuntu's community help page. https://help.ubuntu.com/community/SwapFaq

Ubuntu Linux' default swappiness setting can be queried in terminal by using cat command (short for concatenate) for '/proc/sys/vm/swappiness' file:  
```bash
cat /proc/sys/vm/swappiness
```
result:
```bash
60
```
Swappiness can be changed in fly with:
```bash  
sudo sysctl vm.swappiness=10
```
resulting:
```bash
cat /proc/sys/vm/swappiness
```
```bash
10
```
Swap can be emptied with disabling swap:  
```bash
sudo swapoff -a
```
...and enabling it again:
```bash
sudo swapon -a
```
