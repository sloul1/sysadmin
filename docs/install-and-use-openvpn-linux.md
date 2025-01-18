# Install and use OpenVPN connection in Linux

> [!NOTE]
> Created 2025/01   
Tested on native `Ubuntu desktop 24.04.1 LTS (Noble Numbat)`

## Table of Contents

1. [Check if openvpn is alredy installed](#Installed)
2. [Check installation candidates](#Candidates)
3. [Install openvpn](#Install)
4. [Connecting to server with openvpn client using `.ovpn` file](#Connect)
5. [Testing connection](#Testing)
4. [Created according to openvpn community documentation](#Documentation)


## Installed
Check if openvpn is already installed.
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
## Candidates
Check installation candidates with `apt-cache` command:
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
Refresh local software package index and install openvpn. Option `-y` installs without user interaction.
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
## Connect
To connect with `.ovpn` file type:
```bash
sudo openvpn --config yourfile.ovpn
```
> [!NOTE]  
> This output has been redacted with `*` for security reasons:
```bash
2025-01-18 17:57:05 OpenVPN 2.6.12 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] [DCO]
2025-01-18 17:57:05 library versions: OpenSSL 3.0.13 30 Jan 2024, LZO 2.10
2025-01-18 17:57:05 DCO version: N/A
Enter Private Key Password: •••••••                 
2025-01-18 17:57:09 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
2025-01-18 17:57:09 TCP/UDP: Preserving recently used remote address: [AF_INET]***.***.***.**:****
2025-01-18 17:57:09 UDPv4 link local: (not bound)
2025-01-18 17:57:09 UDPv4 link remote: [AF_INET]***.***.***.**:****
2025-01-18 17:57:09 [url.for.your.connection] Peer Connection Initiated with [AF_INET]***.***.***.**:****
2025-01-18 17:57:09 TUN/TAP device tun0 opened
2025-01-18 17:57:09 net_iface_mtu_set: mtu 1500 for tun0
2025-01-18 17:57:09 net_iface_up: set tun0 up
2025-01-18 17:57:09 net_addr_ptp_v4_add: **.***.*.** peer **.***.*.** dev tun0
2025-01-18 17:57:09 Initialization Sequence Completed
```
## Testing
Open another terminal `ctrl + alt +t` for testing the connection with `ping` command.  

`$ ping ***.***.***.*`
> [!NOTE]  
> Note that pinged address in this example is private range in local area network. This is just for demonstration purposes.  

Issuing command `ping` with `-c` and integer `5` defines `count`of pings. 
```bash
ping -c 5 192.168.0.1
```
Reply:
```bash
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=5.37 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=2.81 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=1.40 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=2.71 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=2.54 ms

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4008ms
rtt min/avg/max/mdev = 1.403/2.965/5.371/1.303 ms

```
## Disconnect
To disconnect openvpn press `ctrl + c` in terminal you typed `sudo openvpn --config yourfile.ovpn` command.

## Documentation  
https://community.openvpn.net/openvpn/wiki/OpenVPN3Linux

https://community.openvpn.net/openvpn/wiki/OpenVPN3Linux#Stablerepository-DebianUbuntu

https://community.openvpn.net/openvpn/wiki/OpenVPN3Linux#Quickstart-howtouseOpenVPN3Linux