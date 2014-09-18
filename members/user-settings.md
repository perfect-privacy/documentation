# Perfect Privacy API: User Settings
> Document version: **1.2**

This API is intended for getting user account information such as expiration date and setting user related settings like port forwarding and whether to use a random exit IP address.

## TOC

1. [URL](#url)
2. [Data Types](#datatypes)
3. [Request GET Parameters](#request)
4. [Response JSON Keys](#response)
  1. [Standard Response](#standard_response)
  2. [Custom Port Forwarding Object](#custom_port_forwardings_object)
  3. [Server Groups Object](#server_groups_object)
  4. [Errors](#errors)
5. [Calculate Default Port Forwardings](#calculate_pf)
6. [Polling Strategy](#polling)
7. [Examples](#ex)

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
## 3. Request POST Parameters
Parameter               | Data Type  |  Notice                                                                                                                                                                                                                                                                                                                  | Example
----------------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------
username                | string     | (required)<br><br>**Errors:**<br>errorUsernamePassword, errorInvalidchars, errorExpired, errorDisabled, errorApiCallLimit                                                                                                                                                                                                |
password                | string     | (required)<br><br>**Errors:**<br>see username                                                                                                                                                                                                                                                                            |
defaultPortForwarding   | boolean    | enable / disable default port forwarding (create 3 temporary port forwardings when VPN connection is established)                                                                                                                                                                                                        | "defaultPortForwarding=1" - enable
randomExit              | boolean    | enable / disable random exit IP address (VPN only)                                                                                                                                                                                                                                                                       | "randomExit=0" - disable
autorenew_pf            | boolean    | enable / disable auto-renew port forwarding                                                                                                                                                                                                                                                                              |
getServerGroups         | none       | extend the [Standard Response](#standard_response) by [a *serverGroups* object](#server_groups_object) which contains an array of all server groups.                                                                                                                                                                     |
setPortForwarding[]     | (1,2)-list | add port forwarding, format: "serverGroupId[,dstPort]", if no dstPort is provided it will be randomly chosen, multiple possible, port forwardings on other server groups will be deleted, max. 5 port forwardings, check response if new port forwarding is in *customPorts*<br><br>**Errors:**<br>errorMissingServerGrp | "setPortForwarding[]=375<br>&setPortForwarding[]=375,1842"<br>add port forwarding on server group 375 (random destination), add another with destination port 1842
deletePortForwarding[]  | n-list     | delete port forwarding by id, multiple possible, check response if deleted port forwarding is not in *customPorts* anymore                                                                                                                                                                                               | "deletePortForwarding[]=1337<br>&deletePortForwarding[]=1338"<br>==<br>"deletePortForwarding[]=1337,1338"


<a name="response">
## 4. Response JSON Keys
<a name="standard_response">
### 4.1 Standard Response
This JSON object is the standard response if no error occurs.

username and password only:
```
wget -q --post-data "username=USERNAME&password=PASSWORD" -O - "https://www.perfect-privacy.com/api/user.php"
```

Key                     | Data Type                   | Notice
----------------------- | --------------------------- | -----------------------------------------------------------------------------
error                   | string                      | (only if an error occurs, then this may be the only field) see [Errors](#errors)
validUntil              | datetime                    | the date and time the account will expire
randomExit              | boolean (string)            | whether random exit IP address is enabled
defaultPortForwarding   | boolean (string)            | whether default port forwarding is enabled, [calculate the ports by using the internal IP address](#calculate_pf)
autorenew_pf            | boolean (string)            | whether auto-renew port forwardings is enabled
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

<a name="calculate_pf">
## 5. Calculate Default Port Forwardings
If you enable default port forwarding, 3 port forwardings will be set up automatically when you connect to the VPN.

The default port forwarding ports are based on the internal VPN IP address and can be calculated like so:

```
10.22.16.9
  last |  \ entire
 digit |  | part
       |  |
     1 6009
         ^ zero-fill
     2 6009
     3 6009
     ^ add 1, 2, 3
```

### Step 1: Take the last digit of the third part of the IP address:
```
10.22.16.9
       ^ => 6
```

### Step 2: Take the last part of the IP address and zero-fill it to 3 digits:
```
10.22.16.9
         ^ => 009
```

### Step 3: Concatenate it and add a leading 1, 2 or 3:
```
16009
26009
36009
```
Voilà!

### Examples:
IP address      | Default Ports
--------------- | ---------------
10.23.6.112     | 16112, 26112, 36112
10.2.23.42      | 13042, 23042, 33042
10.23.123.125   | 13125, 23125, 33125


<a name="polling">
## 6. Polling Strategy
You only need to get this once. Update again when the window becomes visible or gets the focus (possibly the user changed some settings directly on the web site).


<a name="ex">
## 7. Examples
### 7.1 Example 1: General Information
```
wget -q --post-data "username=USERNAME&password=PASSWORD" -O - "https://www.perfect-privacy.com/api/user.php"
```
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

### 7.2 Example 2: Error (invalid characters in username)
```
wget -q --post-data "username=USERNAME%123&password=PASSWORD" -O - "https://www.perfect-privacy.com/api/user.php"
```
```json
{
  "error":"errorInvalidchars"
}
```

### 7.3 Example 3: Get Server Groups
```
wget -q --post-data "username=USERNAME&password=PASSWORD&getServerGroups=" -O - "https://www.perfect-privacy.com/api/user.php"
```
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

### 7.4 Example 4: Set Default Port Forwarding
```
wget -q --post-data "username=USERNAME&password=PASSWORD&defaultPortForwarding=0" -O - "https://www.perfect-privacy.com/api/user.php"
```
```json
{
    "validUntil": "2100-01-01 00:00:00",
    "randomExit": "1",
    "defaultPortForwarding": "0",
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
