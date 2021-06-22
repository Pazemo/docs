# Recipients

## Create Recipients

Create a Recipients to receive withdrawal. You can add recipients with 2 ways, directly from your `Withdraw` dashboard or create from `Recipient Lists` dashboard.

### Create Recipient in Withdraw Dashboard

<a href="https://raw.githubusercontent.com/Pazemo/docs/main/source/images/add-recipients-withdraw.jpg" target="_blank" title="Click To View Full Screen Image In New Tab"><img src="https://raw.githubusercontent.com/Pazemo/docs/main/source/images/add-recipients-withdraw.jpg"></a>

After select currency account, select `New Address`, select available Banks, then input number and name for your new recipient, so you next time can use it from `Recipients list` easily.

### Create Recipient in Recipients Dashboard

<a href="https://raw.githubusercontent.com/Pazemo/docs/main/source/images/add-recipients.jpg" target="_blank" title="Click To View Full Screen Image In New Tab"><img src="https://raw.githubusercontent.com/Pazemo/docs/main/source/images/add-recipients.jpg"></a>

Another way to create Recipients, from sidebar menu click `Recipients`, `+ ADD NEW RECIPIENT` then select from available currencies and banks provided then fill account number and label.

> Example Request:

```shell
curl -X 'POST' \
  'http://api.stg.pazemo.com/beneficiaries' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "updatedTime": "2019-08-24T14:15:22Z",
  "accountId": "string",
  "bankId": "string",
  "address": "string",
  "email": "string",
  "label": "string",
  "type": "personal"
}'
```

> Example Response:

```json
{
  "id": 0,
  "accountId": "string",
  "bankId": "string",
  "address": "string",
  "name": "string",
  "email": "string",
  "label": "string",
  "status": "pending",
  "type": "personal"
}
```
Create New Recipient

**Request**

<code>POST http://api.stg.pazemo.com/beneficiaries</code>

Field | Description | Format
--------- | ------- | -----------
updatedTime | Updated Time | "yyyy-mm-dd".
accountId | Account ID | Text.
bankId | Bank ID | Text.
address | Address | Text.
name | Name | Text.
email | Email | Text.
label | Label | Text.
status | Status | Text.
type | Type | Text.

**Response**

Field | Description | Format
--------- | ------- | -----------
id | Recipient ID | Text.
accountId | Account ID | Text.
bankId | Bank ID | Text.
address | Address | Text.
name | Name | Text.
email | Email | Text.
label | Label | Text.
status | Status | Text.
type | Type | Text.