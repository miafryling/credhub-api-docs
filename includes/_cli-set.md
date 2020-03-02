# Set Credentials

| Long Flag     | Short Flag | Used For Type         | Description                                                                                                        |
|---------------|------------|-----------------------|--------------------------------------------------------------------------------------------------------------------|
| --name        | -n         | All                   | Name of the credential to set                                                                                      |
| --type        | -t         | All                   | Sets the credential type. Valid types include 'value', 'json', 'password', 'user', 'certificate', 'ssh' and 'rsa'. |
| --value       | -v         | Value, Json           | Sets the value for the credential                                                                                  |
| --ca-name     | -m         | Certificate           | Sets the root CA to a stored CA credential                                                                         |
| --root        | -r         | Certificate           | Sets the root CA from file or value                                                                                |
| --certificate | -c         | Certificate           | Sets the certificate from file or value                                                                            |
| --private     | -p         | Certificate, SSH, RSA | Sets the private key from file or value                                                                            |
| --public      | -u         | SSH, RSA              | Sets the public key from file or value                                                                             |
| --username    | -z         | User                  | Sets the username value of the credential                                                                          |
| --password    | -w         | User, Password        | Sets the password value of the credential                                                                          |



## Type: Value

> CredHub CLI

```shell
user$ credhub set --type value --name '/example-value' --password 'sample'
id: 67fc3def-bbfb-4953-83f8-4ab0682ad675
name: /example-value
type: value
value: sample
version_created_at: 2017-01-01T04:07:18Z
```

This request sets a value credential with a user-provided value.



## Type: JSON

> CredHub CLI

```shell
user$ credhub set --type json --name '/example-json' --value '{ "key": 123, "key_list": ["val1","val2"], "is_true": true }'
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

This request sets a json credential with a user-provided value.



## Type: Password

> CredHub CLI

```shell
user$ credhub set --type password --name '/example-password' --password '3t6Y2OFP0jQIcLnki1h7p3NtSfDx4l9bamr1ja6R'
id: 67fc3def-bbfb-4953-83f8-4ab0682ad675
name: /example-password
type: password
value: 3t6Y2OFP0jQIcLnki1h7p3NtSfDx4l9bamr1ja6R
version_created_at: 2017-01-01T04:07:18Z
```

This request sets a password credential with a user-provided value.



## Type: User

> CredHub CLI

```shell
user$ credhub set --type user --name '/example-user' --username 'FQnwWoxgSrDuqDLmeLpU' --password '6mRPZB3bAfb8lRpacnXsHfDhlPqFcjH2h9YDvLpL'
id: 67fc3def-bbfb-4953-83f8-4ab0682ad675
name: /example-user
type: user
value:
  username: FQnwWoxgSrDuqDLmeLpU
  password: 6mRPZB3bAfb8lRpacnXsHfDhlPqFcjH2h9YDvLpL
  password_hash: $6$h3b3JsG5$MnrPIrF6T3zAWk9uaun64vWY.vaBQ5nTRFZjjVqKuDWccxWXn8n6vstQykXEReamb4GYh2q1HC7vFy11wflXd0
version_created_at: 2017-01-01T04:07:18Z
```

This request sets a user credential with a user-provided value.



## Type: Certificate

> CredHub CLI

```shell
user$ credhub set --type certificate --name '/example-certificate' --root ./root.pem --certificate ./cert.pem --private ./private.pem
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

This request sets a certificate credential with a user-provided value.



## Type: RSA

> CredHub CLI

```shell
user$ credhub set --type rsa --name '/example-rsa' --public ./public.pem --private ./private.pem
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

This request sets a RSA credential with a user-provided value.



## Type: SSH

> CredHub CLI

```shell
user$ credhub set --type ssh --name '/example-ssh' --public ./public.pem --private ./private.pem
id: 67fc3def-bbfb-4953-83f8-4ab0682ad675
name: /example-ssh
type: ssh
value:
  public_key: ssh-rsa AAAAB3NzaC1y...W9RWFM1
  private_key: |
    -----BEGIN RSA PRIVATE KEY-----
    ...
    -----END RSA PRIVATE KEY-----
version_created_at: 2017-01-01T04:07:18Z
```

This request sets a SSH credential with a user-provided value.

