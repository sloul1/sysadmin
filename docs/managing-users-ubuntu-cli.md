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
...which lists all users in the system.
```bash

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
