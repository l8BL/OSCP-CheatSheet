---
sticker: lucide//database
---
## Database version

### Oracle
```
SELECT banner FROM v$version
SELECT version FROM v$instance
```

### MSSQL
```
SELECT @@version
```

### PostgreSQL
```
SELECT version()
```

### MySQL
```
SELECT @@version
```



