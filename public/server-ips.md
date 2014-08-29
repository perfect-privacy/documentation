# Perfect Privacy Public API: Server IPs
>Document version: **1.0**

This API provides a tab separated list of all Perfect Privacy servers (FQDN) and comma separated list of related IP addresses in the following format:

```
<host><tab><ip>[,<ip>]*
```

Like the [SSH Fingerprints API](ssh-fingerprints.md) and the [Traffic API](traffic.md) you can use this list to determine all available servers.

To get the FQDN of the server *group*, just drop the number and you are ready to go: "server1.perfect-privacy.com" becomes "server.perfect-privacy.com"

---

## URL
https://www.perfect-privacy.com/api/serverips

## Example
```
server1.perfect-privacy.com	42.42.42.42,42.42.42.23,42.42.23.42
server2.perfect-privacy.com	42.42.23.23,42.23.42.42
....
```
