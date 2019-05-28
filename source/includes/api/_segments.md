# Segments

## The Segment object

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Identifier of this record
securityGroupId | true | Identifier of the associated security group
customerId | true | Identifier of the customer this resource belongs to
data | true | Segment data

### data

Attribute | Required? | Description
--------- | --------- | -----------
name | true | Name of the segment
description | false | Description of the segment
campaignId | false | Identifier of the campaign this segment belongs to
surveyId | false | Identifier of the survey this segment will use
criteria | true | Defines the criteria used to analyze the contacts.
precedence | false | Level of precedence between segments

### data/criteria

Attribute | Required? | Description
--------- | --------- | -----------
filter | true | Can be `any` or `all`.
clauses | true | Specifies something. Minimum 1 clause

### data/criteria/clauses

Attribute | Required? | Description
--------- | --------- | -----------
source | true | Path to the contact attribute.
operator | true | Operator used to compare the value and the contact attribute retrieved using the source path. Can be `eq`, `neq`, `gt`, `gte`, `lt`, `lte` or `in`.
value | true | Value used for comparison.

### meta

[See documentation](#metadata-object)



```json
{
	"id": "2e4bfb7c-82aa-4373-9b7c-9c7cf9d9765c",
	"data": {
		"name": "Default Segment",
		"criteria": {
			"filter": "any",
			"clauses": [
				{
					"value": "1",
					"source": "1",
					"operator": "eq"
				}
			]
		},
		"surveyId": "76a86650-5524-4634-bbad-ad52f5237f7d",
		"campaignId": "b29dd2bc-677a-42ba-a327-51f1d9a155e9",
		"precedence": 1
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03 T18:55:29.763Z",
		"modified": "2019-04-03 T18:55:29.763Z",
		"resource": "segments",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```


## Get many segments

> Example Request

```http
GET /segments?filter%5B%2Fdata%2FcampaignId%5D=b29dd2bc-677a-42ba-a327-51f1d9a155e9&skip=0&limit=9007199254740991&sort=id&sort=ASC HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"data": [
		{
			"id": "2e4bfb7c-82aa-4373-9b7c-9c7cf9d9765c",
			"data": {
				"name": "Default Segment",
				"criteria": {
					"filter": "any",
					"clauses": [
						{
							"value": "1",
							"source": "1",
							"operator": "eq"
						}
					]
				},
				"surveyId": "76a86650-5524-4634-bbad-ad52f5237f7d",
				"campaignId": "b29dd2bc-677a-42ba-a327-51f1d9a155e9",
				"precedence": 1
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03 T18:55:29.763Z",
				"modified": "2019-04-03 T18:55:29.763Z",
				"resource": "segments",
				"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
				"isDeleted": false,
				"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		},
		{
			"id": "ba192430-14b5-44f7-3820-fc6b9aa35813",
			"data": {
				"name": "Default Segment 2",
				"criteria": {
					"filter": "any",
					"clauses": [
						{
							"value": "1",
							"source": "1",
							"operator": "eq"
						}
					]
				},
				"surveyId": "76a86650-5524-4634-bbad-ad52f5237f7d",
				"campaignId": "b29dd2bc-677a-42ba-a327-51f1d9a155e9",
				"precedence": 2
			},
			"meta": {
				"etag": "",
				"created": "2019-02-01 T18:55:19.762Z",
				"modified": "2019-02-01 T18:55:19.762Z",
				"resource": "segments",
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

`GET /segments`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | false | Query to filter data. e.g. `/data/campaignId eq "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319"`
limit | true | Limits number of result-rows. Should be a positive integer. Useful for pagination.
skip | true | Offset data by given number. Useful for pagination.
sort | true | Sort the column in `ASC` or `DESC` e.g. ['id', 'ASC']


## Get a segment

> Example Request

```http
GET /segments/2e4bfb7c-82aa-4373-9b7c-9c7cf9d9765c HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"id": "2e4bfb7c-82aa-4373-9b7c-9c7cf9d9765c",
	"data": {
		"name": "Default Segment",
		"criteria": {
			"filter": "any",
			"clauses": [
				{
					"value": "1",
					"source": "1",
					"operator": "eq"
				}
			]
		},
		"surveyId": "76a86650-5524-4634-bbad-ad52f5237f7d",
		"campaignId": "b29dd2bc-677a-42ba-a327-51f1d9a155e9",
		"precedence": 1
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03 T18:55:29.763Z",
		"modified": "2019-04-03 T18:55:29.763Z",
		"resource": "segments",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`GET /segments/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the segment to be retrieved.


## Create a segment

> Example Request

```http
POST /segments HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"data": {
		"campaignId": "b29dd2bc-677a-42ba-a327-51f1d9a155e9",
		"name": "Default Segment",
		"surveyId": "76a86650-5524-4634-bbad-ad52f5237f7d",
		"criteria": {
			"filter": "any",
			"clauses": [
				{
					"source": "1",
					"operator": "eq",
					"value": "1"
				}
			]
		}
	}
}
```

> Example Response

```json
{
	"id": "2e4bfb7c-82aa-4373-9b7c-9c7cf9d9765c",
	"data": {
		"name": "Default Segment",
		"criteria": {
			"filter": "any",
			"clauses": [
				{
					"value": "1",
					"source": "1",
					"operator": "eq"
				}
			]
		},
		"surveyId": "76a86650-5524-4634-bbad-ad52f5237f7d",
		"campaignId": "b29dd2bc-677a-42ba-a327-51f1d9a155e9",
		"precedence": 1
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03 T18:55:29.763Z",
		"modified": "2019-04-03 T18:55:29.763Z",
		"resource": "segments",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`POST /segments`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
data | true | Data of the segment to be created


## Swap precedences between two segments

> Example Request

```http
POST /segments/swap-precedences HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"data": {
		"segments": [
			{
				"id": "ba192430-14b5-44f7-3820-fc6b9aa35813",
				"etag": "277-ZiR5elWikIT8dF9V8hS/O/LSLDU"
			},
			{
				"id": "2e4bfb7c-82aa-4373-9b7c-9c7cf9d9765c",
				"etag": "27d-nhGX43ixs4LwVlZq03E7K3NF2yE"
			}
		]
	}
}
```

> Example Response

```json
{
	"data": [
		{
			"id": "ba192430-14b5-44f7-3820-fc6b9aa35813",
			"data": {
				"name": "Default Segment 2",
				"criteria": {
					"filter": "any",
					"clauses": [
						{
							"value": "1",
							"source": "1",
							"operator": "eq"
						}
					]
				},
				"surveyId": "76a86650-5524-4634-bbad-ad52f5237f7d",
				"campaignId": "b29dd2bc-677a-42ba-a327-51f1d9a155e9",
				"precedence": 1
			},
			"meta": {
				"etag": "",
				"created": "2019-02-01 T18:55:19.762Z",
				"modified": "2019-02-01 T18:55:19.762Z",
				"resource": "segments",
				"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
				"isDeleted": false,
				"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		},
		{
			"id": "2e4bfb7c-82aa-4373-9b7c-9c7cf9d9765c",
			"data": {
				"name": "Default Segment",
				"criteria": {
					"filter": "any",
					"clauses": [
						{
							"value": "1",
							"source": "1",
							"operator": "eq"
						}
					]
				},
				"surveyId": "76a86650-5524-4634-bbad-ad52f5237f7d",
				"campaignId": "b29dd2bc-677a-42ba-a327-51f1d9a155e9",
				"precedence": 2
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03 T18:55:29.763Z",
				"modified": "2019-04-03 T18:55:29.763Z",
				"resource": "segments",
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

`POST /segments/swap-precedences`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
data | false | Data containing 2 segments whose precedences are to be swapped

## Update a segment

> Example Request

```http
PATCH /segments/2e4bfb7c-82aa-4373-9b7c-9c7cf9d9765c HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
{
	"data": [
		{
			"op": "replace",
			"path": "/name",
			"value": "My Segment Name Changed"
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
	"id": "2e4bfb7c-82aa-4373-9b7c-9c7cf9d9765c",
	"data": {
		"name": "My Segment Name Changed",
		"criteria": {
			"filter": "any",
			"clauses": [
				{
					"value": "1",
					"source": "1",
					"operator": "eq"
				}
			]
		},
		"surveyId": "76a86650-5524-4634-bbad-ad52f5237f7d",
		"campaignId": "b29dd2bc-677a-42ba-a327-51f1d9a155e9",
		"precedence": 1
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03 T18:55:29.763Z",
		"modified": "2019-04-12 T13:34:19.333Z",
		"resource": "segments",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`PATCH /segments/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the segment to be updated.
data | true | The patch data


## Delete a segment

> Example Request

```http
DELETE /segments/2e4bfb7c-82aa-4373-9b7c-9c7cf9d9765c HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
```

### HTTP Request

`DELETE /segments/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the segment to be deleted.

