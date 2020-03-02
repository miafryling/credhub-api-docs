#Import/Export Credentials

## Bulk Export

> CredHub CLI

```shell
user$ credhub export --file export.yml
```

This CLI command gets multiple credentials and exports them to either standard out, or a file. The output will be in yaml format, with the key `credentials` whose value is a list of credential objects. Each credential will contain a name, type and value. An example is shown to the right. This file is compatible with the bulk import process.

Use `--file` to specify a file to write the export to. Use `--path` to specify a path, which will restrict the credentials exported to those with a prefix matching the given path.


## Bulk Import

> CredHub CLI

```shell
user$ credhub import --file import.yml
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

id: 2ba73fbd-439e-40ef-b005-0e1db8815063
name: /example-password
type: password
value: SqFcE2c0AuRvet2YhrxdFbPtkBmjiq
version_created_at: 2017-01-01T04:07:28Z

id: 22a1e87b-ba0b-4bc9-bb26-4e5fc5fb1b2f
name: /example-value
type: value
value: sample
version_created_at: 2017-01-01T04:07:38Z

Import complete.
Successfully set: 3
Failed to set: 0
```

This CLI command sets multiple credentials from an import file. The import file must be in yaml format, with the key `credentials` whose value is a list of credential objects. Each credential must contain a name, type and value. An example is shown to the right.