# Authentication

## 1. Authorization Code

From your application, redirect your customer to the following URL

`https://knock.polisapp.com/oauth/authorize?response_type=code&client_id={client_id}&redirect_uri={redirect_uri}&state={state}`

Where the parameters adhere to the standards in [RFC-6749 The OAuth 2.0 authorization framework](https://tools.ietf.org/html/rfc6749#section-4.1.1)

Parameter | Required? | Description
--------- | -------- | -----------
response_type | true |The type of response. Value must always be set to `'code'`.
client_id | true | Client ID of the application provided during registration.
redirect_uri | false | The redirect uri to which your customer must be directed to after authorization.
state | false | An opaque value used to maintain state between the request and callback.


When the authorization is successful, the user will be redirected back to your website with the `authorization_code` , `organizationId` and `state` (if provided). The redirect URL is based on either the one configured during your application registration or the `redirect_uri` in the authorization request url. Below is an example redirect URL


`https://my.app.com/authorize?code={authorization_code}&state={state}&organizationId={organizationId}`

The `organizationId` is the target organization identifier selected by the customer.

## 2. Access Token

> Request

```http
POST /auth/oauth2/token HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json

{
  "client_id": "{client_identifier}",
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

### Body Parameters

Parameter | Description
--------- | -----------
client_id | Client ID of the application provided during registration.
client_secret | Client Secret of the application provided during registration.
code | Authorization code provided in the redirected URI.
grant_type | Authorization type. Use `authorization_code`.

## 3. Using the API

Polis API expects the access token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer {access_token}`
