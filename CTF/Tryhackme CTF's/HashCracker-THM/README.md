# [Crack The Hash | THM ]()

Can you complete the level 1 tasks by cracking the hashes?
This task increases the difficulty. All of the answers will be in the classic rock you password list.
You might have to start using hashcat here and not online tools. It might also be handy to look at some example hashes on hashcats page.


------------

# TOOLS :

**Hash Identify :** [Hash Analyzer](https://www.tunnelsup.com/hash-analyzer/)


**Hash Cracker :** [CrackStation](https://crackstation.net/) |  [HashKiller](https://hashkiller.io/listmanager)


**Hash BruteForce :** **John The Ripper** | **HashCat**

-----

# LEVEL 1 :


## HASH 1 :

**Hash Analyzer**

```bash
Hash type:	MD5 or MD4
```

**HashKiller**

```bash
48bb6e862e54f2a795ffc4e541caed4d:easy
```


## HASH 2 :

**Hash Analyzer**

```bash
Hash type:	SHA1 (or SHA 128)
```

**CrackStation**

```bash
CBFDAC6008F9CAB4083784CBD1874F76618D2A97	sha1	password123
```


## HASH 3 :

**Hash Analyzer**

```bash
Hash type:	SHA2-256
```

**CrackStation**

```bash
1C8BFE8F801D79745C4631D09FFF36C82AA37FC4CCE4FC946683D7B336B63032	sha256	letmein
```


## HASH 4 :

**Hash Analyzer**

```bash
Hash type:	bcrypt
```

**HashCat**

```bash
hashcat -m 3200 hash-3.txt rockyou.txt
bleh
```


## HASH 5 :

**Hash Analyzer**

```bash
Hash type:	MD5 or MD4
```

**CrackStation**

```bash
279412f945939ba78ce0758d3fd83daa	md4	Eternity22
```

---

# Level 2 :

## HASH 1 :

**Hash Analyzer**

```bash
Hash type:	SHA2-256
```

**CrackStation**

```bash
F09EDCB1FCEFC6DFB23DC3505A882655FF77375ED8AA2D1C13F640FCCC2D0C85	sha256	paule
```

## HASH 2 :

**Hash Analyzer**

```bash
Hash type:	MD5 or MD4
```

**CrackStation**

```bash
1DFECA0C002AE40B8619ECF94819CC1B	NTLM	n63umy8lkf4i
```

## HASH 3 :

**HashKiller Hash Identify**

```bash
Possible algorithms: sha512crypt $6$, SHA512 (Unix)
```

**HashCat**

```bash
hashcat -m 1800 “/$6/$aReallyHardSalt/$6WKUTqzq.UQQmrm0p/T7MPpMbGNnzXPMAXi4bJMl9be.cfi3/qxIf.hsGpS41BqMhSrHVXgMpdjS6xeKZAs02.” /../…/../rockyou.txt

waka99
```

## HASH 4 :

**Hash Analyzer**

```bash
Hash type:	SHA1 (or SHA 128)
```

**HashCat**

```bash
hashcat -m 110 e5d8870e5bdd26602cab8dbe07a942c8669e56d6:tryhackme ../../rockyou.txt

481616481616
```
