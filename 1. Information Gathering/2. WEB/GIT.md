### .git download
```bash

# git recursive down 
wget -r http://10.10.11.177/dev/.git 
wget --mirror -I .git http://192.168.218.144/.git/

```
### git dumper
```sh
git-dumper <URL_TO_DUMP>/.git <DIRNAME_TO_SAVE>
```

### GIT
```bash
# git 파일 되돌리기
git restore ./
# git 로그와 커밋해시
git log
# git 로그 통계
git log --stat
# 최근 2 커밋 코드 디핑
git log -p -2
# git 커밋 내역 상세
git show <commit_hash>
```
