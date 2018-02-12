# Integrations

## Set Credentials

> Request

```http
POST /v1/integrations/credentials HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}

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
HTTP 201 Created
```

If you are integrating with Polis and you'd like Polis to push contact interactions back to your application, you need to set the `access_token` used to make requests to your API.

### HTTP Request

`POST https://api.polisapp.com/v1/integrations/credentials`

### Query Parameters

Parameter | Description
--------- | -----------
clientId | Client ID of the application provided during registration.
organizationId | Organization ID that has the integration activated.
accessToken | Access token used for Polis to make requests to the integration API.


## Remove Credentials

> Request

```http
DELETE /v1/integrations/credentials HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}

{
	"data": {
		"clientId": "{client_id}",
		"organizationId": "65576faf-4937-4871-8029-bb6f4e902f5f"	
	}
}
```

> Response

```http
HTTP 200 Success
```

If you would like to disable your integration with Polis, you only need to send the clientId and organizationId.

### HTTP Request

`DELETE https://api.polisapp.com/v1/integrations/credentials`

### Query Parameters

Parameter | Description
--------- | -----------
clientId | Client ID of the application provided during registration.
organizationId | Organization ID that has the integration activated.
