# Organizations

## The Organization object

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Identifier of this record
securityGroupId | true | Identifier of the associated securitygroup
customerId | true | Identifier of the associated customer
data | true | Organization data

### data

Attribute | Required? | Description
--------- | --------- | -----------
name | true | Name of the organization
description | false | Description text of the organization
discoverable | true | Flag indicating whether the organization is public. Default `false`
editOldTurfs | false | Flag indicating whether the old turfs belonging to this organization are editable. Default `true`
viewUnassignedData | false | Enables canvassers to view unassigned data. Default true
parentId | false | Id of the `parent` Organization
token | false | Token used to join an organization
requireSignUpConfirmation | false | Joining organization by link, if `false`, doesn't need to be approved by a manager. Default `true`

### meta

[See documentation](#metadata-object)



```json
{
	"id": "a930ds08-f426-488a-bd1b-0ca3fe3c2cc7",
	"data": {
		"name": "Demo Customer 1",
		"token": "aPUmNudxf3",
		"discoverable": true,
		"editOldTurfs": true,
		"viewUnassignedData": true,
		"requireSignUpConfirmation": true
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:25.267Z",
		"modified": "2019-04-03T18:55:25.267Z",
		"resource": "organizations",
		"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
		"isDeleted": false,
		"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```


## Get many organizations

> Example Request

```http
GET /organizations?filter%5B%2FcustomerId%5D=286d1af1-c2c5-4069-a19d-3987fdacc0d6&skip=0&limit=9007199254740991&sort=id&sort=ASC HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"data": [
		{
			"id": "a930ds08-f426-488a-bd1b-0ca3fe3c2cc7",
			"data": {
				"name": "Demo Customer 1",
				"token": "aPUmNudxf3",
				"discoverable": true,
				"editOldTurfs": true,
				"viewUnassignedData": true,
				"requireSignUpConfirmation": true
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:25.267Z",
				"modified": "2019-04-03T18:55:25.267Z",
				"resource": "organizations",
				"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
				"isDeleted": false,
				"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		},
		{
			"id": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7",
			"data": {
				"name": "Demo Customer 2",
				"token": "dQYmIsdtr3",
				"discoverable": true,
				"editOldTurfs": true,
				"viewUnassignedData": true,
				"requireSignUpConfirmation": true
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:25.267Z",
				"modified": "2019-04-03T18:55:25.267Z",
				"resource": "organizations",
				"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
				"isDeleted": false,
				"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		}
	],
	"meta": {}
}
```

### HTTP Request

`GET /organizations`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | false | Query to filter data. e.g. `/customerId eq "f51b86dd-aaba-485e-b14d-65cbea28b8e4"`
limit | true | Limits number of result-rows. Should be a positive integer. Useful for pagination.
skip | true | Offset data by given number. Useful for pagination.
sort | true | Sort the column in `ASC` or `DESC` e.g. ['id', 'ASC']


## Get a organization

> Example Request

```http
GET /organizations/a930ds08-f426-488a-bd1b-0ca3fe3c2cc7 HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"id": "a930ds08-f426-488a-bd1b-0ca3fe3c2cc7",
	"data": {
		"name": "Demo Customer 1",
		"token": "aPUmNudxf3",
		"discoverable": true,
		"editOldTurfs": true,
		"viewUnassignedData": true,
		"requireSignUpConfirmation": true
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:25.267Z",
		"modified": "2019-04-03T18:55:25.267Z",
		"resource": "organizations",
		"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
		"isDeleted": false,
		"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`GET /organizations/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the organization to be retrieved.

