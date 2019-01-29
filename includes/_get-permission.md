# Get Permissions

> CredHub CLI

```shell
[not supported]
```

> cURL

```shell
curl "https://example.com/api/v2/permissions/example-permission-uuid" \
  -X GET \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
   "path":"/example-credential-namespace",
   "operations":[
      "read",
      "write"
   ],
   "actor":"uaa-user:f6b2f8f6-1654-4a5d-aba4-c4d024a43560",
   "uuid":"example-permission-uuid"
} 
```

This request returns the permissions of a path given the permission UUID. 

### HTTP Request

`GET: https://example.com/api/v2/permissions`

### Query Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
uuid | none | yes | string | UUID of permission, that was returned when permission was created.
