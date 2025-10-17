주요 활용법
```bash
# id:hash:password -> id:password 추
cat user.hash.pw.txt | awk -F: '{print $1":"$3}'
```

ID:PW 에서 PW값만 추출
```bash
awk -F':' '{print $2}' original.txt > hashes.txt
```

lsass NT 추출 → awk 로 해시만 추려내기 → 중복 제거 예시
```bash
cat lsass.txt | grep "NT" | awk -F: '{print $2}' | sort | uniq > ntlm.hash
```


