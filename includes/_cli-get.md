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

This request retrieves a credential by ID. Exactly one value will be returned.

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

This request returns a credential's value(s) by name. The current value will be returned unless `--versions=<NUMBER OF VERSIONS>` is specified. To return only the value of a credential, use the `--quiet` or `-q` flags. If you would only like to see one key from the value (i.e. a certificate's private key), use the `-k <NAME OF KEY>` or `--key=<NAME OF KEY>` flags.

## Output JSON

> CredHub CLI

```shell

user$ credhub get --name '/example-json'
{
	"id": "b508a5d6-c1ed-4218-8ed3-aca98d8b2c25",
	"name": "/example-json",
	"type": "json",
	"value": {
		"is_true": true,
		"key": 123,
		"key_list": [
			"val1",
			"val2"
		]
	},
	"version_created_at": "2020-03-10T16:32:37Z"
}
```

All responses default to YAML unless the `-j` or `--output-json` flags are passed in.

##Type: Value

> CredHub CLI

```shell
user$ credhub get --name '/example-value'
id: 67fc3def-bbfb-4953-83f8-4ab0682ad675
name: /example-value
type: value
value: sample
version_created_at: 2017-01-01T04:07:18Z
```

This request returns a credential by name. The example provided shows the request parameters and response structure of a value type credential.

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

This request returns a credential by name. The example provided shows the request parameters and response structure of a JSON type credential. The response is formatted as YAML by default, but can be formatted as json using the `-j` flag.


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


This request returns a credential by name. The example provided shows the request parameters and response structure of a user type credential.



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

This request returns a credential by name. The example provided shows the request parameters and response structure of a certificate type credential.


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

This request returns a credential by name. The example provided shows the request parameters and response structure of an RSA type credential.


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

This request returns a credential by name. The example provided shows the request parameters and response structure of an SSH type credential.

