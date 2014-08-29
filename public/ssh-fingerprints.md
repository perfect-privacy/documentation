# Perfect Privacy Public API: SSH Fingerprints
>Document version: **1.0**

This API provides a tab separated list of all Perfect Privacy servers (FQDN) and SSH Fingerprints (RSA/DSA) in the following format:

```
<host><tab><fingerprint>
```

Like the [Server IPs API](server-ips.md) and the [Traffic API](traffic.md) you can use this list to determine all available servers.

To get the FQDN of the server *group*, just drop the number and you are ready to go: "server1.perfect-privacy.com" becomes "server.perfect-privacy.com"


## URLs
Purpose          | URL
---------------- | ---------------------------------------------------------
RSA Fingerprints | https://www.perfect-privacy.com/api/ssh-fingerprints-rsa
DSA Fingerprints | https://www.perfect-privacy.com/api/ssh-fingerprints-dsa

## Example
```
server1.perfect-privacy.com	00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00
server2.perfect-privacy.com	ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff
...
```
