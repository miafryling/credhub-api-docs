# Get Permissions

> CredHub
CLI

``` shell
[not supported]
```

> cURL

``` bash
$ curl 'http://localhost:8080/api/v2/permissions?path=some-path&actor=some-actor' -i -X GET \
    -H 'Content-Type: application/json'
```

``` bash
{
  "path" : "some-path",
  "operations" : [ ],
  "actor" : "some-actor",
  "uuid" : "48faba92-5492-3e23-b262-75e30a7ddb6a"
}
```

This request returns the permissions of a path given the permission
UUID.

## HTTP Request

``` http
GET /api/v2/permissions?path=some-path&actor=some-actor HTTP/1.1
Content-Type: application/json
Host: localhost:8080
```

## Request Parameters

| Parameter | Default | Required | Type   | Description          |
| --------- | ------- | -------- | ------ | -------------------- |
| path      | none    | yes      | string | The credential path  |
| actor     | none    | yes      | string | The credential actor |
