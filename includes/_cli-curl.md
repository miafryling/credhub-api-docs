# Curl

Make an arbitrary request to the targeted CredHub server

| Long Flag | Short Flag | Description                                     |
|-----------|------------|-------------------------------------------------|
| --path    | -p         | The server endpoint to make the request against |
| --fail    | -f         | Fail silently (no output at all) on HTTP errors |
|           | -X         | HTTP method (default: GET)                      |
|           | -d         | HTTP data to include in the request body        |
|           | -i         | Include the response headers in the output      |

>CredHub CLI

```shell
user$ credhub curl -p api/v1/certificates
{
  "certificates": [
    {
      "id": "933cd14f-3d3b-4637-a61b-474648fad0ca",
      "name": "/bosh-maestro/zookeeper/tom-leaf",
      "signed_by": "/bosh-maestro/zookeeper/tom-ca",
      "signs": [],
      "versions": [
        {
          "certificate_authority": false,
          "expiry_date": "2021-03-13T15:15:13Z",
          "generated": true,
          "id": "410148ab-5479-4c26-8036-eb9dfd825c68",
          "self_signed": false,
          "transitional": false
        },
        {
          "certificate_authority": false,
          "expiry_date": "2021-03-12T14:25:06Z",
          "generated": true,
          "id": "c4432134-79cc-4c70-8932-8d5e911097f5",
          "self_signed": false,
          "transitional": false
        }
       ]
    }
  ]
}
```