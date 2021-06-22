# Withdraw

Pazemo can be added as a withdraw option on your site for beneficiaries to receive their withdraw through to a bank account, you can choose from your bank, from recipients list or add new recipients.

Before you can request a withdraw, make sure you have create Multy-Currency accounts and add proper recipients, for example if you want to withdraw to Indonesian Bank, you have to create IDR account or exchange from another account (USD, SGD, MYR, EUR) to IDR.

From your dashboard, go to `Withdraw` tab from sidebar menu, select available currency accounts, recipients, fill amount and click `WITHDRAW IDR` button to process your withdraw.

<a href="https://raw.githubusercontent.com/Pazemo/docs/main/source/images/withdraw.jpg" target="_blank" title="Click to View In New Tab"><img src="https://raw.githubusercontent.com/Pazemo/docs/main/source/images/withdraw.jpg"></a>

## Create Withdraw

> Example Request:

```shell
curl  -X POST "http://api.stg.pazemo.com/accounts/{accountId}/withdraw" \
      -H "Accept: application/json" \
      -H "Authorization: Bearer <your api token>"
      -d "{
  "id": "string",
  "updatedTime": "2019-08-24T14:15:22Z",
  "accountId": "string",
  "address": "string",
  "addressName": "string",
  "amount": 0,
  "notes": "string",
  "prefix": "string",
  "beneficiaryId": 0,
  "reference": "string",
  "referenceData": {}
}"
```

> The above command returns JSON structured like this:

```json
{
  "id": "string",
  "createdTime": "2019-08-24T14:15:22Z",
  "updatedTime": "2019-08-24T14:15:22Z",
  "accountId": "string",
  "transactionId": 0,
  "status": "pending",
  "network": "flip",
  "address": "string",
  "addressName": "string",
  "amount": 0,
  "feeAmount": 0,
  "notes": "string",
  "prefix": "string",
  "beneficiaryId": 0,
  "reference": "string",
  "referenceData": {}
}
```

**Request**

<code>POST http://api.stg.pazemo.com/accounts/{accountId}/withdraw</code>

Field | Description | Format
--------- | ------- | -----------
accountId | Account ID | Text.
id | Withdraw ID | Text.
updatedTime | Update Date | "yyyy-mm-dd".
address | Address | Text.
adressName | Address Name | Text.
amount | Amount | Number.
notes | Notes | Text.
prefix | Prefix | Text.
beneficiaryId | Beneficiary ID | Number.
reference | Reference | Text.
referenceData | Reference Data | Object.

**Response**

Field | Description | Format
--------- | ------- | -----------
id | Withdraw ID | Text.
createdTime | Creation Date | "yyyy-mm-dd".
updatedTime | Update Date | "yyyy-mm-dd".
accountId | Account ID | Text.
transactionId | Transaction ID | Number.
status | WIthdraw Status | Text.
network | Network Name | Text.
address | Address | Text.
amount | Amount | Number.
feeAmount | Fee Amount | Number.
notes | Notes | Text.
prefix | Prefix | Text.
beneficiaryId | Beneficiary ID | Number.
reference | Reference | Text.
referenceData | Reference Data | Object.

## Confirmation

> Example Request:

```shell
curl -X 'POST' \
  'http://api.stg.pazemo.com/accounts/{accountId}/withdraw/{id}/confirm' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
"authorizationCode": "string"
}'
```

> Example Response:

```json
{
  "id": "string",
  "createdTime": "2019-08-24T14:15:22Z",
  "updatedTime": "2019-08-24T14:15:22Z",
  "accountId": "string",
  "transactionId": 0,
  "status": "pending",
  "network": "flip",
  "address": "string",
  "addressName": "string",
  "amount": 0,
  "feeAmount": 0,
  "notes": "string",
  "prefix": "string",
  "beneficiaryId": 0,
  "reference": "string",
  "referenceData": {}
}
```
Withdraw Confirmation

**Request**

<code>POST http://api.stg.pazemo.com/accounts/{accountId}/withdraw/{id}/confirm</code>

Field | Description | Format
--------- | ------- | -----------
accountID | Account ID | Text.
ID | ID | Text.
authorizationCode | Autorization Code | Text.

**Response**

Field | Description | Format
--------- | ------- | -----------
id | Withdraw ID | Text.
createdTime | Creation Date | "yyyy-mm-dd".
updatedTime | Update Date | "yyyy-mm-dd".
accountId | Account ID | Text.
transactionId | Transaction ID | Number.
status | WIthdraw Status | Text.
network | Network Name | Text.
address | Address | Text.
amount | Amount | Number.
feeAmount | Fee Amount | Number.
notes | Notes | Text.
prefix | Prefix | Text.
beneficiaryId | Beneficiary ID | Number.
reference | Reference | Text.
referenceData | Reference Data | Object.

## Cancellation

> Example Request:

```shell
curl -X 'POST' \
  'http://api.stg.pazemo.com/accounts/{accountId}/withdraw/{id}/cancel' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
"authorizationCode": "string"
}'
```

> Example Response:

```json
{
  "id": "string",
  "createdTime": "2019-08-24T14:15:22Z",
  "updatedTime": "2019-08-24T14:15:22Z",
  "accountId": "string",
  "transactionId": 0,
  "status": "pending",
  "network": "flip",
  "address": "string",
  "addressName": "string",
  "amount": 0,
  "feeAmount": 0,
  "notes": "string",
  "prefix": "string",
  "beneficiaryId": 0,
  "reference": "string",
  "referenceData": {}
}
```
Withdraw Confirmation

**Request**

<code>POST http://api.stg.pazemo.com/accounts/{accountId}/withdraw/{id}/confirm</code>

Field | Description | Format
--------- | ------- | -----------
accountID | Account ID | Text.
ID | ID | Text.
authorizationCode | Autorization Code | Text.

**Response**

Field | Description | Format
--------- | ------- | -----------
id | Withdraw ID | Text.
createdTime | Creation Date | "yyyy-mm-dd".
updatedTime | Update Date | "yyyy-mm-dd".
accountId | Account ID | Text.
transactionId | Transaction ID | Number.
status | WIthdraw Status | Text.
network | Network Name | Text.
address | Address | Text.
amount | Amount | Number.
feeAmount | Fee Amount | Number.
notes | Notes | Text.
prefix | Prefix | Text.
beneficiaryId | Beneficiary ID | Number.
reference | Reference | Text.
referenceData | Reference Data | Object.