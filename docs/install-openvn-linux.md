# Install OpenVPN in Linux

> [!NOTE]
> Created 2025/01   
Tested on native `Ubuntu desktop 24.04.1 LTS (Noble Numbat)`

## Table of Contents

1. [Check if openvpn is alredy installed](#Installed?)
2. [Check installation candidates](#Candidates?)
3. [Install openvpn](#Install)
4. [Created according to openvpn community documentation](#Documentation)


## Installed?

```bash
which openvpn
```
Output when openvpn is installed: 
```bash
/usr/sbin/openvpn
```
You can make further query with `whereis`command.
```bash
whereis openvpn
```
`whereis` locates the binary executable file for a given program name, as well as any associated source and manual page files.
```bash
openvpn: /usr/sbin/openvpn /usr/lib/x86_64-linux-gnu/openvpn /usr/lib/openvpn /etc/openvpn /usr/include/openvpn /usr/share/openvpn /usr/share/man/man8/openvpn.8.gz
```
Check openvpn version:
```bash
openvpn --version
```
> [!NOTE]  
> This output has been shortened:
```bash
OpenVPN 2.6.12 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] [DCO]
library versions: OpenSSL 3.0.13 30 Jan 2024, LZO 2.10
DCO version: N/A
Originally developed by James Yonan
Copyright (C) 2002-2024 OpenVPN Inc <sales@openvpn.net>
```
## Candidates?
```bash
sudo apt-cache policy openvpn
```
Output:
```bash
openvpn:
  Installed: (none)
  Candidate: 2.6.12-0ubuntu0.24.04.1
  Version table:
     2.6.12-0ubuntu0.24.04.1 500
        500 http://fi.archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.6.9-1ubuntu4.1 500
        500 http://security.ubuntu.com/ubuntu noble-security/main amd64 Packages
     2.6.9-1ubuntu4 500
        500 http://fi.archive.ubuntu.com/ubuntu noble/main amd64 Packages
```
## Install

```bash
sudo apt update && sudo apt install openvpn -y
```
Output:
```bash
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Suggested packages:
  openvpn-dco-dkms openvpn-systemd-resolved easy-rsa
The following NEW packages will be installed:
  openvpn
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 681 kB of archives.
After this operation, 1,798 kB of additional disk space will be used.
Get:1 http://fi.archive.ubuntu.com/ubuntu noble-updates/main amd64 openvpn amd64 2.6.12-0ubuntu0.24.04.1 [681 kB]
Fetched 681 kB in 0s (1,817 kB/s)
Preconfiguring packages ...
Selecting previously unselected package openvpn.
(Reading database ... 247497 files and directories currently installed.)
Preparing to unpack .../openvpn_2.6.12-0ubuntu0.24.04.1_amd64.deb ...
Unpacking openvpn (2.6.12-0ubuntu0.24.04.1) ...
Setting up openvpn (2.6.12-0ubuntu0.24.04.1) ...
Processing triggers for man-db (2.12.0-4build2) ...
```
## Documentation  
https://community.openvpn.net/openvpn/wiki/OpenVPN3Linux

https://community.openvpn.net/openvpn/wiki/OpenVPN3Linux#Stablerepository-DebianUbuntu

https://community.openvpn.net/openvpn/wiki/OpenVPN3Linux#Quickstart-howtouseOpenVPN3Linux