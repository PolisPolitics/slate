# Households

## The Household object

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Identifier of this record
securityGroupId | true | Identifier of the associated security group
customerId | true | Identifier of the associated customer
data | true | Household data

### meta

[See documentation](#metadata-object)



```json
{
	"id": "1b6e3e26-511c-48c5-ab38-1317072f7276",
	"data": {
		"unitNum": "Apt. 2",
		"addressId": "d58ff153-ddd4-4b91-9f80-07de095b1b19"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:30.088Z",
		"modified": "2019-04-03T18:55:30.088Z",
		"resource": "households",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

## Get many households

> Example Request

```http
GET /households?filter%5B%2FcustomerId%5D=286d1af1-c2c5-4069-a19d-3987fdacc0d6&skip=0&limit=9007199254740991&sort=id&sort=ASC HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"data": [
		{
			"id": "1b6e3e26-511c-48c5-ab38-1317072f7276",
			"data": {
				"unitNum": "Apt. 2",
				"addressId": "d58ff153-ddd4-4b91-9f80-07de095b1b19"
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:30.088Z",
				"modified": "2019-04-03T18:55:30.088Z",
				"resource": "households",
				"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
				"isDeleted": false,
				"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		},
		{
			"id": "b810c49b-9585-46a3-9e62-77b48c293d88",
			"data": {
				"unitNum": "Apt. 1",
				"addressId": "3a2be50d-a8bc-47b4-833f-1962ef197751"
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:30.088Z",
				"modified": "2019-04-03T18:55:30.088Z",
				"resource": "households",
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

`GET /households`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | false | Query to filter data. `/data/customerId eq "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319"`
limit | true | Limits number of result-rows. Should be a positive integer. Useful for pagination.
skip | true | Offset data by given number. Useful for pagination.
sort | true | Sort the column in `ASC` or `DESC` e.g. ['id', 'ASC']


## Get a household

> Example Request

```http
GET /households/1b6e3e26-511c-48c5-ab38-1317072f7276 HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"id": "1b6e3e26-511c-48c5-ab38-1317072f7276",
	"data": {
		"unitNum": "Apt. 2",
		"addressId": "d58ff153-ddd4-4b91-9f80-07de095b1b19"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:30.088Z",
		"modified": "2019-04-03T18:55:30.088Z",
		"resource": "households",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`GET /households/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the household to be retrieved.


## Create a household

> Example Request

```http
POST /households HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"data": {
		"unitNum": "Apt. 2",
		"address": {
			"data": {
				"number": "1",
				"streetName": "Morris Stream",
				"city": "North Vincefurt",
				"coords": {
					"lat": 42.3795514,
					"lng": -71.2525621
				},
				"country": "USA",
				"county": null,
				"neighborhood": null,
				"state": "Idaho",
				"postalCode": "25079-7079"
			}
		}
	},
	"customerId": "b1b101cf-646c-4ad2-86e7-9683209b1633"
}
```

> Example Response

```json
{
	"id": "1b6e3e26-511c-48c5-ab38-1317072f7276",
	"data": {
		"unitNum": "Apt. 2",
		"addressId": "d58ff153-ddd4-4b91-9f80-07de095b1b19"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:30.088Z",
		"modified": "2019-04-03T18:55:30.088Z",
		"resource": "households",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`POST /households`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
customerId | true | The id of the customer to which this resoruce belongs
data | true | The data of household to be created


## Update a household

> Example Request

```http
PATCH /households/1b6e3e26-511c-48c5-ab38-1317072f7276 HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
{
	"data": [
		{
			"op": "replace",
			"path": "/unitNum",
			"value": "Apt. 3"
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
	"id": "1b6e3e26-511c-48c5-ab38-1317072f7276",
	"data": {
		"unitNum": "Apt. 3",
		"addressId": "d58ff153-ddd4-4b91-9f80-07de095b1b19"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:30.088Z",
		"modified": "2019-04-04T19:35:30.088Z",
		"resource": "households",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`PATCH /households/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the household to be updated
data | true | The patch data 


## Delete an item from households

> Example Request

```http
DELETE /households/1b6e3e26-511c-48c5-ab38-1317072f7276 HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
```

### HTTP Request

`DELETE /households/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the household to be deleted.

