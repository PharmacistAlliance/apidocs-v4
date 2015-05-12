# Security And Authorization

All calls to the PokitDok API are encrypted over HTTPS. Access to the API is controlled via OAuth2 (for more 
information, reference "OAuth 2.0 Authorization Framework" [here](http://tools.ietf.org/html/rfc6749). If you've already 
signed up and received your client id and client secret, you’ll be able to start calling APIs. Here's a quick example 
using Python and the requests library to demonstrate how to authenticate as your application and access some information 
about an ongoing activity.

```python
import requests
from base64 import urlsafe_b64encode

client_id = YOUR_APP_CLIENT_ID
client_secret = YOUR_APP_CLIENT_SECRET
access_token = requests.post('https://platform.pokitdok.com/oauth2/token',
headers={'Authorization': 'Basic ' +
urlsafe_b64encode(client_id + ':' + client_secret)},
data={'grant_type':'client_credentials'}).json()['access_token']

activity = requests.get('https://platform.pokitdok.com/api/v4/activities/53187d2027a27620f2ec7537',
headers={'Authorization': 'Bearer ' + access_token}).json()
```

```shell
CLIENT_ID=YOUR_APP_CLIENT_ID
CLIENT_SECRET=YOUR_APP_CLIENT_SECRET
BASIC_HEADER=`echo "$CLIENT_ID:$CLIENT_SECRET" | base64`

# On some operating systems, base64 may include extra
# whitespace that needs to be removed
BASIC_HEADER=$(echo $BASIC_HEADER | sed 's/\r//g')
BASIC_HEADER=$(echo $BASIC_HEADER | sed 's/ *//g')

curl -i -XPOST -H "Authorization: Basic $BASIC_HEADER" -d "grant_type=client_credentials"
https://platform.pokitdok.com/oauth2/token
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 06 Mar 2014 04:20:43 GMT
Content-Type: application/json;charset=UTF-8
Content-Length: 127
Connection: keep-alive
Pragma: no-cache
Cache-Control: no-store
{
    "access_token": "s8KYRJGTO0rWMy0zz1CCSCwsSesDyDlbNdZoRqVR",
    "token_type": "bearer",
    "expires": 1393350569,
    "expires_in": 3600
}

ACCESS_TOKEN='s8KYRJGTO0rWMy0zz1CCSCwsSesDyDlbNdZoRqVR'
curl -i -H "Authorization: Bearer $ACCESS_TOKEN"
https://platform.pokitdok.com/api/v4/activities/5317f51527a27620f2ec7533
```