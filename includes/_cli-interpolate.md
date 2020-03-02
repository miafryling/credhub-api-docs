# Interpolating Credentials

Fill a template with values returned from CredHub.

Uses double-paren placeholders in the style of the bosh cli. Example:

something-stored-in-credhub: ((path/to/var))  
something-else: static value

In the above example, the whole value of the cred will be inserted.

If you want just the certificate value, you'd need to use ((path/to/var.certificate)),
which would only have the specified field. Example:

certificate: ((path/to/var.certificate))   
private_key: ((path/to/var.private_key))  

If the prefix flag is provided, the given prefix will be prepended
to any credentials that do not start with the '/' character.

Note: There cannot be spaces inside the parentheses

| Long Flag      | Short Flag | Description                                                                                |
|----------------|------------|--------------------------------------------------------------------------------------------|
| --file         | -f         | Path to the file to interpolate                                                            |
| --prefix       | -p         | Prefix to be applied to credential paths. Will not be applied to paths that start with '/' |
| --skip-missing | -s         | allow skipping missing params                                                              |

> CredHub CLI

```shell
user$ credhub interpolate -f /tmp/creds.yml
db-password: j8aej715TuQZGzQr8FBdnn5hQT2fOp
```