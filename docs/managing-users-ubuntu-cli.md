# Managing users in Ubuntu using terminal

Created in 2025/01 on Android 14 using Ubuntu 22.04 in Termux 

This is a brief guide for managing user accounts in Ubuntu terminal or cli (command line interface).  
Using system mentioned above user is logged in as root by default. This means user doesn't have to run commands as super user (sudo). 
`When using unprivileged user account one has to use sudo for making changes on root user level.`

## Adding new user

If user is desired to have home directory switch '-m' is to be used in command below. Otherwise it can left off.  
```bash
sudo useradd -m user-to-be-added-to-system
```

Generation of user can be checked :
```bash
cat /etc/passwd
```
...which lists all users in the system most recently added user on last line. 
```bash
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
_apt:x:100:65534::/nonexistent:/usr/sbin/nologin
systemd-network:x:101:102:systemd Network Management,,,:/run/systemd:/usr/sbin/nologin
systemd-resolve:x:102:103:systemd Resolver,,,:/run/systemd:/usr/sbin/nologin
messagebus:x:103:104::/nonexistent:/usr/sbin/nologin
systemd-timesync:x:104:105:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin
usbmux:x:105:46:usbmux daemon,,,:/var/lib/usbmux:/usr/sbin/nologin
pepper:x:1000:1000::/home/pepper:/bin/sh
```
Generation of home directory can be checked:
```bash
ls -l /home
```
Which prints:
```bash
total 4
drwxr-x---. 2 root root 3452 Jan 10 11:57 pepper
```
## Creating system user for running task automation

System user account is handy for example automating various tasks using cron job scheduler

```bash
sudo useradd -r usename-for-system-user
```
 
## Changing password for newly created (or any) user
```bash
sudo passwd user-which-password-is-to-be-created 
```
## Remove user with user's home directory

```bash
sudo userdel -r user-to-be-deleted
```
