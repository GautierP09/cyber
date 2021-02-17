# CC: Pen Testing

## Section 1: Network Utilities

### nmap

#### Questions about Nmap

* Nmap= network mapper
* Specify port: -p
* Ping scan: -sn / -sP
* UDP scan: -sU
* Run default script: -sC
* Aggresive mode: -A
* OS detection: -o

#### Scanning of the vm

```
nmap -A -p- 10.10.26.251
```

Output:
```
Starting Nmap 7.91 ( https://nmap.org ) at 2021-02-17 04:54 EST
Nmap scan report for 10.10.26.251
Host is up (0.026s latency).
Not shown: 65534 closed ports
PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 18.97 seconds
```
Comments:
+ One port opened: 80 http
- Service running: Apache
- Version of the service: 2.4.18

### Netcat

#### NetCat commands

* Listen for connections: -l
* Enable verbose mode: -v
* Specify a port: -p
* Execute a program after connection: -e
* Connect to UDP ports: -u


Can reduce all this command with:
```
nc -nlvp 9999
```

## Section 2: Web Enumeration

### Gobuster

#### Gobuster commands

* Specify directory bruteforcing mode: dir
* Specify dns bruteforcing mode: dns
* Set extensions: -x
* Set a worlist: -w
* Set Username: -U
* Set Password: -P
* Set which status codes gobuster will interpret as valid: -s
* Skip ssl certificate verification: -k
* Specify a User-Agent: -a
* Specify a HTTP header: -H
* Set the URL to bruteforce: -u

#### Example with the vm

Command:
```
gobuster dir -u http://10.10.162.37 -w /usr/share/wordlists/dirb/common.txt
```

Output:
```
===============================================================
2021/02/17 05:30:18 Starting gobuster
===============================================================
/.hta (Status: 403)
/.htaccess (Status: 403)
/.htpasswd (Status: 403)
/index.html (Status: 200)
/secret (Status: 301)
/server-status (Status: 403)
===============================================================
2021/02/17 05:30:31 Finished
===============================================================
```

Comments:

* One secret file: /secret => empty page in browser

Command:
```
gobuster dir -u http://10.10.162.37 -w /usr/share/wordlists/dirb/common.txt -x xxa
```

Output:
```
===============================================================
2021/02/17 05:32:24 Starting gobuster
===============================================================
/.hta (Status: 403)
/.hta.xxa (Status: 403)
/.htaccess (Status: 403)
/.htaccess.xxa (Status: 403)
/.htpasswd (Status: 403)
/.htpasswd.xxa (Status: 403)
/index.html (Status: 200)
/password.xxa (Status: 200)
/secret (Status: 301)
/server-status (Status: 403)
===============================================================
2021/02/17 05:32:49 Finished
===============================================================
```

Comments:

* One secret file: /password.xxa => in browser, we find : Easter Egg!


### Nikto

#### Nikto commands

* Specify a host: -h
* SSL: -ssl / -nossl
* Specify auth: -id
* Select which plugin to use: -Plugins
* Plugin to enumerate apache users: apacheusers
* Update the plugin list: -update
* List all possible plugins: -list-plugins
