# [Linux Fundamentals](https://tryhackme.com/room/linuxfundamentalspart1)

It's fair to say that Linux is a lot more intimidating to approach than Operating System's (OSs) such as Windows. Both variants have their own advantages and disadvantages. For example, Linux is considerably much more lightweight and you'd be surprised to know that there's a good chance you've used Linux in some form or another every day! Linux powers things such as:
* Websites that you visit
* Car entertainment/control panels
* Point of Sale (PoS) systems such as checkout tills and registers in shops
* Critical infrastructures such as traffic light controllers or industrial sensors

> Hamza , 27/2/22

-----------


**& :** This operator allows you to run commands **in the background** of your terminal.

**&& :** This operator allows you to **combine multiple commands together in one line** of your terminal.

**> :** This operator is a **redirector**.

**>> :** Appends the output rather than replacing **(meaning nothing is overwritten)**.

-----
## PART 1 :

* Research: What year was the **first release** of a Linux operating system? 

`1991`

* If we wanted to **output** the text "TryHackMe", what would our command be?

`echo TryHackMe`

* What is the **username** of who you're **logged** in as on your deployed Linux machine?

```bash
$ whoami
tryhackme
```

* On the Linux machine that you deploy, how many **folders** are there?


```bash
$ ls
folder1 folder2 folder3 folder4
```

* Which directory **contains** a file? 
```bash
$ cd folder4
$ ls
file
```

* What is the **contents** of this file?

```bash
$ cat file
hello world!
```

* What is the **path**?

```bash
$ pwd
/home/tryhackme/folder4
````

* Use **grep** on **"access.log"** to find the flag that has a prefix of **"THM"**. What is the flag?

```bash
$ grep "THM" access.log
```

* If we wanted to run a **command in the background**, what operator would we want to use? 

```bash
$ command & command
```

* If I wanted to **replace** the contents of a file named "passwords" with the word "password123", what would my command be?


```bash
$ echo password123 > passwords
```

* Now if I wanted to **add** "tryhackme" to this file named "passwords" but also keep "passwords123", what would my command be

```bash
$ echo tryhackme >> passwords
```



------------------------

## PART 2 :

* Manual of **listing**

```bash
$ man ls
$ ls -h
```



* What directional **arrow key** would we use to navigate down the manual page?

`down`

* What flag would we use to display the output in a **"human-readable"** way?

`-h`

* How would you **create** the file named "newnote"?

```bash
$ touch newnote
```

* On the deployable machine, what is the file **type of "unknown1"** in "tryhackme's" home directory? 

```bash
$ file unknown1
ASCII text
```

* How would we **move** the file "myfile" to the directory "myfolder" 

```bash
$ mv myfile myfolder
```

* What are the **contents** of this file?
```bash
$ cat myfile
```

* On the deployable machine, who is **the owner** of "important"?
```bash
$ ls -l
user2 important
```

* What would the command be to **switch** to the user "user2"?
```bash
$ su user2
```

* **Output** the contents of "important", what is the flag?
```bash
$ cat important
```

* What is the directory path that would we expect **logs to be stored in**?

`/var/log`

* What root directory is similar to how RAM on a computer works?

`/tmp`

* Name the home directory of the root user 

`/root`

-----------

## PART 3 :

* **Edit** "task3" located in "tryhackme"'s home directory using Nano. What is the flag?

```bash
$ nano tryhackme/task3
```

* use Python 3's **"HTTPServer"**

```bash
$ python3 -m http.server
```

* **Download** the file http://MACHINE_IP:8000/.flag.txt onto the TryHackMe AttackBox
```bash
$ wget http://127.0.0.1:8000/file
```

- If we were to launch a process where the **previous ID was "300"**, what would the ID of this new process be?

`301`

- If we wanted to cleanly kill a process, what signal would we send it?

```bash
$ SIGTERM myProcess
```

- Locate the **process** that is running on the deployed instance (MACHINE_IP). What flag is given?


```bash
$ ps aux
```

- What command would we use to **stop** the service "myservice"?

```bash
$ systemctl stop myservice
```

- What command would we use to start the same service on the boot-up of the system?

```bash
$ systemctl enable myservice
```
- What command would we use to bring a previously **backgrounded process** back to the foreground?
```bash
$ fg
```
- When will the crontab on the **deployed instance (MACHINE_IP)** run?

`@reboot`

- What is the **IP address of the user who visited the site**?

```bash
$ cd var/log/apache2
$ ls
$ cat access.log
10.9.x.x
```

- What file did they access?

`catsanddogs.jpg`




