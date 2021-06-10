---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='https://pazemo.com/signup'>Sign Up for a Developer Key</a>
  - <a href='https://api.stg.pazemo.com/explorer/'>Pazemo API Explorer</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Pazemo Platform API

Welcome to the Pazemo Platform API documentation, You can explore the different ways to use our API and choose the right one for you below.

Pazemo API is organized around REST. We use built-in HTTP features and HTTP verbs and we return all responses in JSON.

- Payouts and Account Automation
- Banks
- Affiliates
- Receive Money
- Open Banking

> Base URL Open API:

```
https://api.stg.pazemo.com/
```

## Payouts and Account Automation

This lets you to automate how you use your Pazemo account. You can automate payments, connect your business tools, and create ways to manage your finances.

You can:

- Power your cross-border and domestic payouts with a single API integration.
- Pay out directly to bank accounts or email recipients.
- Monitor payments received to your Pazemo local bank details (AUD, EUR, GBP, NZD, USD, PLN).
- Get statements for balance reconciliation and accounting purposes.
- Fully automate transfer creation and track statuses.
- Always get the mid-market exchange and our low cost transparent fees.
- Use our platform to create and build your own tool to manage your finances

## Banks

Our bank integration lets banks build Pazemo payments seamlessly into their own desktop and mobile apps. Banks can also build their own native user experience directly onto our API, co-branded with Pazemo.

### What are the benefits for my bank?

- Provide your customers access to some of the fastest and cheapest cross-border payments available to - - consumers and businesses today.
- Offer competitive, fair, and transparent pricing to customers at the mid-market exchange rate.
- Reduce your operational costs of cross-border payments.
- Stop losing out on cross-border revenues because your customers are finding better alternatives.

### How does it work?

- Transparent and fair pricing - Your customers will get the same price no matter if they make transfers via your bank integration or directly via Pazemo.
- Same great Pazemo service - Your customers get access to our 24/7 customer support.
- Custom solution - We’ll work together to find and build a solution that works for your bank. There’s no one-size-fits-all approach. Together we’ll decide:
  - How do we set up flow of funds?
  - How do we handle customer support?
  - How do we harmonise customer onboarding and AML processes?

Please contact infi@pazemo.com to get started.

## Affiliates

When you apply to the Pazemo affiliates program you can get access to our API to help you build your own valuable content for your customers or readers.

### The Pazemo Platform API lets you to:

- Get the real-time mid-market exchange rates for any currency route.
- Get up to 30 days of historical mid-market exchange rates for any currency route.
- Get a Pazemo quote for any supported currency route, which includes our fees and estimated delivery time.

## Receive Money
You can receive money to the local bank details that come with your Pazemo account (USD, EUR, GBP, AUD, NZD and PLN) and reconcile these incoming payments via the API.

You’re also able to create a webhook subscription to receive event callbacks to your server when payments are received. Here’s more information about the webhooks.

Please note that we don't send any information over webhook calls that might contain personally identifiable information (PII) about the sender (including the payment reference).

To reconcile incoming payments you might also need to match the information received via webhooks with the information that can be obtained from the statements.

## Checkout flows

We currently don’t offer the option to build Pazemo into your checkout flow as a payment option to receive money. Note though that Pazemo can be added as a payout option on your site for beneficiaries to choose to receive their payout through to an email address, directly to a bank account or any other mechanism we support in our standard product.

## Open Banking

Under the Second Payment Services Directive (PDS2) we are opening up the standardized version of our API to the rest of the world. Find out more about our Open Banking API

# Payouts Guide

Welcome to the Pazemo payouts API documentation. Before you start coding, please take few moments to review some important information about Pazemo and our API.

## Getting started

1. Learn about Pazemo.
Pazemo and its multi-currency account features and pricing are best explained below.

https://pazemo.com/multi-currency-account/pricing

2. Sign up for your Pazemo account, activate your multi-currency account, and complete verification.
Using the product before integrating with our API will help you understand how our payment flow works. Just follow these four steps

- Sign up for your Pazemo account https://pazemo.com/multi-currency-account.

- Complete verification – you need to do this before you start your technical integration. Also ensure you’re compliant with our Terms and Conditions and Acceptable Use Policy. Also make sure two-step log in is set up.

- Activate at least one currency in your multi-currency account, deposit small amount (via card or bank transfer) and setup your first payment. This penny-testing is not mandatory of course, but we do recommended it so you will understand how Pazemo payment flow works.

- Verify that our coverage includes your currency route(s). Check Supported Currencies. Please note that there are few restrictions for businesses, please review Restricted Business Routes

- Please note that our Fixed Rate functionality is intended to provide time for customers to send funds to Pazemo, while holding the rate for them. Pazemo is not a trading platform and the Fixed Rate functionality is automatically disabled if abusive behaviour (such as multiple transfer creation and selective completion) is detected.

3. Choose the best tool for you
- You don’t necessarily need to integrate with the API to make a large number of payouts. We have two ways you can do it:

- Batch payments. Create and send up to 1,000 transfers with just one payment using our Batch Payments tool. All you need to do is fill a CSV file with all the transfer details, upload it to Wise, and pay for the batch. No development effort needed.

- API integration. Completely automate your payment process by sending payment orders via the Wise Platform API.

## API access

### Authentication

> To authorize, use this code:

```ruby
require 'pazemo'

api = Kittn::APIClient.authorize!('xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx')
```

```python
import pazemo

api = kittn.authorize('xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx"
```

```javascript
const kittn = require('pazemo');

let api = kittn.authorize('xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx');
```

> Make sure to replace `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx` with your API key.

Sign up for a developer account and get your personal API token for our sandbox. https://pazemo.com/register

NB! Two factor authentication (2FA) code for sandbox login is 111111.

Your developer account will have some test money that you can use to start making payments in same way as you would in a live environment. You can get your API tokens in the Settings tab of your account page.

Add your API token as header parameter to every request like this:

Authorization: Bearer xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx

<aside class="notice">
You must replace <code>xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx</code> with your personal API key.
</aside>

### Acquiring your API token

Your API tokens section can be found at the bottom of the Settings page inside your Wise account. By default, you have no active tokens. You can issue new tokens after enabling 2-step login.

We support tokens of two permission levels:

- Read only - List and show transfers, recipients and multi-currency account information
- Full access - Create, manage and fund transfers

### Keeping your API token safe

Your API tokens should be guarded closely. They represent your identity and authorization and can be used to interact with your Wise account on your behalf. Whoever has access to your token can access your account details and history. In the case of a Full access token, they can also send transfers. Once you obtain an API token from us, it is on you to keep it safe.

Below is technical advise and guidance on how to protect your tokens. Not everything may apply to the application you are building and the goal is not to provide a long checklist of things to do. Rather, we attempt to provide generic guidance and best-practices, to send you in the right direction. You will have to do additional research and consider the specific technology and purpose of your application.

### Source code

> Don't store API tokens as plaintext files in Git

```
$ git clone https://github.com/mycompany/myapp.git
$ cat myapp.git/apiconfig.json
{
  "token": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx",
  "url": "https://api.stg.pazemo.com/"
}
```

A common mistake made by engineers is storing access tokens in source code, in plaintext - which is then shared in a version control system, sometimes publicly.

When an API token is stored like this, it can be accessed and used by anyone who has access to the source code. Avoid storing secrets in code.

Instead:

- Use environment variables to pass secrets into your application. You can configure them in your web server settings, startup script or platform-specific tools such as Docker or Kubernetes.
- If your deployment platform has a dedicated mechanism for storing secrets, use it
- Use a configuration file that is excluded from your version control. It can be created manually, or put into the deployment server by automated tools. Make sure the file can only be read by your web application

> Limit permissions of a sensitive configuration file

```
$ cp .env.sample .env
$ echo .env >> .gitignore
$ chown myapp:root .env && chmod 600 .env
```

### Token lifecycle

If you suspect that your token has leaked, revoke and rotate it. If you accidentally push a token to a remote public repository, rotate it. Quickly deleting an access token from VCS might not be enough - remember that VCS stores historical changes, is distributed and might have automation assigned to new pushes.

Revoke old tokens that you no longer need or use.

During the lifetime of an active token, limit the amount of people and systems who can access it. E-mail inboxes and chat logs are archived and not a secure place to hold tokens. Ideally, your access token would live only in Wise systems and your production system(s) that actually need it. You do not need to hold a backup copy of the token, as you can reveal an existing token from your profile settings page.

### Encryption

Wise Platform API is using HTTPS with >=TLS 1.2. Non-encrypted HTTP connections are not accepted. Do not connect to our API with unencrypted HTTP, as this will transmit your access token in plaintext over the network.

> Verifying certificates in client code

```php
<?php
// Secure - this will fail when an invalid HTTPS certificate is returned.
// Such failure is not normal and most likely means there is something
// in-between you and Wise, intercepting communications.
$ch = curl_init();
curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 1);
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, 1);
curl_setopt($ch, CURLOPT_URL, 'https://api.transferwise.com');


// Insecure - do not do this. This will not validate certificates and
// might leak your access token to an attacker.
// See https://curl.haxx.se/libcurl/c/CURLOPT_SSL_VERIFYPEER.html
$ch = curl_init();
curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 0);
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, 0);
curl_setopt($ch, CURLOPT_URL, 'https://api.transferwise.com');
```

Validate certificates. You should not proceed with a connection when you receive a certificate validation error from Wise. Make sure all parts of your application are using encryption and HTTPS and failing when certificate validation fails.

### Application design

Secure your application against common security flaws (OWASP Top 10). Think how an attacker could leverage Unrestricted File Upload or Insecure Direct Object Reference to read the contents of your server's environment or config files.

If your application is larger, consider extracting Wise-specific functionality into a separate middleware or service layer. This would enable you to move API tokens there, separate from the main application.

Do not store the token in user-accessible code such as browser-side JavaScript or Android apps that can be decompiled. The token should always live server-side, exposing domain-logic via API-s.

If you need to pass the token around via HTTP requests, use HTTP headers or POST body - do not store the token in URI or query parameters. Web servers usually log the URL and browsers pass it between websites via the Referrer header.

### Limiting token access by IP

You can enhance your integration security by only allowing certain IP addresses to use your API token.

Typically, you would integrate with our API from a set number of fixed IP addresses. Restricting access from all other IPs will make it harder to misuse your API token, should it ever leak. IP whitelisting does not protect against cases where several clients egress from the same whitelisted IP (shared external IP for the office network, an egress proxy in front of all of your servers).

Each token can be limited to single IP addresses, a set of IP addresses or entire IP ranges. You can do this in the API token edit view.

Please note:

- IP addresses should use only IPv4 format e.g. 192.168.100.14
- IP ranges should use CIDR notation e.g. 192.168.100.0/24 which would include 192.168.100.0 up to 192.168.100.255
- You can authorize multiple discrete IP-s or IP ranges for one token

If a request is being made using an IP address that is not in the whitelisted IP addresses, the server will respond with a 401 Unauthorized HTTP status code.

### Testing

By default in our sandbox environment strong customer authentication is disabled. You can enable it for your account on the public keys management page.

The option for toggling the check yourself will also be available in production as long as it is optional.

### LIVE environments

- The LIVE API is located at https://api.stg.pazemo.com/

Please note Sandbox environment is limited. We do not send any emails from it as well as transfer processing is not simulated. Please consider Simulation endpoints to change transfer state after funding.

## Get your profile id

> Example Request:

```shell
curl -X GET http://api.stg.pazemo.com/users/ \
     -H "Authorization: Bearer <your api token>"
```
> The above command returns JSON structured like this:

```json
{
  "id": "string",
  "createdTime": "2021-06-09T09:46:26.065Z",
  "updatedTime": "2021-06-09T09:46:26.065Z",
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


You only need to call this endpoint once to obtain your user profile id. Your personal and business profiles have different IDs. Profile id values are required when making payouts.

It’s recommended to always provide profileId when you’re creating new resources later (Create Quote, Create Recipient Account, Create Transfer). If you omit profileId then resource will by default belong to your personal profile. This might not be your intention, as you most probably want to execute transfers under your business profile.

Request
GET http://api.stg.pazemo.com/users/

### Response

Personal Profile Fields

Field | Description | Format
--------- | ------- | -----------
id | Personal profile id | Text.
createdTime | Creation Date | "yyyy-mm-dd".
updatedTime | Update Date | "yyyy-mm-dd".
status | Status | Text.
email | Email | Text.
mobile | Mobile Number | Text.
name | Person Name | Text.
partnerId | Partner ID | Text.
roles | Role | Text.

## Create quote

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
There are four steps to execute payouts:

**Step 1: Create a quote**

Step 2: Create a recipient account

Step 3: Create a transfer

Step 4: Fund a transfer

Quote fetches current mid-market exchange rate that will be used for your transfer. Quote also calculates our fee and estimated delivery time.

### Request

POST https://api.stg.pazemo.com/quotes

Field | Description | Format
--------- | ------- | -----------
sendCurrencyId | Currency Code | Text.
receiveCurrencyId | Currency Code | Text.
sendAmount | Send Amount | Decimal.

### Response

The payOut field is used to select the correct entry in the paymentOptions array in order to know which fees to display to your customer. Find the paymentOption that matches the payOut field shown at the top level of the quote resource and payIn based on the settlement model the bank is using. By default this is BANK_TRANSFER, unless you are using a prefunded or bulk settlement model.

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

There are four steps to execute payouts:

Step 1: Create a quote

**Step 2: Create a recipient account**

Step 3: Create a transfer

Step 4: Fund a transfer

Recipient is a person or institution who is the ultimate beneficiary of your payment.

Recipient bank account details are different for different currencies. For example, you only need to know the IBAN number to send payments to most European and Nordic countries. But in order to send money to Canada, you’d need to fill out four fields: You recipient’s institution number, transit number, account number, and account type.

### Request

POST http://api.stg.pazemo.com/users/{userId}/accounts

Field | Description | Format
--------- | ------- | -----------
sendCurrencyId | Currency Code | Text.
receiveCurrencyId | Currency Code | Text.
sendAmount | Send Amount | Decimal.

### Response

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