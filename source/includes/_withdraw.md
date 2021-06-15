# Withdraw

## Withdraw flows

Pazemo can be added as a withdraw option on your site for beneficiaries to receive their withdraw through to an bank account, you can choose from recipient list or add new address .

## Get Account ID

> Example Request:

```shell
curl -X GET http://api.stg.pazemo.com/users/{userId}/accounts \
     -H "Accept: application/json" \
     -H "Authorization: Bearer <your api token>"
```
> The above command returns JSON structured like this:

```json
[
  {
    "id": "string",
    "createdTime": "1970-01-01T00:00:00.000Z",
    "updatedTime": "1970-01-01T00:00:00.000Z",
    "userId": "string",
    "currencyId": "string",
    "number": "string",
    "user": "https://api.stg.pazemo.com/openapi.json#/components/schemas/UserWithRelations",
    "currency": {
      "id": "string",
      "name": "string",
      "symbol": "string",
      "position": 0,
      "visible": false,
      "precision": 0,
      "iconUrl": "string",
      "countries": [
        "https://api.stg.pazemo.com/openapi.json#/components/schemas/CountryWithRelations"
      ],
      "base": [
        "https://api.stg.pazemo.com/openapi.json#/components/schemas/ForexRateWithRelations"
      ]
    },
    "transactions": [
      "https://api.stg.pazemo.com/openapi.json#/components/schemas/TransactionWithRelations"
    ]
  }
]
```

You only need to call this endpoint once to obtain your Account id. Account id values are required when making withdraws.

It’s recommended to always provide accountId when you’re creating new resources later. If you omit accountId then resource will by default belong to your personal profile.

**Request**

<code>GET http://api.stg.pazemo.com/users/{userId}/accounts</code>

**Response**

Personal Profile Fields

Field | Description | Format
--------- | ------- | -----------
id | Account id | Text.
createdTime | Creation Date | "yyyy-mm-dd".
updatedTime | Update Date | "yyyy-mm-dd".
userID | User ID | Text.
currencyID | Currency ID | Text.
number | Mobile Number | Text.
user |User | Text.

## Get Account ID

> Example Request:

```shell
curl -X 'POST' \
  'http://api.stg.pazemo.com/quotes' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "sendCurrencyId": "string",
  "receiveCurrencyId": "string",
  "sendAmount": 0,
  "rate": 0
}'
```

> Example Response:

```json
{
  "id": "string",
  "createdTime": "2021-06-09T10:22:50.378Z",
  "userId": "string",
  "sendCurrencyId": "string",
  "receiveCurrencyId": "string",
  "sendAmount": 0,
  "receiveAmount": 0,
  "status": "string",
  "rate": 0
}
```

**Request**

<code>POST https://api.stg.pazemo.com/quotes</code>

Field | Description | Format
--------- | ------- | -----------
sendCurrencyId | Currency Code | Text.
receiveCurrencyId | Currency Code | Text.
sendAmount | Send Amount | Decimal.

**Response**

The withdraw field is used to select the correct entry in the paymentOptions array in order to know which fees to display to your customer. Find the paymentOption that matches the withdraw field shown at the top level of the quote resource and payIn based on the settlement model the bank is using. By default this is BANK_TRANSFER, unless you are using a prefunded or bulk settlement model.

When showing the price of a transfer, always show the total fees of a payment option.

Field | Description | Format
--------- | ------- | -----------
id | Personal profile id | Text.
createdTime | Creation Date | "yyyy-mm-dd".
userId | User ID | Text.
sendCurrencyId | Currency Code | Text.
receiveCurrencyId | Currency Code | Text.
sendAmount | Send Amount | Decimal.
receiveAmount | Receive Amount| Decimal.
status | Status | Text.

## Create recipient account

> Example Request:

```shell
curl -X 'POST' \
  'http://api.stg.pazemo.com/users/12345/accounts' \
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
  "createdTime": "2021-06-09T11:27:45.513Z",
  "updatedTime": "2021-06-09T11:27:45.513Z",
  "currencyId": "string",
  "number": "string"
}
```

Recipient is a person or institution who is the ultimate beneficiary of your payment.

Recipient bank account details are different for different currencies. For example, you only need to know the IBAN number to send payments to most European and Nordic countries. But in order to send money to Canada, you’d need to fill out four fields: You recipient’s institution number, transit number, account number, and account type.

**Request**

<code>POST http://api.stg.pazemo.com/users/{userId}/accounts</code>

Field | Description | Format
--------- | ------- | -----------
sendCurrencyId | Currency Code | Text.
receiveCurrencyId | Currency Code | Text.
sendAmount | Send Amount | Decimal.

**Response**

Recipient id is needed for creating transfers in step 3

Field | Description | Format
--------- | ------- | -----------
id | Personal profile id | Text.
createdTime | Creation Date | "yyyy-mm-dd".
userId | User ID | Text.
sendCurrencyId | Currency Code | Text.
receiveCurrencyId | Currency Code | Text.
sendAmount | Send Amount | Decimal.
receiveAmount | Receive Amount| Decimal.
status | Status | Text.

## Create transfer

>Example Request:

```shell
curl -X 'POST' \
  'http://api.stg.pazemo.com/transfers' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "senderAccountId": "string",
  "receiverAccountId": "string",
  "quoteId": "string",
  "senderTransactionId": 0,
  "receiverTransactionId": 0
}'
```

> Example Response:

```json
{
"id": "string",
"createdTime": "2019-08-24T14:15:22Z",
"senderAccountId": "string",
"receiverAccountId": "string",
"quoteId": "string",
"senderTransactionId": 0,
"receiverTransactionId": 0
}
```

A transfer is a withdraw order you make to a recipient account based on a quote. Once created, a transfer will need to be funded within the next 14 days (7 days for email transfers) or it’ll automatically get cancelled.

**Request**

<code>POST http://api.stg.pazemo.com/transfers</code>

Field | Description | Format
--------- | ------- | -----------
senderAccountId | Account ID | Text.
receiverAccountId | Account ID | Text.
quoteId | Quote ID | Text.
senderTransactionId | Transaction | Number.
receiverTransactionId | Transaction | Number.

There are two options to deal with conditionally required fields:

- Always provide values for these fields
- Always call transfers-requirements endpoint and submit values only if indicated so

**Response**

Field | Description | Format
--------- | ------- | -----------
id | Personal profile id | Text.
createdTime | Creation Date | "yyyy-mm-dd".
senderAccountId | Account ID | Text.
receiverAccountId | Account ID | Text.
quoteId | Quote ID | Text.
senderTransactionId | Transaction | Number.
receiverTransactionId | Transaction | Number.


## Fund transfer

>Example Request:

```shell
curl -X POST http://api.stg.pazemo.com/accounts/{accountId}/transactions/{id} \
     -H "Authorization: Bearer <your api token>" \
     -H "Content-Type: application/json" \
     -d '{ 
          "type": "BALANCE"   
         }'
```

>Example Response:

```json
{
  "type": "BALANCE",
  "status": "COMPLETED",
  "errorCode": null
}
```

This API call is the final step for executing withdraws. Pazemo will now debit funds from your multi-currency account and start processing your withdraw. If your multi-currency account does not have the required funds to complete the action then this call will fail with an "insufficient funds" error.

Initial developer account has by default plentiful funds available for IDR, USD, SGD, MYR and EUR.
You can add new currencies to your account via the user interface.

You can then top up your new currencies by converting funds from other currencies.

Unless you are sending to a small number of recipients who you trust, it is recommended to implement the referenced measures for your integration.