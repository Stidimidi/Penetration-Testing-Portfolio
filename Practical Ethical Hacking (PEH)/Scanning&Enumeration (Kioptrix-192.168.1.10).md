## **Arp Scan to detect host and ip address in LAN Network**

- **Using Nmap (sudo nmap -sn -PR 192.168.1.0/24)** instead of using arp scan default package **(arp-scan -l)**

## Netdiscover to detect host ip address in LAN Network

- **sudo netdiscover -r 192.168.1.0/24**

## Nmap Full Port Scan Result

**Command Used**
```bash
- nmap -T4 -p- -A 192.168.1.10

Starting Nmap 7.95 ( [https://nmap.org](https://nmap.org/) ) at 2025-10-24 16:52 PDT
Nmap scan report for 192.168.1.10
Host is up (0.00044s latency).
Not shown: 65529 closed tcp ports (reset)
PORT      STATE SERVICE     VERSION
22/tcp    open  ssh         OpenSSH 2.9p2 (protocol 1.99)
|*sshv1: Server supports SSHv1
| ssh-hostkey:
|   1024 b8:74:6c:db:fd:8b:e6:66:e9:2a:2b:df:5e:6f:64:86 (RSA1)
|   1024 8f:8e:5b:81:ed:21:ab:c1:80:e1:57:a3:3c:85:c4:71 (DSA)
|*  1024 ed:4e:a9:4a:06:14:ff:15:14:ce:da:3a:80:db:e2:81 (RSA)
80/tcp    open  http        Apache httpd 1.3.20 ((Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b)
|*http-title: Test Page for the Apache Web Server on Red Hat Linux
| http-methods:
|*  Potentially risky methods: TRACE
|*http-server-header: Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
111/tcp   open  rpcbind     2 (RPC #100000)
| rpcinfo:
|   program version    port/proto  service
|   100000  2            111/tcp   rpcbind
|   100000  2            111/udp   rpcbind
|   100024  1          32768/tcp   status
|*  100024  1          32768/udp   status
139/tcp   open  netbios-ssn Samba smbd (workgroup: rMYGROUP)
443/tcp   open  ssl/https   Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
|_ssl-date: 2025-10-25T03:53:32+00:00; +4h00m00s from scanner time.
|_http-server-header: Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
|*http-title: 400 Bad Request
| sslv2:
|   SSLv2 supported
|   ciphers:
|     SSL2_RC2_128_CBC_WITH_MD5
|     SSL2_DES_192_EDE3_CBC_WITH_MD5
|     SSL2_DES_64_CBC_WITH_MD5
|     SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
|     SSL2_RC4_128_WITH_MD5
|     SSL2_RC4_64_WITH_MD5
|*    SSL2_RC4_128_EXPORT40_WITH_MD5
| ssl-cert: Subject: commonName=localhost.localdomain/organizationName=SomeOrganization/stateOrProvinceName=SomeState/countryName=--
| Not valid before: 2009-09-26T09:32:06
|_Not valid after:  2010-09-26T09:32:06
32768/tcp open  status      1 (RPC #100024)
MAC Address: 08:00:27:8B:01:52 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
Device type: general purpose
Running: Linux 2.4.X
OS CPE: cpe:/o:linux:linux_kernel:2.4
OS details: Linux 2.4.9 - 2.4.18 (likely embedded)
Network Distance: 1 hop

Host script results:
|_smb2-time: Protocol negotiation failed (SMB2)
|_nbstat: NetBIOS name: KIOPTRIX, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
|_clock-skew: 3h59m59s

TRACEROUTE
HOP RTT     ADDRESS
1   0.44 ms 192.168.1.10

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 42.20 seconds 
``` 

## HTTP (80) & HTTPS (443) Enumeration

- 80/443 192.168.1.10 11:03 pm
- 80/tcp    open  http        Apache httpd 1.3.20 ((Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b)
- Default webpage - Apache - PHP
- Information disclosure - 404 page
- Dirbuster, Dirb, Gobuster (Web Directory Busting)
    - dirbuster&
- **Webalizer Version 2.01 -** http://192.168.1.10/usage/usage_200909.html

 

## Nikto web vulnerability scanning

- nikto -h http://192.168.1.10
- mod_ssl/2.8.4 - mod_ssl 2.8.7 and lower are vulnerable to a remote buffer overflow which may allow a remote shell.
    - *By google search of mod_ssl 2.8.4 exploit*, (Port:80/443) - Potentially vulnerable to OpenLuck (https://www.exploit-db.com/exploits/47080, https://github.com/heltonWernik/OpenLuck)
        
        

### Burpsuite

- Information disclosure - Server headers disclose version information - Server: Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b

## SMB Enumeration

- Nmap scan result - 139/tcp   open  netbios-ssn Samba smbd (workgroup: rMYGROUP)
- Nmap scan result - _smb2-time: Protocol negotiation failed (SMB2)
- Use metasploit (msfconsole) - auxiliary(scanner/smb/smb_version) - Unix (Samba 2.2.1a)
    - *By google search of Samba 2.2.1a exploit*, (Port:139) - Potentially vulnerable to **Samba trans2open Overflow (Linux x86)** (https://www.rapid7.com/db/modules/exploit/linux/samba/trans2open/, https://www.exploit-db.com/exploits/7, https://www.exploit-db.com/exploits/10)
- smbclient -L \\\\192.168.1.10\\
    - Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       IPC Service (Samba Server)
    ADMIN$          IPC       IPC Service (Samba Server)
    - smbclient \\\\192.168.1.10\\ADMIN$ OR smbclient \\\\192.168.1.10\\IPC$
        - Could anonymously connect to IPC with smbclient, but not Admin

## SSH Enumeration

- Nmap scan result - 22/tcp    open  ssh         OpenSSH 2.9p2 (protocol 1.99)
- ssh 192.168.1.10 -oKexAlgorithms=+diffie-hellman-group1-sha1 -oHostKeyAlgorithms=+ssh-rsa -c aes128-cbc = for banner grabbing ssh
