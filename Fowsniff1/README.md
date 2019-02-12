## Fowsniff 1

* Author: berzerk0
* Web page: [https://www.peerlyst.com/posts/ctf-virtual-machines-created-by-the-peerlyst-community-hack-these-peerlyst](https://www.peerlyst.com/posts/ctf-virtual-machines-created-by-the-peerlyst-community-hack-these-peerlyst)
* Download: [vulnhub](https://www.vulnhub.com/entry/fowsniff-1,262/)

### Solution:

Local network scan:

```shell
$ nmap -sn 192.168.1.0-

...
Nmap scan report for 192.168.1.107
Host is up (0.0023s latency).
...
```

And after that target scan:

```shell
$ nmap -A -p- 192.168.1.107

Starting Nmap 7.60 ( https://nmap.org ) at 2019-02-12 20:20 CET
Nmap scan report for 192.168.1.107
Host is up (0.00044s latency).
Not shown: 65531 closed ports
PORT    STATE SERVICE VERSION
22/tcp  open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.4 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 90:35:66:f4:c6:d2:95:12:1b:e8:cd:de:aa:4e:03:23 (RSA)
|   256 53:9d:23:67:34:cf:0a:d5:5a:9a:11:74:bd:fd:de:71 (ECDSA)
|_  256 a2:8f:db:ae:9e:3d:c9:e6:a9:ca:03:b1:d7:1b:66:83 (EdDSA)
80/tcp  open  http    Apache httpd 2.4.18 ((Ubuntu))
| http-robots.txt: 1 disallowed entry 
|_/
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Fowsniff Corp - Delivering Solutions
110/tcp open  pop3    Dovecot pop3d
|_pop3-capabilities: PIPELINING RESP-CODES USER CAPA SASL(PLAIN) TOP UIDL AUTH-RESP-CODE
143/tcp open  imap    Dovecot imapd
|_imap-capabilities: more have ENABLE SASL-IR capabilities ID OK LOGIN-REFERRALS listed post-login AUTH=PLAINA0001 IMAP4rev1 LITERAL+ Pre-login IDLE
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.22 seconds
```

You can see here that `pop3` and `imap` services are running as well as some `http` server.<br>
After entering the site, `Fowsniff Corp` company website appears.<br>

![fowsniff website](img/fowsniff_website.png)

The website is `Out Of Service`, and the description shows that Fowsniff has recently been hacked and the company employees data was leaked.<br>
The description also states that the company's Twitter account `@fowsniffcorp` has been hijacked and the attacker has shared some information there.<br>

![fowsniff twitter](img/fowsniff_twitter.png)

On Twitter you can actually find a link to pastebin which judging by the description contains passwords dump<br>

![fowsniff pastebin](img/fowsniff_pastebin.png)

Additionally there is an information, that `pop3 server` is open.

