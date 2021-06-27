# Pings

## Check

>Example Request:

```shell
curl -X GET "http://api.stg.pazemo.com/check" \
     -H "Accept: application/json" \
     -H "Authorization: Bearer <your api token>" \
```

>Example Response:

```json
{
  "greeting": "string",
  "date": "string",
  "url": "string",
  "headers": {
    "Content-Type": "string"
  }
}
```
Check server

### Request

<code>GET http://api.stg.pazemo.com/check</code>

### Response

Field | Description | Format
--------- | ------- | -----------
greeting | Greeting| string
date | Date | date-time
url | URL | date-time
Content-Type | Content Type | string

## Ping

>Example Request:

```shell
curl    -X GET "http://api.stg.pazemo.com/ping" \
        -H "Authorization: Bearer <your api token>" 
```

>Example Response:

```json
Return value of PingController.ping
```

Ping the server and retrieve the server version.

### Request

<code>GET http://api.stg.pazemo.com/ping</code>

### Response

Return value of PingController.ping

## Ping Queue

>Example Request:

```shell
curl    -X GET "http://api.stg.pazemo.com/pingQueue" \
        -H "Accept: application/json" \
        -H "Authorization: Bearer <your api token>" \
```

>Example Response:

```json
{
  "greeting": "string",
  "date": "string",
  "url": "string",
  "headers": {
    "Content-Type": "string"
  }
}
```

Get Ping Queue

### Request

<code>GET http://api.stg.pazemo.com/pingQueue</code>

### Response

Field | Description | Format
--------- | ------- | -----------
greeting | Greeting| string
date | Date | date-time
url | URL | date-time
Content-Type | Content Type | string