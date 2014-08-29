# Perfect Privacy Public API: Check IP
>Document version: **1.0**

The Check IP API returns client information like the client's IP address,
whether it is connected to Perfect Privacy or TOR and the client's city and country.
See [Response JSON Keys](#response) for details.

## TOC

1. [URLs](#urls)
2. [Data Types](#datatypes)
3. [Response JSON Keys](#response)
4. [Polling Strategy](#polling)
5. [Examples](#ex)

---

<a name="urls">
## 1. URLs
Format                    | URL
------------------------- | -----------------------------------------
HTML - for viewing only   | https://checkip.perfect-privacy.com/
JSON                      | https://checkip.perfect-privacy.com/json
XML                       | https://checkip.perfect-privacy.com/xml
CSV                       | https://checkip.perfect-privacy.com/csv
TSV                       | https://checkip.perfect-privacy.com/tsv

<a name="datatypes">
## 2. Data Types
Data Type | Notice
--------- | ----------------------
string    |
boolean   | true/false, lowercase
IP        | (string) IPv4 address
host      | (string) Fully Qualified Domain Name (FQDN)

<a name="response">
## 3. Response JSON Keys
Key     | Data Type | Notice
------- | --------- | ----------
VPN     | boolean   | whether the client is using Perfect Privacy (the client's IP address belongs to any Perfect Privacy server)
TOR     | boolean   | whether the client is using TOR, based on a list of TOR exit IP addresses
IP      | IP        | the public IP address of the client
DNS     | host      | rDNS host, empty string if no result
CITY    | string    | the city the client apparently is located, based on the client's IP address using the [Maxmind GeoLite database](http://dev.maxmind.com/geoip/legacy/geolite/). If it is a known Perfect Privacy IP address, the known server location will be used. English language, empty string if no result.
COUNTRY | string    | the country the client apparently is located, see CITY


<a name="polling">
## 4. Polling Strategy
Use smart polling: e.g. start with a 1 minute polling interval and increase it gradually to 15 minutes. If a connect / disconnect event occurs, poll immediately and start over. If the user can't see the window (because it's minimized or hidden), you don't have to poll at all.

<a name="ex">
## 5. Examples

<a name="ex-json">
### 5.1 JSON
```json
{
  "VPN": true,
  "TOR": false,
  "IP": "42.42.23.23",
  "DNS": "server1.perfect-privacy.com",
  "CITY": "London",
  "COUNTRY": "United Kingdom"
}
```

<a name="ex-xml">
### 5.2 XML
```xml
<?xml version="1.0" encoding="UTF-8"?>
<root>
   <IP>42.42.23.23</IP>
   <DNS>server1.perfect-privacy.com</DNS>
   <VPN>true</VPN>
   <TOR>false</TOR>
   <COUNTRY>United Kingdom</COUNTRY>
   <CITY>London</CITY>
</root>
```

<a name="ex-csv">
### 5.3 CSV
```
IP,DNS,VPN,TOR,COUNTRY,CITY
42.42.23.23,server1.perfect-privacy.com,true,false,United Kingdom,London
```

<a name="ex-tsv">
### 5.4 TSV
```
IP	DNS	VPN	TOR	COUNTRY	CITY
42.42.23.23	server1.perfect-privacy.com	true	false	United Kingdom	London
```
