# Users

## Get the currently logged in user

Get authenticated user details for the loged in user's. Response includes also personal user profile info.

>Example Request:

```shell
curl    -X GET "http://api.stg.pazemo.com/users/me" \
        -H "Accept: application/json" \
        -H "Authorization: Bearer <your api token>" \
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'http://api.stg.pazemo.com/users/me',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
  CURLOPT_HTTPHEADER => array(
    'Authorization: Bearer <your api token>'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

```

>Example Response:

```json
{
  "id": "string",
  "email": "string",
  "name": "string"
}
```

### Request

<code>GET http://api.stg.pazemo.com/users/me</code>

### Response

Field | Description | Format
--------- | ------- | -----------
id | User ID| string
email | User email | email
name | User name | string

## Get by ID

Get authenticated user details by user id. Response includes also personal user profile info.

>Example Request:

```shell
curl -X GET "http://api.stg.pazemo.com/users/{userid}" \
      -H "Accept: application/json" \
      -H "Authorization: Bearer <your api token>" \
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'http://api.stg.pazemo.com/users/{userid}',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
  CURLOPT_HTTPHEADER => array(
    'Authorization: Bearer <your api token>'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

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