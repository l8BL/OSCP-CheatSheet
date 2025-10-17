```bash
# .kdbx to hash
keepass2john <INFILE> > <OUTFILE>
# 유효한 값만 추출
keepass2john CrackThis.kdb | grep -o "$keepass$.*" >  CrackThis.hash
# id_rsa to hash
ssh2john <INFILE> > <OUTFILE>
# zip to hash
# check zip info by "7z x <file_name>"
zip2john <INFILE> > <OUTFILE>
# pfx to hash
pfx2john <INFILE> > <OUTFILE>
# psafe3 to hash
pwsafe2john <INFILE> > <OUTFILE>
# Basic Format
john <FILE> --wordlist=/PATH/TO/WORDLIST/<WORDLIST>
# crypt hash crack
john <FILE> --wordlist=/PATH/TO/WORDLIST/<WORDLIST> --format=crypt
# crack password with variation
john <FILE> --rules --wordlist=/PATH/TO/WORDLIST/<WORDLIST>
# print cracked password
john --show <FILE>
```
