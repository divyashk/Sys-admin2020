# Networking



## Question - 2
I initially wanted to use the command
```whois students.iitmandi.ac.in```
but as it turns out, 'students.iitmandi.ac.in' is a subdomain and therefore whois might not work.

Therefore I tried the same command with 'iitmandi.ac.in' and it worked.
```
whois iitmandi.ac.in
```
The output was-
```
Domain Name: iitmandi.ac.in
Registry Domain ID: D4020030-IN
Registrar WHOIS Server:
Registrar URL: http://www.ernet.in
Updated Date: 2020-03-18T10:09:09Z
Creation Date: 2010-02-02T10:09:08Z
Registry Expiry Date: 2021-02-02T10:09:08Z
Registrar: ERNET India
Registrar IANA ID: 800068
```

It listed [ERNET India](http://www.ernet.in) as the registrar.

ERNET India has been appointed as an exclusive domain registrar for the education and research domains registering the domains under the .in registry from 2005. It registers Domains at second and third level for ac.in, edu.in and res.in zones.

One can also visit the site [whois.domaintools](https://whois.domaintools.com) and enter the sub-domain [students.iitmandi.ac.in] itself and will get the same result.

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


