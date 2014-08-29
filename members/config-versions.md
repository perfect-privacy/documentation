# Perfect Privacy Member's API: Config Versions
>Document version: **1.0**

Get the version (timestamp) and checksum of the latest OpenVPN, IPSec and SSH configurations.

---

## URL
>**[Authentication](authenticate.md) needed!**

https://www.perfect-privacy.com/member/download/?file=configVersions.json

## Config Version Object
Key     | Notice
------- | ----------------------------------------------------
sha1    | SHA1 checksum of the file
version | timestamp of the time the config has been generated


## Files
You can download these files: https://www.perfect-privacy.com/member/download/?file=FILE

File                               | Purpose
---------------------------------- | -----------------------------------
VPNManager_configbundle.tar.gz     | configs for Perfect Privacy VPN windows client, with additional up and down scripts and server information in the comments, tar.gz
VPNManager_configbundle.zip        | see above, ZIP
ppConfig_linux.tar.gz              | OpenVPN configs for Linux, UDP, tar.gz
ppConfig_linux.zip                 | OpenVPN configs for Linux, UDP, ZIP
ppConfig_linux_single.tar.gz       | OpenVPN configs for Linux, UDP, single, tar.gz
ppConfig_linux_single.zip          | OpenVPN configs for Linux, UDP, single, ZIP
ppConfig_linux_tcp.tar.gz          | OpenVPN configs for Linux, TCP, tar.gz
ppConfig_linux_tcp.zip             | OpenVPN configs for Linux, TCP, ZIP
ppConfig_linux_tcp_single.tar.gz   | OpenVPN configs for Linux, TCP, single, tar.gz
ppConfig_linux_tcp_single.zip      | OpenVPN configs for Linux, TCP, single, ZIP
ppConfig_mac.tar.gz                | OpenVPN configs for Mac OS X, UDP, tar.gz
ppConfig_mac.zip                   | OpenVPN configs for Mac OS X, UDP, ZIP
ppConfig_mac_single.tar.gz         | OpenVPN configs for Mac OS X, UDP, single, tar.gz
ppConfig_mac_single.zip            | OpenVPN configs for Mac OS X, UDP, single, ZIP
ppConfig_mac_tcp.tar.gz            | OpenVPN configs for Mac OS X, TCP, tar.gz
ppConfig_mac_tcp.zip               | OpenVPN configs for Mac OS X, TCP, ZIP
ppConfig_mac_tcp_single.tar.gz     | OpenVPN configs for Mac OS X, TCP, single, tar.gz
ppConfig_mac_tcp_single.zip        | OpenVPN configs for Mac OS X, TCP, single, ZIP
ppConfig.tblk.tar.gz               | OpenVPN configs for Tunnelblick (Mac Client), UDP, tar.gz
ppConfig.tblk.zip                  | OpenVPN configs for Tunnelblick (Mac Client), UDP, ZIP
ppConfig_single.tblk.tar.gz        | OpenVPN configs for Tunnelblick (Mac Client), UDP, single, tar.gz
ppConfig_single.tblk.zip           | OpenVPN configs for Tunnelblick (Mac Client), UDP, single, ZIP
ppConfig_tcp.tblk.tar.gz           | OpenVPN configs for Tunnelblick (Mac Client), TCP, tar.gz
ppConfig_tcp.tblk.zip              | OpenVPN configs for Tunnelblick (Mac Client), TCP, ZIP
ppConfig_tcp_single.tblk.tar.gz    | OpenVPN configs for Tunnelblick (Mac Client), TCP, single, tar.gz
ppConfig_tcp_single.tblk.zip       | OpenVPN configs for Tunnelblick (Mac Client), TCP, single, ZIP
ppConfig_mobile_tcp.tar.gz         | OpenVPN configs for mobile clients (Android and iOS), TCP, tar.gz (embedded certs and keys)
ppConfig_mobile_tcp.zip            | OpenVPN configs for mobile clients (Android and iOS), TCP, ZIP (embedded certs and keys)
ppConfig_mobile_tcp_single.tar.gz  | OpenVPN configs for mobile clients (Android and iOS), TCP, single, tar.gz (embedded certs and keys)
ppConfig_mobile_tcp_single.zip     | OpenVPN configs for mobile clients (Android and iOS), TCP, single, ZIP (embedded certs and keys)
ppConfig_win.tar.gz                | OpenVPN configs for Windows, UDP, tar.gz
ppConfig_win.zip                   | OpenVPN configs for Windows, UDP, ZIP
ppConfig_win_single.tar.gz         | OpenVPN configs for Windows, UDP, single, tar.gz
ppConfig_win_single.zip            | OpenVPN configs for Windows, UDP, single, ZIP
ppConfig_win_tcp.tar.gz            | OpenVPN configs for Windows, TCP, tar.gz
ppConfig_win_tcp.zip               | OpenVPN configs for Windows, TCP, ZIP
ppConfig_win_tcp_single.tar.gz     | OpenVPN configs for Windows, TCP, single, tar.gz
ppConfig_win_tcp_single.zip        | OpenVPN configs for Windows, TCP, single, ZIP
ppIPSec_Certs.tar.gz               | IPSec certificates
ppIPSec_Certs.zip                  | IPSec certificates
ipsec_psks.csv                     | IPSec PSKs, csv
ipsec_psks.json                    | IPSec PSKs, json
servergroups.json                  | Server Groups, see [Server Groups documentation](server-groups.md)
ssh_fingerprints.csv               | SSH fingerprints by server group, csv, for a public list, see [SSH Fingerprints documentation](../public/ssh-fingerprints.md)
ssh_fingerprints.json              | SSH fingerprints by server group, json

## Example
```json
{
    "VPNManager_configbundle.tar.gz": {
        "sha1": "6f1e497b6b4bfbbc14eda0b1998696740b6a73a1",
        "version": 1408462907
    },
    "VPNManager_configbundle.zip": {
        "sha1": "d4e6ebc89502b5a23cbac61cfb7bf8067372d5d5",
        "version": 1408462907
    },
    "ipsec_psks.csv": {
        "sha1": "eab653e0d3511747cacb78785107a3161829a8c3",
        "version": 1408462907
    },
    "ipsec_psks.json": {
        "sha1": "3342477492ba904e875210f9ab3bcde37200b707",
        "version": 1408462907
    },
    "ppConfig.tblk.tar.gz": {
        "sha1": "21d1d28b485614b5bf9e8651cb512d4aeeeba898",
        "version": 1408462907
    },
    "ppConfig.tblk.zip": {
        "sha1": "b8c88b010fc35eee26fec6a23f1317cc4b5404ba",
        "version": 1408462907
    },
    "ppConfig_linux.tar.gz": {
        "sha1": "82045382954fddc4027b6d6a86e99a484ca99538",
        "version": 1408462907
    },
    "ppConfig_linux.zip": {
        "sha1": "b22ce9d30008f101036e32b03f98053f171dfab1",
        "version": 1408462907
    },
    "ppConfig_linux_single.tar.gz": {
        "sha1": "b186a14b9719bc6b32f83e98607619095527b609",
        "version": 1408462907
    },
    "ppConfig_linux_single.zip": {
        "sha1": "977303b11f399f464de9e00982d9d0242f61d684",
        "version": 1408462907
    },
    "ppConfig_linux_tcp.tar.gz": {
        "sha1": "8ab5f7e54edb91caa5431c02a0076e9f792f8cb7",
        "version": 1408462907
    },
    "ppConfig_linux_tcp.zip": {
        "sha1": "a00eb7b32f2accf17d01dbc48d9e7b99c5c3eed0",
        "version": 1408462907
    },
    "ppConfig_linux_tcp_single.tar.gz": {
        "sha1": "e47731d2bffe91a9adfe5c50d22cb5909c12fc4c",
        "version": 1408462907
    },
    "ppConfig_linux_tcp_single.zip": {
        "sha1": "73854d544bb98f2542602b1c333b31c38dbbb500",
        "version": 1408462907
    },
    "ppConfig_mac.tar.gz": {
        "sha1": "01679cb412fbe755d4826e0a02aeb4b4f03a2a3e",
        "version": 1408462907
    },
    "ppConfig_mac.zip": {
        "sha1": "6ac11fe53c1299b366c279c714ad66a989bbff46",
        "version": 1408462907
    },
    "ppConfig_mac_single.tar.gz": {
        "sha1": "72996f47572b86ed3d7d0b5a63708aad8dcdd9b3",
        "version": 1408462907
    },
    "ppConfig_mac_single.zip": {
        "sha1": "7499691aeafd0d16c2aa1cf944719bb24b29e87c",
        "version": 1408462907
    },
    "ppConfig_mac_tcp.tar.gz": {
        "sha1": "c6b99c0c9b37076a04ad0c797bcc02965a02235f",
        "version": 1408462907
    },
    "ppConfig_mac_tcp.zip": {
        "sha1": "536c4ac0902aa22e3ebaa578274994575c14f710",
        "version": 1408462907
    },
    "ppConfig_mac_tcp_single.tar.gz": {
        "sha1": "6a73803ad0ece8eaf7520364fd4d76511dc631c0",
        "version": 1408462907
    },
    "ppConfig_mac_tcp_single.zip": {
        "sha1": "d01ef69ecebf0263f8227b809fe424c672cafc2c",
        "version": 1408462907
    },
    "ppConfig_mobile_tcp.tar.gz": {
        "sha1": "e045c526a34c591e3131172e1b235bcdef4115e1",
        "version": 1408462907
    },
    "ppConfig_mobile_tcp.zip": {
        "sha1": "6949964cd9f4055698b4a23c08828f5cd2e89d22",
        "version": 1408462907
    },
    "ppConfig_mobile_tcp_single.tar.gz": {
        "sha1": "0cc65a3bc73ecc7d7e4d68fe5f2f63e20112d3bc",
        "version": 1408462907
    },
    "ppConfig_mobile_tcp_single.zip": {
        "sha1": "c697199acde1efe49be6271e2ff6f904dd04d68d",
        "version": 1408462907
    },
    "ppConfig_single.tblk.tar.gz": {
        "sha1": "dc96071cefed01df0f54f2f853472e43bf1585aa",
        "version": 1408462907
    },
    "ppConfig_single.tblk.zip": {
        "sha1": "0099b30f744c86f1333e3f5075670e4a857586fa",
        "version": 1408462907
    },
    "ppConfig_tcp.tblk.tar.gz": {
        "sha1": "920828aec48e1f30bf45e615baba1dcfd7c58f3c",
        "version": 1408462907
    },
    "ppConfig_tcp.tblk.zip": {
        "sha1": "99488a3cf10de455b089963daf00861bf89c9d95",
        "version": 1408462907
    },
    "ppConfig_tcp_single.tblk.tar.gz": {
        "sha1": "490d7c2f2ebd9f1d2cfb03390033f6921c240b0e",
        "version": 1408462907
    },
    "ppConfig_tcp_single.tblk.zip": {
        "sha1": "506f82b037a5b1b8b79f6b6e61b5efe8eb61bc71",
        "version": 1408462907
    },
    "ppConfig_win.tar.gz": {
        "sha1": "f117f88cc561cc625717b7dc3841a39862704c80",
        "version": 1408462907
    },
    "ppConfig_win.zip": {
        "sha1": "b4fb067c4b414b9cb45fb16ca1dfdee37cfcd9db",
        "version": 1408462907
    },
    "ppConfig_win_single.tar.gz": {
        "sha1": "ea89e27f3eaefb892e887f8a208f034c9f54a921",
        "version": 1408462907
    },
    "ppConfig_win_single.zip": {
        "sha1": "68cd32bf2a81abcb9c8387cdf9b1e259fa3902ad",
        "version": 1408462907
    },
    "ppConfig_win_tcp.tar.gz": {
        "sha1": "025b3366d8f477768e6fe085d4ec71a9d20e6627",
        "version": 1408462907
    },
    "ppConfig_win_tcp.zip": {
        "sha1": "e8e10b0354c8bbf1dffc2cfed5cbd9308d4b78b6",
        "version": 1408462907
    },
    "ppConfig_win_tcp_single.tar.gz": {
        "sha1": "ad2cf2ea1366294dab106b2fce09848ecf29b25e",
        "version": 1408462907
    },
    "ppConfig_win_tcp_single.zip": {
        "sha1": "5f877a9eda500ea06a4f1b743e6fe5ff3259a036",
        "version": 1408462907
    },
    "ppIPSec_Certs.tar.gz": {
        "sha1": "067b664903eb9a3a04753a334b2e5cf9d5c36f3f",
        "version": 1408462907
    },
    "ppIPSec_Certs.zip": {
        "sha1": "dd5c500aeab5adb3aacd8af0fe1ca9c7ac950f59",
        "version": 1408462907
    },
    "servergroups.json": {
        "sha1": "a8d875328158cdb377bc747df6e13d9dce1dd77c",
        "version": 1408462907
    },
    "ssh_fingerprints.csv": {
        "sha1": "19b719cbdc8093228a7d2166a9869d9fb903262f",
        "version": 1408462907
    },
    "ssh_fingerprints.json": {
        "sha1": "9779397f956cee47ae3a4398b45e58cb395ff147",
        "version": 1408462907
    }
}
```
