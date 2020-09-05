# Networking



## Question - 2
I initially used the 'whois' command in linux

```whois students.iitmandi.ac.in```

 but it returned an unsual 'No data found'.
So I went onto the site [whois.domaintools](https://whois.domaintools.com) and entered the domain [students.iitmandi.ac.in] there.

It listed [ERNET India](http://www.ernet.in) as the registrar after a successful captcha.

## Question - 3
I used the command nmap with flag '-p' to scan all the ports from 1-2000

```nmap -p 1-2000 iitmandi.co.in```

It returned the following as open.
```
21/tcp   open     ftp
22/tcp   open     ssh
53/tcp   open     domain
80/tcp   open     http
443/tcp  open     https
554/tcp  open     rtsp
1723/tcp open     pptp

```


