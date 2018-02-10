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
```
anonymous login?
bruteforce?
use msf module to see if read/write access
OS version
Other software you can find on the machine (Prog Files, yum.log, /bin)
password files
DLLs for msfpescan / BOF targets
Do you have UPLOAD potential?
Can you trigger execution of uploads?
Swap binaries?
Vulnerabilities in version / RCE / #WINNING?-D

```

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

# Other possibilities
Heartbleed / CRIME / Other similar attacks
Read the actual SSL CERT to:
find out potential correct vhost to GET
is the clock skewed
any names that could be usernames for bruteforce/guessing.
```
### UDP 161 (snmp)

```
snmp-check
snmpwalk
onesixtyone
```

### UDP 69 (tftp)

```
# read/write access?```
```

### SMB 139/445
```
enum4linux -a 10.x.x.x
searchsploit version
smbclient -L 10.x.x.x

Mount shares
mount -t cifs -o user=USERNAME,sec=ntlm,dir_mode=0077 "//10.x.x.x/share_name" /mnt/share_name
```

### EMAIL Protocols
```
Email - 25, 110/995 or 143/993
SMTP, POP3(s) and IMAP(s) are good for enumerating users.
searchsploit
```
