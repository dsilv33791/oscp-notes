# Passwords

## Windows Tools
### fgdump.exe
Injects dll code into lsass process with hash cracking code.

Dumps Windows Password Hashes (requires Administrative Privs)

### wce.exe (Windows Credential Editor)
wce64.exe for x64

wce.exe for x86


### pwdump.exe

Injects dll code into lsass process with hash cracking code.

Dumps Windows Password Hashes (requires Administrative Privs)

### Crunch
See man page for examples

### Passing the Hash
Capture NT/LM hash

```
export SMBHASH=<NT/LMHASH>
pth-winexe -U administrator% //10.x.x.x cmd
```

### Password Profiling
```
cewl www.google.com -m 6 -w /root/Desktop/google-words.txt
```

John tricks

add 2 numbers to the end of every password

```
$[0-9]$[0-90]  # (/etc/john/john.conf)
john --wordlist=/root/Desktop/google-words.txt --rules --stdout | > /root/Desktop/mangled.txt
```

## Online Attacks

### Medusa

### Ncrack

### Hydra

## Offline Attacks

### Password Hashes

### Cracking Hashes

### LM/NTLM
