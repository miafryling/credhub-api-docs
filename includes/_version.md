# Get Version

> CredHub CLI

```shell
user$ credhub --version
CLI Version: 2.0.1
Server Version: 1.9.1
```

> cURL

```shell
curl "https://example.com/version" \
  -X GET \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "version": "1.9.1"
}
```

This request displays the server version.

### HTTP Request

`GET: https://example.com/version`

### Request Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
none | | | |

