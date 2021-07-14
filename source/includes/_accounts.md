# Accounts

Create a Multy-Currency Account: Indonesian Rupiah (IDR), US Dollar (USD), Singapore Dollar (SGD), Malaysian Ringgit (MYR), Euro (EUR).

<img src="https://raw.githubusercontent.com/Pazemo/docs/main/source/images/account-list.jpg">

## Create Account

You can create account from sidebar menu and click `+ New Account`, then select from available currencies provided.

<img src="https://raw.githubusercontent.com/Pazemo/docs/main/source/images/create-account.jpg">

> Example Request:

```shell
   curl -X POST 'http://api.stg.pazemo.com/users/{userId}/accounts' \
        -H "Content-Type: application/json" \
        -H "Authorization: Bearer <your api token>"
        -d '{
             "currencyId": "string",
             "number": "string"
            }'
```

> Example Response:

```json
{
  "id": "string",
  "createdTime": "2019-08-24T14:15:22Z",
  "updatedTime": "2019-08-24T14:15:22Z",
  "currencyId": "string",
  "number": "string"
}
```

**Request**

<code>POST http://api.stg.pazemo.com/users/{userId}/accounts</code>

Field | Description | Format
--------- | ------- | -----------
userID | User ID | Text.
currencyId | Currency ID | Text.
number | Account Number | Text.

**Response**

Field | Description | Format
--------- | ------- | -----------
id | Account ID | Text.
createdTime | Creation Date | "yyyy-mm-dd".
updatedTime | Update Date | "yyyy-mm-dd".
currencyId | Currency ID | Text.
number | Account Number | Text.

## Get Accounts Info

Get information from all your available multy-currency accounts.

> Example Request:

```shell
   curl -X GET 'http://api.stg.pazemo.com/users/{userId}/accounts' \
        -H "Accept: application/json" \
        -H "Authorization: Bearer <your api token>"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'http://api.stg.pazemo.com/users/{userId}/accounts',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
  CURLOPT_HTTPHEADER => array(
    'Authorization: Bearer'.' '.<your api token>
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

```

> Example Response:

```json
[
    {
        "id": "string",
        "createdTime": "2021-06-11T03:56:25.871Z",
        "updatedTime": "2021-06-11T03:56:25.871Z",
        "userId": "string",
        "currencyId": "USD",
        "number": "112456475114",
        "balance": 0,
        "locked": 0
    },
    {
        "id": "string",
        "createdTime": "2021-06-11T03:56:17.167Z",
        "updatedTime": "2021-06-11T03:56:17.168Z",
        "userId": "string",
        "currencyId": "IDR",
        "number": "11286762273",
        "balance": 948775.42,
        "locked": -84311
    },
    {
        "id": "string",
        "createdTime": "2021-06-11T03:56:30.137Z",
        "updatedTime": "2021-06-11T03:56:30.137Z",
        "userId": "string",
        "currencyId": "SGD",
        "number": "112826187955",
        "balance": 9.1,
        "locked": 0
    }
]
```

**Request**

<code>GET http://api.stg.pazemo.com/users/{userId}/accounts</code>

Field | Description | Format
--------- | ------- | -----------
userID | User ID | Text.

**Response**

Field | Description | Format
--------- | ------- | -----------
id | Account ID | Text.
createdTime | Creation Date | "yyyy-mm-dd".
updatedTime | Update Date | "yyyy-mm-dd".
currencyId | Currency ID | Text.
number | Account Number | Text.
balance | Account Balance | Number.

## Get Account Info by ID

Get information from your accounts by ID

> Example Request:

```shell
   curl -X GET 'http://api.stg.pazemo.com/users/{userId}/accounts/{id}' \
        -H "Accept: application/json" \
        -H "Authorization: Bearer <your api token>"
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'http://api.stg.pazemo.com/users/{userId}/accounts/{id}',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
  CURLOPT_HTTPHEADER => array(
    'Authorization: Bearer'.' '.<your api token>
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

```

> Example Response:

```json
{
    "id": "string",
    "createdTime": "2021-06-11T03:56:25.871Z",
    "updatedTime": "2021-06-11T03:56:25.871Z",
    "userId": "string",
    "currencyId": "USD",
    "number": "112456475114",
    "balance": 0,
    "locked": 0
}
```

**Request**

<code>GET http://api.stg.pazemo.com/users/{userId}/accounts/{id}</code>

Field | Description | Format
--------- | ------- | -----------
userID | User ID | Text.
id | Account ID | Text.

**Response**

Field | Description | Format
--------- | ------- | -----------
id | Account ID | Text.
createdTime | Creation Date | "yyyy-mm-dd".
updatedTime | Update Date | "yyyy-mm-dd".
currencyId | Currency ID | Text.
number | Account Number | Text.
balance | Account Balance | Number.

