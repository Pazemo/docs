# Users

## Get by ID

>Example Request:

```shell
curl -X GET "http://api.stg.pazemo.com/users/{userid}" \
      -H "Accept: application/json" \
      -H "Authorization: Bearer <your api token>" \
```
>Example Response:

```json
{
  "id": "string",
  "createdTime": "1970-01-01T00:00:00.000Z",
  "updatedTime": "1970-01-01T00:00:00.000Z",
  "status": "string",
  "email": "user@example.com",
  "mobile": "string",
  "name": "string",
  "partnerId": "string",
  "roles": [
    "string"
  ],
  "configs": {}
}
```
Get authenticated user details by user id. Response includes also personal user profile info.

### Request

<code>GET http://api.stg.pazemo.com/users/{userid}</code>

### Response

Field | Description | Format
--------- | ------- | -----------
id | User ID| string
createdTime | Created Date | date-time
updatedTime | Updated Date | date-time
status | Status | string
email | User email | email
mobile | User mobile | string
name | User name | string
partnerId | Parter ID | string
roles | User Role | string

## Get the currently logged in user

>Example Request:

```shell
curl    -X GET "http://api.stg.pazemo.com/users/me" \
        -H "Accept: application/json" \
        -H "Authorization: Bearer <your api token>" \
```

>Example Response:

```json
{
  "id": "string",
  "email": "string",
  "name": "string"
}
```

Get authenticated user details for the user's token submitted in the Authorization header. Response includes also personal user profile info.

### Request

<code>GET http://api.stg.pazemo.com/users/me</code>

### Response

Field | Description | Format
--------- | ------- | -----------
id | User ID| string
email | User email | email
name | User name | string