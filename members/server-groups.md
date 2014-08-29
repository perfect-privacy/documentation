# Perfect Privacy Member's API: Server Groups
>Document version: **1.0**

All Perfect Privacy servers (e. g. "london1.perfect-privacy.com", "london2...") are member of a server group (e. g. "london.perfect-privacy.com").  This JSON file contains an array with server group objects. Those provide information like the human-readable name, the location, available service ports, external and internal IP addresses and so on.
Use this file with care, see [Polling Strategy](#polling).

---

## URL
>**[Authentication](authenticate.md) needed!**

https://www.perfect-privacy.com/member/download/?file=servergroups.json


## Data Types
Data Type | Notice
--------- | ----------------------
string    |
host      | (string) Fully Qualified Domain Name (FQDN)
IP        | (string) IPv4 address

## Keys

### Server group object
Key                     | Data Type                | Notice
----------------------- | ------------------------ | -------------------------------------------
name                    | string                   | human-readable name of the server group
url                     | host                     | URL of the server group (e. g. "server.perfect-privacy.com")
locations               | array (location objects) | locations of the servers in the server group
email_blocked           | boolean                  | whether e-mail is blocked on this server group
p2p_blocked             | boolean                  | whether P2P is blocked on this server group
ipsec_psk               | string                   | IPsec PSK
openvpn_ca_crt          | string                   | OpenVPN CA certificate. The certs and keys in this file are intended for custom purposes - use the zip file in the download area instead.
openvpn_client_crt      | string                   | OpenVPN client certificate
openvpn_client_key      | string                   | OpenVPN key
openvpn_client_p12      | string                   | OpenVPN p12
openvpn_client_pem      | string                   | OpenVPN PEM
openvpn_ta_key          | string                   | OpenVPN tls-auth
openvpn_tcp_1_ports     | array (string)           | OpenVPN ports (TCP)
openvpn_tcp_2_ports     | array (string)           | .
openvpn_udp_1_ports     | array (string)           | OpenVPN ports (UDP)
openvpn_udp_2_ports     | array (string)           | .
openvpn_udp_3_ports     | array (string)           | .
openvpn_udp_4_ports     | array (string)           | .
openvpn_udp_5_ports     | array (string)           | .
openvpn_udp_6_ports     | array (string)           | .
pptpd_ports             | array (string)           | PPTP ports
3proxy_ports            | array (string)           | SOCKS proxy ports (this is not 3proxy anymore)
squid_ports             | array (string)           | HTTP (Squid) ports
ssh_ports               | array (string)           | SSH ports
ssh_fingerprint_rsa     | string                   | SSH fingerprint (RSA)
ssh_fingerprint_dsa     | string                   | SSH fingerprint (DSA)
xl2tpd_ports            | array (string)           | L2PD ports
servers                 | array (server objects)   | servers in this group


### Location object
Key     | Data Type | Notice
------- | --------- | --------------------------------------------------
city    | string    | City, english language
country | string    | Country, english language
lati    | string    | Latitude, signed floating-point number as string
longi   | string    | Longitude, signed floating-point number as string


### Server object
Key                     | Data Type         | Notice
----------------------- | ----------------- | ----------------------------------------------------------------------------------------------------------------------
name                    | string            | human-readable name of the server, usually in this format: "< server group name >[< number >]", e. g. "London1", "Zurich"
url                     | host              | URL of the server, e. g. "london1.perfect-privacy.com"
ip                      | IP                | primary IP address of the server
alternative_ips         | array (IP)        | secondary (alternative) IP addresses of the server
bandwidth               | number            | Mbit/s available in each direction (incoming/outgoing). The real traffic can exceed the maximum bandwidth, see [public Traffic API](../public/traffic.md)
location                | location object   | location of the server
openvpn_tcp_1_localip   | IP                | internal OpenVPN (TCP) IP address, e.g. "10.1.42.42"
openvpn_tcp_2_localip   | IP                | .
openvpn_udp_1_localip   | IP                | internal OpenVPN (UDP) IP address, e.g. "10.1.42.44"
openvpn_udp_2_localip   | IP                | .
openvpn_udp_3_localip   | IP                | .
openvpn_udp_4_localip   | IP                | .
openvpn_udp_5_localip   | IP                | .
openvpn_udp_6_localip   | IP                | .
pptpd_localip           | IP                | internal PPTP IP address, e.g. "10.1.42.50"
xl2tpd_localip          | IP                | internal L2TP IP address, e.g. "10.1.42.51"

<a name="polling">
## Polling Strategy
This file is huge and it contains static information only. Because of that you don't have to poll this file at all. If you need it, get it once and poll the [Config Versions API](config-versions.md) for changes in configuration. If you only need the location, use the [Server Locations API](../public/server-locations.md).

<a name="ex">
## Example
```json
[
    {
        "name": "London",
        "url": "london.perfect-privacy.com",
        "locations": [
            {
                "city": "London",
                "country": "United Kingdom",
                "lati": "0.0",
                "longi": "0.0"
            }
        ],
        "email_blocked": false,
        "p2p_blocked": false,
        "ipsec_psk": "AAAAAAAAAAAAAAAA",
        "openvpn_ca_crt": "-----BEGIN CERTIFICATE-----\r\n............\r\n-----END CERTIFICATE-----\r\n",
        "openvpn_client_crt": "Certificate:\r\n......\r\n-----BEGIN CERTIFICATE-----\r\n.........\r\n-----END CERTIFICATE-----\r\n",
        "openvpn_client_key": "-----BEGIN RSA PRIVATE KEY-----\r\n............\r\n-----END RSA PRIVATE KEY-----\r\n",
        "openvpn_client_p12": "AAAAAAAAAAAAAAAAA....",
        "openvpn_client_pem": "Certificate:\r\n......\r\n-----BEGIN CERTIFICATE-----\r\n.........\r\n-----END CERTIFICATE-----\r\n",
        "openvpn_ta_key": "#\r\n# 2048 bit OpenVPN static key\r\n#\r\n-----BEGIN OpenVPN Static key V1-----\r\n......\r\n-----END OpenVPN Static key V1-----\r\n",
        "openvpn_tcp_1_ports": [
            "1234"
        ],
        "openvpn_tcp_2_ports": [
            "1235"
        ],
        "openvpn_udp_1_ports": [
            "1236"
        ],
        "openvpn_udp_2_ports": [
            "1237"
        ],
        "openvpn_udp_3_ports": [
            "1238"
        ],
        "openvpn_udp_4_ports": [
            "1239"
        ],
        "openvpn_udp_5_ports": [
            "1240"
        ],
        "openvpn_udp_6_ports": [
            "1241"
        ],
        "pptpd_ports": [
            "1242"
        ],
        "3proxy_ports": [
            "1337",
            "1338",
            "1339"
        ],
        "squid_ports": [
            "1340",
            "1341",
            "1342",
            "1343"
        ],
        "ssh_ports": [
            "1344",
            "1345"
        ],
        "ssh_fingerprint_dsa": "00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00",
        "ssh_fingerprint_rsa": "00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00",
        "xl2tpd_ports": [
            "1346"
        ],
        "servers": [
            {
                "name": "London1",
                "url": "london1.perfect-privacy.com",
                "ip": "42.42.42.42",
                "alternative_ips": [
                    "42.42.42.23",
                    "42.42.23.42",
                    "42.42.23.23",
                    "42.23.42.42"
                ],
                "bandwidth": 100,
                "location": {
                    "city": "London",
                    "country": "United Kingdom",
                    "lati": "0.0",
                    "longi": "0.0"
                },
                "openvpn_tcp_1_localip": "10.1.42.42",
                "openvpn_tcp_2_localip": "10.1.42.43",
                "openvpn_udp_1_localip": "10.1.42.44",
                "openvpn_udp_2_localip": "10.1.42.45",
                "openvpn_udp_3_localip": "10.1.42.46",
                "openvpn_udp_4_localip": "10.1.42.47",
                "openvpn_udp_5_localip": "10.1.42.48",
                "openvpn_udp_6_localip": "10.1.42.49",
                "pptpd_localip": "10.1.42.50",
                "xl2tpd_localip": "10.1.42.51"
            },
            ..... more servers .....
        ]
    },
    ..... more server groups .....
]
```
