# Generating Credentials

| Long Flag           | Short Flag | Used For Type         | Description                                                                                                   |
|---------------------|------------|-----------------------|---------------------------------------------------------------------------------------------------------------|
| --name              | -n         | All                   | Name of the credential to generate                                                                            |
| --type              | -t         | All                   | Sets the credential type to generate. Valid types include 'password', 'user', 'certificate', 'ssh' and 'rsa'. |
| --no-overwrite      | -O         | All                   | Credential is not modified if stored value already exists                                                     |
| --username          | -z         | User                  | Sets the username value of the credential                                                                     |
| --password          | -w         | User, Password        | Sets the password value of the credential                                                                     |
| --length            | -l         | User, Password        | Length of the generated value (Default: 30)                                                                   |
| --include-special   | -S         | User, Password        | Include special characters in the generated value                                                             |
| --exclude-number    | -N         | User, Password        | Exclude number characters from the generated value                                                            |
| --exclude-upper     | -U         | User, Password        | Exclude upper alpha characters from the generated value                                                       |
| --exclude-lower     | -L         | User, Password        | Exclude lower alpha characters from the generated value                                                       |
| --ssh-comment       | -m         | SSH                   | Comment appended to public key to help identify in environment                                                |
| --key-length        | -k         | SSH, RSA, Certificate | Bit length of the generated key (Default: 2048)                                                               |
| --duration          | -d         | Certificate           | Valid duration (in days) of the generated certificate (Default: 365)                                          |
| --common-name       | -c         | Certificate           | Common name of the generated certificate                                                                      |
| --organization      | -o         | Certificate           | Organization of the generated certificate                                                                     |
| --organization-unit | -u         | Certificate           | Organization unit of the generated certificate                                                                |
| --locality          | -i         | Certificate           | Locality/city of the generated certificate                                                                    |
| --state             | -s         | Certificate           | State/province of the generated certificate                                                                   |
| --country           | -y         | Certificate           | Country of the generated certificate                                                                          |
| --alternative-name  | -a         | Certificate           | A subject alternative name of the generated certificate (may be specified multiple times)                     |
| --key-usage         | -g         | Certificate           | Key Usage extensions for the generated certificate (may be specified multiple times)                          |
| --ext-key-usage     | -e         | Certificate           | Extended Key Usage extensions for the generated certificate (may be specified multiple times)                 |
| --ca                |            | Certificate           | Name of CA used to sign the generated certificate                                                             |
| --is-ca             |            | Certificate           | The generated certificate is a certificate authority                                                          |
| --self-sign         |            | Certificate           | The generated certificate will be self-signed                                                                 |

## Type: Password

This request generates a password credential based on the provided parameters.

> CredHub CLI

```shell
user$ credhub generate --type password --name '/example-password'
id: 67fc3def-bbfb-4953-83f8-4ab0682ad675
name: /example-password
type: password
value: 3t6Y2OFP0jQIcLnki1h7p3NtSfDx4l9bamr1ja6R
version_created_at: 2017-01-01T04:07:18Z
```

## Type: User

This request generates a user credential based on the provided parameters.

> CredHub CLI

```shell
user$ credhub generate --type user --name '/example-user'
id: 67fc3def-bbfb-4953-83f8-4ab0682ad675
name: /example-user
type: user
value:
  username: FQnwWoxgSrDuqDLmeLpU
  password: 6mRPZB3bAfb8lRpacnXsHfDhlPqFcjH2h9YDvLpL
  password_hash: $6$h3b3JsG5$MnrPIrF6T3zAWk9uaun64vWY.vaBQ5nTRFZjjVqKuDWccxWXn8n6vstQykXEReamb4GYh2q1HC7vFy11wflXd0
version_created_at: 2017-01-01T04:07:18Z
```

## Type: Certificate

This request generates a user credential based on the provided parameters.

> CredHub CLI

```shell
user$ credhub generate --type certificate --name '/example-certificate' --common-name 'example.com' --ca '/example-ca'
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

## Type: RSA

This request generates an RSA credential based on the provided parameters.

> CredHub CLI

```shell
user$ credhub generate --type rsa --name '/example-rsa'
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


## Type: SSH

This request generates an SSH credential based on the provided parameters.

>CredHub CLI

```shell
user$ credhub generate --type ssh --name '/example-ssh'
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

