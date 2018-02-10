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
gobuster -u http://10.x.x.x/ -w /usr/share/seclists/Discovery/Web_Content/common.txt -s '200,204,301,302,307,403,500' -e
gobuster -u http://10.x.x.x/ -w /usr/share/seclists/Discovery/Web_Content/Top1000-RobotsDisallowed.txt
gobuster -u http://10.x.x.x/ -w /usr/share/seclists/Discovery/Web_Content/common.txt
dirbuster
bruteforce?
curl -i http://10.x.x.x/index.php
curl -i http://10.x.x.x/robots.txt
```
## UDP 161 (snmp)

```
snmp-check
snmpwalk
onesixtyone
```

## UDP 69 (tftp)

```
# read/write access?```
```

## EMAIL Protocols
```
Email - 25, 110/995 or 143/993
SMTP, POP3(s) and IMAP(s) are good for enumerating users.
searchsploit
```
