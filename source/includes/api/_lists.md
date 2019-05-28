# Lists

## The List object

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Identifier of this record
securityGroupId | true | Identifier of the associated securitygroup
customerId | true | Identifier of the associated customer
data | true | The list data
contactsCount | false | Number of contacts in this list

### data

Attribute | Required? | Description
--------- | --------- | -----------
organizationId | true | Identifier of the organization to which this list belongs
name | true | Name of this list
description | false | Description text of this list
required | false | Array of strings
integrations | false | Array of the integrations associated with this list

### meta

[See documentation](#metadata-object)



```json
{
	"id": "588b44db-3444-4732-92db-158db44202eb",
	"data": {
		"name": "Default List",
		"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:26.876Z",
		"modified": "2019-04-03T18:55:26.876Z",
		"resource": "lists",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```


## Get many lists

> Example Request

```http
GET /lists?filter%5B%2Fdata%2ForganizationId%5D=309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7&skip=0&limit=9007199254740991&sort=id&sort=ASC HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"data": [
		{
			"id": "588b44db-3444-4732-92db-158db44202eb",
			"data": {
				"name": "Default List",
				"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:26.876Z",
				"modified": "2019-04-03T18:55:26.876Z",
				"resource": "lists",
				"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
				"isDeleted": false,
				"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		},
		{
			"id": "588b44db-3444-4732-92db-158db44202eb",
			"data": {
				"name": "Default List2",
				"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
			},
			"meta": {
				"created": "2019-04-22T18:33:19.206Z",
				"createdBy": "399afc5b-b121-41c1-ba79-79ef0ab609e2",
				"etag": "1db-a3NjEibf5QsgGhIG//sl4LFKeJg",
				"isDeleted": false,
				"modified": "2019-04-22T18:33:19.206Z",
				"modifiedBy": "399afc5b-b121-41c1-ba79-79ef0ab609e2",
				"resource": "lists"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		}
	],
	"meta": {}
}
```

### HTTP Request

`GET /lists`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | false | Query to filter data. <br/> e.g. '"/data/customerId": "c10cbd70-5a2f-440d-9e0d-7b9ea23daf3b"'
limit | true | Limits number of result-rows. Should be a positive integer. Useful for pagination.
skip | true | Offset data by given number. Useful for pagination.
sort | true | Sort the column in `ASC` or `DESC` e.g. ['id', 'ASC']

## Get a list

> Example Request

```http
GET /lists/588b44db-3444-4732-92db-158db44202eb HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"id": "588b44db-3444-4732-92db-158db44202eb",
	"data": {
		"name": "Default List",
		"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:26.876Z",
		"modified": "2019-04-03T18:55:26.876Z",
		"resource": "lists",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`GET /lists/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the list.


## Get all contact-households associated with this list

> Example Request

```http
GET /lists/588b44db-3444-4732-92db-158db44202eb/contact-households HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"meta": {},
	"data": [
		{
			"id": "588b44db-3444-4732-92db-158db44202eb",
			"data": {
				"contact": {
					"id": "d0962192-9176-41fa-b273-49012b60d1ad",
					"data": {
						"fields": {
							"00f958a1-59a0-4c24-9934-4055c331b346": "et",
							"06da30ef-2965-4ee6-8a50-4f382bac8624": "tenetur",
							"0cd21b15-8695-4a38-9f4b-4b0f7b3e027a": [
								"Parrot"
							],
							"8cbb5d35-2b3e-42d2-808a-489aea71d53b": "Moved",
							"acb72116-dac5-4c58-8ec4-4aa0921a5b66": "voluptas",
							"c00b6f02-ee45-4787-a048-9d1e2a543856": "true",
							"fd9f52f4-d09f-42b6-87c6-5eebddc559e2": "false"
						},
						"profile": {
							"age": 18,
							"name": {
								"anglican": {
									"given": "Jon",
									"surname": "Snow"
								}
							},
							"emails": [
								{
									"email": "callmejon@ravenmail.com",
									"active": true,
									"primary": true
								},
								{
									"email": "lordcommander@hotmail.com",
									"active": true,
									"primary": false
								}
							],
							"gender": "n",
							"phones": [
								{
									"phone": "1-329-473-9959 x176",
									"active": true,
									"primary": true,
									"phoneType": "business"
								},
								{
									"phone": "777-881-3298 x5830",
									"active": true,
									"primary": false,
									"phoneType": "home"
								}
							]
						},
						"primaryHouseholdId": "4b5474ae-7919-46d1-b0f3-81fc8601e86a"
					},
					"meta": {
						"created": "2019-04-22T21:39:36.904Z",
						"modified": "2019-04-22T21:39:44.443Z",
						"resource": "contacts",
						"createdBy": "4ace517e-f253-4a0d-9b34-552d22600b94",
						"isDeleted": false,
						"modifiedBy": "4ace517e-f253-4a0d-9b34-552d22600b94",
						"etag": "534-Nnn/uWEldLz7tKDVfHod5MjpkXQ"
					},
					"customerId": "76057c16-2490-413f-830e-643f17f6af93",
					"securityGroupId": "32f55cea-8e11-45d3-b0f2-923bf6d18964"
				},
				"household": {
					"id": "4b5474ae-7919-46d1-b0f3-81fc8601e86a",
					"data": {
						"unitNum": "Apt. 411",
						"address": {
							"id": "6e849c5e-c779-41fb-8908-3492841d2229",
							"data": {
								"city": "East Kaylinshire",
								"coords": {
									"lat": 42.3795514,
									"lng": -71.2525621
								},
								"number": "0",
								"postalCode": "96417",
								"streetName": "Kshlerin Walks",
								"country": "USA",
								"state": "Michigan"
							}
						},
						"formattedAddress": "0 Kshlerin Walks #Apt. 411 East Kaylinshire, USA 96417"
					},
					"meta": {
						"etag": "1da-rAZEuT2ZoWLufs4eahShFIAAxcM",
						"created": "2019-04-22T21:39:36.727Z",
						"modified": "2019-04-22T21:39:36.727Z",
						"resource": "households",
						"createdBy": "4ace517e-f253-4a0d-9b34-552d22600b94",
						"isDeleted": false,
						"modifiedBy": "4ace517e-f253-4a0d-9b34-552d22600b94"
					},
					"customerId": "76057c16-2490-413f-830e-643f17f6af93",
					"securityGroupId": "32f55cea-8e11-45d3-b0f2-923bf6d18964"
				}
			},
			"meta": {
				"etag": "202-mPx7m4qVdNwR9bstKfUGvGCI2wE",
				"created": "2019-04-22T21:39:37.725Z",
				"modified": "2019-04-22T21:39:37.725Z",
				"resource": "contact-households",
				"createdBy": "4ace517e-f253-4a0d-9b34-552d22600b94",
				"isDeleted": false,
				"modifiedBy": "4ace517e-f253-4a0d-9b34-552d22600b94"
			},
			"securityGroupId": "32f55cea-8e11-45d3-b0f2-923bf6d18964",
			"customerId": "76057c16-2490-413f-830e-643f17f6af93"
		},
		{
			"id": "c0cd34e0-b2ea-400b-adf4-d3e4e7d821d0",
			"data": {
				"contact": {
					"id": "41de2227-3690-4787-8902-f75de381d708",
					"data": {
						"fields": {
							"00f958a1-59a0-4c24-9934-4055c331b346": "dignissimos",
							"06da30ef-2965-4ee6-8a50-4f382bac8624": "deserunt",
							"0cd21b15-8695-4a38-9f4b-4b0f7b3e027a": [
								"Dog"
							],
							"22ed0c4b-125c-46f0-9d68-cb7d893efc3b": 4,
							"3d1d5fbc-3b45-4bb4-a000-4c480e6ea8fd": "Apartment",
							"801e8511-aded-459d-ba0c-5dda80c4e400": [
								"Horse"
							]
						},
						"profile": {
							"age": 70,
							"name": {
								"anglican": {
									"given": "James",
									"surname": "Bond"
								}
							},
							"emails": [
								{
									"email": "007@licensetokill.com",
									"active": true,
									"primary": false
								}
							],
							"gender": "n",
							"phones": [
								{
									"phone": "(135) 200-5286",
									"active": true,
									"primary": true,
									"phoneType": "home"
								},
								{
									"phone": "1-547-600-5799",
									"active": true,
									"primary": false,
									"phoneType": "home"
								}
							]
						},
						"primaryHouseholdId": "c1c47185-e981-4d51-92a0-3818de7f6ef4"
					},
					"meta": {
						"created": "2019-04-22T21:39:36.900Z",
						"modified": "2019-04-22T21:39:42.839Z",
						"resource": "contacts",
						"createdBy": "4ace517e-f253-4a0d-9b34-552d22600b94",
						"isDeleted": false,
						"modifiedBy": "4ace517e-f253-4a0d-9b34-552d22600b94",
						"etag": "543-vnCuT7dj0G7yAz2uGC08IGJFYKI"
					},
					"customerId": "76057c16-2490-413f-830e-643f17f6af93",
					"securityGroupId": "32f55cea-8e11-45d3-b0f2-923bf6d18964"
				},
				"household": {
					"id": "c1c47185-e981-4d51-92a0-3818de7f6ef4",
					"data": {
						"unitNum": "Apt. 222",
						"address": {
							"id": "e17c981d-482b-4f2d-8bb9-749250e0f026",
							"data": {
								"city": "Christiansenberg",
								"coords": {
									"lat": 42.3795514,
									"lng": -71.2525621
								},
								"number": "0",
								"postalCode": "62567",
								"streetName": "Marks Road",
								"country": "USA",
								"state": "North Dakota"
							}
						},
						"formattedAddress": "0 Marks Road #Apt. 3L Christiansenberg, USA 62567"
					},
					"meta": {
						"etag": "1d9-XMrIOhRDGR1IPrW9kp5ghTbtl2g",
						"created": "2019-04-22T21:39:36.727Z",
						"modified": "2019-04-22T21:39:36.727Z",
						"resource": "households",
						"createdBy": "4ace517e-f253-4a0d-9b34-552d22600b94",
						"isDeleted": false,
						"modifiedBy": "4ace517e-f253-4a0d-9b34-552d22600b94"
					},
					"customerId": "76057c16-2490-413f-830e-643f17f6af93",
					"securityGroupId": "32f55cea-8e11-45d3-b0f2-923bf6d18964"
				}
			},
			"meta": {
				"etag": "202-5IM96VQACJhHi0WQvr1AeT6loIg",
				"created": "2019-04-22T21:39:37.753Z",
				"modified": "2019-04-22T21:39:37.753Z",
				"resource": "contact-households",
				"createdBy": "4ace517e-f253-4a0d-9b34-552d22600b94",
				"isDeleted": false,
				"modifiedBy": "4ace517e-f253-4a0d-9b34-552d22600b94"
			},
			"securityGroupId": "32f55cea-8e11-45d3-b0f2-923bf6d18964",
			"customerId": "76057c16-2490-413f-830e-643f17f6af93"
		}
	]
}
```

### HTTP Request

`GET /lists/{id}/contact-households`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | false | Query to filter data.
limit | true | Limits number of result-rows. Should be a positive integer. Useful for pagination.
skip | true | Offset data by given number. Useful for pagination.
sort | true | Sort the column in `ASC` or `DESC` e.g. ['/data/profile/name/anglican/given', 'ASC']


## Create a list

> Example Request

```http
POST /lists HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"data": {
		"name": "Default List",
		"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
	}
}
```

> Example Response

```json
{
	"id": "588b44db-3444-4732-92db-158db44202eb",
	"data": {
		"name": "Default List",
		"organizationId": "309f8d1e-f426-488a-bd1b-0ca3fe3c2cc7"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:26.876Z",
		"modified": "2019-04-03T18:55:26.876Z",
		"resource": "lists",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`POST /lists`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
data | true | The data for the list to be created
securityGroupId | false | The identifier of the security group associated with


## Deletes a contact-household-list record

> Example Request

```http
DELETE /lists/588b44db-3444-4732-92db-158db44202eb/contacts/865ab014-ebbd-4246-b13d-ac3fd07475a0/households/a63a4dd6-ade7-4d23-b2f6-2a38dcc17e06 HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
```

### HTTP Request

`DELETE /lists/{listId}/contacts/{contactId}/households/{householdId}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
listId | true | The identifier of a list.
contactId | true | The identifier of a contact.
householdId | true | The identifier of a household.


## Creates a contact-household-list record

> Example Request

```http
PUT /lists/588b44db-3444-4732-92db-158db44202eb/contacts/865ab014-ebbd-4246-b13d-ac3fd07475a0/households/a63a4dd6-ade7-4d23-b2f6-2a38dcc17e06 HTTP/1.1
Host: api2.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"coords": {
		"lat": 42.3795514,
		"lng": -71.2525621
	},
	"listId": "588b44db-3444-4732-92db-158db44202eb",
	"contactHouseholdId": "3d637423-3f11-466d-9a3b-4ad4dccfad8d"
}
```

### HTTP Request

`PUT /lists/{listId}/contacts/{contactId}/households/{householdId}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
listId | true | The id of a list.
contactId | true | The id of a contact.
householdId | true | The id of a household.

