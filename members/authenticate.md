# Perfect Privacy Member's APIs: Authentication
> Document Version: **1.0.1**

If you want to use any of the [members APIs](../README.md#members), you have to authenticate yourself.

Send the following POST data to this URL: https://www.perfect-privacy.com/member/

POST Data | Notice                        | Example
--------- | ----------------------------- | -----------------------------------------
username  | Perfect Privacy user name     | USER24
password  | Perfect Privacy password      | SECRET
uri       | the file you want do download | /member/download/?file=servergroups.json

If you provide the "uri" field, you will be directed to the desired file. **Note:** You have to accept cookies (but you don't have to save them)!

## Example

### wget
Download the [Server Groups JSON file](server-groups.md) and save it to "servergroups.json":
```
wget -v --post-data "username=USERNAME&password=PASSWORD&uri=/member/download/?file=servergroups.json" -O servergroups.json "https://www.perfect-privacy.com/member/"
```
