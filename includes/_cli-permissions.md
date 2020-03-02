# Permissions

Permissions can be defined for namespaces as well as on explicit credential names. Permissions are additive – if any rule exists authorizing a user to take an action, then the action will be permitted.

actor names must be prefixed with the [authentication type](https://github.com/cloudfoundry-incubator/credhub/blob/master/docs/authentication-identities.md#primary-identifiers):  
- mtls-app:APP-GUID (i.e. mtls-app:fdbeb2d4-b601-4a0d-91e8-7e38dde426f7)  
- uaa-user:USER-GUID (i.e. uaa-user:2ae1621a-bb35-4bb7-946a-4761d3b16a04)  
- uaa-client:CLIENT-NAME (i.e. uaa-client:director_to_credhub)  

## Setting/Updating Permissions
This request sets permissions for a path for an actor. You can add permission for a specific credential on a path, as well as all items under a path by using the * syntax.

| Long Flag    | Short Flag | Description                                                    |
|--------------|------------|----------------------------------------------------------------|
| --actor      | -a         | Name of the actor to grant permissions for                     |
| --path       | -p         | Name of path to grant permissions for                          |
| --operations | -o         | Operations allowed (comma separated list)(options: read, write, delete, read_acl, write_acl) |

> CredHub CLI

```shell
user$ credhub set-permission -a uaa-user:2ae1621a-bb35-4bb7-946a-4761d3b16a04 -p /some-path/* -o read,write,delete,read_acl,write_acl
actor: uaa-user:2ae1621a-bb35-4bb7-946a-4761d3b16a04
operations:
- read
- write
- delete
- read_acl
- write_acl
path: /some-path/*
uuid: cf395f8e-130f-48d8-849e-2250e2886490
```

## Getting Permissions

This request retrieves a permission given the path and actor.

| Long Flag | Short Flag | Description                              |
|-----------|------------|------------------------------------------|
| --actor   | -a         | Name of the actor to get permissions for |
| --path    | -p         | Name of path to get permissions for      |

> CredHub CLI

```shell
user$ credhub get-permission -a uaa-user:2ae1621a-bb35-4bb7-946a-4761d3b16a04 -p /some-path/*
actor: uaa-user:2ae1621a-bb35-4bb7-946a-4761d3b16a04
operations:
- read
- write
- delete
- read_acl
- write_acl
path: /some-path/*
uuid: cf395f8e-130f-48d8-849e-2250e2886490
```

## Deleting Permissions

Delete permissions for an actor on a given path

| Long Flag | Short Flag | Description                              |
|-----------|------------|------------------------------------------|
| --actor   | -a         | Name of the actor to delete permissions for |
| --path    | -p         | Name of path to delete permissions for      |

> CredHub CLI

```shell
user$ credhub delete-permission -a uaa-user:2ae1621a-bb35-4bb7-946a-4761d3b16a04 -p /some-path/*
actor: uaa-user:2ae1621a-bb35-4bb7-946a-4761d3b16a04
operations:
- read
- write
- delete
- read_acl
- write_acl
path: /some-path/*
uuid: cf395f8e-130f-48d8-849e-2250e2886490
```

