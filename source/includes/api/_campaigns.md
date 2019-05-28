# Campaigns

## The Campaign object

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Identifier of this record
securityGroupId | true | Identifier of the associated security group
customerId | true | Identifier of the customer to which this resource belongs
data | true | Campaign data

### data

Attribute | Required? | Description
--------- | --------- | -----------
name | true | Name of the campaign
description | false | Description of the campaign
status | true | Current status of this campaign. Can be `pending`, `started` or `complete`
fields | false | Information available to a canvasser about the contact on the mobile app
ended | false | Timestamp of when the campaign was ended
organizationId | true | Organization indentifier that this campaign belongs to
lists | false | Array of lists of contacts associated with the campaign

### meta

[See documentation](#metadata-object)



```json
{
	"id": "b29dd2bc-677a-42ba-a327-51f1d9a155e9",
	"data": {
		"name": "My Campaign",
		"lists": [
			{
				"type": "normal",
				"listId": "588b44db-3444-4732-92db-158db44202eb",
				"statusId": ""
			}
		],
		"fields": [
			[
				{
					"path": "/data/profile/name/anglican/title",
					"type": "field"
				},
				{
					"path": "/data/profile/name/anglican/given",
					"type": "field"
				},
				{
					"path": "/data/profile/name/anglican/surname",
					"type": "field"
				},
				{
					"path": "/data/profile/name/anglican/suffix",
					"type": "field"
				}
			],
			[
				{
					"path": "/data/profile/age",
					"type": "field"
				},
				{
					"type": "separator",
					"value": ","
				},
				{
					"path": "/data/profile/gender",
					"type": "field"
				}
			]
		],
		"status": "started",
		"description": "My Campaign Description",
		"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:26.984Z",
		"modified": "2019-04-03T18:55:26.984Z",
		"resource": "campaigns",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```


## Get many campaigns

> Example Request

```http
GET /campaigns?filter%5B%2Fdata%2ForganizationId%5D=309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7&skip=0&limit=9007199254740991&sort=%2Fdata%2Fname&sort=ASC HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"data": [
		{
			"id": "b29dd2bc-677a-42ba-a327-51f1d9a155e9",
			"data": {
				"name": "My Campaign",
				"lists": [
					{
						"type": "normal",
						"listId": "588b44db-3444-4732-92db-158db44202eb",
						"statusId": ""
					}
				],
				"fields": [
					[
						{
							"path": "/data/profile/name/anglican/title",
							"type": "field"
						},
						{
							"path": "/data/profile/name/anglican/given",
							"type": "field"
						},
						{
							"path": "/data/profile/name/anglican/surname",
							"type": "field"
						},
						{
							"path": "/data/profile/name/anglican/suffix",
							"type": "field"
						}
					],
					[
						{
							"path": "/data/profile/age",
							"type": "field"
						},
						{
							"type": "separator",
							"value": ","
						},
						{
							"path": "/data/profile/gender",
							"type": "field"
						}
					]
				],
				"status": "started",
				"description": "My Campaign Description",
				"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:26.984Z",
				"modified": "2019-04-03T18:55:26.984Z",
				"resource": "campaigns",
				"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
				"isDeleted": false,
				"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		},
		{
			"id": "4f1e6e72-630f-4ff2-b089-4359f4b2a8de",
			"data": {
				"name": "My Campaign 2",
				"lists": [
					{
						"type": "normal",
						"listId": "ea19c3ab-3526-4709-b027-3e3c1d1851b2",
						"statusId": ""
					}
				],
				"fields": [
					[
						{
							"path": "/data/profile/name/anglican/title",
							"type": "field"
						},
						{
							"path": "/data/profile/name/anglican/given",
							"type": "field"
						},
						{
							"path": "/data/profile/name/anglican/surname",
							"type": "field"
						},
						{
							"path": "/data/profile/name/anglican/suffix",
							"type": "field"
						}
					],
					[
						{
							"path": "/data/profile/age",
							"type": "field"
						},
						{
							"type": "separator",
							"value": ","
						},
						{
							"path": "/data/profile/gender",
							"type": "field"
						}
					]
				],
				"status": "started",
				"description": "My Campaign Description 2",
				"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:26.984Z",
				"modified": "2019-04-03T18:55:26.984Z",
				"resource": "campaigns",
				"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
				"isDeleted": false,
				"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		}
	],
	"meta": {}
}
```

### HTTP Request

`GET /campaigns`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | false | Query to filter data. `/data/organizationId eq "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319" and /data/status eq "complete"`
limit | true | Limits number of result-rows. Should be a positive integer. Useful for pagination.
skip | true | Offset data by given number. Useful for pagination.
sort | true | Sort the column in `ASC` or `DESC` e.g. ['id', 'ASC']

## Get a campaign

> Example Request

```http
GET /campaigns/b29dd2bc-677a-42ba-a327-51f1d9a155e9 HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"id": "b29dd2bc-677a-42ba-a327-51f1d9a155e9",
	"data": {
		"name": "My Campaign",
		"lists": [
			{
				"type": "normal",
				"listId": "588b44db-3444-4732-92db-158db44202eb",
				"statusId": ""
			}
		],
		"fields": [
			[
				{
					"path": "/data/profile/name/anglican/title",
					"type": "field"
				},
				{
					"path": "/data/profile/name/anglican/given",
					"type": "field"
				},
				{
					"path": "/data/profile/name/anglican/surname",
					"type": "field"
				},
				{
					"path": "/data/profile/name/anglican/suffix",
					"type": "field"
				}
			],
			[
				{
					"path": "/data/profile/age",
					"type": "field"
				},
				{
					"type": "separator",
					"value": ","
				},
				{
					"path": "/data/profile/gender",
					"type": "field"
				}
			]
		],
		"status": "started",
		"description": "My Campaign Description",
		"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:26.984Z",
		"modified": "2019-04-03T18:55:26.984Z",
		"resource": "campaigns",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`GET /campaigns/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the campaign to be retrieved.


## Get all statuses for the camapaign

> Example Request

```http
GET /campaigns/b29dd2bc-677a-42ba-a327-51f1d9a155e9/statuses HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"data": [
		{
			"id": "33cba02c-742f-4d82-abae-93025bc1a245",
			"data": {
				"icon": "faTimes:solid",
				"name": "Deceased",
				"pinColor": "#C8C8C8",
				"iconColor": "#E95C41",
				"contactState": "contacted-unavailable-other",
				"defaultStatus": true,
				"statusGroupId": "d947f9e1-7d72-4cea-b8dc-b06e5df95e13",
				"defaultStatusId": "dba9b195-8bcf-4240-a17d-7c940f765520"
			},
			"meta": {
				"etag": "296-QrkG0OkfbfSI5yOcYvvaNJ/QMGs",
				"created": "2019-04-03T18:55:24.875Z",
				"modified": "2019-04-03T18:55:24.875Z",
				"resource": "statuses",
				"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
				"isDeleted": false,
				"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		},
		{
			"id": "7589a29b-15dd-48cb-b5d3-544b8de9db5e",
			"data": {
				"icon": "faRedo:solid",
				"name": "Come Back",
				"pinColor": "#C8C8C8",
				"iconColor": "#01B5D6",
				"contactState": "come-back",
				"defaultStatus": true,
				"statusGroupId": "f8e607ff-9e0c-464c-aeb4-e7fe2ba24995",
				"defaultStatusId": "b4f8840e-f597-4c4e-8144-a05a11fd102f"
			},
			"meta": {
				"etag": "284-M6hJkzegO/+QBX1LjTzuUCnNIZ4",
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
				"etag": "28e-AMIhE2ChHfGxCrz0Dbz9ZwajPuo",
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
			"id": "1b4d062e-8363-4588-8fbc-89aa4c3f21b4",
			"data": {
				"icon": "faStar:solid",
				"name": "High Priority",
				"pinColor": "#FFBE00",
				"iconColor": "#FFBE00",
				"contactState": "not-contacted-high-priority",
				"defaultStatus": true,
				"statusGroupId": "990f7d84-7d9b-4e91-9cbc-89537bd52ac5",
				"defaultStatusId": "dfff0caa-5a79-496e-881a-d25e81b08f7c"
			},
			"meta": {
				"etag": "29a-9itz4pp9J6W2ve/LxeV1WqUrfZI",
				"created": "2019-04-03T18:55:24.875Z",
				"modified": "2019-04-03T18:55:24.875Z",
				"resource": "statuses",
				"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
				"isDeleted": false,
				"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		},
		{
			"id": "a1a7f800-1ee5-4748-b00e-efd396a9cece",
			"data": {
				"icon": "faTimes:solid",
				"name": "Refused",
				"pinColor": "#C8C8C8",
				"iconColor": "#E95C41",
				"contactState": "contacted-unavailable-other",
				"defaultStatus": true,
				"statusGroupId": "5572e6d6-84f3-4188-95dd-e73966de1a6f",
				"defaultStatusId": "6adca7e0-a1a6-4990-b665-7473a3c6153f"
			},
			"meta": {
				"etag": "295-LVNoFZMRK4D6TnNd3LPRtZi/bkg",
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
				"etag": "298-9LHRW+IDYK8cT2XgOHC6kL2SI2Q",
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
			"id": "3d7dbd70-a756-43bc-addc-3dbf2e1baa9e",
			"data": {
				"icon": "faTimes:solid",
				"name": "Other Language",
				"pinColor": "#C8C8C8",
				"iconColor": "#E95C41",
				"contactState": "contacted-unavailable-other",
				"defaultStatus": true,
				"statusGroupId": "d947f9e1-7d72-4cea-b8dc-b06e5df95e13",
				"defaultStatusId": "82aa0882-fdf4-4f96-ac84-5509bcfcf264"
			},
			"meta": {
				"etag": "29c-3Q9xsNxbDrfWsCcfANH/XW8NSPc",
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
			"id": "1a2f0106-fc5c-418d-b9af-e9adbd50aa69",
			"data": {
				"icon": "faThumbsUp:solid",
				"name": "Successful",
				"pinColor": "#C8C8C8",
				"iconColor": "#73C1B1",
				"contactState": "contacted-available-successful",
				"defaultStatus": true,
				"statusGroupId": "ea4f7a97-5455-49f5-9e3c-7b84b3f234cf",
				"defaultStatusId": "436d3a44-d5d7-4895-a507-e020bf3f6c9e"
			},
			"meta": {
				"etag": "29e-to6x21/O/dfZlU/C8hOwvxN2sfY",
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
	]
}
```

### HTTP Request

`GET /campaigns/{campaignId}/statuses`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
campaignId | true | Unique identifier of the campaign


## Create a campaign

> Example Request

```http
POST /campaigns HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"data": {
		"status": "started",
		"organizationId": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319",
		"name": "My Campaign",
		"description": "My Campaign Description"
	}
}
```


<aside class='warning'>
You must create a Default Survey and a Default Target for new campaigns.Check Surveys and Segments documentations.
</aside>

> Example Response

```json
{
	"id": "b29dd2bc-677a-42ba-a327-51f1d9a155e9",
	"data": {
		"name": "My Campaign",
		"lists": [
			{
				"type": "normal",
				"listId": "588b44db-3444-4732-92db-158db44202eb",
				"statusId": ""
			}
		],
		"fields": [
			[
				{
					"path": "/data/profile/name/anglican/title",
					"type": "field"
				},
				{
					"path": "/data/profile/name/anglican/given",
					"type": "field"
				},
				{
					"path": "/data/profile/name/anglican/surname",
					"type": "field"
				},
				{
					"path": "/data/profile/name/anglican/suffix",
					"type": "field"
				}
			],
			[
				{
					"path": "/data/profile/age",
					"type": "field"
				},
				{
					"type": "separator",
					"value": ","
				},
				{
					"path": "/data/profile/gender",
					"type": "field"
				}
			]
		],
		"status": "started",
		"description": "My Campaign Description",
		"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:26.984Z",
		"modified": "2019-04-03T18:55:26.984Z",
		"resource": "campaigns",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`POST /campaigns`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
data | true | The data of the campaign record to be created


## Update a campaign

> Example Request

```http
PATCH /campaigns/b29dd2bc-677a-42ba-a327-51f1d9a155e9 HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
{
	"data": [
		{
			"op": "replace",
			"path": "/name",
			"value": "My Campaign Changed"
		},
		{
			"op": "replace",
			"path": "/description",
			"value": "My Campaign Description Changed"
		},
		{
			"op": "replace",
			"path": "/lists",
			"value": [
				{
					"listId": "ea19c3ab-3526-4709-b027-3e3c1d1851b2"
				}
			]
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
	"id": "b29dd2bc-677a-42ba-a327-51f1d9a155e9",
	"data": {
		"name": "My Campaignn Changed",
		"lists": [
			{
				"type": "normal",
				"listId": "ea19c3ab-3526-4709-b027-3e3c1d1851b2",
				"statusId": ""
			}
		],
		"fields": [
			[
				{
					"path": "/data/profile/name/anglican/title",
					"type": "field"
				},
				{
					"path": "/data/profile/name/anglican/given",
					"type": "field"
				},
				{
					"path": "/data/profile/name/anglican/surname",
					"type": "field"
				},
				{
					"path": "/data/profile/name/anglican/suffix",
					"type": "field"
				}
			],
			[
				{
					"path": "/data/profile/age",
					"type": "field"
				},
				{
					"type": "separator",
					"value": ","
				},
				{
					"path": "/data/profile/gender",
					"type": "field"
				}
			]
		],
		"status": "started",
		"description": "My Campaign Description Changed",
		"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:26.984Z",
		"modified": "2019-04-03T18:55:26.984Z",
		"resource": "campaigns",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`PATCH /campaigns/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the campaigns.
data | true | The patch data


## Delete a campaign

> Example Request

```http
DELETE /campaigns/b29dd2bc-677a-42ba-a327-51f1d9a155e9 HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
```

### HTTP Request

`DELETE /campaigns/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the campaign to be deleted.


## Deletes a relation between campaign and status

> Example Request

```http
DELETE /campaigns/a896b2d4-2f81-4ff6-9d73-be47c7ed3670/statuses/1af48f8b-acec-49c2-9e71-909ce7d6ae05 HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
```

### HTTP Request

`DELETE /campaigns/{campaignId}/statuses/{statusId}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
campaignId | true | The id of the campaign from which status is to be removed
statusId | true | The id of the status to be removed


## Creates a relation between campaign and status

> Example Request

```http
PUT /campaigns/a896b2d4-2f81-4ff6-9d73-be47c7ed3670/statuses/1af48f8b-acec-49c2-9e71-909ce7d6ae05 HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"id": "854cae38-2e22-4b5c-a433-1152e0bdcee9",
	"data": {
		"statusId": "1af48f8b-acec-49c2-9e71-909ce7d6ae05",
		"campaignId": "a896b2d4-2f81-4ff6-9d73-be47c7ed3670"
	},
	"meta": {
		"etag": "1fd-5OmGKiMLOAK4TlY/ERoKIFVyaP0",
		"created": "2019-04-22T14:03:12.473Z",
		"modified": "2019-04-22T14:03:12.473Z",
		"resource": "status-campaign",
		"createdBy": "314b9396-4fd6-4402-969a-87b8c2c25daa",
		"isDeleted": false,
		"modifiedBy": "314b9396-4fd6-4402-969a-87b8c2c25daa"
	},
	"customerId": "df375df8-8117-481b-af17-b2c50b6a2bde",
	"securityGroupId": "c6299aab-5e9c-498d-be7c-99d0a3253100"
}
```

### HTTP Request

`PUT /campaigns/{campaignId}/statuses/{statusId}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
campaignId | true | The id of the campaign from which status is to be removed
statusId | true | The id of the status to be removed

