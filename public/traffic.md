# Perfect Privacy Public API: Server Traffic
>Document version: **1.0**

This API provides a JSON object containing traffic load objects for each available Perfect Privacy server.

Like the [SSH Fingerprints API](ssh-fingerprints.md) and the [Server IPs API](server-ips.md) you can use this list to determine all available servers.

To get the FQDN of the server *group*, just drop the number and you are ready to go: "server1.perfect-privacy.com" becomes "server.perfect-privacy.com"

---

## URL
https://www.perfect-privacy.com/api/traffic.json

## Data Types
Data Type | Notice
--------- | ----------------------------------------------------------------------------------------------
host      | (string) Fully Qualified Domain Name (FQDN)
timestamp | (unsigned number) POSIX time - number of seconds elapsed since 00:00:00 (UTC), 1 January 1970

## Keys
Key           | Data Type | Notice
------------- | --------- | ------------------------------------------------------------------------------
timestamp     | timestamp | last update
bandwidth_max | number    | kbit/s available in each direction.<br>**Note:** This is not the absolute maximum! *bandwidth_in* or *bandwidth_out* can exceed *bandwidth_max* on traffic limited and therefore traffic shaped servers. In this case *bandwidth_max* is the average available bandwidth.
bandwidth_in  | number    | kbit/s incoming. For calculating server load percentage, use ```100 * max(bw_in, bw_out) / max(bw_max, bw_in, bw_out)```
bandwidth_out | number    | kbit/s outgoing

## Polling Strategy
The traffic statistics are updated approximately every minute. Therefore a polling interval of 30s is enough. Use smart polling such as described in [Check IP API documentation](checkip.md#polling).

## Example
```json
{
    "server1.perfect-privacy.com": {
        "timestamp": 946681200,
        "bandwidth_in": 4242,
        "bandwidth_max": 100000,
        "bandwidth_out": 4223
    },
    "server2.perfect-privacy.com": {
        "timestamp": 946681200,
        "bandwidth_in": 1337,
        "bandwidth_max": 100000,
        "bandwidth_out": 1338
    },
    ...
}
```
