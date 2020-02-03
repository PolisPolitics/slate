# Notes

## The Note object

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Id of this record.
securityGroupId | true | Id of the associated security group.
customerId | true | Id of the associated customer.
data | true | Note data.

### data

Attribute | Required? | Description
--------- | --------- | -----------
contactId | true | Id of the contact associated with this note.
text | true | Note text.

### meta

[See documentation](#metadata-object)



```json
{
	"id": "a0da6886-1e0e-455a-a647-54444d1d8177",
	"data": {
		"text": "Test Note",
		"contactId": "73418dea-d0fd-4b6a-942c-4b9e5c4aa326"
	},
	"meta": {
		"etag": "1d3-B8XNOdGew5E1MYUhULxvvPls7IY",
		"created": "2019-05-22T16:49:13.133Z",
		"modified": "2019-05-22T16:49:13.133Z",
		"resource": "notes",
		"createdBy": "1aba8dff-e969-47f8-b04f-0108c4e8fe25",
		"isDeleted": false,
		"modifiedBy": "1aba8dff-e969-47f8-b04f-0108c4e8fe25"
	},
	"customerId": "74f47d6d-57d6-4ebf-8fae-75ca92a37fc1",
	"securityGroupId": "d3d173ca-d182-454f-a5fd-c6b873e02204"
}
```


## Retrieve many notes

> Example Request

```http
GET /notes?filter%5B%2Fdata%2FcontactId%5D=ad437213-1ad1-4f01-8662-463b066a4188&skip=0&limit=9007199254740991&sort=id&sort=ASC HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"data": [
		{
			"id": "a0da6886-1e0e-455a-a647-54444d1d8177",
			"data": {
				"text": "Test Note",
				"contactId": "ad437213-1ad1-4f01-8662-463b066a4188"
			},
			"meta": {
				"etag": "1d3-B8XNOdGew5E1MYUhULxvvPls7IY",
				"created": "2019-05-22T16:49:13.133Z",
				"modified": "2019-05-22T16:49:13.133Z",
				"resource": "notes",
				"createdBy": "1aba8dff-e969-47f8-b04f-0108c4e8fe25",
				"isDeleted": false,
				"modifiedBy": "1aba8dff-e969-47f8-b04f-0108c4e8fe25"
			},
			"customerId": "74f47d6d-57d6-4ebf-8fae-75ca92a37fc1",
			"securityGroupId": "d3d173ca-d182-454f-a5fd-c6b873e02204"
		},
		{
			"id": "2206c14b-555e-4aad-9bbe-06f582657d45",
			"data": {
				"text": "Test Note 2",
				"contactId": "ad437213-1ad1-4f01-8662-463b066a4188"
			},
			"meta": {
				"etag": "1d3-sPbBRuVl7ntj4hgRDY4wya0nqvY",
				"created": "2019-05-22T16:53:59.059Z",
				"modified": "2019-05-22T16:53:59.059Z",
				"resource": "notes",
				"createdBy": "01d5bae1-4a81-4384-bf1a-447883e8a10e",
				"isDeleted": false,
				"modifiedBy": "01d5bae1-4a81-4384-bf1a-447883e8a10e"
			},
			"customerId": "6328940b-fcc5-4f6b-a08e-0ad8f02fabe6",
			"securityGroupId": "f641058b-4b29-43c6-ba17-e9f46ef75707"
		}
	],
	"meta": {}
}
```

### HTTP Request

`GET /notes`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | false | Query to filter data. <br/> e.g. '"/data/contactId": "c10cbd70-5a2f-440d-9e0d-7b9ea23daf3b"'
limit | true | Limits number of result-rows. Should be a positive integer. Useful for pagination.
skip | true | Offset data by given number. Useful for pagination.
sort | true | Sort the column in `ASC` or `DESC` e.g. ['id', 'ASC']


## Retrieve a note

> Example Request

```http
GET /notes/a0da6886-1e0e-455a-a647-54444d1d8177 HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"id": "a0da6886-1e0e-455a-a647-54444d1d8177",
	"data": {
		"text": "Test Note",
		"contactId": "ad437213-1ad1-4f01-8662-463b066a4188"
	},
	"meta": {
		"etag": "1d3-B8XNOdGew5E1MYUhULxvvPls7IY",
		"created": "2019-05-22T16:49:13.133Z",
		"modified": "2019-05-22T16:49:13.133Z",
		"resource": "notes",
		"createdBy": "1aba8dff-e969-47f8-b04f-0108c4e8fe25",
		"isDeleted": false,
		"modifiedBy": "1aba8dff-e969-47f8-b04f-0108c4e8fe25"
	},
	"customerId": "74f47d6d-57d6-4ebf-8fae-75ca92a37fc1",
	"securityGroupId": "d3d173ca-d182-454f-a5fd-c6b873e02204"
}
```

### HTTP Request

`GET /notes/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the note to be retrieved.


## Create a note

> Example Request

```http
POST /notes HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"data": {
		"text": "New Note",
		"contactId": "4605efa6-5cab-49fc-ad2b-5af81daf4357"
	}
}
```

> Example Response

```json
{
	"id": "3a009b0b-f9da-4358-8908-95cd71b19870",
	"data": {
		"text": "New Note",
		"contactId": "4605efa6-5cab-49fc-ad2b-5af81daf4357"
	},
	"meta": {
		"etag": "1d4-cam1EaO0GUAtNnDDfangPQvOeRU",
		"created": "2019-05-22T17:03:21.900Z",
		"modified": "2019-05-22T17:03:21.900Z",
		"resource": "notes",
		"createdBy": "e9febcba-3a6b-4d28-bc4c-9bcd33a716be",
		"isDeleted": false,
		"modifiedBy": "e9febcba-3a6b-4d28-bc4c-9bcd33a716be"
	},
	"customerId": "c03b08dc-4134-4546-a23f-b5463cb1334c",
	"securityGroupId": "65e7e1e5-1b08-4c72-9052-d6c869d7de4d"
}
```

### HTTP Request

`POST /notes`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
data | true | The data of the new note to be created.


## Update a note

> Example Request

```http
PATCH /notes/3a009b0b-f9da-4358-8908-95cd71b19870 HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: 1d4-cam1EaO0GUAtNnDDfangPQvOeRU
{
	"data": [
		{
			"op": "replace",
			"path": "/text",
			"value": "Patched note"
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
	"id": "3a009b0b-f9da-4358-8908-95cd71b19870",
	"data": {
		"text": "Patched note",
		"contactId": "4605efa6-5cab-49fc-ad2b-5af81daf4357"
	},
	"meta": {
		"etag": "1d4-cam1EaO0GUAtNnDDfangPQvOeRU",
		"created": "2019-05-22T17:03:21.900Z",
		"modified": "2019-05-22T17:03:21.900Z",
		"resource": "notes",
		"createdBy": "e9febcba-3a6b-4d28-bc4c-9bcd33a716be",
		"isDeleted": false,
		"modifiedBy": "e9febcba-3a6b-4d28-bc4c-9bcd33a716be"
	},
	"customerId": "c03b08dc-4134-4546-a23f-b5463cb1334c",
	"securityGroupId": "65e7e1e5-1b08-4c72-9052-d6c869d7de4d"
}
```

### HTTP Request

`PATCH /notes/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the notes.
data | true | The patch data in [JSONPatch Format](https://tools.ietf.org/html/rfc6902).


## Delete an item from notes

> Example Request

```http
DELETE /notes/a0da6886-1e0e-455a-a647-54444d1d8177 HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: 1d3-B8XNOdGew5E1MYUhULxvvPls7IY
```

> Example Response

```http
HTTP 200 Success
```

### HTTP Request

`DELETE /notes/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the note to be deleted.
