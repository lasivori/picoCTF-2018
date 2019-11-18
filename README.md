# picoCTF-2018 Writeups

Here are the writeups for the challenges I have solved for PicoCTF 2018. The warmups are not included since they are easy enough to not need a writeup.

## Solved Challenges
Challenges | Category | Points
-----------|----------|--------
[grep 1](#grep-1) | General Skills | 75 
[net cat](#net-cat) | General Skills | 75 
[HEEEEEEERE'S Johnny\!](#heeeeeeeres-johnny) | Cryptography | 100
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
[buffer overflow 1](#buffer-overflow-1) | Binary Exploitation | 200
[hertz 2](#hertz-2) | Cryptography | 200
[leak-me](#leak-me) | Binary Exploitation | 200
[now you don't](#now-you-dont) | Forensics | 200
[quackme](#quackme) | Reversing | 200
[shellcode](#shellcode) | Binary Exploitation | 200
[what base is this?](#what-base-is-this) | General Skills | 200
[you can't see me](#you-cant-see-me) | General Skills | 200
[Buttons](#buttons) | Web Exploitation | 250
[Ext Super Magic](#ext-super-magic) | Forensics | 250
[Lying Out](#lying-out) | Forensics | 250
[The Vault](#the-vault) | Web Exploitation | 250
[What's My Name?](#whats-my-name) | Forensics | 250
[absolutely relative](#absolutely-relative) | General Skills | 250
[assembly-2](#assembly-2) | Reversing | 250
[buffer overflow 2](#buffer-overflow-2) | Binary Exploitation | 250
[caesar cipher 2](#caesar-cipher-2) | Cryptography | 250
[rsa-madlibs](#rsa-madlibs) | Cryptography | 250
[echooo](#echooo) | Binary Exploitation | 300
[learn gdb](#learn-gdb) | General Skills | 300
[Flaskcards](#flaskcards) | Web Exploitation | 350
[assembly-3](#assembly-3) | Reversing | 400
[Secure Logon](#secure-logon) | Web Exploitation | 500


---
### grep 1
##### Challenge
>Can you find the flag in [file](https://2018shell.picoctf.com/static/f2e1fdcd5c405ca4170af1a8973b365b/file)? This would be really obnoxious to look through by hand, see if you can find a faster way. You can also find the file in /problems/grep-1_4_0431431e36a950543a85426d0299343e on the shell server.

##### Writeup
I just had to get to the given folder using the given CTF shell, then used `cat file | grep pico` to get the flag from the file: `picoCTF{grep_and_you_will_find_d66382d8}`

---
### net cat
##### Challenge
>Using netcat (nc) will be a necessity throughout your adventure. Can you connect to 2018shell.picoctf.com at port 36356 to get the flag?

##### Writeup
Using the command `nc 2018shell.picoctf.com 36356` gives the flag: `picoCTF{NEtcat_iS_a_NEcESSiTy_9454f3e0}`  

---
### HEEEEEEERE'S Johnny!
##### Challenge
>Okay, so we found some important looking files on a linux computer. Maybe they can be used to get a password to the process. Connect with nc 2018shell.picoctf.com 40157. Files can be found here: [passwd](https://2018shell.picoctf.com/static/7a017af70c0b86ab002896616376499e/passwd) [shadow](https://2018shell.picoctf.com/static/7a017af70c0b86ab002896616376499e/shadow).


##### Writeup
When I first saw this challenge, I honestly had no idea where to start, so I decided I'd come back to it later. After working on the pico2019 challenge related to using John the Ripper, I now have an understanding of what to do, so I used the command `unshadow passwd shadow > file`. Then using the command john file, it shows the password for the user “root” being password1, so I was able to log in to where the challenge told us to, and I received the flag: `picoCTF{J0hn_1$_R1pp3d_1b25af80}`

---
### strings
##### Challenge
>Can you find the flag in this [file](https://2018shell.picoctf.com/static/e78981e684a62559baaef12a27f0e918/strings) without actually running it? You can also find the file in /problems/strings_0_bf57524acf558aca2081eb97ece8e2ee on the shell server.


##### Writeup
I used the command “strings strings” but a wall of text was thrown at me, so I decided to use this command: `strings strings | grep pico` which gives us the flag: `picoCTF{sTrIngS_sAVeS_Time_c09b1444}`

---
### pipe
##### Challenge
>During your adventure, you will likely encounter a situation where you need to process data that you receive over the network rather than through a file. Can you find a way to save the output from this program and search for the flag? Connect with 2018shell.picoctf.com 2015.


##### Writeup
At first I just used the command `nc 2018shell.picoctf.com 2015`, but this just lead to text being thrown at me constantly. I then decided to put all the text to a file: `nc 2018shell.picoctf.com 2015 > file.txt`. I then used grep to find the flag: `strings file.txt | grep pico` which gives us the flag: `picoCTF{almost_like_mario_8861411c}`

---
### Inspect Me
##### Challenge
>Inpect this code! http://2018shell.picoctf.com:28831 ([link](http://2018shell.picoctf.com:28831/))

##### Writeup
I opened the link provided, and what was shown was a simple website titled “My First Website”. I looked into the page source to view the html, and noticed a comment at the bottom showing part ⅓ of the flag. Noticing that the CSS stylesheet and the Javascript were also the writer’s own, I clicked those links to see if the remaining flag parts were there. I found part ⅔ of the flag in the stylesheet. The Javascript had what it claimed to be part 3/3 of the flag, but there was nothing shown to add to the flag. The flag is: `picoCTF{ur_4_real_1nspect0r_g4dget_b4887011}`

---
### grep 2
##### Challenge
>This one is a little bit harder. Can you find the flag in /problems/grep-2_4_06c2058761f24267033e7ca6ff9d9144/files on the shell server? Remember, grep is your friend.

##### Writeup
This one gave me difficulty at first. Of course, I could go through each directory and use the grep command to search through all files, but that would take too long. I did not know how to search through multiple directories, though, so I went to google and found that it was simpler than I thought. I just had to put the path down, so I used the command `grep pico ./*/*` and got the flag: `picoCTF{grep_r_and_you_will_find_036bbb25}`

---
### Aca-Shell-A
##### Challenge
>It's never a bad idea to brush up on those linux skills or even learn some new ones before you set off on this adventure! Connect with nc 2018shell.picoctf.com 58422.

##### Writeup
This challenge took me longer than I expected. It took me many attempts to get the flag. The first couple of parts were easy: all I had to do was get into the ‘secret’ folder, and do as the helper said. I already knew how to use the ‘rm’ command, and echo as well, but when I had to print the username without echo, I was stuck at first. It took me a while to actually get the hint (“Who are you?”), and after probably 15 minutes of retrying different things, I typed `whoami`, giving the username. After that, I just had to copy a file to another location, then print what that file contains. We get the flag: `picoCTF{CrUsHeD_It_4e355279}`

---
### Client Side is Still Bad
##### Challenge
>I forgot my password again, but this time there doesn't seem to be a reset, can you help me? http://2018shell.picoctf.com:55790 ([link](http://2018shell.picoctf.com:55790/))

##### Writeup
This one was almost simpler than ‘Inspect Me’ challenge. All I did was to view the page source, and within all of the if statements: `picoCTF{client_is_bad_3bd366}`

---
### Desrouleaux
##### Challenge
>Our network administrator is having some trouble handling the tickets for all of of our incidents. Can you help him out by answering all the questions? Connect with nc 2018shell.picoctf.com 10493. [incidents.json](https://2018shell.picoctf.com/static/8eed8b873d59e897ae9dea0af40491f3/incidents.json)

##### Writeup
For this challenge, I just followed the instructions on the screen. It would ask me questions about the .json file that was sent, such as what was the most common source IP, for which i would just check the file manually (there are only 10 entries, so it was a quick look over). Then, I it would give a source IP and ask how many unique destination IPs were targeted by it. The final question it what took me the longest. I had to find out the average amount of unique destinations for each file hash. The ‘3eeaf’ file had 2 destinations, but not unique, so I only counted one. ‘9387’ file had 2 unique destinations, and the rest of the files all had only 1 destination. There were a total of 8 files, so the average was 9/8 = 1.125, but they wanted it to 2 decimal places so the answer was 1.13. The flag given at the end was this: `picoCTF{J4y_s0n_d3rUUUULo_a062e5f8}`

---
### Logon 
##### Challenge
>I made a website so now you can log on to! I don't seem to have the admin password. See if you can't get to the flag. http://2018shell.picoctf.com:37861 ([link](http://2018shell.picoctf.com:37861))

##### Writeup
For this one, I understood that I couldn’t just log in as admin, and that putting any other strings into username and password would log me in, but I would be told that I get no flag. After an hour of looking at the page source, and trying random passwords with the admin username, I gave up and decided to look up the challenge. After figuring out that it had something to do with editing cookies, I downloaded a cookie editor. Going back to the page and trying to log in, I noticed that one of the cookies is labelled ‘admin’, and it is set to ‘False’, so it would make sense to just change it to being ‘True’. After doing that and refreshing the page, I got the flag: `picoCTF{l0g1ns_ar3nt_r34l_a280e12c}`

---
### Reading Between the Eyes
##### Challenge
>Stego-Saurus hid a message for you in this [image](https://2018shell.picoctf.com/static/c23d909b52b9a7d96b15f024525d6795/husky.png), can you retreive it?

##### Writeup
This is the given image:
![husky](/images/husky.png)
I’m not too familiar with forensics problems, but this one was a simple one to solve. There is a hidden message inside of an image, and the hint says that we can find a decoder online. I was at first confused by the “stego-saurus” part, but after looking for image decoders, I quickly found out that this was referencing steganography. Finding an online decoder was easy (I used https://stylesuxx.github.io/steganography/), and so all I had to do was put the image in, and I got the flag: `picoCTF{r34d1ng_b37w33n_7h3_by73s}`

---
### Recovering From the Snap
##### Challenge
>There used to be a bunch of [animals](https://2018shell.picoctf.com/static/5d982298cdb725f9e23c6f25c8a37411/animals.dd) here, what did Dr. Xernon do to them?

##### Writeup
I honestly had no idea what to do here. I decided to look up the problem, and the [first writeup](https://github.com/mzfr/ctf-writeups/tree/master/picoCTF-2018/Forensics/Recovering%20From%20the%20Snap) I found let me know that it was really easy, and all I had to do was use tools for it, such as Photorec. Using this program on the file provided, you will get 4 recovered images, one of which is the flag `picoCTF{th3_5n4p_happ3n3d}`.

---
### admin panel
##### Challenge
>We captured some [traffic](https://2018shell.picoctf.com/static/19129d64f5676ff5661da65b9772aff5/data.pcap) logging into the admin panel, can you find the password?

##### Writeup
Using WireShark, I went through the packets of the .pcap file. There is communication with a website, and we are wanting the password for the admin, so we need to look for where ever users log in, which is shown in this pcap with `POST /login`. It doesn't take too long to find the one that the admin is specifically logging in, and we get the password, which is the flag: `picoCTF{n0ts3cur3_894a6546}`

---
### assembly-0
##### Challenge
>What does asm0(0x2a,0x4f) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://2018shell.picoctf.com/static/9dd737e97ccbb554569020e205ffa5c8/intro_asm_rev.S) located in the directory at /problems/assembly-0_3_b7d6c21be1cefd3e53335a66e7815307.

##### Writeup
I downloaded the source code, then opened it in Atom. The challenge shows us that we are putting in two arguments, and asks what the assembly will return (the flag is not normal format). So I just followed the code: the first two lines are setting up stack space for the function, and saving the return address; next, eax gets the first argument, and ebx gets the second; right after that, we put ebx in eax, so now eax = ebx. The second argument (0x4f) is what is returned.

---
### buffer overflow 0
##### Challenge
>Let's start off simple, can you overflow the right buffer in this [program](https://2018shell.picoctf.com/static/8ea6ca6c7edf2c50065e540c90207284/vuln) to get the flag? You can also find it in /problems/buffer-overflow-0_0_6461b382721ccca2318b1d981d363924 on the shell server. [Source](https://2018shell.picoctf.com/static/8ea6ca6c7edf2c50065e540c90207284/vuln.c).

##### Writeup
The source code shows that the flag’s max size is 64, so I ran the vuln program with 65 letters as the argument to get the flag.

---
### caesar cipher 1
##### Challenge
>This is one of the older ciphers in the books, can you decrypt the [message](https://2018shell.picoctf.com/static/2b49cc4b04ae2bc8ea4dcdf8016b10d6/ciphertext)? You can find the ciphertext in /problems/caesar-cipher-1_4_e4dc6dcfb004bdade0b9ce8e44f1bac4 on the shell server.

##### Writeup
It was quite simple to find a caesar cipher decoder, give it the flag, then check for each shift until the flag had recognizable words. The flag is `picoCTF{justagoodoldcaesarciphertobrvmri}` 

---
### environ
##### Challenge
>Sometimes you have to configure environment variables before executing a program. Can you find the flag we've hidden in an environment variable on the shell server?

##### Writeup
All that needed to be done was going into the picoCTF shell and using the command `printenv | grep picoCTF` to get the flag: `picoCTF{eNv1r0nM3nT_v4r14Bl3_fL4g_3758492}`

---
### hertz
##### Challenge
>Here's another simple cipher for you where we made a bunch of substitutions. Can you decrypt it? Connect with nc 2018shell.picoctf.com 48487.

##### Writeup
This challenge was a substitution cipher. At first, I was just going to manually do it by going with some simple crypto analysis, and after finding that q = e, I realized it would take a while. I went online to see if there was an online brute force decoder for it, I quickly found guballa.de, which solved the problem almost immediately, giving us the flag (which was not in normal format): `substitution_ciphers_are_solvable_cdilgndlnp`.

---
### hex editor
##### Challenge
>This [cat](https://2018shell.picoctf.com/static/29531f8d0c0270a32bd186ffcb9271b8/hex_editor.jpg) has a secret to teach you. You can also find the file in /problems/hex-editor_1_10cafee5618ce2cfe32f2188ca1f472e on the shell server.

##### Writeup
This challenge tells us to use hex editors, such as the xxd command. The image being used seems like it would be too large to read through all of the hex, so I piped the output to grep to find the flag: xxd hex_editor.jpg | grep pico. But this only gave me the first piece of the flag. At the beginning of each line, though, is a relative address. The one I was first given was 00012940. I assumed this was hex, and added 8 to it. This gave me no result, probably because each line is a jump of 16, not 8. So afterwards, I just jumped the address up by 0x10 until I got the full flag: xxd hex_editor.jpg | grep 00012950, etc. The flag is `picoCTF{and_thats_how_u_edit_hex_kittos_4bE5aCb8}`

---
### ssh-keyz
##### Challenge
>As nice as it is to use our webshell, sometimes its helpful to connect directly to our machine. To do so, please add your own public key to ~/.ssh/authorized_keys, using the webshell. The flag is in the ssh banner which will be displayed when you login remotely with ssh to with your username

##### Writeup
Following the tutorial in the hints section, I made my own key and had to make a directory and file in the ctf shell to have my key authorized. After that, it was as simple as logging into the shell through ssh: `ssh lasivori@2018shell4.picoctf.com`. The flag is `picoCTF{who_n33ds_p4ssw0rds_38dj21}`

---
### Irish Name Repo
##### Challenge
>There is a website running at http://2018shell.picoctf.com:52012 ([link](http://2018shell.picoctf.com:52012/)). Do you think you can log us in? Try to see if you can login!

##### Writeup
I honestly had no idea what to do with this one. I had looked through all the html, looked through cookies, everything I could think of. I decided to look up this one, and apparently it is week to SQL attacks, so for the password we had to enter  `‘ or ‘x’=’x` which gives us the flag: `picoCTF{con4n_r3411y_1snt_1r1sh_c0d93e2f}`

---
### Mr Robots
##### Challenge
>Do you see the same things I see? The glimpses of the flag hidden away? http://2018shell.picoctf.com:29568 ([link](http://2018shell.picoctf.com:29568))

##### Writeup
The hint tells us we need to search where the creator doesn’t want us to, so we’ll have to enter pages of the website directly. Given the creator’s name is Robots, I start by adding /robots.html to the url, but that didn’t give anything, so next I tried /robots.txt which gave us the next url to go to, which was /74efc.html. Going through here gives us the flag:  `picoCTF{th3_w0rld_1s_4_danger0us_pl4c3_3lli0t_74efc}`

---
### No Login
##### Challenge
>Looks like someone started making a website but never got around to making a login, but I heard there was a flag if you were the admin. http://2018shell.picoctf.com:10573 ([link](http://2018shell.picoctf.com:10573))

##### Writeup
First, I click everything I see on the website to see what does what. Login and Sign out don’t work, since they haven’t been implemented yet. The flag still requires that you are admin. For a while, I was trying to see if I could force a login somehow, but then I remembered the “Logon” challenge, in which I had to change a cookie to log in. This time, I had to make the cookie, called admin, and set it to True. Then clicking the flag button gave me the flag: `picoCTF{n0l0g0n_n0_pr0bl3m_ed714e0e}`

---
### Secret Agent
##### Challenge
>Here's a little website that hasn't fully been finished. But I heard google gets all your info anyway. http://2018shell.picoctf.com:46162 ([link](http://2018shell.picoctf.com:46162))

##### Writeup
For this one, the hint asked how your browser can pretend to be something else, and the initial challenge mentioned google having all the information, so I googled the hint. It led me to downloading a Google Chrome extension called user-agent switcher, which tricks websites into thinking you are using whatever service you select from the extension. Using the “Googlebot” selection, since the challenge mentioned google once already, I clicked on the flag button and got the flag: `picoCTF{s3cr3t_ag3nt_m4n_ac87e6a7}`

---
### Truly an Artist
##### Challenge
>Can you help us find the flag in this [Meta-Material](https://2018shell.picoctf.com/static/69b2020b48082fb24714bf93707183e8/2018.png)? You can also find the file in /problems/truly-an-artist_3_066d6319e350c1d579e5cf32e326ba02.

##### Writeup
For this one, I looked up how to find the metadata of an image, and it led me to this website called [get-metadata](https://www.get-metadata.com/), from which you could upload a file to get it’s metadata. If you look at the artist of the image, you get the flag: `picoCTF{look_in_image_eeea129e}`

---
### assembly-1
##### Challenge
>What does asm1(0x255) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://2018shell.picoctf.com/static/cfdecf913aa65754d8552cbbdad878ec/eq_asm_rev.S) located in the directory at /problems/assembly-1_1_3d18f926da00c5acd1dbe672938d342d.

##### Writeup
Given the .S file, and the input as 0x255, I just followed the code. This one was a bunch of conditional jumps, but it was simple to follow: jump to part_a, since 0x255 > 0xEA; then jump to part_c since 0x255 != 0x6; in part_c, we set eax = 0x255, then add 3. Then we follow to part_d, and return. The value that would be returned is 0x258.

---
### be-quick-or-be-dead-1
##### Challenge
>You find [this](https://www.youtube.com/watch?v=CTt1vk9nM9c) when searching for some music, which leads you to [be-quick-or-be-dead-1](https://2018shell.picoctf.com/static/353d7b6da455d29f7e8701952db901cb/be-quick-or-be-dead-1). Can you run it fast enough? You can also find the executable in /problems/be-quick-or-be-dead-1_4_98374389c5652d0b16055427532f098f.

##### Writeup
First thing I do is download the program and use `objdump -d` to look through it. After a little looking, we see that we want to avoid the timer, overall.

![bequick1](/images/bequick1.png)

So what I’ll do is use a hex editor to ignore these lines so that we can move on to printing the flag, and hopefully that’ll work. Using the online hex editor [“hexed.it”](https://hexed.it/), I open the file and look for the 800 addresses, and after finding 840, I see familiar hex code.

![bequick2](/images/bequick2.png)

![bequick3](/images/bequick3.png)

Replacing them with the “nop” code, we should get the flag. Which did not work:

![bequick4](/images/bequick4.png)

So this time, let’s only remove the call for set_timer:

![bequick5](/images/bequick5.png)

And it worked! The flag is `picoCTF{why_bother_doing_unnecessary_computation_402ca676}`


---
### blaise's cipher
##### Challenge
>My buddy Blaise told me he learned about this cool cipher invented by a guy also named Blaise! Can you figure out what it says? Connect with nc 2018shell.picoctf.com 46966.

##### Writeup
This is a simple challenge. For this one, when we connect to the server, we are given an encrypted text, and a quick look through shows us where we expect our flag to be:

![blaise1](/images/blaise1.png)

pohzCZK{g1gt3w3_n1pn3wd_ax3s7_maj_hof08hk0}
Assuming this is a Vigenere Cipher, I use this code breaking website to help out: https://www.boxentriq.com/code-breaking/vigenere-cipher. We figure out pretty quickly that the key is “FLAG”, but this decoder doesn’t decode the full text, since it is too long. So, I copy the encoded flag, and add letters beforehand until it makes sense:

![blaise2](/images/blaise2.png)

![blaise3](/images/blaise3.png)

Which gives us the flag! `picoCTF{v1gn3r3_c1ph3rs_ar3n7_bad_cdf08bf0}`

---
### buffer overflow 1
##### Challenge
>Okay now you're cooking! This time can you overflow the buffer and return to the flag function in this [program](https://2018shell.picoctf.com/static/089abf876403b47cd1d105a0dc62f2f2/vuln)? You can find it in /problems/buffer-overflow-1_1_8a16ff6a1b3cfb2e42c08d9090051a5d on the shell server. [Source](https://2018shell.picoctf.com/static/089abf876403b47cd1d105a0dc62f2f2/vuln.c).

##### Writeup
This challenge gives a vulnerable program for which we can give an input, but if we put enough characters, it affects the address we would jump. So first, we get the address of where we need to go but using `objdump -d`, and I see that I’d need to jump to 080485cb to get to the “win” function, which I'm assuming will give us the flag. Next, we see how much buffer we need. Looking at the source code, we see that the buffer is 32 characters, so I start with 36 characters to see what happens, then continue adding four each time until the address changes, which we get 48 characters. So we need 44 characters of padding, and then the final 4 would be to get the address. Using python and pwntools, we attach the address in little endian at the end of our 44 character padding: 
`python -c "from pwn import *; print 'A' * 44 + '\xcb\x85\x04\x08'" | ./vuln`
This gives us the right address, and therefore the flag `picoCTF{addr3ss3s_ar3_3asy14941911}`

---
### hertz 2
##### Challenge
>This flag has been encrypted with some kind of cipher, can you decrypt it? Connect with nc 2018shell.picoctf.com 39961.

##### Writeup
This is a substitution cipher, so looking up “substitution cipher decoder” I found this website: https://www.guballa.de/substitution-solver. This solves the cipher really quickly and gives us the flag: `picoCTF{substitution_ciphers_are_too_easy_dngaowmvye}`

![hertz2](/images/hertz2-1.png)

---
### leak-me
##### Challenge
>Can you authenticate to this [service](https://2018shell.picoctf.com/static/c050db17129bdf7e768a0151f554a75d/auth) and get the flag? Connect with nc 2018shell.picoctf.com 1271. [Source](https://2018shell.picoctf.com/static/c050db17129bdf7e768a0151f554a75d/auth.c).

##### Writeup
This challenge is a buffer overflow challenge. Looking at the source code, we see that the password can be 64 characters long, and the username can be 256 characters long. What I did was input 257 characters as the username, and I received the password (as part of the username). I then retried logging in, but with a few letters in the username, then trying out this “really secure password”, which gave me the flag: `picoCTF{aLw4y5_Ch3cK_tHe_bUfF3r_s1z3_958ebb8e}`

---
### now you don't
##### Challenge
>We heard that there is something hidden in this [picture](https://www.youtube.com/watch?v=OBqOAQ4btbU). Can you find it?

##### Writeup
You get a red image for this challenge, along with the hint “is it really all one shade of red?”. So I decided to throw the image in an image editor, and mess with the color balance until I could see letters, which gave me the flag: `picoCTF{n0w_y0u_533_m3}`

![now you don't](/images/see.png)

![now you see me](/images/seeme.png)

---
### quackme
##### Challenge
>Can you deal with the Duck Web? Get us the flag from this [program](https://2018shell.picoctf.com/static/197682216dbdd2c67ae043dc531d4cfc/main). You can also find the program in /problems/quackme_2_45804bbb593f90c3b4cefabe60c1c4e2.

##### Writeup
Looking through the main function, we see that there is a call to a written function <do_magic>. When I looked through this function, I noticed that there are some places that the code is using addresses that may be useful:

![quack](/images/quack1.png)

Such as 0x8048858, and 0x804a038. We can use `objdump -sj .rodata main` to view the hardcoded strings, and their addresses:

![quack](/images/quack2.png)

So we want to get the message “You are the winner!”, which has the address close to 804488a8. So we will probably have to work with the 0x8048858 address, especially since it is added to eax. The exact address of the “winner” message would be 80488ab. Going back through the do_magic function, I actually found that the address we need is already there, so we just need to find a way to get past the checks: 

![quack](/images/quack3.png)

Before the push, there is a jump past if -0x1c(ebp) is not equal to 0x19, which is equal to 25. The code adds 1 to eax with each loop, and the amount of loops is equal to how many letters of input there are. There is also a xor operation between eax and ecx, but what is ecx equal to?
Before the xor, we see that ecx is set to equal the address added to eax, so it’s going through multiple addresses for comparison.

![quack](/images/quack4.png)

And then it goes on to compare to some other address:

![duck](/images/quack5.png)

Which 0x804a038 is apparently located in .data, and gives us an address (in little endian) that brings us back to .rodata, and points to the beginning of the main prompt “you have now entered the Duck Web”

![duck](/images/quack6.png)

From all of this, we see that there is a xor operation happening between what you input and some binaries/hex that is then compared to the starting prompt. So what if we xor the binaries/hex with the prompt?

![goose!](/images/quack7.png)

We get the flag! `picoCTF{qu4ckm3_35246994}`


---
### shellcode
##### Challenge
>This [program](https://2018shell.picoctf.com/static/8e626dbc7f0c1d8b5d673dda3f509de6/vuln) executes any input you give it. Can you get a shell? You can find the program in /problems/shellcode_0_48532ce5a1829a772b64e4da6fa58eed on the shell server. [Source](https://2018shell.picoctf.com/static/8e626dbc7f0c1d8b5d673dda3f509de6/vuln.c).

##### Writeup
For this challenge, we need to get a shell through a program. First we need to write or get shellcode, so after a quick google, we find shellstorm, which has shellcode prepared. Using uname, we find that the shell runs on Linux, so we go to the Linux section and we just need to find a simple code that gives `/bin/sh`. This one seemed to be simple enough: http://shell-storm.org/shellcode/files/shellcode-690.php. We take the characters it gives in the code, and print it into `./vuln`, but this doesn’t keep input open. I didn’t know how to keep the pipe open for continuous input, so after a google search, I’ve found that if I cat the file and add ‘-’ to the end before piping, it keeps it open for input. So, I put the string to get to the shell in `~/shell.txt`. Then, using the line `cat ~/shell.txt - | ./vuln`  I was able to get access to a shell with more permissions. I then used ls to see what there is, and then `cat flag.txt` to get the flag: `picoCTF{shellc0de_w00h00_9ee0edd0}`

---
### what base is this?
##### Challenge
>To be successful on your mission, you must be able read data represented in different ways, such as hexadecimal or binary. Can you get the flag from this program to prove you are ready? Connect with nc 2018shell.picoctf.com 14390.

##### Writeup
This challenge is a fairly simple one. We are asked to give input based off of how data is stored:

![base](/images/base.png)

The first one is binary, the second is hex, and the final is octal. The first two were easy to see what they were, then convert, but for the octal one, I at first thought it’d be decimal, but that didn’t match up, so I had to go find an octal converter. After answering the questions we get the flag: `picoCTF{delusions_about_finding_values_602fd280}`

---
### you can't see me
##### Challenge
>'...reading transmission... Y.O.U. .C.A.N.'.T. .S.E.E. .M.E. ...transmission ended...' Maybe something lies in /problems/you-can-t-see-me_4_8bd1412e56df49a3c3757ebeb7ead77f.

##### Writeup
This challenge gives the hint “What's in the manual page of ls?” and we also get a hint with the "reading transmission" part.
Files with dots in the beginning can be hidden, but using the man page we can see that the ls command can still be used to see those files, using `-a` or `--all`. Using the command `ls -a`, we only see dots. So we need to cat the file, but just using `cat .` does not work, so instead we'll have to read everything starting with '.'

![dots](/images/hidden.png)

Which gives us the flag: `picoCTF{j0hn_c3na_paparapaaaaaaa_paparapaaaaaa_22f627d9}`

---
### Buttons 
##### Challenge
>There is a website running at http://2018shell.picoctf.com:21579 ([link](http://2018shell.picoctf.com:21579/)). Try to see if you can push their buttons.

##### Writeup
For this challenge, you are sent to a website. This website has a button that when you click, it leads to another “button” that leads to a “rick roll” page. Checking the page sources, the main difference between the two buttons is that the first one that actually works is a form

![form](/images/buttons1.png)

But the second one is an href

![href](/images/buttons2.png)

So, using Google Chrome’s ability to edit html, i put the second button in the same format as the first:

![edit](/images/buttons3.png)
 
Which, when I click the button now, it leads to the flag: `picoCTF{button_button_whose_got_the_button_ed306c10}`

---
### Ext Super Magic
##### Challenge
>We salvaged a ruined Ext SuperMagic II-class mech recently and pulled the [filesystem](https://2018shell.picoctf.com/static/9f563e291d847c30879277c3b6c16260/ext-super-magic.img) out of the black box. It looks a bit corrupted, but maybe there's something interesting in there. You can also find it in /problems/ext-super-magic_2_5e1f8bfb15060228f577045924e4fca8 on the shell server.

##### Writeup
This challenge gives a filesystem that is corrupted, and we need to fix it in order to get the flag. We are given a few hints, one of which leads to this website: http://www.nongnu.org/ext2-doc/ext2.html. The first thing I thought to do was look for the words in the challenge title. “Ext” is very common in the website, super is a little less common, but magic only showed up 15 times on the page. Looking through them, we see this section:

![s_magic](/images/supermagic1.png)

This may be helpful, but we have yet to see. Another hint was using the file command:

![hint](/images/supermagic2.png)

Which gives us nothing. What about the last hint:

![hint](/images/supermagic3.png)

It says there is a bad number in the superblock, but how do we know where? According to the website previously listed, the magic number we found before belongs at an offset of 56 bytes, from 1024 (since this format always has the superblock at an offset of 1024). So now we will use a [hexeditor](https://hexed.it/) to hopefully fix the issue.
Decimal 1080 leads to hex 438, and I am assuming we are using little endian format.

![hexedit](/images/supermagic4.png)

![debugfs](/images/supermagic5.png)

It worked, so now we use `debugfs` to access the files in the image: 

![flag.jpg](/images/supermagic6.png)

Surrounded by hundreds of other files, I just searched for “flag” using `/flag`, and found this. Now that I know it is a thing, I need to save it to access it. After a quick google, I found that the way to do this with `debugfs` is to use the command `dump`:

![dump](/images/supermagic7.png)

This gives us a fairly large image with this at the top:

![flag](/images/supermagic8.png)

We got the flag! `picoCTF{ab0CD63BC762514ea2f4fc9eDEC8cb1E}`

---
### Lying Out
##### Challenge
>Some odd [traffic](https://2018shell.picoctf.com/static/abfdb498b12895694285a032f261c545/traffic.png) has been detected on the network, can you identify it? More [info](https://2018shell.picoctf.com/static/abfdb498b12895694285a032f261c545/info.txt) here. Connect with nc 2018shell.picoctf.com 27108 to help us answer some questions.

##### Writeup
This is a simple one. You get an image on the traffic of IPs connecting to a server, which has three spikes (one in the morning, one at noon, and one in the evening).

![graph](/images/lyingout1.png)

Following instructions, and comparing data, we put in the areas that should not have spikes, but are shown to:

![traffic](/images/lyingout2.png)

And we get the flag! `picoCTF{w4y_0ut_de051415}`

---
### The Vault
##### Challenge
>There is a website running at http://2018shell.picoctf.com:53261 ([link](http://2018shell.picoctf.com:53261/)). Try to see if you can login!

##### Writeup
The website is fairly simple, and provides a link under the login, which gives us this:

![vault](/images/vault1.png)

This tells us that they are using SQL to store their passwords, so what we are going to do is the same thing we did with Irish Repo: just enter any username, and have the password of `‘ or ‘ = ‘x`
Which works, and gives us the flag: `picoCTF{w3lc0m3_t0_th3_vault_23495366}`

![vault](/images/vault2.png)

---
### What's My Name?
##### Challenge
>Say my name, say [my name](https://2018shell.picoctf.com/static/b7e6f97343b1e36e6f34f762e95dd819/myname.pcap).

##### Writeup
The hint for this challenge asks “If you visited a website at an IP address, how does it know the name of the domain?” This would be though DNS. We are given a pcap file that we open with wireshark, and we use the ‘dns’ filter:

![dns](/images/name1.png)

Which, we find the flag within the second one: `picoCTF{w4lt3r_wh1t3_ddfad6f8f4255adc73e862e3cebeee9d}`

![name](/images/name2.png)

---
### absolutely relative
##### Challenge
>In a filesystem, everything is relative ¯\\_(ツ)_/¯. Can you find a way to get a flag from this [program](https://2018shell.picoctf.com/static/3a286144f1c251a493c223d6a8ff0a6d/absolutely-relative)? You can find it in /problems/absolutely-relative_0_d4f0f1c47f503378c4bb81981a80a9b6 on the shell server. [Source](https://2018shell.picoctf.com/static/3a286144f1c251a493c223d6a8ff0a6d/absolutely-relative.c).

##### Writeup
Looking at the source code, we see that the program will read for a file called “permission.txt” with the input “yes”. Going to the program location, we cannot make any files or get permissions for the program, so we have to do so from home: 

![relative](/images/relative.png)

And it works! The flag is: `picoCTF{3v3r1ng_1$_r3l3t1v3_befc0ce1}`

---
### assembly-2
##### Challenge
>What does asm2(0xe,0x21) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://2018shell.picoctf.com/static/99d6d3fada6d4f1a63213f45922fd3dc/loop_asm_rev.S) located in the directory at /problems/assembly-2_3_c3ee3603bd2a8e682f1d64cf6dfd21fb.

##### Writeup
For this assembly file, we have the inputs 0xE and 0x21, and some conditional jumps that have us add directly to those inputs. We compare our first input (0xE) to 0x9886; if we are less than or equal, we jump to ‘part_a’ and add 1 to our second variable (0x21) and 0x41 to our first variable (0xE). Since I know that I would be sitting here for a while doing math if I did it by hand, I just decided to use some simple python to tell me how many times we would be adding 0x41 to 0xE before we stop jumping. I used a while loop, adding 1 to a counter each time we go through, and in the end it looped 600 times. I added 600 to 0x21 to get 0x279, but the flag was wrong; I figured I was probably just off by one, and put in 0x27a, which was correct. 

---
### buffer overflow 2
##### Challenge
>Alright, this time you'll need to control some arguments. Can you get the flag from this [program](https://2018shell.picoctf.com/static/bafdb7cd2a833b6af33fec394f4cb6e2/vuln)? You can find it in /problems/buffer-overflow-2_3_02aff35ae94896082cad513865e6c2eb on the shell server. [Source](https://2018shell.picoctf.com/static/bafdb7cd2a833b6af33fec394f4cb6e2/vuln.c).

##### Writeup
This one is a bit more complicated than the last. We need to pass in arguments this time. Using `objdump`, we can see that there is still the ‘win’ function, and the checks that are in the source code are within the ‘win’ function, so first we need to get there, then give the arguments. So, using gdb so that I’d be able to view what’s in registers, I put a breakpoint at vuln and at win. 

![win](/images/overflow2-1.png)

Since a breakpoint is automatically added in main, I just step so that we get to the next break, which is in vuln. We need to set another breakpoint while we are here, right where return is. This way we can give an input and see what we need to in the stack and registers.

![gdb](/images/overflow2-2.png)

To find out where everything is relative to the buffer, we put 100 A’s (the buffer size), then starting with B, continuing the alphabet.

![gdb](/images/overflow2-3.png)

We see here that arglist is “0x4d4c4b4a” which are the letters “MLKJ”, and esp is “0x51504f4e” which are the letters “QPON”. Since we return to where esp gives us, we will replace it with the win address. Now, we restart the program giving a new input:

![cmd](/images/overflow2-4.png)

Now that we would get to win, we continue so that we can see where our arguments belong. We need to stop before the comparison, just to make sure that the arguments are not being edited in any way, so we add another break at 0x0804861a. I got stuck here, since trying to continue to this break keeps on stopping the program so that I cannot look at the arguments being loaded in. After an hour of trying to figure out where I went wrong, I started to watch a video on the challenge and realized that I made a stupid mistake of mistyping where the ‘win’ function is. I had put 0x080485d1, but the win function actually starts at 0x080485cb. After this one, I stopped getting the same error, and instead got a new one telling me that the flag file is missing. 

![gdb](/images/overflow2-5.png)

After this, I tried downloading the files and running it on my virtual machine, but that didn’t work either. 

![vm](/images/overflow2-6.png)

In the end, I just decided to try out answers until it worked. I assumed that the arguments would be in order, so after the part of the buffer that is the return address that we want, I put in the little endian hex values for the arguments: DEADBEEF and DEADC0DE. The first attempt didn’t work, but I put 4 A’s between the arguments and the address, and got the flag: `picoCTF{addr3ss3s_ar3_3asya4104c14}`

![flag](/images/overflow2-7.png)

---
### caesar cipher 2
##### Challenge
>Can you help us decrypt this [message](https://2018shell.picoctf.com/static/bed1fba9caa8aeda29580c36bf0d0276/ciphertext)? We believe it is a form of a caesar cipher. You can find the ciphertext in /problems/caesar-cipher-2_1_ac88f1b12e9dbca252d450d374c4a087 on the shell server.

##### Writeup
Caesar ciphers tend to be simple, so there’s already tons of online tools for decoding them. I used this one, since it’s for the full ascii alphabet: https://www.dcode.fr/ascii-shift-cipher. The cipher text is this weird text given to us by the shell server: `e^Xd8I;pX6ZhVGT8^E]:gHT_jHITVG:cITh:XJg:r`. Decoding it with the website, one of the decryptions is the flag: `picoCTF{cAesaR_CiPhErS_juST_aREnT_sEcUrE}`

---
### rsa-madlibs
##### Challenge
>We ran into some weird puzzles we think may mean something, can you help me solve one? Connect with nc 2018shell.picoctf.com 50652

##### Writeup
This challenge is fairly simple, but took me a few tries since if you took too long, you would be disconnected. All of it has to do with doing math (if possible) to find certain parts of an RSA algorithm. You have to first find out if the math is possible and answer accordingly, then do the math when it is possible to move on to the next question. First it asks if you can find n, given q and p, which you can through multiplying them together. The next question asks if you can find q if given p and n, which you can by dividing n by p. Then it asks if you can find q and p from n and e, which is not possible. The next is finding the totient(n), which can be done by multiplying (q-1) with (p-1). Now is when this starts being a little difficult: we have to make the ciphertext, given plaintext, e and n. Given that the plaintext is larger than what we have dealt with so far, and n is even larger than that, I move on to python to copy and paste everything:

![madlib](/images/rsamadlibs1.PNG)

The given answer is correct. The next question asks for plaintext given ciphertext, e and n, which is not possible. Then we need to find d given q p and e, which is possible but through some complicated math. Trying to find the algorithm I need, I have found that I need to use the inverse modulus function, which is provided in Crypto.Util.number. So using this, I was able to answer the next to problems, which once we complete we get this message: 

![madlib](/images/rsamadlibs2.PNG)

So now we use pwntools to decode this hex into ASCII and we get the flag: `picoCTF{d0_u_kn0w_th3_w@y_2_RS@_c6724916}`

![flag](/images/rsamadlibs3.png)

Here is the full python script that I wrote for the answers: [rsa-madlibs.py](https://github.com/lasivori/picoCTF-2018/blob/master/rsa-madlibs.py)

---
### echooo
##### Challenge
>This program prints any input you give it. Can you leak the flag? Connect with nc 2018shell.picoctf.com 34802. [Source](https://2018shell.picoctf.com/static/ef78275d00e7ab2809e43a6aa9563317/echo.c).

##### Writeup
For this challenge, it tells you that it’s “Time to learn about Format Strings!” and that it will use `printf()` to echo whatever we input. So, I decide to go ahead and just input `%x *64`, since `%x` is used to display integers. Given a number that I assume to be hex, I use python to convert it to ASCII:

![format strings](/images/echo1.png)

And we begin to see the flag (of course in the wrong order). So far we have `picoCTF{foRm4t_stRin`. We can see that this starts at about the 42nd ‘%x’ so we will now use “%42$x” and so on so that we get those parts of the stack. After some testing, I’ve decided to start with `%27$x` and go through `%42$x`, and got the following:

![format strings](/images/echo2.png)

Which I then used Python to decode it into ASCII:

![format strings](/images/echo3.png)

Of course the string is still out of order, so let’s put it in order, but it’s not compete yet: `picoCTF{foRm4t_stRinGs_aRe_DanGer0us_3f8bced`
The last few letters right after are “/a7/d3/38" which does not make sense, it doesn’t give us anything we need, maybe there was an error. "/7d/33" makes sense, it would give us "3}" to add on the end of the flag: `picoCTF{foRm4t_stRinGs_aRe_DanGer0us_3f8bced3}` which is correct!

---
### learn gdb
##### Challenge
>Using a debugging tool will be extremely useful on your missions. Can you run this [program](https://2018shell.picoctf.com/static/999e37c9737d95c105ea29ae5b3fac1f/run) in gdb and find the flag? You can find the file in /problems/learn-gdb_3_f1f262d9d48b9ff39efc3bc092ea9d7b on the shell server.

##### Writeup
For this challenge, we are supposed to use GDB to find the flag in a program. With a quick look using `objdump -d run`, we can see that the program uses a function called “decrypt_flag”. So when I get into gdb, I set a breakpoint at “decrypt_flag”, then run. There is an automatic breakpoint in main, and I run `disas` to see what is going on, and I see that I don’t even need to see the decrypt_flag function. I could just put a break right after it at the point 0x40090a: 

![gdb](/images/gdb.png)

Continuing from here we see that they decrypt the variable “flag_buf”, and so at our next break, we can use the command `x/s flag_buf` to view the string stored in this variable, giving us the flag: `picoCTF{gDb_iS_sUp3r_u53fuL_efaa2b29}`

![flag](/images/gdb2.png)

---
### Flaskcards
##### Challenge
>We found this fishy [website](http://2018shell.picoctf.com:51878/) for flashcards that we think may be sending secrets. Could you take a look?

##### Writeup
I barely knew where to start for this one. It’s supposed to be a flashcard making website, but the challenge name is “misspelled”, which cannot be a coincidence. I looked up “website flask” and found that Flask is used as a framework, and I quickly found this website: https://nvisium.com/blog/2015/12/07/injecting-flask.html which talks about how Flask is vulnerable to injections. I tried putting injections in the URL at first, but that didn’t work. The hints mentioned “Is there anywhere that filtering doesn't get applied?” The only other places to enter things is through logging in and creating cards, so I tested `{{5*5}}` in both. For logging in, I wasn’t allowed to put that as my username, but it worked for the flashcards:

![flask test](/images/flask1.png)
![vulnerability](/images/flask2.png)

But now what? I’ve been reading through Flask framework stuff for a while. One of the things I first searched was this website: https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-iv-database which seems that one of the first things you come to is a “config” object that seems important, so why not test that:

![config](/images/flask3.png)

Which gives us this mess, so let’s search for “picoCTF”.

![config](/images/flask4.png)

And we got the flag! `picoCTF{secret_keys_to_the_kingdom_e8a55760}`

![flag](/images/flask5.png)

---
### assembly-3
##### Challenge
>What does asm3(0xf238999b,0xda0f9ac5,0xcc85310c) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://2018shell.picoctf.com/static/8574a4801ca14ef4666bc4a6e5f694c2/end_asm_rev.S) located in the directory at /problems/assembly-3_2_504fe35f4236db611941d162e2abc6b9.

##### Writeup
assembly-3 400
As we do with the rest of the assembly challenges, we just follow the instructions. The only complications now is for which parts of the input are going into which parts of registers, due to the sizes taken, then used Python to do the math for me:

![assembly](/images/assembly3.PNG)

The flag is 0x56a3.

---
### Secure Logon
##### Challenge
>Uh oh, the login page is more secure... I think. http://2018shell.picoctf.com:13747 ([link](http://2018shell.picoctf.com:13747/)). [Source](https://2018shell.picoctf.com/static/336b6b2aa0b52e8954f817df605cccd7/server_noflag.py).

##### Writeup
ooking at the source code for this web exploitation challenge, at first I thought it would have to do with a Flask weakness due to the website using it. Testing injection code in the username and password areas, I quickly realize it’s not going to work, so I go back to looking at the source code. We see that the cookie for admin is set to 0, and the rest are related to the password and username chosen. The cookie is encrypted using AES CBC, which means that block encryption and decryption relies on previous blocks. Since they are using base64, we will have to as well to exploit the weaknesses of CBC. I’m assuming that the ultimate goal is to have admin set to 1 instead of 0: given the plaintext `{'admin': 0, 'username': 'user', 'password': 'pass'}`, we can see that the number we need to change is the 11th letter. Now we take our cookie, decode it with base64, and edit the hex that we need to (position 10 being the 11th letter):

![b64 to hex](/images/secure1.png)

We XOR the bit we need flipped with 0x01, since CBC is weak to bit flipping attacks. We then replace the 11th letter ‘0xb0’ with ‘0xb1’ and encode it with base64 to get our new cookie:

![cookie edit](/images/secure2.png)

Using a cookie editor in chrome, I put in the new cookie and refresh the page for the flag: `picoCTF{fl1p_4ll_th3_bit3_7d7c2296}`

![flag](/images/secure3.png)

---
