# picoCTF-2018 Writeups

Here are the writeups for the challenges I have solved for PicoCTF 2018. The warmups are not included since they are easy enough to not need a writeup.

## Solved Challenges
Challenges | Category | Points
-----------|----------|--------
[grep 1](#grep-1) | General Skills | 75 
[net cat](#net-cat) | General Skills | 75 
[HEEEEEEERE'S Johnny\!]() | Cryptography | 100
[strings](#strings) | General Skills | 100
[pipe](#pipe) | General Skills | 110 
[Inspect Me](#inspect-me) | Web Exploitation | 125 
[grep 2](#grep-2) | General Skills | 125 
[Aca-Shell-A](#aca-shell-a) | General Skills | 150
[Client Side is Still Bad](#client-side-is-still-bad) | Web Exploitation | 150
[Desrouleaux](#desrouleaux) | Forensics | 150
[Logon](#logon) | Web Exploitation | 150
[Reading Between the Eyes](#reading-between-the-eyes) | Forensics | 150
[Recovering From the Snap](#recovering-from-the-snap) | Forensics | 150
[admin panel](#admin-panel) | Forensics | 150
[assembly-0](#assembly-0) | Reversing | 150
[buffer overflow 0](#buffer-overflow-0) | Binary Exploitation | 150
[caesar cipher 1](#caesar-cipher-1) | Cryptography | 150
[environ](#environ) | General Skills | 150
[hertz](#hertz) | Cryptography | 150
[hex editor](#hex-editor) | Forensics | 150
[ssh-keyz](#ssh-keyz) | General Skills | 150

---
### grep 1
##### Challenge
```
Can you find the flag in file? This would be really obnoxious to look through by hand, see if you can find a faster way. You can also find the file in /problems/grep-1_4_0431431e36a950543a85426d0299343e on the shell server.
```

##### Writeup
I just had to get to the given folder using the given CTF shell, then used “grep picoctf” to get the flag from the file.

---
### net cat
##### Challenge
```
Using netcat (nc) will be a necessity throughout your adventure. Can you connect to 2018shell.picoctf.com at port 36356 to get the flag?
```

##### Writeup
Using the command “nc 2018shell.picoctf.com 36356” gives the flag.

---
### HEEEEEEERE'S Johnny!
##### Challenge
```
Okay, so we found some important looking files on a linux computer. Maybe they can be used to get a password to the process. Connect with nc 2018shell.picoctf.com 40157. Files can be found here: passwd shadow.
```

##### Writeup
When I first saw this challenge, I honestly had no idea where to start, so I decided I'd come back to it later. After working on the pico2019 challenge related to using John the Ripper, I now understand why it’s got the name it chose, so I used the command unshadow passwd shadow > file. Then using the command john file, it shows the password for the user “root” being password1, so I was able to log in to where the challenge told us to, and I received the flag.

---
### strings
##### Challenge
```
Can you find the flag in this file without actually running it? You can also find the file in /problems/strings_0_bf57524acf558aca2081eb97ece8e2ee on the shell server.
```

##### Writeup

---
