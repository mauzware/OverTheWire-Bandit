# 🏴 OverTheWire: Bandit Walkthrough (Levels 0 – 33)

Welcome to my personal walkthrough of the **OverTheWire Bandit wargame**, covering Levels 0 to 16. This wargame is designed to teach beginners the fundamentals of Linux, command line usage, and basic hacking techniques. 
I completed levels 0 to 33 in one session — here’s how I did it.

> 🧠 All activities were done in a legal and authorized lab environment provided by [OverTheWire](https://overthewire.org/wargames/). For educational use only.

---

## 🔧 SSH Access

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
Use the password from the previous level to login to the next one.
```

✅ Level 0 ➜ 1

🧩 Goal: Read contents of readme file in the home directory.

```
bandit0@bandit:~$ ls
readme

bandit0@bandit:~$ cat readme 
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

📥 Password:

```
ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

---

✅ Level 1 ➜ 2

🧩 Goal: The password for the next level is stored in a file called - located in the home directory.

```
bandit1@bandit:~$ ls
-

bandit1@bandit:~$ cat ./-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

📥 Password:

```
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

---

✅ Level 2 ➜ 3

🧩 Goal: The password for the next level is stored in a file called spaces in this filename located in the home directory.

```
bandit2@bandit:~$ ls
spaces in this filename

bandit2@bandit:~$ cat spaces\ in\ this\ filename 
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

bandit2@bandit:~$ cat "spaces in this filename" 
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

📥 Password:

```
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

---

✅ Level 3 ➜ 4

🧩 Goal: The password for the next level is stored in a hidden file in the inhere directory.

```
bandit3@bandit:~$ ls
inhere

bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ls -al
total 12
drwxr-xr-x 2 root    root    4096 Apr 10 14:23 .
drwxr-xr-x 3 root    root    4096 Apr 10 14:23 ..
-rw-r----- 1 bandit4 bandit3   33 Apr 10 14:23 ...Hiding-From-You

bandit3@bandit:~/inhere$ cat ...Hiding-From-You 
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

📥 Password:

```
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

---

✅ Level 4 ➜ 5

🧩 Goal: The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

```
bandit4@bandit:~/inhere$ file -- *
-file00: PGP Secret Sub-key -
-file01: data
-file02: data
-file03: data
-file04: data
-file05: data
-file06: data
-file07: ASCII text
-file08: data
-file09: data

bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

📥 Password:

```
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

---

✅ Level 5 ➜ 6

🧩 Goal: The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable

```
bandit5@bandit:~/inhere$ find . -type f -size 1033c ! -executable -exec file {} + | grep ASCII
./maybehere07/.file2: ASCII text, with very long lines (1000)

bandit5@bandit:~/inhere$ cat maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

📥 Password:

```
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

---

✅ Level 6 ➜ 7

🧩 Goal: The password for the next level is stored somewhere on the server and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

```
bandit6@bandit:~$ find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password

bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password 
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

📥 Password:

```
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

---

✅ Level 7 ➜ 8

🧩 Goal: The password for the next level is stored in the file data.txt next to the word millionth.

```
bandit7@bandit:~$ ls
data.txt

bandit7@bandit:~$ cat data.txt | grep millionth
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

📥 Password:

```
dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

---

✅ Level 8 ➜ 9

🧩 Goal: The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

```
bandit8@bandit:~$ ls
data.txt

bandit8@bandit:~$ sort data.txt | uniq -u
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

📥 Password:

```
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

---

✅ Level 9 ➜ 10

🧩 Goal: The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

```
bandit9@bandit:~$ strings data.txt 
l0@P(
,k=?
[SNIP!]
Ns9(
//'av
========== the
2xG&
[SNIP!]
O;O1
H7*E
========== password{k
]AOJ
[SNIP!]
;`[;z
=========== is
{~j@e
[SNIP!]
*dx%A
2wNXK|
========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
v3A|
"y~ 
```

📥 Password:

```
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```

---

✅ Level 10 ➜ 11

🧩 Goal: The password for the next level is stored in the file data.txt, which contains base64 encoded data.

```
bandit10@bandit:~$ cat data.txt 
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==

bandit10@bandit:~$ cat data.txt | base64 -d
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

📥 Password:

```
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

✅ Level 11 ➜ 12

🧩 Goal: The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

```
bandit11@bandit:~$ cat data.txt 
Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4

bandit11@bandit:~$ echo 'Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4' | tr 'A-Za-z' 'N-ZA-Mn-za-m' 
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m' 
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

📥 Password:

```
7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

---

✅ Level 12 ➜ 13

🧩 Goal: The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. 
For this level it may be useful to create a directory under `/tmp` in which you can work. 
Use `mkdir` with a hard to guess directory name. Or better, use the command `mktemp -d`. 
Then copy the datafile using cp, and rename it using mv (read the manpages!)
Commands you may need to solve this level

```
bandit12@bandit:~$ strings data.txt 
00000000: 1f8b 0808 41d4 f767 0203 6461 7461 322e  ....A..g..data2.
00000010: 6269 6e00 0149 02b6 fd42 5a68 3931 4159  bin..I...BZh91AY
00000020: 2653 59a8 ffa7 8f00 001d 7fff dbeb 7ffa  &SY.............
00000030: bb7f a5ef bb7e f5fb fdff b7c7 f3ff ff7f  .....~..........
00000040: ff7f fff7 deba fdfa eff7 dddf b001 3b19  ..............;.
00000050: a200 d01a 0190 0034 0006 800d 0340 0346  .......4.....@.F
00000060: 8000 0340 0320 0069 a034 0640 0346 4680  ...@. .i.4.@.FF.
00000070: 68d1 a68c 8321 9313 4da4 f510 6406 8003  h....!..M...d...
00000080: 4006 9a00 000d 000d 0069 a007 a9a0 001a  @........i......
00000090: 1b50 03d4 01a6 9a1e a001 a343 4683 469a  .P.........CF.F.
000000a0: 3d40 001a 7a8d 01a0 074c 801e a1a6 8064  =@..z....L.....d
000000b0: 01a3 d434 00c4 0d00 000d 0001 a680 1a19  ...4............
000000c0: 0061 0f53 41a0 0000 0d00 341a 0320 0034  .a.SA.....4.. .4
000000d0: d1ea 0168 4882 8244 0130 5550 f16b f52e  ...hH..D.0UP.k..
000000e0: a322 cb9f bb8c aaf6 e244 cc70 b151 47c8  .".......D.p.QG.
000000f0: 6c03 a3ae 4a81 1ee0 03ce 840e a978 2046  l...J........x F
00000100: 630b 4b0d 9883 7078 e7e8 5bfb 68f1 f685  c.K...px..[.h...
00000110: 6f46 771c 3920 449f f0cb 39e2 0841 10b5  oFw.9 D...9..A..
00000120: 8714 e981 115c d1bc 2da4 318b 106c 904e  .....\..-.1..l.N
00000130: 9328 5e97 405a 4054 21db e049 1a32 5f3d  .(^.@Z@T!..I.2_=
00000140: 7069 408f f0a4 8ce5 fbea 282c 51d1 49e4  pi@.......(,Q.I.
00000150: d52f 0762 dd90 27b8 79d3 0499 52e0 060c  ./.b..'.y...R...
00000160: fd91 a474 d408 88f3 1fda d2d1 325a baeb  ...t........2Z..
00000170: bfe7 f0f6 cc3c 776d f369 e73c 47d4 66ea  .....<wm.i.<G.f.
00000180: 4b90 e404 03b3 6a09 4687 945d 09ef 706b  K.....j.F..]..pk
00000190: 8f82 2503 80d0 0a0a 3e60 f879 bf02 2d42  ..%.....>`.y..-B
000001a0: bf37 9c96 4b22 585c 35c8 3cf1 da9f 518b  .7..K"X\5.<...Q.
000001b0: ccd5 a68c 9647 aa38 8a50 89d2 f89c 1ff0  .....G.8.P......
000001c0: 1042 18c3 6549 400d fe17 ec74 3171 6d74  .B..eI@....t1qmt
000001d0: a8bb 0def f11a 5a69 0e70 aa34 0037 b180  ......Zi.p.4.7..
000001e0: 1540 c4d2 0af7 e290 8784 ce9e 147a 6836  .@...........zh6
000001f0: 944b 3f18 2ba2 c620 af92 fb01 184f 3def  .K?.+.. .....O=.
00000200: 1b7d 0162 733d adca 90ac 7142 8319 f703  .}.bs=....qB....
00000210: 5930 69e2 8320 9110 5d63 0db9 9294 d4ef  Y0i.. ..]c......
00000220: 50b9 5907 0924 92c1 014e a284 25ce a6ef  P.Y..$...N..%...
00000230: 67b2 4e06 6d21 4136 2ac0 292d 6638 033c  g.N.m!A6*.)-f8.<
00000240: 21af be4e 13bb b74f 2c10 18c7 eea3 c436  !..N...O,......6
00000250: c988 05e6 5638 1ff1 7724 5385 090a 8ffa  ....V8..w$S.....
00000260: 78f0 d951 192d 4902 0000                 x..Q.-I...
```

- aj kri evri tim. Now use multiple compressions until you get the password.

  ```
  first change it to binary:

  bandit12@bandit:/tmp/bimbo$ xxd -r data > binary
  bandit12@bandit:/tmp/bimbo$ ls
  binary  data
  bandit12@bandit:/tmp/bimbo$ file binary 
  binary: gzip compressed data, was "data2.bin", last modified: Thu Apr 10 14:22:57 2025, max compression, from Unix, original size modulo 2^32 585
    
  now gunzip:
    
  bandit12@bandit:/tmp/bimbo$ mv binary binary.gz
  bandit12@bandit:/tmp/bimbo$ gunzip binary.gz 
  bandit12@bandit:/tmp/bimbo$ ls
  binary  data
  bandit12@bandit:/tmp/bimbo$ file binary 
  binary: bzip2 compressed data, block size = 900k
    
  now bzip:
    
  bandit12@bandit:/tmp/bimbo$ bunzip2 binary 
  bunzip2: Can't guess original name for binary -- using binary.out
  bandit12@bandit:/tmp/bimbo$ ls
  binary.out  data
  bandit12@bandit:/tmp/bimbo$ file binary.out 
  binary.out: gzip compressed data, was "data4.bin", last modified: Thu Apr 10 14:22:57 2025, max compression, from Unix, original size modulo 2^32 20480
    
  now gzip again:
    
  bandit12@bandit:/tmp/bimbo$ mv binary.out binary.gz
  bandit12@bandit:/tmp/bimbo$ gunzip binary.gz 
  bandit12@bandit:/tmp/bimbo$ ls
  binary  data
  bandit12@bandit:/tmp/bimbo$ file binary 
  binary: POSIX tar archive (GNU)
    
  now tar:
    
  bandit12@bandit:/tmp/bimbo$ tar -xf binary
  bandit12@bandit:/tmp/bimbo$ ls
  binary  data  data5.bin
  bandit12@bandit:/tmp/bimbo$ file data5.bin 
  data5.bin: POSIX tar archive (GNU)
  ```

- NOW DELETE BINARY AND DATA AND KEEP REPEATING ALL COMMANDS TO DATA.BIN FILES !!!!!

  ```
  bandit12@bandit:/tmp/bimbo$ tar -xf data5.bin
  bandit12@bandit:/tmp/bimbo$ ls
  data5.bin  data6.bin
  bandit12@bandit:/tmp/bimbo$ file data6.bin 
  data6.bin: bzip2 compressed data, block size = 900k
    
  bandit12@bandit:/tmp/bimbo$ bunzip2 data6.bin
  bunzip2: Can't guess original name for data6.bin -- using data6.bin.out
  bandit12@bandit:/tmp/bimbo$ ls
  data6.bin.out
  bandit12@bandit:/tmp/bimbo$ file data6.bin.out 
  data6.bin.out: POSIX tar archive (GNU)
    
  bandit12@bandit:/tmp/bimbo$ tar -xf data6.bin.out
  bandit12@bandit:/tmp/bimbo$ ls
  data6.bin.out  data8.bin
  bandit12@bandit:/tmp/bimbo$ file data8.bin 
  data8.bin: gzip compressed data, was "data9.bin", last modified: Thu Apr 10 14:22:57 2025, max compression, from Unix, original size modulo 2^32 49
    
  bandit12@bandit:/tmp/bimbo$ mv data8.bin data8.gz
  bandit12@bandit:/tmp/bimbo$ gunzip data8.gz 
  bandit12@bandit:/tmp/bimbo$ ls
  data6.bin.out  data8
  bandit12@bandit:/tmp/bimbo$ file data8
  data8: ASCII text
  bandit12@bandit:/tmp/bimbo$ cat data8 
  The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
  ```

- FU**IN HELL AHAHHAHAHAHAHAHAHAHAHAHAHAHAHAH.

📥 Password:

```
FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```

---

✅ Level 13 ➜ 14

🧩 Goal: The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. 
For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. 
Note: localhost is a hostname that refers to the machine you are working on

```
$ ssh bandit13@bandit.labs.overthewire.org -p 2220
FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

copy sshkey in bandit13 directory

paste it to your machine, chmod 700 and login as bandit14

$ ssh -i bandit14_key bandit14@bandit.labs.overthewire.org -p 2220
Welcome to OverTheWire!

Enjoy your stay!

bandit14@bandit:~$ whoami
bandit14
bandit14@bandit:~$ pwd
/home/bandit14
```

---

✅ Level 14 ➜ 15

🧩 Goal: The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

```
bandit14@bandit:/etc/bandit_pass$ telnet 127.0.0.1 30000
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

Connection closed by foreign host.
```

📥 Password:

```
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```

---

✅ Level 15 ➜ 16

🧩 Goal: The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption. 
Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.

```
bandit15@bandit:~$ openssl s_client -connect 127.0.0.1:30001
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil

---
read R BLOCK
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
Correct!
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

closed
```

📥 Password:

```
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```

✅ Level 16 → Level 17

🧠 Objective: The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. 
First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. 
There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.

🛠 Commands:

```
bandit16@bandit:~$ nmap -sV -p 31000-32000 localhost
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-06-04 14:18 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00011s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT      STATE SERVICE     VERSION
31046/tcp open  echo
31518/tcp open  ssl/echo
31691/tcp open  echo
31790/tcp open  ssl/unknown
31960/tcp open  echo
```

```
bandit16@bandit:~$ openssl s_client -connect 127.0.0.1:31790 -quiet
Can't use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
Correct!
-----BEGIN RSA PRIVATE KEY-----
[SNIP!]
-----END RSA PRIVATE KEY-----


$ chmod 400 bandit17_key
$ ssh -i bandit17_key bandit17@bandit.labs.overthewire.org -p 2220

bandit17@bandit:~$ cat /etc/bandit_pass/bandit17
EReVavePLFHtFlFsjn3hyzMlvSuSAcRD
```

📥 Password:

```
EReVavePLFHtFlFsjn3hyzMlvSuSAcRD
```

---

✅ Level 17 → Level 18

🧠 Objective: There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new.

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19

🛠 Command:

```
bandit17@bandit:~$ diff passwords.new passwords.old 
42c42
< x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
---
> C6XNBdYOkgt5ARXESMKWWOUwBeaIQZ0Y
```

🏁 Password:

```
x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```

---

✅ Level 18 → Level 19

🧠 Objective: The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

🛠 Trick:
Use the ssh -t flag to run a command immediately after connecting.

```
ssh -t bandit18@bandit.labs.overthewire.org -p 2220 cat readme

                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

bandit18@bandit.labs.overthewire.org's password: 
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```

🏁 Password:

```
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```

---

✅ Level 19 → Level 20

🧠 Objective: To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. 
The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

🛠 Command:

```
bandit19@bandit:~$ ./bandit20-do 
Run a command as another user.
  Example: ./bandit20-do id

bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```

🏁 Flag:

```
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```

---

✅ Level 20 → Level 21

🧠 Objective: There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. 
It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). 
If the password is correct, it will transmit the password for the next level (bandit21).

NOTE: Try connecting to your own network daemon to see if it works as you think

🛠 Steps:

```
bandit20@bandit:~$ echo -n '0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO' | nc -l -p 1234 &
[1] 1431432

bandit20@bandit:~$ ./suconnect 1234
Read: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
Password matches, sending next password
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
[1]+  Done                    echo -n '0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO' | nc -l -p 1234
```

🏁 Password:

```
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
```

---

✅ Level 21 → Level 22

🧠 Objective: A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.


🛠 Commands:

```
bandit21@bandit:~$ cd /etc/cron.d
bandit21@bandit:/etc/cron.d$ ls -al
total 48
drwxr-xr-x   2 root root  4096 Apr 10 14:24 .
drwxr-xr-x 121 root root 12288 Apr 21 12:42 ..
-rw-r--r--   1 root root   123 Apr 10 14:16 clean_tmp
-rw-r--r--   1 root root   120 Apr 10 14:23 cronjob_bandit22
-rw-r--r--   1 root root   122 Apr 10 14:23 cronjob_bandit23
-rw-r--r--   1 root root   120 Apr 10 14:23 cronjob_bandit24
-rw-r--r--   1 root root   201 Apr  8  2024 e2scrub_all
-rwx------   1 root root    52 Apr 10 14:24 otw-tmp-dir
-rw-r--r--   1 root root   102 Mar 31  2024 .placeholder
-rw-r--r--   1 root root   396 Jan  9  2024 sysstat

bandit21@bandit:/etc/cron.d$ cat clean_tmp 
*/30 * * * * root find /tmp -amin 60 -type f -delete &> /dev/null && find /tmp -amin 5 -type d -empty -delete &> /dev/null

bandit21@bandit:/etc/cron.d$ cat cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null

bandit21@bandit:/etc/cron.d$ cat cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null

bandit21@bandit:/etc/cron.d$ cat cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null

bandit21@bandit:/etc/cron.d$ cat e2scrub_all 
30 3 * * 0 root test -e /run/systemd/system || SERVICE_MODE=1 /usr/lib/x86_64-linux-gnu/e2fsprogs/e2scrub_all_cron
10 3 * * * root test -e /run/systemd/system || SERVICE_MODE=1 /sbin/e2scrub_all -A -r

bandit21@bandit:/etc/cron.d$ cat otw-tmp-dir 
cat: otw-tmp-dir: Permission denied

bandit21@bandit:/etc/cron.d$ cat .placeholder 
# DO NOT EDIT OR REMOVE
# This file is a simple placeholder to keep dpkg from removing this directory

bandit21@bandit:/etc/cron.d$ cat sysstat 
# The first element of the path is a directory where the debian-sa1
# script is located
PATH=/usr/lib/sysstat:/usr/sbin:/usr/sbin:/usr/bin:/sbin:/bin

# Activity reports every 10 minutes everyday
5-55/10 * * * * root command -v debian-sa1 > /dev/null && debian-sa1 1 1

# Additional run at 23:59 to rotate the statistics file
59 23 * * * root command -v debian-sa1 > /dev/null && debian-sa1 60 2

bandit21@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv

bandit21@bandit:/etc/cron.d$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
```

🏁 Password:

```
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
```

---

✅Level 22 → Level 23

🧠 Objective: A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. 
If you are having problems understanding what it does, try executing it to see the debug information it prints.

🛠 Steps:

```
bandit22@bandit:~$ cd /etc/cron.d
bandit22@bandit:/etc/cron.d$ ls -al
total 48
drwxr-xr-x   2 root root  4096 Apr 10 14:24 .
drwxr-xr-x 121 root root 12288 Apr 21 12:42 ..
-rw-r--r--   1 root root   123 Apr 10 14:16 clean_tmp
-rw-r--r--   1 root root   120 Apr 10 14:23 cronjob_bandit22
-rw-r--r--   1 root root   122 Apr 10 14:23 cronjob_bandit23
-rw-r--r--   1 root root   120 Apr 10 14:23 cronjob_bandit24
-rw-r--r--   1 root root   201 Apr  8  2024 e2scrub_all
-rwx------   1 root root    52 Apr 10 14:24 otw-tmp-dir
-rw-r--r--   1 root root   102 Mar 31  2024 .placeholder
-rw-r--r--   1 root root   396 Jan  9  2024 sysstat

bandit22@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit23.sh
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget

bandit22@bandit:/etc/cron.d$ ls -al /usr/bin/cronjob_bandit23.sh
-rwxr-x--- 1 bandit23 bandit22 211 Apr 10 14:23 /usr/bin/cronjob_bandit23.sh

bandit22@bandit:/etc/cron.d$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349

bandit22@bandit:/etc/cron.d$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
```

🏁 Password:

```
0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
```

---

✅ Level 23 → Level 24

🧠 Objective: A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

You must create a script and a world-writable file that gets written to by the script.

🛠 Steps:

```
echo 'cat /etc/bandit_pass/bandit24 > /tmp/flag24' > /tmp/mauz_script.sh
chmod +x /tmp/mauz_script.sh

cp /tmp/mauz_script.sh /var/spool/bandit24/mauzy.sh
```

📄 Wait and check:

```
bandit23@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done

bandit23@bandit:/etc/cron.d$ cd /var/spool/bandit24/foo
bandit23@bandit:/var/spool/bandit24/foo$ ls -al
ls: cannot open directory '.': Permission denied

bandit23@bandit:/var/spool/bandit24/foo$ ls -al
ls: cannot open directory '.': Permission denied

bandit23@bandit:/var/spool/bandit24/foo$ cd ..
bandit23@bandit:/var/spool/bandit24$ ls -al
total 12
dr-xr-x---  3 bandit24 bandit23 4096 Apr 10 14:23 .
drwxr-xr-x  5 root     root     4096 Apr 10 14:23 ..
drwxrwx-wx 43 root     bandit24 4096 Jun  4 15:13 foo

bandit23@bandit:/var/spool/bandit24$ mktemp -d
/tmp/tmp.Sn3V5m9XNG
bandit23@bandit:/var/spool/bandit24$ cd /tmp/tmp.Sn3V5m9XNG
bandit23@bandit:/tmp/tmp.Sn3V5m9XNG$ ls -al
total 9980
drwx------    2 bandit23 bandit23     4096 Jun  4 15:15 .
drwxrwx-wt 1804 root     root     10211328 Jun  4 15:15 ..
```

- Now create a script that will overwrite the current one.

```
#!/bin/bash

mkdir -p /tmp/tmp.qylmId2Ser/$(cat /etc/bandit_pass/bandit24)
```

```
bandit23@bandit:/tmp/tmp.Sn3V5m9XNG$ ls -al /tmp/tmp.qylmId2Ser/
total 9984
drwxrwxr-x    3 bandit24 bandit24     4096 Jun  4 15:32 .
drwxrwx-wt 1826 root     root     10211328 Jun  4 15:32 ..
drwxrwxr-x    2 bandit24 bandit24     4096 Jun  4 15:32 gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
bandit23@bandit:/tmp/tmp.Sn3V5m9XNG$ cd /tmp/tmp.qylmId2Ser/
bandit23@bandit:/tmp/tmp.qylmId2Ser$ ls
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
bandit23@bandit:/tmp/tmp.qylmId2Ser$ cd gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8/
```

🏁 Password:

```
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
```

---

✅ Level 24 → Level 25

🧠 Objective: A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. 
There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.
You do not need to create new connections each time

🛠 Bruteforce Script:

```
#!/bin/bash

for i in {0000..9999}
do
        echo gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 $i >> possibilities.txt
done

cat possibilities.txt | nc localhost 30002 > result.txt
```

```
bandit24@bandit:$ mktemp -d
bandit24@bandit:$ cd /tmp/tmp.ImCqV5PqR7
bandit24@bandit:/tmp/tmp.ImCqV5PqR7$ nano brute.sh
bandit24@bandit:/tmp/tmp.ImCqV5PqR7$ chmod +x brute.sh
bandit24@bandit:/tmp/tmp.ImCqV5PqR7$ ./brute.sh

bandit24@bandit:/tmp/tmp.ImCqV5PqR7$ ls -al
total 10516
drwx------    2 bandit24 bandit24     4096 Jun  4 15:42 .
drwxrwx-wt 1850 root     root     10211328 Jun  4 15:43 ..
-rwxrwxr-x    1 bandit24 bandit24      170 Jun  4 15:42 brute.sh
-rw-rw-r--    1 bandit24 bandit24   380000 Jun  4 15:42 possibilities.txt
-rw-rw-r--    1 bandit24 bandit24   162214 Jun  4 15:42 result.txt

bandit24@bandit:/tmp/tmp.ImCqV5PqR7$ cat result.txt

[SNIP!]
Correct!
The password of user bandit25 is iCi86ttT4KSNe1armKiwbQNmB3YJP3q4
```

🏁 Password:

```
iCi86ttT4KSNe1armKiwbQNmB3YJP3q4
```

---

✅ Level 25 → Level 26

🧠 Goal: Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

NOTE: if you’re a Windows user and typically use Powershell to ssh into bandit: Powershell is known to cause issues with the intended solution to this level. You should use command prompt instead.

```
bandit25@bandit:~$ cat bandit26.sshkey 
-----BEGIN RSA PRIVATE KEY-----
[SNIP!]
-----END RSA PRIVATE KEY-----

bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0
```

- Now you have to make terminal ultra small in order to access `vim` and read the password.

```
:set shell=/bin/bash
:shell

bandit26@bandit:~$ whoami
bandit26
bandit26@bandit:~$ cat /etc/bandit_pass/bandit26
s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ
```

✅ Password: 

```
s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ
```

---

✅ Level 26 → Level 27

🧠 Goal: Good job getting a shell! Now hurry and grab the password for bandit27!

```
bandit26@bandit:~$ ls                                                                                                       
bandit27-do  text.txt 

bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB 
```

✅ Password: 

```
upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB
```

---

✅ Level 27 → Level 28

🧠 Goal: There is a git repository at ssh://bandit27-git@localhost/home/bandit27-git/repo via the port 2220. The password for the user bandit27-git is the same as for the user bandit27.

Clone the repository and find the password for the next level.

```
bandit27@bandit:~$ mktemp -d
/tmp/tmp.7iH83ASxFx

bandit27@bandit:~$ cd /tmp/tmp.7iH83ASxFx
bandit27@bandit:/tmp/tmp.7iH83ASxFx$ ls -al
total 9980
drwx------    2 bandit27 bandit27     4096 Jun  4 21:36 .
drwxrwx-wt 2378 root     root     10211328 Jun  4 21:37 ..

bandit27@bandit:/tmp/tmp.7iH83ASxFx$ git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo 
Cloning into 'repo'...
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit27/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit27/.ssh/known_hosts).
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

bandit27-git@localhost's password: 
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.

bandit27@bandit:/tmp/tmp.7iH83ASxFx$ cd repo
bandit27@bandit:/tmp/tmp.7iH83ASxFx/repo$ ls
README

bandit27@bandit:/tmp/tmp.7iH83ASxFx/repo$ cat README 
The password to the next level is: Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
```

✅ Password: 

```
Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
```

---

✅ Level 28 → Level 29

🧠 Goal: There is a git repository at ssh://bandit28-git@localhost/home/bandit28-git/repo via the port 2220. The password for the user bandit28-git is the same as for the user bandit28.

Clone the repository and find the password for the next level.

```
bandit28@bandit:~$ mktemp -d
/tmp/tmp.TZAblgFfzU

bandit28@bandit:~$ cd /tmp/tmp.TZAblgFfzU

bandit28@bandit:/tmp/tmp.TZAblgFfzU$ git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
Cloning into 'repo'...
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit28/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit28/.ssh/known_hosts).
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

bandit28-git@localhost's password: 
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 9 (delta 2), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (2/2), done.

bandit28@bandit:/tmp/tmp.TZAblgFfzU$ cd repo
bandit28@bandit:/tmp/tmp.TZAblgFfzU/repo$ ls -al
total 16
drwxrwxr-x 3 bandit28 bandit28 4096 Jun  4 21:44 .
drwx------ 3 bandit28 bandit28 4096 Jun  4 21:44 ..
drwxrwxr-x 8 bandit28 bandit28 4096 Jun  4 21:44 .git
-rw-rw-r-- 1 bandit28 bandit28  111 Jun  4 21:44 README.md

bandit28@bandit:/tmp/tmp.TZAblgFfzU/repo$ cat README.md 
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx

bandit28@bandit:/tmp/tmp.TZAblgFfzU/repo/.git/logs/refs/heads$ cat master 
0000000000000000000000000000000000000000 674690a00a0056ab96048f7317b9ec20c057c06b Ben Dover <noone@overthewire.org> 1749073474 +0000 clone: from ssh://localhost:2220/home/bandit28-git/repo

bandit28@bandit:/tmp/tmp.TZAblgFfzU/repo$ git log
commit 674690a00a0056ab96048f7317b9ec20c057c06b (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Apr 10 14:23:19 2025 +0000

    fix info leak

commit fb0df1358b1ff146f581651a84bae622353a71c0
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Apr 10 14:23:19 2025 +0000

    add missing data

commit a5fdc97aae2c6f0e6c1e722877a100f24bcaaa46
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Apr 10 14:23:19 2025 +0000

    initial commit of README.md

bandit28@bandit:/tmp/tmp.TZAblgFfzU/repo$ git show 674690a00a0056ab96048f7317b9ec20c057c06b
commit 674690a00a0056ab96048f7317b9ec20c057c06b (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Apr 10 14:23:19 2025 +0000

    fix info leak

diff --git a/README.md b/README.md
index d4e3b74..5c6457b 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials
 
 - username: bandit29
-- password: 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
+- password: xxxxxxxxxx
```

✅ Password: 

```
4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
```

---

✅ Level 29 → Level 30

🧠 Goal: There is a git repository at ssh://bandit29-git@localhost/home/bandit29-git/repo via the port 2220. The password for the user bandit29-git is the same as for the user bandit29.

Clone the repository and find the password for the next level.

```
bandit29@bandit:~$ mktemp -d
/tmp/tmp.fQlQ5NqX1x

bandit29@bandit:~$ cd /tmp/tmp.fQlQ5NqX1x

bandit29@bandit:/tmp/tmp.fQlQ5NqX1x$ cd repo
bandit29@bandit:/tmp/tmp.fQlQ5NqX1x/repo$ ls -al
total 16
drwxrwxr-x 3 bandit29 bandit29 4096 Jun  4 21:52 .
drwx------ 3 bandit29 bandit29 4096 Jun  4 21:52 ..
drwxrwxr-x 8 bandit29 bandit29 4096 Jun  4 21:52 .git
-rw-rw-r-- 1 bandit29 bandit29  131 Jun  4 21:52 README.md
bandit29@bandit:/tmp/tmp.fQlQ5NqX1x/repo$ cat README.md 
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>

bandit29@bandit:/tmp/tmp.fQlQ5NqX1x/repo$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev

bandit29@bandit:/tmp/tmp.fQlQ5NqX1x/repo$ git checkout dev
branch 'dev' set up to track 'origin/dev'.
Switched to a new branch 'dev'
bandit29@bandit:/tmp/tmp.fQlQ5NqX1x/repo$ ls -al
total 20
drwxrwxr-x 4 bandit29 bandit29 4096 Jun  4 21:56 .
drwx------ 3 bandit29 bandit29 4096 Jun  4 21:52 ..
drwxrwxr-x 2 bandit29 bandit29 4096 Jun  4 21:56 code
drwxrwxr-x 8 bandit29 bandit29 4096 Jun  4 21:56 .git
-rw-rw-r-- 1 bandit29 bandit29  134 Jun  4 21:56 README.md

bandit29@bandit:/tmp/tmp.fQlQ5NqX1x/repo$ cat README.md 
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
```

✅ Password: 

```
qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
```

---

✅ Level 30 → Level 31

🧠 Goal: There is a git repository at ssh://bandit30-git@localhost/home/bandit30-git/repo via the port 2220. The password for the user bandit30-git is the same as for the user bandit30.

Clone the repository and find the password for the next level.

```
git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo

bandit30@bandit:/tmp/tmp.cd6sjvU8zl$ cd repo
bandit30@bandit:/tmp/tmp.cd6sjvU8zl/repo$ ls -al
total 16
drwxrwxr-x 3 bandit30 bandit30 4096 Jun  4 21:58 .
drwx------ 3 bandit30 bandit30 4096 Jun  4 21:58 ..
drwxrwxr-x 8 bandit30 bandit30 4096 Jun  4 21:58 .git
-rw-rw-r-- 1 bandit30 bandit30   30 Jun  4 21:58 README.md

bandit30@bandit:/tmp/tmp.cd6sjvU8zl/repo$ cat README.md 
just an epmty file... muahaha

bandit30@bandit:/tmp/tmp.cd6sjvU8zl/repo$ git tag
secret

bandit30@bandit:/tmp/tmp.cd6sjvU8zl/repo$ git show secret
fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
```

✅ Password:

```
fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
```

---

✅ Level 31 → Level 32

🧠 Goal: There is a git repository at ssh://bandit31-git@localhost/home/bandit31-git/repo via the port 2220. The password for the user bandit31-git is the same as for the user bandit31.

Clone the repository and find the password for the next level.

```
$ git clone ssh://bandit31-git@localhost:2220/home/bandit31-git/repo

bandit31@bandit:/tmp/tmp.uhWeVauavQ$ cd repo
bandit31@bandit:/tmp/tmp.uhWeVauavQ/repo$ ls -al
total 20
drwxrwxr-x 3 bandit31 bandit31 4096 Jun  4 22:03 .
drwx------ 3 bandit31 bandit31 4096 Jun  4 22:02 ..
drwxrwxr-x 8 bandit31 bandit31 4096 Jun  4 22:03 .git
-rw-rw-r-- 1 bandit31 bandit31    6 Jun  4 22:03 .gitignore
-rw-rw-r-- 1 bandit31 bandit31  147 Jun  4 22:03 README.md


bandit31@bandit:/tmp/tmp.uhWeVauavQ/repo$ cat README.md 
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master

bandit31@bandit:/tmp/tmp.uhWeVauavQ/repo$ cat .gitignore 
*.txt

bandit31@bandit:/tmp/tmp.uhWeVauavQ/repo$ echo 'May I come in?' > key.txt
bandit31@bandit:/tmp/tmp.uhWeVauavQ/repo$ ls -al
total 24
drwxrwxr-x 3 bandit31 bandit31 4096 Jun  4 22:07 .
drwx------ 3 bandit31 bandit31 4096 Jun  4 22:02 ..
drwxrwxr-x 8 bandit31 bandit31 4096 Jun  4 22:06 .git
-rw-rw-r-- 1 bandit31 bandit31    6 Jun  4 22:03 .gitignore
-rw-rw-r-- 1 bandit31 bandit31   15 Jun  4 22:07 key.txt
-rw-rw-r-- 1 bandit31 bandit31  147 Jun  4 22:03 README.md

bandit31@bandit:/tmp/tmp.uhWeVauavQ/repo$ rm .gitignore
bandit31@bandit:/tmp/tmp.uhWeVauavQ/repo$ git add .
bandit31@bandit:/tmp/tmp.uhWeVauavQ/repo$ git commit -m "Added key.txt"
[master 2048060] Added key.txt
 2 files changed, 1 insertion(+), 1 deletion(-)
 delete mode 100644 .gitignore
 create mode 100644 key.txt
 
bandit31@bandit:/tmp/tmp.uhWeVauavQ/repo$ git push origin master
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit31/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit31/.ssh/known_hosts).
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

bandit31-git@localhost's password: 
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 2 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 289 bytes | 289.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: ### Attempting to validate files... ####
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
remote: Well done! Here is the password for the next level:
remote: 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K 
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
To ssh://localhost:2220/home/bandit31-git/repo
 ! [remote rejected] master -> master (pre-receive hook declined)
error: failed to push some refs to 'ssh://localhost:2220/home/bandit31-git/repo'
```

✅ Password: 

```
3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K
```

---

✅ Level 32 → Level 33

🧠 After all this git stuff, it’s time for another escape. Good luck!

```
WELCOME TO THE UPPERCASE SHELL
>> ls
sh: 1: LS: Permission denied
>> whoami
sh: 1: WHOAMI: Permission denied
>> man
sh: 1: MAN: Permission denied
>> strings
sh: 1: STRINGS: Permission denied

>> $0
$ ls -al
total 36
drwxr-xr-x  2 root     root      4096 Apr 10 14:23 .
drwxr-xr-x 70 root     root      4096 Apr 10 14:24 ..
-rw-r--r--  1 root     root       220 Mar 31  2024 .bash_logout
-rw-r--r--  1 root     root      3771 Mar 31  2024 .bashrc
-rw-r--r--  1 root     root       807 Mar 31  2024 .profile
-rwsr-x---  1 bandit33 bandit32 15140 Apr 10 14:23 uppershell
$ whoami
bandit33
$ pwd
/home/bandit32

$ cat /etc/bandit_pass/bandit33
tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0
```

✅ Password: 

```
tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0
```

---

## 🧠 Summary

This was a great crash course in:

- Linux CLI basics

- File permission handling

- Encoding/decoding

- Network interaction via nc and openssl

- Logical thinking & enumeration

---

## 📚 Resources

[Over The Wire: Bandit Challenges](https://overthewire.org/wargames/bandit/bandit0.html)

`man pages: man cat, man find, man grep, etc.`

## 👋 Follow my journey

If you liked this walkthrough, feel free to follow me on:

<a href="https://medium.com/@mauzware"><img src="https://img.shields.io/badge/Medium-style?style=for-the-badge&logo=medium&color=black" alt="Medium"/></a>
<a href="https://www.linkedin.com/in/filip-milenkovic-576a73228/"><img src="https://img.shields.io/badge/LinkedIn-style?style=for-the-badge&color=blue" alt="LinkedIn"/></a>
<a href="https://github.com/mauzware"><img src="https://img.shields.io/badge/GitHub-style?style=for-the-badge&logo=github&color=black" alt="GitHub"/></a>

## ⚠️ Disclaimer ⚠️

⚠️ The content in this repository is for educational and informational purposes only; the author holds no responsibility for misuse. 
Ensure proper authorization before use, act responsibly at your own risk, and comply with all legal and ethical guidelines. ⚠️

