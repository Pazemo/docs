# Accounts

Create a Multy-Currency Account: Indonesian Rupiah (IDR), US DOllar (USD), Singapore Dollar (SGD), Malaysian Ringgit (MYR), Euro (EUR).

<img src="https://raw.githubusercontent.com/Pazemo/docs/main/source/images/account-list.jpg">

## Create Account

You can create account from sidebar menu and click `+ New Account`, then select from available currencies provided.

<img src="https://raw.githubusercontent.com/Pazemo/docs/main/source/images/create-account.jpg">

> Example Request:

```shell
curl -X 'POST' \
  'http://api.stg.pazemo.com/users/{userId}/accounts' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
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
Create New Account

**Request**

<code>POST http://api.stg.pazemo.com/users/{userId}/accounts</code>

Field | Description | Format
--------- | ------- | -----------
userID | User ID | Text.
number | number | Text.

**Response**

Field | Description | Format
--------- | ------- | -----------
id | Account ID | Text.
createdTime | Creation Date | "yyyy-mm-dd".
updatedTime | Update Date | "yyyy-mm-dd".
currencyId | Currency ID | Text.
number | Number | Text.