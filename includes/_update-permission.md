# Add Permissions

> CredHub CLI

```shell
[not supported]
```

> cURL

```shell
curl "https://example.com/api/v2/permissions/example-permission-uuid" \
  -X PUT \
  -d '
  {
    "path": "/example-directory/example-credential",
    "actor": "uaa-user:106f52e2-5d01-4675-8d7a-c05ff9a2c081"
    "operations": ["read", "write"]
  }' \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "uuid": "example-permission-uuid",
  "path": "/example-directory/example-credential",
  "actor": "uaa-user:106f52e2-5d01-4675-8d7a-c05ff9a2c081",
  "operations": ["read","write"]
}
```

```shell
curl "https://example.com/api/v2/permissions/example-permission-uuid" \
  -X PATCH \
  -d '
  {
    "operations": ["read", "write"]
  }' \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "uuid": "example-permission-uuid",
  "path": "/example-directory/example-credential",
  "actor": "uaa-user:106f52e2-5d01-4675-8d7a-c05ff9a2c081",
  "operations": ["read","write"]
}
```

This request updates the operations for a permission keeping the same path and actor. It replaces the operations that were set before with the new operations that are provided in the request.

### HTTP Request

`POST: https://example.com/api/v2/permissions`

### Request Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
uuid      | none | yes | string | The permission uuid that was returned when a permission was created
path      | none | yes | string | The path of the permission you would like to update the operations for
actor | none | yes | string | The actor that you would like to update the operations for
operations | none | yes | array of strings | The new list of operations you would like to update this permission for

<sup>1</sup> Authentication-specific identities [explained here.](https://github.com/cloudfoundry-incubator/credhub/blob/master/docs/authentication-identities.md) <br>
<sup>2</sup> Supported operations: read, write, delete, read_acl, write_acl

