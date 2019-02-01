# Get Permissions

## Get by ID

> CredHub
CLI

``` shell
[not supported]
```

> cURL

``` shell
curl 'http://localhost:8080/api/v2/permissions/abcd1234-ab12-ab12-ab12-abcdef123456' \
    -i -X GET \
    -H 'Content-Type: application/json'
```

``` json
{
  "path" : "some-path",
  "operations" : [ ],
  "actor" : "some-actor",
  "uuid" : "abcd1234-ab12-ab12-ab12-abcdef123456"
}
```

This request retrieves a permission given the UUID.

### HTTP Request

`GET: /api/v2/permissions/abcd1234-ab12-ab12-ab12-abcdef123456`

### Request Parameters

| Parameter | Default | Required | Type | Description |
| --------- | ------- | -------- | ---- | ----------- |

## Get by Path and Actor

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
  "uuid" : "abcd1234-ab12-ab12-ab12-abcdef123456"
}
```

This request retrieves a permission given the path and actor.

### HTTP Request

`GET: /api/v2/permissions?path=some-path&actor=some-actor`

### Request Parameters

| Parameter | Default | Required | Type   | Description          |
| --------- | ------- | -------- | ------ | -------------------- |
| path      | none    | yes      | string | The credential path  |
| actor     | none    | yes      | string | The credential actor |
