# Get Credentials

## Get by ID

> CredHub CLI

```shell
user$ credhub get --id 2993f622-cb1e-4e00-a267-4b23c273bf3d
id: 2993f622-cb1e-4e00-a267-4b23c273bf3d
name: /example-password
type: password
value: 6mRPZB3bAfb8lRpacnXsHfDhlPqFcjH2h9YDvLpL
version_created_at: 2017-01-05T01:01:01Z
```

> cURL

```shell
curl "https://example.com/api/v1/data/2993f622-cb1e-4e00-a267-4b23c273bf3d" \
  -X GET \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "type": "password",
  "version_created_at": "2017-01-05T01:01:01Z",
  "id": "2993f622-cb1e-4e00-a267-4b23c273bf3d",
  "name": "/example-password",
  "value": "6mRPZB3bAfb8lRpacnXsHfDhlPqFcjH2h9YDvLpL"
}
```

This request retrieves a credential by ID. Exactly one value will be returned.

### HTTP Request

`GET: https://example.com/api/v1/data/[Credential-ID]`

### Query Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
none | | | |

## Get by Name

> CredHub CLI

```shell
user$ credhub get --name '/example-password'
id: 2993f622-cb1e-4e00-a267-4b23c273bf3d
name: /example-password
type: password
value: 6mRPZB3bAfb8lRpacnXsHfDhlPqFcjH2h9YDvLpL
version_created_at: 2017-01-05T01:01:01Z
```

> cURL

```shell
curl "https://example.com/api/v1/data?name=/example-password" \
  -X GET \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "data": [
    {
      "type": "password",
      "version_created_at": "2017-01-05T01:01:01Z",
      "id": "2993f622-cb1e-4e00-a267-4b23c273bf3d",
      "name": "/example-password",
      "value": "6mRPZB3bAfb8lRpacnXsHfDhlPqFcjH2h9YDvLpL"
    },
    {
      "type": "password",
      "version_created_at": "2017-01-01T04:07:18Z",
      "id": "67fc3def-bbfb-4953-83f8-4ab0682ad674",
      "name": "/example-password",
      "value": "3t6Y2OFP0jQIcLnki1h7p3NtSfDx4l9bamr1ja6R"
    }
  ]
}
```

This request returns a credential's value(s) by name. All historical values will be returned unless `"current": true` or `"versions": #` is specified.

### HTTP Request

`GET: https://example.com/api/v1/data`

### Query Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
name | none | yes | string | Name of credential to retrieve
current | false | no | string | Return only latest credential version
versions | none | no | integer | Return latest N credential versions

## Type: Value

> CredHub CLI

```shell
user$ credhub get --name '/example-value'
id: 67fc3def-bbfb-4953-83f8-4ab0682ad675
name: /example-value
type: value
value: sample
version_created_at: 2017-01-01T04:07:18Z
```

> cURL

```shell
curl "https://example.com/api/v1/data?name=/example-value" \
  -X GET \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "data": [
    {
      "type": "value",
      "version_created_at": "2017-01-01T04:07:18Z",
      "id": "67fc3def-bbfb-4953-83f8-4ab0682ad675",
      "name": "/example-value",
      "value": "sample"
    }
  ]
}
```

This request returns a credential by name. The example provided shows the request parameters and response structure of a value type credential.

### HTTP Request

`GET: https://example.com/api/v1/data`

### Query Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
name | none | yes | string | Name of credential to retrieve
current | false | no | string | Return only latest credential version
versions | none | no | integer | Return latest N credential versions

## Type: JSON

> CredHub CLI

```shell
user$ credhub get --name '/example-json'
id: 67fc3def-bbfb-4953-83f8-4ab0682ad675
name: /example-json
type: json
value:
  key: 123
  key_list:
  - val1
  - val2
  is_true: true
version_created_at: 2017-01-01T04:07:18Z
```

> cURL

```shell
curl "https://example.com/api/v1/data?name=/example-json" \
  -X GET \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "data": [
    {
      "type": "json",
      "version_created_at": "2017-01-01T04:07:18Z",
      "id": "67fc3def-bbfb-4953-83f8-4ab0682ad675",
      "name": "/example-json",
      "value": {
        "key": 123,
        "key_list": [
          "val1",
          "val2"
        ],
        "is_true": true
      }
    }
  ]
}
```

This request returns a credential by name. The example provided shows the request parameters and response structure of a JSON type credential.

### HTTP Request

`GET: https://example.com/api/v1/data`

### Query Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
name | none | yes | string | Name of credential to retrieve
current | false | no | string | Return only latest credential version
versions | none | no | integer | Return latest N credential versions

## Type: Password

> CredHub CLI

```shell
user$ credhub get --name '/example-password'
id: 67fc3def-bbfb-4953-83f8-4ab0682ad675
name: /example-password
type: password
value: 3t6Y2OFP0jQIcLnki1h7p3NtSfDx4l9bamr1ja6R
version_created_at: 2017-01-01T04:07:18Z
```

> cURL

```shell
curl "https://example.com/api/v1/data?name=/example-password" \
  -X GET \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "data": [
    {
      "type": "password",
      "version_created_at": "2017-01-05T01:01:01Z",
      "id": "67fc3def-bbfb-4953-83f8-4ab0682ad675",
      "name": "/example-password",
      "value": "6mRPZB3bAfb8lRpacnXsHfDhlPqFcjH2h9YDvLpL"
    }
  ]
}
```

This request returns a credential by name. The example provided shows the request parameters and response structure of a password type credential.

### HTTP Request

`GET: https://example.com/api/v1/data`

### Query Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
name | none | yes | string | Name of credential to retrieve
current | false | no | string | Return only latest credential version
versions | none | no | integer | Return latest N credential versions

## Type: User

> CredHub CLI

```shell
user$ credhub get --name '/example-user'
id: 67fc3def-bbfb-4953-83f8-4ab0682ad675
name: /example-user
type: user
value:
  username: FQnwWoxgSrDuqDLmeLpU
  password: 6mRPZB3bAfb8lRpacnXsHfDhlPqFcjH2h9YDvLpL
  password_hash: $6$h3b3JsG5$MnrPIrF6T3zAWk9uaun64vWY.vaBQ5nTRFZjjVqKuDWccxWXn8n6vstQykXEReamb4GYh2q1HC7vFy11wflXd0
version_created_at: 2017-01-01T04:07:18Z
```

> cURL

```shell
curl "https://example.com/api/v1/data?name=/example-user" \
  -X GET \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "data": [
    {
      "type": "user",
      "version_created_at": "2017-01-05T01:01:01Z",
      "id": "67fc3def-bbfb-4953-83f8-4ab0682ad675",
      "name": "/example-user",
      "value": {
        "username": "FQnwWoxgSrDuqDLmeLpU",
        "password": "6mRPZB3bAfb8lRpacnXsHfDhlPqFcjH2h9YDvLpL",
        "password_hash": "$6$uu8ybZiNiPRu$6AYClxVqMXA3LAIdDAnEuWLUlWGlm0RRJI2wdHd8R9hKkKtiYupyKBjdRBI1ZhsyHwYetCpySew9ZXXLf.Mih0"
      }
    }
  ]
}
```

This request returns a credential by name. The example provided shows the request parameters and response structure of a user type credential.

### HTTP Request

`GET: https://example.com/api/v1/data`

### Query Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
name | none | yes | string | Name of credential to retrieve
current | false | no | string | Return only latest credential version
versions | none | no | integer | Return latest N credential versions

## Type: Certificate

> CredHub CLI

```shell
user$ credhub get --name '/example-certificate'
id: 67fc3def-bbfb-4953-83f8-4ab0682ad675
name: /example-certificate
type: certificate
value:
  root: |
    -----BEGIN CERTIFICATE-----
    ...
    -----END CERTIFICATE-----
  certificate: |
    -----BEGIN CERTIFICATE-----
    ...
    -----END CERTIFICATE-----
  private_key: |
    -----BEGIN RSA PRIVATE KEY-----
    ...
    -----END RSA PRIVATE KEY-----
version_created_at: 2017-01-01T04:07:18Z
```

> cURL

```shell
curl "https://example.com/api/v1/data?name=/example-certificate" \
  -X GET \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "data": [
    {
      "type": "certificate",
      "version_created_at": "2017-01-01T04:07:18Z",
      "id": "67fc3def-bbfb-4953-83f8-4ab0682ad676",
      "name": "/example-certificate",
      "value": {
        "ca": "-----BEGIN CERTIFICATE-----\n...\n-----END CERTIFICATE-----",
        "certificate": "-----BEGIN CERTIFICATE-----\n...\n-----END CERTIFICATE-----",
        "private_key": "-----BEGIN RSA PRIVATE KEY-----\n...\n-----END RSA PRIVATE KEY-----"
      }
    }
  ]
}
```

This request returns a credential by name. The example provided shows the request parameters and response structure of a certificate type credential.

### HTTP Request

`GET: https://example.com/api/v1/data`

### Query Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
name | none | yes | string | Name of credential to retrieve
current | false | no | string | Returns latest credential version and transitional version, if one exists
versions | none | no | integer | Return latest N credential versions

## Type: RSA

> CredHub CLI

```shell
user$ credhub get --name '/example-rsa'
id: 67fc3def-bbfb-4953-83f8-4ab0682ad675
name: /example-rsa
type: rsa
value:
  public_key: |
    -----BEGIN PUBLIC KEY-----
    ...
    -----END PUBLIC KEY-----
  private_key: |
    -----BEGIN RSA PRIVATE KEY-----
    ...
    -----END RSA PRIVATE KEY-----
version_created_at: 2017-01-01T04:07:18Z
```

> cURL

```shell
curl "https://example.com/api/v1/data?name=/example-rsa" \
  -X GET \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "data": [
    {
      "type": "rsa",
      "version_created_at": "2017-01-01T04:07:18Z",
      "id": "67fc3def-bbfb-4953-83f8-4ab0682ad677",
      "name": "/example-rsa",
      "value": {
        "public_key": "-----BEGIN PUBLIC KEY-----\n...\n-----END PUBLIC KEY-----",
        "private_key": "-----BEGIN RSA PRIVATE KEY-----\n...\n-----END RSA PRIVATE KEY-----"
      }
    }
  ]
}
```

This request returns a credential by name. The example provided shows the request parameters and response structure of an RSA type credential.

### HTTP Request

`GET: https://example.com/api/v1/data`

### Query Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
name | none | yes | string | Name of credential to retrieve
current | false | no | string | Return only latest credential version
versions | none | no | integer | Return latest N credential versions

## Type: SSH

> CredHub CLI

```shell
user$ credhub get --name '/example-ssh'
id: 67fc3def-bbfb-4953-83f8-4ab0682ad675
name: /example-ssh
type: ssh
value:
  public_key: ssh-rsa AAAAB3Nz...
  private_key: |
    -----BEGIN RSA PRIVATE KEY-----
    ...
    -----END RSA PRIVATE KEY-----
version_created_at: 2017-01-01T04:07:18Z
```

> cURL

```shell
curl "https://example.com/api/v1/data?name=/example-ssh" \
  -X GET \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "data": [
    {
      "type": "ssh",
      "version_created_at": "2017-01-01T04:07:18Z",
      "id": "67fc3def-bbfb-4953-83f8-4ab0682ad678",
      "name": "/example-ssh",
      "value": {
        "public_key": "ssh-rsa AAAAB3Nz...",
        "private_key": "-----BEGIN RSA PRIVATE KEY-----\n...\n-----END RSA PRIVATE KEY-----",
        "public_key_fingerprint": "EvI0/GIUgDjcoCzUQM+EtwnVTryNsKRd6TrHAGKJJSI"
      }
    }
  ]
}
```

This request returns a credential by name. The example provided shows the request parameters and response structure of an SSH type credential.

### HTTP Request

`GET: https://example.com/api/v1/data`

### Query Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
name | none | yes | string | Name of credential to retrieve
current | false | no | string | Return only latest credential version
versions | none | no | integer | Return latest N credential versions

## Bulk Export

> CredHub CLI

```shell
user$ credhub export --file export.yml
```

> Sample Export File

```yml
credentials:
- name: /example-ssh
  type: ssh
  value:
    public_key: ssh-rsa AAAAB3NzaC1y...W9RWFM1
    private_key: |
      -----BEGIN RSA PRIVATE KEY-----
      ...
      -----END RSA PRIVATE KEY-----
- name: /example-password
  type: password
  value: SqFcE2c0AuRvet2YhrxdFbPtkBmjiq
- name: /example-value
  type: value
  value: sample
```

This CLI command gets multiple credentials and exports them to either standard out, or a file. The output will be in yaml format, with the key `credentials` whose value is a list of credential objects. Each credential will contain a name, type and value. An example is shown to the right. This file is compatible with the bulk import process.

Use `--file` to specify a file to write the export to. Use `--path` to specify a path, which will restrict the credentials exported to those with a prefix matching the given path.



### HTTP Request

n/a

### Request Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | ------------
n/a |  |  |  |

