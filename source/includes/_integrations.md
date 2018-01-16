# Integrations

## Set Credentials

> Request

```http
POST /v1/integrations/credentials HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
Cache-Control: no-cache

{
	"data": {
		"clientId": "{client_id}",
		"organizationId": "65576faf-4937-4871-8029-bb6f4e902f5f",
		"accessToken": "1234"
	}
}
```

> Response

```http
201 Created
```

If you are integrating with Polis and you'd like Polis to push contact interaction back to your application, you need to set the `access_token` used to make requests to your API.

### HTTP Request

`POST https://api.polisapp.com/v1/integrations/credentials`

### Query Parameters

Parameter | Description
--------- | -----------
clientId | Client ID of the application provided during registration.
organizationId | Organization ID that has the integration activated.
accessToken | Access token used for Polis to make requests to the integration API.
