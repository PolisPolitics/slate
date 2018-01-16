---
title: Polis API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - http

includes:
  - integrations
  - errors

search: true
---

# Introduction

Welcome to the Polis API!

# Requesting API access

Applications using Polis API are required to be registered. You can register a new application by sending an email to <support@polisapp.com>.

# Authentication

## 1. Authorization Code

From your application, redirect your customer to the following URL, replacing the `clientId` with the one provided for your application.

`https://knock.polisapp.com/oauth/authorize?clientId={clientId}`

When the authorization is successful, the user will be redirected back to your website with the `authorization_code`. The redirect URL is configured during your application registration.

`https://my.app.com/authorize?code={authorization_code}`


## 2. Access Token

> Request

```http
POST /auth/oauth2/token HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Cache-Control: no-cache

{
  "client_id": "{client_id}",
  "client_secret": "{client_secret}",
  "code": "{authorization_code}",
  "grant_type": "authorization_code"
}
```

> Response

```json
{
    "token_type": "bearer",
    "access_token": "soihgonwos384h29sjbeg29h3g9s9",
}
```

Once you have the `authorization_code`, you can exchange it for the `access_token` used to make requests to Polis API.

### HTTP Request

`POST https://api.polisapp.com/auth/oauth2/token`

### Query Parameters

Parameter | Description
--------- | -----------
client_id | Client ID of the application provided during registration.
client_secret | Client Secret of the application provided during registration.
code | Authorization code provided in the redirec URI.
grant_type | Authorization type. Use `authorization_code`.

## 3. Using the API

Polis API expects for the access token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer {access_token}`

