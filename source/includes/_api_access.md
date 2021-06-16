# API access

## Authentication

> To authorize, use this code:


```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: bearer xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx"
```

> Make sure to replace `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx` with your API key.

Sign up for a developer account and get your personal API token for our sandbox. https://pazemo.com/register

Add your API token as header parameter to every request like this:

Authorization: Bearer xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx

<aside class="notice">
You must replace <code>xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx</code> with your personal API key.
</aside>

## Acquiring your API token

Your API tokens section can be found at the bottom of the Settings page inside your Pazemo account. By default, you have no active tokens, You can create up to five API tokens.

<img src="https://raw.githubusercontent.com/Pazemo/docs/main/source/images/api-key.jpg">

## Keeping your API token safe

Your API tokens should be guarded closely. They represent your identity and authorization and can be used to interact with your Pazemo account on your behalf. Whoever has access to your token can access your account details and history. In the case of a Full access token, they can also send transfers. Once you obtain an API token from us, it is on you to keep it safe.

Below is technical advise and guidance on how to protect your tokens. Not everything may apply to the application you are building and the goal is not to provide a long checklist of things to do. Rather, we attempt to provide generic guidance and best-practices, to send you in the right direction. You will have to do additional research and consider the specific technology and purpose of your application.

## Source code

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

## Token lifecycle

If you suspect that your token has leaked, revoke and rotate it. If you accidentally push a token to a remote public repository, rotate it. Quickly deleting an access token from VCS might not be enough - remember that VCS stores historical changes, is distributed and might have automation assigned to new pushes.

Revoke old tokens that you no longer need or use.

During the lifetime of an active token, limit the amount of people and systems who can access it. E-mail inboxes and chat logs are archived and not a secure place to hold tokens. Ideally, your access token would live only in Pazemo systems and your production system(s) that actually need it. You do not need to hold a backup copy of the token, as you can reveal an existing token from your profile settings page.

### Encryption

Pazemo Platform API is using HTTPS with <code>>=TLS 1.2.</code> Non-encrypted HTTP connections are not accepted. Do not connect to our API with unencrypted HTTP, as this will transmit your access token in plaintext over the network.

> Verifying certificates in client code

```php
<?php
// Secure - this will fail when an invalid HTTPS certificate is returned.
// Such failure is not normal and most likely means there is something
// in-between you and Pazemo, intercepting communications.
$ch = curl_init();
curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 1);
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, 1);
curl_setopt($ch, CURLOPT_URL, 'https://api.stg.pazemo.com');


// Insecure - do not do this. This will not validate certificates and
// might leak your access token to an attacker.
// See https://curl.haxx.se/libcurl/c/CURLOPT_SSL_VERIFYPEER.html
$ch = curl_init();
curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 0);
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, 0);
curl_setopt($ch, CURLOPT_URL, 'https://api.stg.pazemo.com');
```

Validate certificates. You should not proceed with a connection when you receive a certificate validation error from Pazemo. Make sure all parts of your application are using encryption and HTTPS and failing when certificate validation fails.

## Application design

Secure your application against common security flaws (<a href="https://www.owasp.org/index.php/Top_10-2017_Top_10">OWASP Top 10</a>). Think how an attacker could leverage Unrestricted File Upload or Insecure Direct Object Reference to read the contents of your server's environment or config files.

If your application is larger, consider extracting Pazemo-specific functionality into a separate middleware or service layer. This would enable you to move API tokens there, separate from the main application.

Do not store the token in user-accessible code such as browser-side JavaScript or Android apps that can be decompiled. The token should always live server-side, exposing domain-logic via API-s.

If you need to pass the token around via HTTP requests, use HTTP headers or POST body - do not store the token in URI or query parameters. Web servers usually log the URL and browsers pass it between websites via the Referrer header.

## Limiting token access by IP

You can enhance your integration security by only allowing certain IP addresses to use your API token.

Typically, you would integrate with our API from a set number of fixed IP addresses. Restricting access from all other IPs will make it harder to misuse your API token, should it ever leak. IP whitelisting does not protect against cases where several clients egress from the same whitelisted IP (shared external IP for the office network, an egress proxy in front of all of your servers).

Each token can be limited to single IP addresses, a set of IP addresses or entire IP ranges. You can do this in the API token edit view.

Please note:

- IP addresses should use only IPv4 format e.g. 192.168.100.14
- IP ranges should use CIDR notation e.g. 192.168.100.0/24 which would include 192.168.100.0 up to 192.168.100.255
- You can authorize multiple discrete IP-s or IP ranges for one token

If a request is being made using an IP address that is not in the whitelisted IP addresses, the server will respond with a 401 Unauthorized HTTP status code.

## Testing

By default in our sandbox environment strong customer authentication is disabled. You can enable it for your account on the public keys management page.

The option for toggling the check yourself will also be available in production as long as it is optional.

## Environments

- The LIVE API is located at

<code><a href="https://api.pazemo.com/">https://api.pazemo.com/</a></code>

- The SANDBOX API is located at

<code><a href="https://api.stg.pazemo.com/">https://api.stg.pazemo.com/</a></code>