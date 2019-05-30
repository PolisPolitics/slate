# Integrations

## The Integration object

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Identifier of this record.
securityGroupId | true | Identifier of the associated security group.
customerId | true | Identifier of the customer to which this resource belongs.
data | true | Integration data.

### data

Attribute | Required? | Description
--------- | --------- | -----------
status | false | State of this integration. Should be either `active` or `paused`.
accountName | false | Name of the account holder for this integration.
provider | true | Name of the provider. Should be one of [`escoware`, `nationBuilder`, `republicanNationalCommittee`,
  `stripe`, `crowdskout`].
slug | false | Identifies Polis when it's integrating with 3rd party.
interactionTypeId | false | The interaction type.Should be a number.
pushAllInteractions | false | Flag indicating whether all interactions should be pushed to the database.
clientId | false | Identifier for 3rd parties using Polis's API.

### meta

[See documentation](#metadata-object)

## Sets the credentials of an existing integration

> Example Request

```http
POST /integrations/credentials HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"data": {
		"clientId": "{client_id}",
		"customerId": "65576faf-4937-4871-8029-bb6f4e902f5f",
		"accessToken": "1234"
	}
}
```

> Example Response

```http
HTTP 201 Created
```

### HTTP Request

`POST /integrations/credentials`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
data | true | The data for the new credentials. Should contain `clientId`, `customerId`, `accessToken`


## Deletes the credentials of an existing integration

> Example Request

```http
DELETE /integrations/credentials HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
{
	"data": {
		"clientId": "{client_id}",
		"customerId": "65576faf-4937-4871-8029-bb6f4e902f5f"
	}
}
```

> Example Response

```http
HTTP 200 Success
```

### HTTP Request

`DELETE /integrations/credentials`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
data | true | Should contain `clientId`, `customerId`