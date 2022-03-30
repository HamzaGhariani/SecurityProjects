# H4mS3c Penetration Testing Methodologies 

> Hamza Ghariani , 30/3/2022


****

## Information Gathering

Collecting as much **Publically** accessible information about a target.

* Whois Lookup
  
  ```bash
  whois url/IP
  ```

* View Source Code `ctrl` + `u`
* Email Adresses `Contact@mysite.com`
* Website Paths `/path`
* Rebots file `Robots.txt`
* Sitemap `Sitemap.xml`
* Favicon Framework `favico.ico`

```bash
curl website.com/favico.ico | md5sum
```
* HTTP Headers
```bash
curl url -v
```
- Framework & CMS
  
  * Source Code
  *  [WhatCMS](https://whatcms.org/)


# Enumeration

Discovering applications and services running on the systems , **may be potentially vulnerable.**

* `DNS` Lookup
  
  ```bash
  dnsenum url
  ```

* Open `PORTS`
    ```bash
    nmap -sC -sV url
    ```
* Directories  `PATHS`
  
  ```bash
  gobuster dir -u url -w file.txt
  ```
  ```bash
  gobuster dir -u url -w file.txt -x html,php,txt
  ```
- Exploits Scan
  
  * `WordPress`
  ```bash
  wpscan --url url
  ```
  - `SQLi`
    * Link Scan
  ```bash
  sqlmap -u url
  ```
    * Request Scan
    ```bash
    sqlmap -r file.req
    ```

  * General
  ```bash
  nikto --host url
  ```

# Exploitation

Use of public exploits or exploiting application logic.

* Public Exploits
  ```bash
  searchsploit cms/framework
  ```
- Logic Explois
  * HTML
  * PHP
  * Javascript
  * Python
  * Java

# Privilege Escalation

Attempt to expand your access to a system. You can escalate horizontally and vertically, where horizontally is accessing another account of the same permission group (i.e. another user), whereas vertically is that of another permission group (i.e. an administrator).

* Linux
* Windows

--------

