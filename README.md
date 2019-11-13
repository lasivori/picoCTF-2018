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
[Irish Name Repo](#irish-name-repo) | Web Exploitation | 200
[Mr Robots](#mr-robots) | Web Exploitation | 200
[No Login](#no-login) | Web Exploitation | 200
[Secret Agent](#secret-agent) | Web Exploitation | 200
[Truly an Artist](#truly-an-artist) | Forensics | 200
[assembly-1](#assembly-1) | Reversing | 200
[be-quick-or-be-dead-1](#be-quick-or-be-dead-1) | Reversing | 200
[blaise's cipher](#blaises-cipher) | Cryptography | 200


---
### grep 1
##### Challenge
```
Can you find the flag in file? This would be really obnoxious to look through by hand, see if you can find a faster way. You can also find the file in /problems/grep-1_4_0431431e36a950543a85426d0299343e on the shell server.
```

##### Writeup
I just had to get to the given folder using the given CTF shell, then used `grep picoctf` to get the flag from the file.

---
### net cat
##### Challenge
```
Using netcat (nc) will be a necessity throughout your adventure. Can you connect to 2018shell.picoctf.com at port 36356 to get the flag?
```

##### Writeup
Using the command `nc 2018shell.picoctf.com 36356` gives the flag.

---
### HEEEEEEERE'S Johnny!
##### Challenge
```
Okay, so we found some important looking files on a linux computer. Maybe they can be used to get a password to the process. Connect with nc 2018shell.picoctf.com 40157. Files can be found here: passwd shadow.
```

##### Writeup
When I first saw this challenge, I honestly had no idea where to start, so I decided I'd come back to it later. After working on the pico2019 challenge related to using John the Ripper, I now have an understanding of what to do, so I used the command `unshadow passwd shadow > file`. Then using the command john file, it shows the password for the user “root” being password1, so I was able to log in to where the challenge told us to, and I received the flag.

---
### strings
##### Challenge
```
Can you find the flag in this file without actually running it? You can also find the file in /problems/strings_0_bf57524acf558aca2081eb97ece8e2ee on the shell server.
```

##### Writeup
I used the command “strings strings” but a wall of text was thrown at me, so I decided to use this command: `strings strings | grep pico` which gives us the flag.

---
### pipe
##### Challenge
```
During your adventure, you will likely encounter a situation where you need to process data that you receive over the network rather than through a file. Can you find a way to save the output from this program and search for the flag? Connect with 2018shell.picoctf.com 2015.
```

##### Writeup
At first I just used the command `nc 2018shell.picoctf.com 2015`, but this just lead to text being thrown at me constantly. I then decided to put all the text to a file: `nc 2018shell.picoctf.com 2015 > file.txt`. I then used grep to find the flag: `strings file.txt | grep pico` which gives us the flag. 

---
### Inspect Me
##### Challenge
```
Inpect this code! http://2018shell.picoctf.com:28831 (link)
```

##### Writeup
I opened the link provided, and what was shown was a simple website titled “My First Website”. I looked into the page source to view the html, and noticed a comment at the bottom showing part ⅓ of the flag. Noticing that the CSS stylesheet and the Javascript were also the writer’s own, I clicked those links to see if the remaining flag parts were there. I found part ⅔ of the flag in the stylesheet. The Javascript had what it claimed to be part 3/3 of the flag, but there was nothing shown to add to the flag

---
### grep 2
##### Challenge
```
This one is a little bit harder. Can you find the flag in /problems/grep-2_4_06c2058761f24267033e7ca6ff9d9144/files on the shell server? Remember, grep is your friend.
```

##### Writeup
This one gave me difficulty at first. Of course, I could go through each directory and use the grep command to search through all files, but that would take too long. I did not know how to search through multiple directories, though, so I went to google and found that it was simpler than I thought. I just had to put the path down, so I used the c`ommand grep ‘pico’ ./*/*` and got the flag.

---
### Aca-Shell-A
##### Challenge
```
It's never a bad idea to brush up on those linux skills or even learn some new ones before you set off on this adventure! Connect with nc 2018shell.picoctf.com 58422.
```

##### Writeup
This challenge took me longer than I expected. It took me many attempts to get the flag. The first couple of parts were easy: all I had to do was get into the ‘secret’ folder, and do as the helper said. I already knew how to use the ‘rm’ command, and echo as well, but when I had to print the username without echo, I was stuck at first. It took me a while to actually get the hint (“Who are you?”), and after probably 15 minutes of retrying different things, I typed `whoami`, giving the username. After that, I just had to copy a file to another location, then print what that file contains.

---
### Client Side is Still Bad
##### Challenge
```
I forgot my password again, but this time there doesn't seem to be a reset, can you help me? http://2018shell.picoctf.com:55790 (link)
```

##### Writeup
This one was almost simpler than ‘Inspect Me’ challenge. All I did was to view the page source, and within all of the if statements.

---
### Desrouleaux
##### Challenge
```
Our network administrator is having some trouble handling the tickets for all of of our incidents. Can you help him out by answering all the questions? Connect with nc 2018shell.picoctf.com 10493. incidents.json
```

##### Writeup
For this challenge, I just followed the instructions on the screen. It would ask me questions about the .json file that was sent, such as what was the most common source IP, for which i would just check the file manually (there are only 10 entries, so it was a quick look over). Then, I it would give a source IP and ask how many unique destination IPs were targeted by it. The final question it what took me the longest. I had to find out the average amount of unique destinations for each file hash. The ‘3eeaf’ file had 2 destinations, but not unique, so I only counted one. ‘9387’ file had 2 unique destinations, and the rest of the files all had only 1 destination. There were a total of 8 files, so the average was 9/8 = 1.125, but they wanted it to 2 decimal places so the answer was 1.23.

---
### Logon 
##### Challenge
```
I made a website so now you can log on to! I don't seem to have the admin password. See if you can't get to the flag. http://2018shell.picoctf.com:37861 (link)
```

##### Writeup
For this one, I understood that I couldn’t just log in as admin, and that putting any other strings into username and password would log me in, but I would be told that I get no flag. After an hour of looking at the page source, and trying random passwords with the admin username, I gave up and decided to look up the challenge. After figuring out that it had something to do with editing cookies, I downloaded a cookie editor. Going back to the page and trying to log in, I noticed that one of the cookies is labelled ‘admin’, and it is set to ‘False’, so it would make sense to just change it to being ‘True’. After doing that and refreshing the page, I got the flag.

---
### Reading Between the Eyes
##### Challenge
```
Stego-Saurus hid a message for you in this image, can you retreive it?
```

##### Writeup
This is the given image:
![husky](/images/husky.png)
I’m not too familiar with forensics problems, but this one was a simple one to solve. There is a hidden message inside of an image, and the hint says that we can find a decoder online. I was at first confused by the “stego-saurus” part, but after looking for image decoders, I quickly found out that this was referencing steganography. Finding an online decoder was easy (I used https://stylesuxx.github.io/steganography/), and so all I had to do was put the image in, and I got the flag.

---
### Recovering From the Snap
##### Challenge
```
There used to be a bunch of animals here, what did Dr. Xernon do to them?
```

##### Writeup
I honestly had no idea what to do here. I decided to look up the problem, and the [first writeup](https://github.com/mzfr/ctf-writeups/tree/master/picoCTF-2018/Forensics/Recovering%20From%20the%20Snap) I found let me know that it was really easy, and all I had to do was use tools for it, such as Photorec. Using this program on the file provided, you will get 4 recovered images, one of which is the flag picoCTF{th3_5n4p_happ3n3d}.

---
### admin panel
##### Challenge
```
We captured some traffic logging into the admin panel, can you find the password?
```

##### Writeup
Using WireShark, I went through the packets of the .pcap file. Where there was communication with a website, I would see some readable text, so I just kept going through all of them until I found the flag. 

---
### assembly-0
##### Challenge
```
What does asm0(0x2a,0x4f) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. Source located in the directory at /problems/assembly-0_3_b7d6c21be1cefd3e53335a66e7815307.
```

##### Writeup
I downloaded the source code, then opened it in Atom. The challenge shows us that we are putting in two arguments, and asks what the assembly will return (the flag is not normal format). So I just followed the code: the first two lines are setting up stack space for the function, and saving the return address; next, eax gets the first argument, and ebx gets the second; right after that, we put ebx in eax, so now eax = ebx. The second argument (0x4f) is what is returned.

---
### buffer overflow 0
##### Challenge
```
Let's start off simple, can you overflow the right buffer in this program to get the flag? You can also find it in /problems/buffer-overflow-0_0_6461b382721ccca2318b1d981d363924 on the shell server. Source.
```

##### Writeup
The source code shows that the flag’s max size is 64, so I ran the vuln program with 65 letters as the argument to get the flag.

---
### caesar cipher 1
##### Challenge
```
This is one of the older ciphers in the books, can you decrypt the message? You can find the ciphertext in /problems/caesar-cipher-1_4_e4dc6dcfb004bdade0b9ce8e44f1bac4 on the shell server.
```

##### Writeup
It was quite simple to find a caesar cipher decoder, give it the flag, then check for each shift until the flag had recognizable words. 

---
### environ
##### Challenge
```
Sometimes you have to configure environment variables before executing a program. Can you find the flag we've hidden in an environment variable on the shell server?
```

##### Writeup
All that needed to be done was going into the picoCTF shell and using the command `printenv | grep picoCTF` to get the flag.

---
### hertz
##### Challenge
```
Here's another simple cipher for you where we made a bunch of substitutions. Can you decrypt it? Connect with nc 2018shell.picoctf.com 48487.
```

##### Writeup
This challenge was a substitution cipher. At first, I was just going to manually do it by going with some simple crypto analysis, and after finding that q = e, I realized it would take a while. I went online to see if there was an online brute force decoder for it, I quickly found guballa.de, which solved the problem almost immediately, giving us the flag (which was not in normal format): substitution_ciphers_are_solvable_cdilgndlnp.

---
### hex editor
##### Challenge
```
This cat has a secret to teach you. You can also find the file in /problems/hex-editor_1_10cafee5618ce2cfe32f2188ca1f472e on the shell server.
```

##### Writeup
This challenge tells us to use hex editors, such as the xxd command. The image being used seems like it would be too large to read through all of the hex, so I piped the output to grep to find the flag: xxd hex_editor.jpg | grep pico. But this only gave me the first piece of the flag. At the beginning of each line, though, is a relative address. The one I was first given was 00012940. I assumed this was hex, and added 8 to it. This gave me no result, probably because each line is a jump of 16, not 8. So afterwards, I just jumped the address up by 0x10 until I got the full flag: xxd hex_editor.jpg | grep 00012950, etc.

---
### ssh-keyz
##### Challenge
```
As nice as it is to use our webshell, sometimes its helpful to connect directly to our machine. To do so, please add your own public key to ~/.ssh/authorized_keys, using the webshell. The flag is in the ssh banner which will be displayed when you login remotely with ssh to with your username
```

##### Writeup
Following the tutorial in the hints section, I made my own key and had to make a directory and file in the ctf shell to have my key authorized. After that, it was as simple as logging into the shell through ssh: `ssh lasivori@2018shell4.picoctf.com`

---
### Irish Name Repo
##### Challenge

##### Writeup

---
### title
##### Challenge

##### Writeup

---
### title
##### Challenge

##### Writeup

---
