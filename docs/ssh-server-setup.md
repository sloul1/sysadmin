> [!IMPORTANT]  
> WIP! Work in progress. This warning will be removed when guide is complete.
# Setting up openssh-server in Ubuntu

This is a brief guide for setting up openssh-server on Ubuntu Linux.

More information on subject.  
[Ubuntu OpenSSH server documentation](https://documentation.ubuntu.com/server/how-to/security/openssh-server/)  
[OpenSSH project](https://www.openssh.com/)

## Enabling openssh-service

1. Update system 
```bash
sudo apt update && sudo apt upgrade -y
```
2. Install openssh-server
```bash
sudo apt install openssh-server -y
```
3. Check ssh-service status
```bash
sudo systemctl status ssh.service
```
Service shows currently "inactive (dead)" 
```bash
○ ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; disabled; preset: enabled)
     Active: inactive (dead)
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
```
4. Start ssh.service and enable it to start when system boots up
```bash
sudo systemctl start ssh.service
```
```bash
sudo systemctl enable ssh.service 
```
5. Check ssh.service status again
```bash
sudo systemctl status ssh.service
```
```bash
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; enabled; preset: enabled)
     Active: active (running) since Fri 2025-01-03 13:21:27 EET; 2min 24s ago
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 52849 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
   Main PID: 52851 (sshd)
      Tasks: 1 (limit: 17662)
     Memory: 1.3M (peak: 1.6M)
        CPU: 21ms
     CGroup: /system.slice/ssh.service
             └─52851 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"

Jan 03 13:21:27 peppertp15ubu-ThinkPad-E15-Gen-3 systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
Jan 03 13:21:27 peppertp15ubu-ThinkPad-E15-Gen-3 sshd[52851]: Server listening on :: port 22.
Jan 03 13:21:27 peppertp15ubu-ThinkPad-E15-Gen-3 systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
```
> [!TIP]  
> Press 'q' or Ctrl + c to exit status window.
