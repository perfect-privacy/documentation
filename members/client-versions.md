# Perfect Privacy Member's API: Client Versions
>Document version: **1.0**

Get the current version and checksum of the Perfect Privacy clients.

---

## URL
>**[Authentication](authenticate.md) needed!**

https://www.perfect-privacy.com/member/download/?file=clientVersions.json

## Client Version Object
Key     | Notice
------- | ----------------------------------------------------
sha1    | SHA1 checksum of the file
version | current version of the client (format: "n.n.n[.n]")

## Clients
You can download these clients: https://www.perfect-privacy.com/member/download/?file=CLIENT

Client                             | Notice
---------------------------------- | ----------------------------------------------------------------
Perfect-Privacy-VPN_Setup.exe      | Windows Client, stable
Perfect-Privacy-VPN_BETA_Setup.exe | Windows Client, BETA version - for testing / bug reporting only
CertInstaller.exe                  | Windows Certificate installer tool for IPSec
PP_TunnelManager_Setup.exe         | Windows SSH Client
PP_TunnelManager_XP_Setup.exe      | Windows XP SSH Client (won't be updated anymore - XP is dead)
PP_ConnectionManager.deb           | deprecated
PP_OpenVPNManager_Setup.exe        | deprecated

## Example
```json
{
    "CertInstaller.exe": {
        "sha1": "774d236baed4bc83902137ee914a46e648572893",
        "version": "1.0.0"
    },
    "PP_ConnectionManager.deb": {
        "sha1": "b61d95d9538cd206a74d57bf23e255c0a5a84dd9",
        "version": "0.0.1"
    },
    "PP_OpenVPNManager_Setup.exe": {
        "sha1": "19f6e26ea2b56d37f26814fb53ca63f8a2a92e71",
        "version": "0.0.1"
    },
    "PP_TunnelManager_Setup.exe": {
        "sha1": "ea84e919682b50e2f1327cd595e98b8b33474053",
        "version": "0.0.1"
    },
    "PP_TunnelManager_XP_Setup.exe": {
        "sha1": "d96b987ef82007e01edcef5b7b35f0e06b106b0a",
        "version": "0.0.1"
    },
    "Perfect-Privacy-VPN_BETA_Setup.exe": {
        "sha1": "12f5e7eea847c92926f57a06067e9de535ecaf96",
        "version": "1.7.3"
    },
    "Perfect-Privacy-VPN_Setup.exe": {
        "sha1": "96682096b6aed2d3d42f5628c293dd03146fe19c",
        "version": "1.6.69"
    }
}
```
