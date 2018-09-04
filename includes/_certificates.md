# Certificates

### CA Rotation

CredHub offers support for zero-downtime rotation of certificate credentials by allowing certificates to have multiple "active" versions at the same time. 

The workflow at a high-level for transitioning to a new certificate is:

1. Regenerate your CA certificate with the `transitional` flag. This creates a new version that will _not_ be used for signing yet, but can be added to your servers trusted certificate lists.
1. Remove the transitional flag from the new certificate, and add it to the old certificate. This means that the new certificate will start to be used for signing, but the old one will remain as trusted.
1. Remove the transitional flag from the old certificate. Now that all your clients should have certificates signed by the new CA's certificate, the old one can be removed from your servers trusted lists.

### Step 1: Regenerate

First we'll need to get the ID of the certificate. Assuming you're logged in with the CredHub CLI, this curl -k command will get you the ID:

`curl "https://example.com/api/v1/certificates?name=[certificate-name]" -H "Content-Type: application/json" -H "Authorization: bearer [token]"`

Next, we use that ID to generate the new, transitional version:

`curl "https://example.com/api/v1/certificates/[certificate-id]/regenerate" -X POST -d '{"set_as_transitional": true}' -H "Content-Type: application/json" -H "Authorization: bearer [token]"`

You should now see that when you request the "current" versions of that credential, that both certificates are returned:

`curl "https://example.com/api/v1/data?name=[certificate-name]&current=true" -H "Content-Type: application/json" -H "Authorization: bearer [token]"`

### Step 2: Moving the transitional flag

To move the transitional flag off of the new certificate and onto the older version, we'll need to grab the older versions ID:

`curl "https://example.com/api/v1/data?name=[certificate-name]&current=true" -H "Content-Type: application/json" -H "Authorization: bearer [token]"`

Find the ID of the certificate that currently has `transitional: false`, and then pass it to the next command:

`curl "https://example.com/api/v1/certificates/[certificate-id]/update_transitional_version" -X PUT -d '{"version": "[Non-Transitional-ID]"}' -H "Content-Type: application/json" -H "Authorization: bearer [token]"`

You can confirm that now the two certificates have swapped:

`curl "https://example.com/api/v1/data?name=[certificate-name]&current=true" -H "Content-Type: application/json" -H "Authorization: bearer [token]"`

### Step 3: Removing the transitional flag

After you have regenerated all your client certificates to be signed by the new cert, you can safely remove the transitional flag from the old one:

`curl "https://example.com/api/v1/certificates/[certificate-id]/update_transitional_version" -X PUT -d '{"version": null}' -H "Content-Type: application/json" -H "Authorization: bearer [token]"`

You can now confirm that only one certificate is active:

`curl "https://example.com/api/v1/data?name=[certificate-name]&current=true" -H "Content-Type: application/json" -H "Authorization: bearer [token]"`


## Get All Certificates

> cURL

```shell
curl "https://example.com/api/v1/certificates" \
  -X GET \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "certificates": [
    {
      "id": "2993f622-cb1e-4e00-a267-4b23c273bf3d",
      "name": "/example-certificate"
    }
  ]
}
```

This request retrieves all certificates.

### HTTP Request

`GET: https://example.com/api/v1/certificates`

### Query Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
none | | | |


## Get Certificate by Name

> cURL

```shell
curl "https://example.com/api/v1/certificates?name=/example-certificate" \
  -X GET \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "certificates": [
    {
      "id": "2993f622-cb1e-4e00-a267-4b23c273bf3d",
      "name": "/example-certificate"
    }
  ]
}
```

This request retrieves a certificate by name. Exactly one value will be returned.

### HTTP Request

`GET: https://example.com/api/v1/certificates`

### Query Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
name | none | yes | string | Name of credential to retrieve


## Regenerate Certificate

>cURL

```shell
curl "https://example.com/api/v1/certificates/[certificate-ID]/regenerate" \
  -X POST \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json' \
  -d '{"set_as_transitional": true/false}'
```

```json
{
  "type": "certificate",
  "expiry_date": "2019-09-04T17:39:54Z",
  "transitional": true/false,
  "version_created_at": "2018-09-04T17:39:54Z",
  "id": "3e208a47-715d-4669-a3df-492b932a0c98",
  "name": "/example-certificate",
  "value": {
    "ca": "CA certificate",
    "certificate": "Certificate",
    "private_key": "Private-key"
  }
}
```

This regenerates a certificate. Only one version of a certificate may be transitional at a given time.


### HTTP Request

`POST: https://example.com/api/v1/certificates/[certificate-ID]/regenerate`

### Request Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
set_as_transitional | false | no | boolean | Make version transitional or not


## Update Transitional Version

>cURL

```shell
curl "https://example.com/api/v1/certificates/[certificate-ID]/update_transitional_version" \
  -X PUT \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json' \
  -d '{"version": "[certificate-version]"}'
```

```json
[
  {
    "type": "certificate",
    "expiry_date": "2019-09-04T17:51:45Z",
    "transitional": false,
    "version_created_at": "2018-09-04T17:51:45Z",
    "id": "3e208a47-715d-4669-a3df-492b932a0c98",
    "name": "/example-certificate",
    "value": {
      "ca": "CA certificate",
      "certificate": "Certificate",
      "private_key": "Private-key"
    }
  },
  {
    "type": "certificate",
    "expiry_date": "2019-09-04T17:52:40Z",
    "transitional": true,
    "version_created_at": "2018-09-04T17:52:40Z",
    "id": "be9ee5ca-69da-4e90-9d2d-b78a4a28625d",
    "name": "/example-certificate",
    "value": {
      "ca": "CA certificate",
      "certificate": "Certificate",
      "private_key": "Private-key"
    }
  }
]
```

This sets the given version of a certificate as transitional and marks the current transitional version, if one exists, as not transitional.

Setting `"version": null` will ensure no version is transitional.

Returns the latest certificate version in addition to the latest transitional version, if one exists.


### HTTP Request

`PUT: https://example.com/api/v1/certificates/[certificate-ID]/update_transitional_version`

### Request Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
version | none | yes | string | The version to make transitional

