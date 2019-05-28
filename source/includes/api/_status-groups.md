# Status-groups

## The Status-group object

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Identifier of this record
data | true | The status-group data

### data

Attribute | Required? | Description
--------- | --------- | -----------
name | true | Name of the status-group
icon | true | Name of the icon
iconColor | true | Hex code for the icon color
pinColor | true | Hex code for the pin color
statusType | true | Category of the status-group. Can be `successful`, `unsucessful`, `appointment`, `unavailable`, `list`.
contactState | true | Compatibility attribute that maps a status-group to an older version of statuses 

### meta

[See documentation](#metadata-object)



```json
{
	"id": "0ed0ff24-039e-402a-aaef-88a65ad73f0a",
	"data": {
		"icon": "faThumbsDown:solid",
		"name": "Not Successful",
		"pinColor": "#C8C8C8",
		"iconColor": "#E95C41",
		"statusType": "unsuccessful",
		"contactState": "contacted-available-not-successful"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:24.164Z",
		"modified": "2019-04-03T18:55:24.164Z",
		"resource": "status-groups",
		"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
		"isDeleted": false,
		"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
	}
}
```


## Get many status-groups

> Example Request

```http
GET /status-groups?skip=0&limit=9007199254740991&sort=id&sort=ASC HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"data": [
		{
			"id": "0ed0ff24-039e-402a-aaef-88a65ad73f0a",
			"data": {
				"icon": "faThumbsDown:solid",
				"name": "Not Successful",
				"pinColor": "#C8C8C8",
				"iconColor": "#E95C41",
				"statusType": "unsuccessful",
				"contactState": "contacted-available-not-successful"
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:24.164Z",
				"modified": "2019-04-03T18:55:24.164Z",
				"resource": "status-groups",
				"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
				"isDeleted": false,
				"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
			}
		},
		{
			"id": "d947f9e1-7d72-4cea-b8dc-b06e5df95e13",
			"data": {
				"icon": "faTimes:solid",
				"name": "Bad Contact Info",
				"pinColor": "#C8C8C8",
				"iconColor": "#E95C41",
				"statusType": "unavailable",
				"contactState": "contacted-unavailable-other"
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:24.175Z",
				"modified": "2019-04-03T18:55:24.175Z",
				"resource": "status-groups",
				"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
				"isDeleted": false,
				"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
			}
		}
	],
	"meta": {}
}
```

### HTTP Request

`GET /status-groups`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | false | Query to filter data. [See documentation](#Filters)
limit | true | Limits number of result-rows. Should be a positive integer. Useful for pagination.
skip | true | Offset data by given number. Useful for pagination.
sort | true | Sort the column in `ASC` or `DESC` e.g. ['id', 'ASC']


## Get a status-group

> Example Request

```http
GET /status-groups/0ed0ff24-039e-402a-aaef-88a65ad73f0a HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"id": "0ed0ff24-039e-402a-aaef-88a65ad73f0a",
	"data": {
		"icon": "faThumbsDown:solid",
		"name": "Not Successful",
		"pinColor": "#C8C8C8",
		"iconColor": "#E95C41",
		"statusType": "unsuccessful",
		"contactState": "contacted-available-not-successful"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:24.164Z",
		"modified": "2019-04-03T18:55:24.164Z",
		"resource": "status-groups",
		"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
		"isDeleted": false,
		"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
	}
}
```

### HTTP Request

`GET /status-groups/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the status-group to be retrieved.

