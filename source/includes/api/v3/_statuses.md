# Statuses

## The Status object

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Identifier of this record.
securityGroupId | true | Identifier of the associated security group.
customerId | true | Identifier of the associated customer.
data | true | Status data.

### data

Attribute | Required? | Description
--------- | --------- | -----------
defaultStatus | false | Boolean that determines if this is a default status. Defaults value is `false`.
defaultStatusId | false | Identifier of the default status.
name | true | Name of the status-group.
icon | true | Name of the icon to be displayed. [details](#icon-property-naming-rules)
iconColor | true | Hex code for the icon color.
pinColor | true | Hex code for the pin color.
statusGroupId | true | Identifier of the status-group that a status belongs to.
contactState | true | Compatibility attribute that maps a status to the state property of a contact instance.

### icon property naming rules

The icon property determines the displayed icon for a status.
We support all Free and Pro [Font Awesome's](https://fontawesome.com/icons?d=gallery) icons.

The following naming rules must be applied from Font Awesome's icon names to status icon property values:

1. status icon property values must start with the constant `fa`
2. Convert Font Awesome's icon name from dash-case to PascalCase
3. status icon property values must end with `:icon-style` where `icon-style` stands for one of the four Font Awesome's packages. Possible values: (`solid`, `regular`, `light` or `brands`)

> icon naming example

* Font Awesome's book-open icon from Light Style package.
* status' icon value: `'faBookOpen:light'

### meta

[See documentation](#metadata-object)



```json
{
	"id": "22c5dacc-c37b-4f6b-96f1-fbd061b5f6e3",
	"data": {
		"icon": "polisNotHome",
		"name": "Not Home",
		"pinColor": "#C8C8C8",
		"iconColor": "#C8C8C8",
		"contactState": "contacted-unavailable-not-home",
		"defaultStatus": true,
		"statusGroupId": "9fd80174-194e-4697-83c5-d45ec56a7ee2",
		"defaultStatusId": "7eac7959-db2d-4209-8532-9214c859de2e"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:24.874Z",
		"modified": "2019-04-03T18:55:24.874Z",
		"resource": "statuses",
		"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
		"isDeleted": false,
		"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

## Get many statuses

> Example Request

```http
GET /v1/statuses?filter%5B%2FcustomerId%5D=286d1af1-c2c5-4069-a19d-3987fdacc0d6&skip=0&limit=9007199254740991&sort=id&sort=ASC HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"data": [
		{
			"id": "22c5dacc-c37b-4f6b-96f1-fbd061b5f6e3",
			"data": {
				"icon": "polisNotHome",
				"name": "Not Home",
				"pinColor": "#C8C8C8",
				"iconColor": "#C8C8C8",
				"contactState": "contacted-unavailable-not-home",
				"defaultStatus": true,
				"statusGroupId": "9fd80174-194e-4697-83c5-d45ec56a7ee2",
				"defaultStatusId": "7eac7959-db2d-4209-8532-9214c859de2e"
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:24.874Z",
				"modified": "2019-04-03T18:55:24.874Z",
				"resource": "statuses",
				"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
				"isDeleted": false,
				"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		},
		{
			"id": "c4004392-f81a-4bbf-806a-2a76c401b89b",
			"data": {
				"icon": "faCalendar:regular",
				"name": "Appointment",
				"pinColor": "#C8C8C8",
				"iconColor": "#01B5D6",
				"contactState": "appointment",
				"defaultStatus": true,
				"statusGroupId": "9d1c4405-249e-41e4-ba1c-8068c775021d",
				"defaultStatusId": "42c375a4-c229-4a2f-80c7-0b7ef695637b"
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:24.874Z",
				"modified": "2019-04-03T18:55:24.874Z",
				"resource": "statuses",
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

`GET https://api.polisapp.com/v1/statuses`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | false | Query to filter data. Allowed attribute: `/customerId`. [See documentation](#Filters)
limit | true | Limits number of result-rows. Should be a positive integer. Useful for pagination.
skip | true | Offset data by given number. Useful for pagination.
sort | true | Sort the column in `ASC` or `DESC` e.g. ['id', 'ASC']

## Get a status

> Example Request

```http
GET /v1/statuses/22c5dacc-c37b-4f6b-96f1-fbd061b5f6e3 HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"id": "22c5dacc-c37b-4f6b-96f1-fbd061b5f6e3",
	"data": {
		"icon": "polisNotHome",
		"name": "Not Home",
		"pinColor": "#C8C8C8",
		"iconColor": "#C8C8C8",
		"contactState": "contacted-unavailable-not-home",
		"defaultStatus": true,
		"statusGroupId": "9fd80174-194e-4697-83c5-d45ec56a7ee2",
		"defaultStatusId": "7eac7959-db2d-4209-8532-9214c859de2e"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:24.874Z",
		"modified": "2019-04-03T18:55:24.874Z",
		"resource": "statuses",
		"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
		"isDeleted": false,
		"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`GET https://api.polisapp.com/v1/statuses/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the status to be retrieved.


## Create a status

> Example Request

```http
POST /v1/statuses HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"data": {
		"icon": "polisNotHome",
		"name": "Not Home",
		"pinColor": "#C8C8C8",
		"iconColor": "#C8C8C8",
		"contactState": "contacted-unavailable-not-home",
		"statusGroupId": "9fd80174-194e-4697-83c5-d45ec56a7ee2"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6"
}
```

> Example Response

```json
{
	"id": "22c5dacc-c37b-4f6b-96f1-fbd061b5f6e3",
	"data": {
		"icon": "polisNotHome",
		"name": "Not Home",
		"pinColor": "#C8C8C8",
		"iconColor": "#C8C8C8",
		"contactState": "contacted-unavailable-not-home",
		"defaultStatus": true,
		"statusGroupId": "9fd80174-194e-4697-83c5-d45ec56a7ee2",
		"defaultStatusId": "7eac7959-db2d-4209-8532-9214c859de2e"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:24.874Z",
		"modified": "2019-04-03T18:55:24.874Z",
		"resource": "statuses",
		"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
		"isDeleted": false,
		"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`POST https://api.polisapp.com/v1/statuses`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
customerId | true | Identifier of the customer to which this resource belongs
data | true | The status data
securityGroupId | false | Identifier of the security group of this resource


## Update a status

> Example Request

```http
PATCH /v1/statuses/22c5dacc-c37b-4f6b-96f1-fbd061b5f6e3 HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
{
	"data": [
		{
			"op": "replace",
			"path": "/name",
			"value": "New Status Name"
		}
	]
}
```


<aside class='notice'>
You can only patch attributes inside <b>data</b> key.
</aside>

> Example Response

```json
{
	"id": "22c5dacc-c37b-4f6b-96f1-fbd061b5f6e3",
	"data": {
		"icon": "polisNotHome",
		"name": "New Status Name",
		"pinColor": "#C8C8C8",
		"iconColor": "#C8C8C8",
		"contactState": "contacted-unavailable-not-home",
		"defaultStatus": true,
		"statusGroupId": "9fd80174-194e-4697-83c5-d45ec56a7ee2",
		"defaultStatusId": "7eac7959-db2d-4209-8532-9214c859de2e"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:24.874Z",
		"modified": "2019-04-03T18:55:24.874Z",
		"resource": "statuses",
		"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
		"isDeleted": false,
		"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`PATCH https://api.polisapp.com/v1/statuses/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the statuses.
data | true | The patch data


## Delete a status

> Example Request

```http
DELETE /v1/statuses/22c5dacc-c37b-4f6b-96f1-fbd061b5f6e3 HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
```

### HTTP Request

`DELETE https://api.polisapp.com/v1/statuses/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the status to be deleted.
