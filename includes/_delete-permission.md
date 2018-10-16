# Delete Permissions

> CredHub CLI

```shell
[not supported]
```

> cURL

```shell
curl "https://example.com/api/v2/permissions/example-permission-uuid" \
  -X DELETE \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "uuid": "example-permission-uuid",
  "path": "/example-specific-credential",
  "actor": "uaa-user:106f52e2-5d01-4675-8d7a-c05ff9a2c081",
  "operations": ["read","write"]
}
```

This request deletes a permission.

### HTTP Request

`DELETE: https://example.com/api/v2/permissions/example-permission-uuid`

### Query Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
uuid | none | yes | string | The UUID of the permission that was returned when permission was created.

<sup>1</sup> Authentication-specific identities [explained here.](https://github.com/cloudfoundry-incubator/credhub/blob/master/docs/authentication-identities.md)

