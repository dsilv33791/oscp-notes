# Enumeration

## Port Scan
```
nmap 10.x.x.x
nmap -sV -A --script vuln -p-
unicornscan
UDP Scan
SNMP Scan
```

### Port 21

anonymous login?

bruteforce?

use msf module to see if read/write access

### Port 80,443,8080,8888
```
nikto -host 10.x.x.x
gobuster -u http://10.11.1.71/ -w /usr/share/seclists/Discovery/Web_Content/common.txt -s '200,204,301,302,307,403,500' -e
dirbuster
bruteforce?
curl -i http://10.x.x.x/index.php
```
