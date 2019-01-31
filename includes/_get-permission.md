# Get Permissions

## Get by path and actor

> CredHub
CLI

``` shell
[not supported]
```

> cURL

``` shell
curl 'http://localhost:8080/api/v2/permissions?path=some-path&actor=some-actor' \
    -i -X GET \
    -H 'Content-Type: application/json'
```

``` json
{
  "path" : "some-path",
  "operations" : [ ],
  "actor" : "some-actor",
  "uuid" : "48faba92-5492-3e23-b262-75e30a7ddb6a"
}
```

This request retrieves a permission by path and actor.

### HTTP Request

`GET: /api/v2/permissions?path=some-path&actor=some-actor`

### Request Parameters

| Parameter | Default | Required | Type   | Description          |
| --------- | ------- | -------- | ------ | -------------------- |
| path      | none    | yes      | string | The credential path  |
| actor     | none    | yes      | string | The credential actor |
