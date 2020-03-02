# Authentication

## Login

Authenticate with CredHub. UAA password and client credential grants are supported. If client credentials exist in the environment, authentication will be
performed automatically without the need to explicitly call this command.

| Long Flag             | Short Flag | Description                                                       |
|-----------------------|------------|-------------------------------------------------------------------|
| --username            | -u         | Authentication username                                           |
| --password            | -p         | Authentication password                                           |
| --client-name         |            | Client name for UAA client grant [$CREDHUB_CLIENT]                |
| --client-secret       |            | Client secret for UAA client grant [$CREDHUB_SECRET]              |
| --server              | -s         | URI of API server to target [$CREDHUB_SERVER]                     |
| --ca-cert             |            | Trusted CA for API and UAA TLS connections [$CREDHUB_CA_CERT]     |
| --skip-tls-validation |            | Skip certificate validation of the API endpoint. Not recommended! |
| --sso                 |            | Prompt for a one-time passcode to login                           |
| --sso-passcode        |            | One-time passcode                                                 |


>CredHub CLI

```shell
user$ credhub login -s https://10.0.0.6:8844 --client-name=some-name --client-secret=some-secret
Setting the target url: https://10.0.0.6:8844
Login Successful
```

## Api

Get or set the CredHub API target where commands are sent. The api command without any flags will return the current target. If --ca-cert or
--skip-tls-validation are provided, these preferences will be cached for future requests.

| Long Flag             | Short Flag | Description                                                       |
|-----------------------|------------|-------------------------------------------------------------------|
| --server              | -s         | URI of API server to target [$CREDHUB_SERVER]                     |
| --ca-cert             |            | Trusted CA for API and UAA TLS connections [$CREDHUB_CA_CERT]     |
| --skip-tls-validation |            | Skip certificate validation of the API endpoint. Not recommended! |

>CredHub CLI

```shell
user$ credhub api --server https://10.0.0.6:8844
Setting the target url: https://10.0.0.6:8844
```

## Logout

Discard authenticated session. Refresh token revocation will be attempted for password grants.

>CredHub CLI

```shell
user$ credhub logout
Logout Successful
```