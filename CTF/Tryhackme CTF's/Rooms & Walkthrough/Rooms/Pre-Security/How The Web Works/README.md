# [How The Web Works](https://tryhackme.com/room/httpindetail)

to become a better hacker it's vital to understand the underlying functions of the world wide web and what makes it work.

> Hamza 22/2/2022

---------

## PART 1 :

**What is DNS?**

DNS (Domain Name System) provides a simple way for us to communicate with devices on the internet without remembering complex numbers. Much like every house has a unique address for sending mail directly to it, every computer on the internet has its own unique address to communicate with it called an IP address. An IP address looks like the following 104.26.10.229, 4 sets of digits ranging from 0 - 255 separated by a period. When you want to visit a website, it's not exactly convenient to remember this complicated set of numbers, and that's where DNS can help. So instead of remembering 104.26.10.229, you can remember tryhackme.com instead.

![](https://assets.tryhackme.com/additional/dnsindetail/ip2domaindrawing.png)


- What does DNS stand for?

`Domain Name System`

![](https://assets.tryhackme.com/additional/dnsindetail/domain_levels.png)

**A Record**

These records resolve to IPv4 addresses, for example 104.26.10.229

**AAAA Record**

These records resolve to IPv6 addresses, for example 2606:4700:20::681a:be5

**CNAME Record**

These records resolve to another domain name, for example, TryHackMe's online shop has the subdomain name store.tryhackme.com which returns a CNAME record shops.shopify.com. Another DNS request would then be made to shops.shopify.com to work out the IP address.

**MX Record**

These records resolve to the address of the servers that handle the email for the domain you are querying, for example an MX record response for tryhackme.com would look something like alt1.aspmx.l.google.com. These records also come with a priority flag. This tells the client in which order to try the servers, this is perfect for if the main server goes down and email needs to be sent to a backup server.

**TXT Record**

TXT records are free text fields where any text-based data can be stored. TXT records have multiple uses, but some common ones can be to list servers that have the authority to send an email on behalf of the domain (this can help in the battle against spam and spoofed email). They can also be used to verify ownership of the domain name when signing up for third party services.

- What is the maximum length of a subdomain?

`63`

- Which of the following characters cannot be used in a subdomain ( 3 b _ - )?

`_`

- What is the maximum length of a domain name?

`253`

- What type of TLD is .co.uk?

`ccTLD`

- What type of record would be used to advise where to send email?

`MX`

- What type of record handles IPv6 addresses?

`AAAA`

- What field specifies how long a DNS record should be cached for?

`TTL`

- What type of DNS Server is usually provided by your ISP?

`recursive`

- What type of server holds all the records for a domain?

`authoritative`


## PRACTICE

- What is the CNAME of shop.website.thm?

```bash
$ nslookup --type=CNAME shop.website.thm
```

- What is the value of the TXT record of website.thm?

```bash
$ nslookup --type=TXT website.thm
```

- What is the numerical priority value for the MX record?

```bash
$ nslookup --type=MX website.thm
```

- What is the IP address for the A record of www.website.thm?

```bash
$ nslookup --type=A website.thm
```

---------------------

## PART 2

**What is HTTP? (HyperText Transfer Protocol)**

HTTP is what's used whenever you view a website, developed by Tim Berners-Lee and his team between 1989-1991. HTTP is the set of rules used for communicating with web servers for the transmitting of webpage data, whether that is HTML, Images, Videos, etc.

**What is HTTPS? (HyperText Transfer Protocol Secure)**

HTTPS is the secure version of HTTP. HTTPS data is encrypted so it not only stops people from seeing the data you are receiving and sending, but it also gives you assurances that you're talking to the correct web server and not something impersonating it.

- What does HTTP stand for?

`HyperText Transfer Protocol`

- What does the S in HTTPS stand for?

`secure`

- On the mock webpage on the right there is an issue, once you've found it, click on it. What is the challenge flag?

![](https://cdn.arstechnica.net/wp-content/uploads/2017/01/example-dot-com-control-center-600x417.png)


- What HTTP protocol is being used in the above example?

```html

HTTP/1.1 200 OK
Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:03 GMT
Content-Type: text/html
Content-Length: 98

<html>
<head>
    <title>TryHackMe</title>
</head>
<body>
    Welcome To TryHackMe.com
</body>
</html>

```

`HTTP/1.1`



- What response header tells the browser how much data to expect?

`Content-Length`

-----

**GET Request**

This is used for getting information from a web server.

**POST Request**

This is used for submitting data to the web server and potentially creating new records

**PUT Request**

This is used for submitting data to a web server to update information

**DELETE Request**

This is used for deleting information/records from a web server.

-------

- What method would be used to create a new user account?

`POST`

- What method would be used to update your email address?

`PUT`

- What method would be used to remove a picture you've uploaded to your account?

`DELETE`

- What method would be used to view a news article?

`GET`


## [HTTP CODES](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)


- What response code might you receive if you've created a new user or blog post article?

`201`

- What response code might you receive if you've tried to access a page that doesn't exist?

`404`

- What response code might you receive if the web server cannot access its database and the application crashes?

`503`

- What response code might you receive if you try to edit your profile without logging in first?

`401`

- What header tells the web server what browser is being used?

`User-Agent`

- What header tells the browser what type of data is being returned?

`Content-Type`

- What header tells the web server which website is being requested?

`Host`

-  Which header is used to save cookies to your computer?

`Set-Cookie`

- Make a GET request to /roomom

```bash
curl $ip/roomom | grep "flag"
```

- Make a GET request to /blog and using the gear icon set the id parameter to 1 in the URL field

```bash
curl -X GET -d id=1
```

- Make a DELETE request to /user/1/1

```bash
curl -X DELETE -d id=1
```

- Make a PUT request to /user/2 with the username parameter set to admin

```bash
curl -X PUT -d id=2
```

- POST the username of thm and a password of letmein to /login

```bash
curl -X POST -d "username=x password=x"
```

