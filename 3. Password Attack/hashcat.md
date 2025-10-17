```bash
# Basic
hashcat -m 1000 nelly.hash /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule --force

# cheatsheet
hashcat -m 0 md5 /PATH/TO/WORDLIST/<WORDLIST>
hashcat -m 100 sha-1 /PATH/TO/WORDLIST/<WORDLIST>
hashcat -m 1400 sha256 /PATH/TO/WORDLIST/<WORDLIST>
hashcat -m 3200 bcrypt /PATH/TO/WORDLIST/<WORDLIST>
hashcat -m 900 md4 /PATH/TO/WORDLIST/<WORDLIST>
hashcat -m 1000 ntlm /PATH/TO/WORDLIST/<WORDLIST>
hashcat -m 1800 sha512 /PATH/TO/WORDLIST/<WORDLIST>
hashcat -m 160 hmac-sha1 /PATH/TO/WORDLIST/<WORDLIST>
hashcat -a 0 -m 0 hash.txt SecLists/Passwords/xato-net-10-million-passwords-1000000.txt -O --force
hashcat -O -m 500 -a 3 -1 ?l -2 ?d -3 ?u  --force hash.txt ?3?3?1?1?1?1?2?3

```
