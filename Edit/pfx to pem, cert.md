```bash
# Infos
openssl pkcs12 -in legacyy_dev_auth.pfx -info
# Convert Pem
openssl pkcs12 -in legacyy_dev_auth.pfx -nocerts -out key.pem -nodes
# Convert Cert
openssl pkcs12 -in legacyy_dev_auth.pfx -nokeys -out key.cert
```