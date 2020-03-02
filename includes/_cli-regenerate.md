# Regenerating Credentials

## Regenerate

Set a credential with a generated value using the same attributes as the stored value

> CredHub CLI

```shell
user$ credhub regenerate --name '/example-password'
id: 67fc3def-bbfb-4953-83f8-4ab0682ad675
name: /example-password
type: password
value: 3t6Y2OFP0jQIcLnki1h7p3NtSfDx4l9bamr1ja6R
version_created_at: 2017-01-01T04:07:18Z
```

## Bulk Regenerate

Recursively regenerate all certificates signed by the provided certificate

> CredHub CLI

```shell
user$ credhub bulk-regenerate --signed-by /bosh-maestro/zookeeper/tom-ca
regenerated_credentials:
- /bosh-maestro/zookeeper/tom-leaf
```
