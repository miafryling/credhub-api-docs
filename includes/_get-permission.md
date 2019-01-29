# Get Permissions

> CredHub
CLI

``` shell
[not supported]
```

> cURL

``` bash
$ curl 'http://localhost:8080/api/v2/permissions?path=/some-path&actor=some-actor' -i -X GET \
    -H 'Content-Type: application/json'
```

    {
      "path" : "/some-path",
      "operations" : [ ],
      "actor" : "some-actor",
      "uuid" : "48faba92-5492-3e23-b262-75e30a7ddb6a"
    }

This request returns the permissions of a path given the permission
UUID.

## HTTP Request

``` http
GET /api/v2/permissions?path=/some-path&actor=some-actor HTTP/1.1
Content-Type: application/json
Host: localhost:8080
```

## Request Parameters

| Parameter | Description          |
| --------- | -------------------- |
| `path`    | The credential path  |
| `actor`   | The credential actor |

## HTTP Response

``` http
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
Content-Length: 125

{
  "path" : "/some-path",
  "operations" : [ ],
  "actor" : "some-actor",
  "uuid" : "48faba92-5492-3e23-b262-75e30a7ddb6a"
}
```

## Response Fields

| Path         | Type     | Description                                                                                                                            |
| ------------ | -------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `path`       | `String` | The path that represents the credential                                                                                                |
| `operations` | `Array`  | The operations that are permitted to be done with the credential. Available operations are: read, write, delete, read\_acl, write\_acl |
| `actor`      | `String` | The username that can interact with the credential                                                                                     |
| `uuid`       | `String` | The unique identifier that represents the credential                                                                                   |
