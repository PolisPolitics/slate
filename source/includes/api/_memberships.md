# Memberships

## The Membership object

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Identifier of this record
securityGroupId | true | Identifier of the associated securitygroup
customerId | true | Identifier of the associated customer
data | true | The membership data

### data

Attribute | Required? | Description
--------- | --------- | -----------
organizationId | true | Identifier of the organization this membership belongs to
userId | true | Identifier of the user associated with this membership
roleId | true | Identifier of the role associated with this membership
status | false | Status of this membership. Should be one of the `active`, `disabled`, `unconfirmed`, `invited`
notifications | false | Notifications object

### data/notifications

Attribute | Required? | Description
--------- | --------- | -----------
dailySummary | false | Flag indicating whether user is subscribed to dailySummary

### meta

[See documentation](#metadata-object)



```json
{
	"id": "cd7a7a03-6303-4778-a5f6-a0d94fcc763d",
	"data": {
		"roleId": "ba192430-14b5-44f7-abcf-fc6b9aa35813",
		"status": "active",
		"userId": "cff4a05f-2612-471d-821d-8782627d42aa",
		"notifications": {
			"dailySummary": true
		},
		"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:25.416Z",
		"modified": "2019-04-03T18:55:25.416Z",
		"resource": "memberships",
		"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
		"isDeleted": false,
		"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```


## Get many memberships

> Example Request

```http
GET /memberships?filter%5B%2Fdata%2FuserId%5D=cff4a05f-2612-471d-821d-8782627d42aa&filter%5B%2Fdata%2Fstatus%5D=active&skip=0&limit=9007199254740991&sort=id&sort=ASC HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"data": [
		{
			"id": "cd7a7a03-6303-4778-a5f6-a0d94fcc763d",
			"data": {
				"roleId": "ba192430-14b5-44f7-abcf-fc6b9aa35813",
				"status": "active",
				"userId": "cff4a05f-2612-471d-821d-8782627d42aa",
				"notifications": {
					"dailySummary": true
				},
				"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:25.416Z",
				"modified": "2019-04-03T18:55:25.416Z",
				"resource": "memberships",
				"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
				"isDeleted": false,
				"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		},
		{
			"id": "cd7a7a03-6303-4778-a5f6-a0d94fcc763d",
			"data": {
				"roleId": "ba192430-14b5-44f7-abcf-fc6b9aa35813",
				"status": "active",
				"userId": "cff4a05f-2612-471d-821d-8782627d42aa",
				"notifications": {
					"dailySummary": true
				},
				"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:25.416Z",
				"modified": "2019-04-03T18:55:25.416Z",
				"resource": "memberships",
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

`GET /memberships`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | false | Query to filter data. e.g. `/data/userId eq "08f35132-7b4f-44d9-b212-6e5fad31aad3" and /data/status eq "active"`
limit | true | Limits number of result-rows. Should be a positive integer. Useful for pagination.
skip | true | Offset data by given number. Useful for pagination.
sort | true | Sort the column in `ASC` or `DESC` e.g. ['id', 'ASC']


## Get a membership

> Example Request

```http
GET /memberships/cd7a7a03-6303-4778-a5f6-a0d94fcc763d HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"id": "cd7a7a03-6303-4778-a5f6-a0d94fcc763d",
	"data": {
		"roleId": "ba192430-14b5-44f7-abcf-fc6b9aa35813",
		"status": "active",
		"userId": "cff4a05f-2612-471d-821d-8782627d42aa",
		"notifications": {
			"dailySummary": true
		},
		"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:25.416Z",
		"modified": "2019-04-03T18:55:25.416Z",
		"resource": "memberships",
		"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
		"isDeleted": false,
		"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`GET /memberships/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the membership to be retrieved.


## Post to memberships

> Example Request

```http
POST /memberships HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"data": {
		"organizationId": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319",
		"userId": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
		"roleId": "187e61d8-7571-46c6-a384-19aa700cf6af"
	},
	"customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466"
}
```

> Example Response

```json
{
	"id": "ec15c251-01d9-4146-8957-68debc821588",
	"data": {
		"roleId": "187e61d8-7571-46c6-a384-19aa700cf6af",
		"status": "unconfirmed",
		"userId": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
		"notifications": {
			"dailySummary": true
		},
		"organizationId": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319"
	},
	"meta": {
		"etag": "268-77iKRUrM3zlu3FHeZ1lJ5S9XJoM",
		"created": "2018-09-21T17:07:26.676Z",
		"modified": "2018-09-21T17:07:26.676Z",
		"resource": "memberships",
		"createdBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
		"isDeleted": false,
		"modifiedBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c"
	},
	"customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466",
	"securityGroupId": "3453b386-60b5-4e58-b7f6-46b4977791ad"
}
```

### HTTP Request

`POST /memberships`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
customerId | false | Identifier of the customer to which this membership belongs
data | true | The data for the membership to be created


## Reset user passwords using memberships

Allows managers to reset user passwords using memberships

> Example Request

```http
POST /memberships/password-reset HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

### HTTP Request

`POST /memberships/password-reset`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
data.membershipId	| true | Membership ID of user whose password will be changed.
params.password |	true	| New password for the `canvasser` user.
params.contextPassword	| true	| Password of the user owner of the API token.


## Update a membership

> Example Request

```http
PATCH /memberships/cd7a7a03-6303-4778-a5f6-a0d94fcc763d HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"data": [
		{
			"op": "replace",
			"path": "/status",
			"value": "disabled"
		}
	],
	"params": {
		"roleId": "187e61d8-7571-46c6-a384-19aa700cf6af",
		"action": "changeRole"
	}
}
```


<aside class='notice'>
You can only patch attributes inside <b>data</b> key.
</aside>

> Example Response

```json
{
	"id": "cd7a7a03-6303-4778-a5f6-a0d94fcc763d",
	"data": {
		"roleId": "187e61d8-7571-46c6-a384-19aa700cf6af",
		"status": "disabled",
		"userId": "cff4a05f-2612-471d-821d-8782627d42aa",
		"notifications": {
			"dailySummary": true
		},
		"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:25.416Z",
		"modified": "2019-04-03T18:55:25.416Z",
		"resource": "memberships",
		"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
		"isDeleted": false,
		"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`PATCH /memberships/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the memberships.
data | true | The patch data
params | false | For updating roles


## Delete a membership

> Example Request

```http
DELETE /memberships/cd7a7a03-6303-4778-a5f6-a0d94fcc763d HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
```

> Example Response

```http
HTTP 200 Success
```

### HTTP Request

`DELETE /memberships/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the membershis item to be deleted.
