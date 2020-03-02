# Finding Credentials

## Find by Partial Name 

This request retrieves a list of stored credential names which contain the search.

>CredHub CLI

```shell
user$ credhub find --name-like 'password'
credentials: 
- name: /password1
  version_created_at: 2017-05-09T21:09:26Z
- name: /test/example/password
  version_created_at: 2017-05-09T21:09:07Z
```

## Find by Path

This request retrieves a list of stored credential names which are within the specified path.

> CredHub CLI

```shell
user$ credhub find --path '/director-name/deployment-name'
credentials:
- name: /director-name/deployment-name/db-password
  version_created_at: 2017-05-09T21:09:26Z
- name: /director-name/deployment-name/user-password
  version_created_at: 2017-05-09T21:09:07Z
- name: /director-name/deployment-name/api-tls
  version_created_at: 2017-05-10T11:13:07Z
```