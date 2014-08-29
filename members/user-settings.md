# Perfect Privacy API: User Settings
> Document version: **1.0**

This API is intended for getting user account information such as expiration date and setting user related settings like port forwarding and random exit IP address.

## TOC

1. [URL](#url)
2. [Data Types](#datatypes)
3. [Request GET Parameters](#request)
4. [Response JSON Keys](#response)
  1. [Standard Response](#standard_response)
  2. [Custom Port Forwarding Object](#custom_port_forwardings_object)
  3. [Server Groups Object](#server_groups_object)
  4. [Errors](#errors)
5. [Polling Strategy](#polling)
6. [Examples](#ex)

---

<a name="url">
## 1. URL
Base URL: https://www.perfect-privacy.com/api/user.php?


<a name="datatypes">
## 2. Data Types
Data Type | Notice
--------- | ----------------------------------------------------------------------------------
boolean   | (string) 1/0
datetime  | (string) Date/Time in 24h format (UTC): "YYYY-mm-dd HH:MM:SS" (%Y-%m-%d %H:%M:%S)

<a name="request">
## 3. Request GET Parameters
Parameter               | Data Type  | Errors                | Notice                                                                                                             | Example
----------------------- | ---------- | --------------------- | ------------------------------------------------------------------------------------------------------------------ | -----------------
username                | string     | errorUsernamePassword,<br> errorInvalidchars,<br> errorExpired,<br> errorDisabled,<br> errorApiCallLimit                                   | (required) |
password                | string     | (see username)        | (required)                                                                                                         |
defaultPortForwarding   | boolean    |                       | enable / disable default port forwarding (create 3 temporary port forwardings when VPN connection is established)  | "defaultPortForwarding=1" - enable
randomExit              | boolean    |                       | enable / disable random exit IP address (VPN only)                                                                 | "randomExit=0" - disable
autorenew_pf            | boolean    |                       | enable / disable auto-renew port forwarding                                                                        |
getServerGroups         | none       |                       | extend the [Standard Response](#standard_response) by [a *serverGroups* object](#server_groups_object) which contains an array of all server groups.                                                                                                                           |
setPortForwarding[]     | (1,2)-list | errorMissingServerGrp | add port forwarding, format: "serverGroupId[,dstPort]", if no dstPort is provided it will be randomly chosen, multiple possible, port forwardings on other server groups will be deleted, max. 5 port forwardings, check response if new port forwarding is in *customPorts*   | "setPortForwarding[]=375&setPortForwarding[]=375,1842"<br>add port forwarding on server group 375 (random destination), add another with destination port 1842
deletePortForwarding[]  | n-list     |                       | delete port forwarding by id, multiple possible, check response if deleted port forwarding is not in *customPorts* anymore                                                                                                                                                     | "deletePortForwarding[]=1337&deletePortForwarding[]=1338", "deletePortForwarding[]=1337,1338"

<a name="response">
## 4. Response JSON Keys
<a name="standard_response">
### 4.1 Standard Response
This JSON object is the standard response if no error occurs.

username and password only:
https://www.perfect-privacy.com/api/user.php?username=user123&password=secret

Key                     | Data Type                   | Notice
----------------------- | --------------------------- | -----------------------------------------------------------------------------
error                   | string                      | (only if an error occurs, then this may be the only field) see [Errors](#errors)
validUntil              | datetime                    | the date and time the account will expire
randomExit              | boolean (string)            | random exit IP address
defaultPortForwarding   | boolean (string)            | default port forwarding
autorenew_pf            | boolean (string)            | auto-renew port forwardings
customPorts             | array ([custom port forwardings objects](#custom_port_forwardings_object)) | array containing [Custom Port Forwarding Objects](#custom_port_forwardings_object)

<a name="custom_port_forwardings_object">
### 4.2 Custom Port Forwarding Object
Key                     | Data Type       | Notice
----------------------- | --------------- | -----------------------------------------------
id                      | number (string) | ID of the port forwarding, for deleting
serverGroupId           | number (string) | the server group ID of this port forwarding
srcPort                 | number (string) | the source port - it will be randomly chosen
destPort                | number (string) | the destination port (can be provided by the user)
validUntil              | datetime        | the port forwarding will last 7 days

<a name="server_groups_object">
### 4.3 Server Groups Object
Key                     | Data Type       | Notice
----------------------- | --------------- | -----------------------------------------------
id                      | number          | the ID of the server group. **Note:** For immediate use only - don't save it, it will change.
name                    | string          | the human-readable name of the server group, english language


<a name="errors">
### 4.4 Errors
Error                 | Notice
--------------------- | ----------------------------------------
errorUsernamePassword | wrong username / password
errorInvalidchars     | Invalid characters in username
errorExpired          | Account expired
errorDisabled         | Account disabled
errorApiCallLimit     | API limit exceeded
errorMissingServerGrp | setPortForwarding without serverGroupId

<a name="polling">
## 5. Polling Strategy


<a name="ex">
## 6. Examples
### 6.1 Example 1: General Information
https://www.perfect-privacy.com/api/user.php?username=user123&password=secret
```json
{
    "validUntil": "2100-01-01 00:00:00",
    "randomExit": "1",
    "defaultPortForwarding": "1",
    "autorenew_pf": "0",
    "customPorts": [
        {
            "id": "1000",
            "serverGroupId": "42",
            "srcPort": "1234",
            "destPort": "1234",
            "validUntil": "2100-01-01 00:00:00"
        },
        ... more port forwardings ...
    ]
}
```

### 6.2 Example 2: Error (invalid characters in username)
https://www.perfect-privacy.com/api/user.php?username=user%123&password=secret
```json
{
  "error":"errorInvalidchars"
}
```

### 6.3 Example 3: Get Server Groups
https://www.perfect-privacy.com/api/user.php?username=user123&password=secret&getServerGroups
```json
{
    ... see Example 1 ...
    "serverGroups": [
        {
            "id": "1",
            "name": "Amsterdam"
        },
        {
            "id": "2",
            "name": "Brisbane"
        },
        ... more server groups ...
    ]
}
```
