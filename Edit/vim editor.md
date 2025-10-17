유용한 vim editor 커맨드
```bash
# 중간 공백 없애기
:%s/[ ]*//g
# | 구분자를 개행으로 변경
:%s/|/\r/g
# 개행 없애기
:%s/\n//g
# 개행 사이 space 한칸
:%join
```
