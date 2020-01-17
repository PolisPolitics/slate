# Contacts

## The Contacts object

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Identifier of this record.
securityGroupId | true | Identifier of the associated security group.
customerId | true | Identifier of the associated customer.
data | true | Contacts data.

### data

Attribute | Required? | Description
--------- | --------- | -----------
profile | true | Contact profile. [details](#data-profile)
notes | false | String with custom text (max length: 2048 characters).
fields | true | Custom fields.
externalId | false | An external identifier for imports and exports.
primaryHouseholdId | false | Id of the primary household associated for this contact.

### data/profile

Attribute | Required? | Description
--------- | --------- | -----------
name | false | Contact name.
emails | false | Array of emails. [details](#data-profile-emails)
phones | false | Array of phones. [details](#data-profile-phones)
gender | false | decline: 'd', female: 'f', male: 'm', nonbinary: 'n', other: 'o'.
languages | false | [ISO 639-1 alpha-2](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) language code (i.e.: en, es, af).
birthdate | false | Birthdate in ISO-8601 format (YYYY-MM-DD).
age | false | Number representing the age of the contact.

### data/profile/name

Attribute | Required? | Description
--------- | --------- | -----------
anglican | true | Name in anglican format.

### data/profile/name/anglican

Attribute | Required? | Description
--------- | --------- | -----------
title | false | Title.
given | true | First name.
middlename | false | Middle name.
surname | true | Surname.
suffix | false | Name Suffix

### data/profile/emails
Array of the following object:

Attribute | Required? | Description
--------- | --------- | -----------
email | false | Email.
active | false | Flag indicating whether this email is active. Default `true`.
primary | false | Flag indicating whether this email is primary. Default `false`.

### data/profile/phones
Array of the following object:

Attribute | Required? | Description
--------- | --------- | -----------
phone | false | Phone.
phoneType | false | Type of the phone. Allowed values `home`, `mobile` or `business`.
active | false | Flag indicating whether this email is active. Default `true`.
primary | false | Flag indicating whether this email is primary. Default `false`.

### meta

[See documentation](#metadata-object)



```json
{
	"id": "b7a9a3e2-e419-4c0a-9d03-4c8f280b2967",
	"data": {
		"fields": {
			"2438cc93-4395-4ded-99f0-0a4ac88e2577": 1,
			"510922c1-0a7e-40e1-b329-168b88c6cf3b": "laboriosam",
			"60a528b7-1b36-483a-9bdb-65c00b067e62": [
				"Snake"
			],
			"77227e62-d098-46b3-985b-a83e19a4850d": "House",
			"7e23f830-23a1-42dc-a33b-5617402cd880": "nemo",
			"83439622-cf55-4f0d-a7da-046862b73761": "true",
			"940f694b-d8d6-4b40-9f3d-efe9b6b110b5": "at",
			"b0f2bc7e-3089-401d-afb7-5e6659d0f1e6": "Deceased",
			"eb444550-4f38-43a2-a5c0-6634c3d9a003": [
				"Dog"
			],
			"fea9b266-3def-4d4e-89fd-824bfed902a3": "true"
		},
		"status": "pending",
		"profile": {
			"age": 66,
			"name": {
				"anglican": {
					"given": "James",
					"surname": "Bond"
				}
			},
			"emails": [
				{
					"email": "007@hotmail.com",
					"active": true,
					"primary": true
				},
				{
					"email": "licensetokill@hotmail.com",
					"active": true,
					"primary": false
				}
			],
			"gender": "m",
			"phones": [
				{
					"phone": "777.777.7007 x72507",
					"active": true,
					"primary": true,
					"phoneType": "mobile"
				},
				{
					"phone": "1-960-777-7777",
					"active": true,
					"primary": false,
					"phoneType": "mobile"
				}
			]
		},
		"primaryHouseholdId": "d2aa6679-62e2-40ec-aeb7-616ad3a3f77d"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:30.718Z",
		"modified": "2019-04-03T18:55:30.718Z",
		"resource": "contacts",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```


## Get many contacts

> Example Request

```http
GET /v2/contacts?filter%5B%2FcustomerId%5D=286d1af1-c2c5-4069-a19d-3987fdacc0d6&skip=0&limit=9007199254740991&sort=id&sort=ASC HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"data": [
		{
			"id": "b7a9a3e2-e419-4c0a-9d03-4c8f280b2967",
			"data": {
				"fields": {
					"2438cc93-4395-4ded-99f0-0a4ac88e2577": 1,
					"510922c1-0a7e-40e1-b329-168b88c6cf3b": "laboriosam",
					"60a528b7-1b36-483a-9bdb-65c00b067e62": [
						"Snake"
					],
					"77227e62-d098-46b3-985b-a83e19a4850d": "House",
					"7e23f830-23a1-42dc-a33b-5617402cd880": "nemo",
					"83439622-cf55-4f0d-a7da-046862b73761": "true",
					"940f694b-d8d6-4b40-9f3d-efe9b6b110b5": "at",
					"b0f2bc7e-3089-401d-afb7-5e6659d0f1e6": "Deceased",
					"eb444550-4f38-43a2-a5c0-6634c3d9a003": [
						"Dog"
					],
					"fea9b266-3def-4d4e-89fd-824bfed902a3": "true"
				},
				"status": "pending",
				"profile": {
					"age": 66,
					"name": {
						"anglican": {
							"given": "James",
							"surname": "Bond"
						}
					},
					"emails": [
						{
							"email": "007@hotmail.com",
							"active": true,
							"primary": true
						},
						{
							"email": "licensetokill@hotmail.com",
							"active": true,
							"primary": false
						}
					],
					"gender": "m",
					"phones": [
						{
							"phone": "777.777.7007 x72507",
							"active": true,
							"primary": true,
							"phoneType": "mobile"
						},
						{
							"phone": "1-960-777-7777",
							"active": true,
							"primary": false,
							"phoneType": "mobile"
						}
					]
				},
				"primaryHouseholdId": "d2aa6679-62e2-40ec-aeb7-616ad3a3f77d"
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:30.718Z",
				"modified": "2019-04-03T18:55:30.718Z",
				"resource": "contacts",
				"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
				"isDeleted": false,
				"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		},
		{
			"id": "3189f3ed-b78a-4586-a86d-b7e1aa1a1099",
			"data": {
				"fields": {
					"2438cc93-4395-4ded-99f0-0a4ac88e2577": 3,
					"510922c1-0a7e-40e1-b329-168b88c6cf3b": "perferendis",
					"60a528b7-1b36-483a-9bdb-65c00b067e62": [
						"Horse"
					],
					"77227e62-d098-46b3-985b-a83e19a4850d": "House",
					"7e23f830-23a1-42dc-a33b-5617402cd880": "sed",
					"83439622-cf55-4f0d-a7da-046862b73761": "false",
					"940f694b-d8d6-4b40-9f3d-efe9b6b110b5": "aliquid",
					"b0f2bc7e-3089-401d-afb7-5e6659d0f1e6": "Refused",
					"eb444550-4f38-43a2-a5c0-6634c3d9a003": [
						"Dog"
					],
					"fea9b266-3def-4d4e-89fd-824bfed902a3": "true"
				},
				"status": "pending",
				"profile": {
					"age": 63,
					"name": {
						"anglican": {
							"given": "Aegon",
							"surname": "Targaeryan"
						}
					},
					"emails": [
						{
							"email": "callmejon@ravenmail.com",
							"active": true,
							"primary": true
						},
						{
							"email": "lordcommander@nightswatch.com",
							"active": true,
							"primary": false
						}
					],
					"gender": "n",
					"phones": [
						{
							"phone": "(111) 111-1111",
							"active": true,
							"primary": true,
							"phoneType": "home"
						}
					]
				},
				"primaryHouseholdId": "f0cbc9d5-28e0-4123-bcb5-80ece858153c"
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:30.719Z",
				"modified": "2019-04-03T18:55:30.719Z",
				"resource": "contacts",
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

`GET https://api.polisapp.com/v2/contacts`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | false | Query to filter data. `/customerId eq "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319"`
limit | true | Limits number of result-rows. Should be a positive integer. Useful for pagination.
skip | true | Offset data by given number. Useful for pagination.
sort | true | Sort the column in `ASC` or `DESC` e.g. ['id', 'ASC']


## Get a contact

> Example Request

```http
GET /v2/contacts/b7a9a3e2-e419-4c0a-9d03-4c8f280b2967 HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"id": "b7a9a3e2-e419-4c0a-9d03-4c8f280b2967",
	"data": {
		"fields": {
			"2438cc93-4395-4ded-99f0-0a4ac88e2577": 1,
			"510922c1-0a7e-40e1-b329-168b88c6cf3b": "laboriosam",
			"60a528b7-1b36-483a-9bdb-65c00b067e62": [
				"Snake"
			],
			"77227e62-d098-46b3-985b-a83e19a4850d": "House",
			"7e23f830-23a1-42dc-a33b-5617402cd880": "nemo",
			"83439622-cf55-4f0d-a7da-046862b73761": "true",
			"940f694b-d8d6-4b40-9f3d-efe9b6b110b5": "at",
			"b0f2bc7e-3089-401d-afb7-5e6659d0f1e6": "Deceased",
			"eb444550-4f38-43a2-a5c0-6634c3d9a003": [
				"Dog"
			],
			"fea9b266-3def-4d4e-89fd-824bfed902a3": "true"
		},
		"status": "pending",
		"profile": {
			"age": 66,
			"name": {
				"anglican": {
					"given": "James",
					"surname": "Bond"
				}
			},
			"emails": [
				{
					"email": "007@hotmail.com",
					"active": true,
					"primary": true
				},
				{
					"email": "licensetokill@hotmail.com",
					"active": true,
					"primary": false
				}
			],
			"gender": "m",
			"phones": [
				{
					"phone": "777.777.7007 x72507",
					"active": true,
					"primary": true,
					"phoneType": "mobile"
				},
				{
					"phone": "1-960-777-7777",
					"active": true,
					"primary": false,
					"phoneType": "mobile"
				}
			]
		},
		"primaryHouseholdId": "d2aa6679-62e2-40ec-aeb7-616ad3a3f77d"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:30.718Z",
		"modified": "2019-04-03T18:55:30.718Z",
		"resource": "contacts",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`GET https://api.polisapp.com/v2/contacts/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the contact to be retrieved.


## Get all the households for a contact

> Example Request

```http
GET /v2/contacts/e5554be7-0b3c-45cf-9c78-266dc45e2878/households/ HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"data": [
		{
			"id": "e5554be7-0b3c-45cf-9c78-266dc45e2878",
			"data": {
				"unitNum": "1119",
				"address": {
					"id": "1733d7c1-a86a-45ca-a482-b2c966f40d94",
					"data": {
						"city": "Cambridge",
						"coords": {
							"lat": 42.3795514,
							"lng": -71.2525621
						},
						"number": "10",
						"postalCode": "02115",
						"streetName": "Ware St",
						"country": "USA",
						"state": "Massachusetts"
					}
				}
			},
			"meta": {
				"etag": "1d6-xrQmtj+iIt6a0EB+5vdp6DrDDxg",
				"created": "2019-04-22T20:53:20.615Z",
				"modified": "2019-04-22T20:53:20.615Z",
				"resource": "households",
				"createdBy": "c9891431-53b1-4be6-81bb-bc853b035618",
				"isDeleted": false,
				"modifiedBy": "c9891431-53b1-4be6-81bb-bc853b035618"
			},
			"customerId": "5edda33d-0268-4fb5-849f-cd100e02ef04",
			"securityGroupId": "b5464d3b-6ac1-45a9-b804-9a5009e894ed",
			"params": {
				"contactHouseholdId": "1321a9bb-fb90-4cdb-a964-6e63c895cd73"
			}
		},
		{
			"id": "273b66d6-e1b6-466d-816f-f85ea74cdc73",
			"data": {
				"unitNum": "200",
				"address": {
					"id": "1d329289-f846-43bd-ae3a-1922844d4367",
					"data": {
						"city": "Cambridge",
						"coords": {
							"lat": 42.3795514,
							"lng": -71.2525621
						},
						"number": "20",
						"postalCode": "02115",
						"streetName": "Main St",
						"country": "USA",
						"state": "Massachusetts"
					}
				}
			},
			"meta": {
				"etag": "1d5-QxGl3LA77FwIqKGkf0z6KZr2dHU",
				"created": "2019-04-22T20:53:20.998Z",
				"modified": "2019-04-22T20:53:20.998Z",
				"resource": "households",
				"createdBy": "c9891431-53b1-4be6-81bb-bc853b035618",
				"isDeleted": false,
				"modifiedBy": "c9891431-53b1-4be6-81bb-bc853b035618"
			},
			"customerId": "5edda33d-0268-4fb5-849f-cd100e02ef04",
			"securityGroupId": "b5464d3b-6ac1-45a9-b804-9a5009e894ed",
			"params": {
				"contactHouseholdId": "81499955-c476-49bc-b091-caf8d2a649de"
			}
		}
	],
	"meta": {}
}
```

### HTTP Request

`GET https://api.polisapp.com/v2/contacts/{contactId}/households/`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
contactId | true | The id of the contact
filter | false | Query to filter data.
limit | true | Limits number of result-rows. Should be a positive integer. Useful for pagination.
skip | true | Offset data by given number. Useful for pagination.
sort | true | Sort the column in `ASC` or `DESC` e.g. ['id', 'ASC']


## Create a contact

> Example Request

```http
POST /v2/contacts HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"data": {
		"fields": {},
		"profile": {
			"emails": [
				{
					"email": "007@hotmail.com",
					"active": true,
					"primary": true
				},
				{
					"email": "licensetokill@hotmail.com",
					"active": true,
					"primary": false
				}
			],
			"gender": "m",
			"phones": [
				{
					"phone": "777.777.7007 x72507",
					"active": true,
					"primary": true,
					"phoneType": "mobile"
				},
				{
					"phone": "1-960-777-7777",
					"active": true,
					"primary": false,
					"phoneType": "mobile"
				}
			]
		},
		"primaryHouseholdId": "d2aa6679-62e2-40ec-aeb7-616ad3a3f77d"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6"
}
```

> Example Response

```json
{
	"id": "b7a9a3e2-e419-4c0a-9d03-4c8f280b2967",
	"data": {
		"fields": {
			"2438cc93-4395-4ded-99f0-0a4ac88e2577": 1,
			"510922c1-0a7e-40e1-b329-168b88c6cf3b": "laboriosam",
			"60a528b7-1b36-483a-9bdb-65c00b067e62": [
				"Snake"
			],
			"77227e62-d098-46b3-985b-a83e19a4850d": "House",
			"7e23f830-23a1-42dc-a33b-5617402cd880": "nemo",
			"83439622-cf55-4f0d-a7da-046862b73761": "true",
			"940f694b-d8d6-4b40-9f3d-efe9b6b110b5": "at",
			"b0f2bc7e-3089-401d-afb7-5e6659d0f1e6": "Deceased",
			"eb444550-4f38-43a2-a5c0-6634c3d9a003": [
				"Dog"
			],
			"fea9b266-3def-4d4e-89fd-824bfed902a3": "true"
		},
		"status": "pending",
		"profile": {
			"age": 66,
			"name": {
				"anglican": {
					"given": "James",
					"surname": "Bond"
				}
			},
			"emails": [
				{
					"email": "007@hotmail.com",
					"active": true,
					"primary": true
				},
				{
					"email": "licensetokill@hotmail.com",
					"active": true,
					"primary": false
				}
			],
			"gender": "m",
			"phones": [
				{
					"phone": "777.777.7007 x72507",
					"active": true,
					"primary": true,
					"phoneType": "mobile"
				},
				{
					"phone": "1-960-777-7777",
					"active": true,
					"primary": false,
					"phoneType": "mobile"
				}
			]
		},
		"primaryHouseholdId": "d2aa6679-62e2-40ec-aeb7-616ad3a3f77d"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:30.718Z",
		"modified": "2019-04-03T18:55:30.718Z",
		"resource": "contacts",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`POST https://api.polisapp.com/v2/contacts`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
data | true | The data of contact to be created
customerId | false | The id of the customer to which this resource belongs

## Create many contacts

> Example Request

```http
POST /v2/contacts/bulk HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"data": [
		{
			"data": {
				"fields": {},
				"profile": {
					"emails": [
						{
							"email": "007@hotmail.com",
							"active": true,
							"primary": true
						},
						{
							"email": "licensetokill@hotmail.com",
							"active": true,
							"primary": false
						}
					],
					"gender": "m",
					"phones": [
						{
							"phone": "777.777.7007 x72507",
							"active": true,
							"primary": true,
							"phoneType": "mobile"
						},
						{
							"phone": "1-960-777-7777",
							"active": true,
							"primary": false,
							"phoneType": "mobile"
						}
					]
				},
				"primaryHouseholdId": "d2aa6679-62e2-40ec-aeb7-616ad3a3f77d"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6"
		},
		{
			"data": {
				"fields": {},
				"profile": {
					"age": 63,
					"name": {
						"anglican": {
							"given": "Aegon",
							"surname": "Targaeryan"
						}
					},
					"emails": [
						{
							"email": "callmejon@ravenmail.com",
							"active": true,
							"primary": true
						},
						{
							"email": "lordcommander@nightswatch.com",
							"active": true,
							"primary": false
						}
					],
					"gender": "n",
					"phones": [
						{
							"phone": "(111) 111-1111",
							"active": true,
							"primary": true,
							"phoneType": "home"
						}
					]
				},
				"primaryHouseholdId": "f0cbc9d5-28e0-4123-bcb5-80ece858153c"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6"
		}
	]
}
```

> Example Response

```json
{
	"id": "b7a9a3e2-e419-4c0a-9d03-4c8f280b2967",
	"data": {
		"fields": {
			"2438cc93-4395-4ded-99f0-0a4ac88e2577": 1,
			"510922c1-0a7e-40e1-b329-168b88c6cf3b": "laboriosam",
			"60a528b7-1b36-483a-9bdb-65c00b067e62": [
				"Snake"
			],
			"77227e62-d098-46b3-985b-a83e19a4850d": "House",
			"7e23f830-23a1-42dc-a33b-5617402cd880": "nemo",
			"83439622-cf55-4f0d-a7da-046862b73761": "true",
			"940f694b-d8d6-4b40-9f3d-efe9b6b110b5": "at",
			"b0f2bc7e-3089-401d-afb7-5e6659d0f1e6": "Deceased",
			"eb444550-4f38-43a2-a5c0-6634c3d9a003": [
				"Dog"
			],
			"fea9b266-3def-4d4e-89fd-824bfed902a3": "true"
		},
		"status": "pending",
		"profile": {
			"age": 66,
			"name": {
				"anglican": {
					"given": "James",
					"surname": "Bond"
				}
			},
			"emails": [
				{
					"email": "007@hotmail.com",
					"active": true,
					"primary": true
				},
				{
					"email": "licensetokill@hotmail.com",
					"active": true,
					"primary": false
				}
			],
			"gender": "m",
			"phones": [
				{
					"phone": "777.777.7007 x72507",
					"active": true,
					"primary": true,
					"phoneType": "mobile"
				},
				{
					"phone": "1-960-777-7777",
					"active": true,
					"primary": false,
					"phoneType": "mobile"
				}
			]
		},
		"primaryHouseholdId": "d2aa6679-62e2-40ec-aeb7-616ad3a3f77d"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:30.718Z",
		"modified": "2019-04-03T18:55:30.718Z",
		"resource": "contacts",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`POST https://api.polisapp.com/v2/contacts/bulk`


## Update many contacts

> Example Request

```http
PATCH /v2/contacts/bulk HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
{
	"data": [
		{
			"id": "b7a9a3e2-e419-4c0a-9d03-4c8f280b2967",
			"etag": "4bb-1m+umYrN3hg8k/ds2fLTxdWH/Nw",
			"data": [
				{
					"op": "replace",
					"path": "/profile/name/anglican/given",
					"value": "John"
				},
				{
					"op": "replace",
					"path": "/profile/name/anglican/surname",
					"value": "Doe"
				}
			]
		},
		{
			"id": "3189f3ed-b78a-4586-a86d-b7e1aa1a1099",
			"etag": "4b5-a05nAD4wrRsbnVc/lNBlVCtyPSI",
			"data": [
				{
					"op": "replace",
					"path": "/profile/name/anglican/given",
					"value": "John"
				},
				{
					"op": "replace",
					"path": "/profile/name/anglican/surname",
					"value": "Doe"
				}
			]
		}
	]
}
```

> Example Response

```json
{
	"data": [
		{
			"id": "b7a9a3e2-e419-4c0a-9d03-4c8f280b2967",
			"data": {
				"fields": {
					"2438cc93-4395-4ded-99f0-0a4ac88e2577": 1,
					"510922c1-0a7e-40e1-b329-168b88c6cf3b": "laboriosam",
					"60a528b7-1b36-483a-9bdb-65c00b067e62": [
						"Snake"
					],
					"77227e62-d098-46b3-985b-a83e19a4850d": "House",
					"7e23f830-23a1-42dc-a33b-5617402cd880": "nemo",
					"83439622-cf55-4f0d-a7da-046862b73761": "true",
					"940f694b-d8d6-4b40-9f3d-efe9b6b110b5": "at",
					"b0f2bc7e-3089-401d-afb7-5e6659d0f1e6": "Deceased",
					"eb444550-4f38-43a2-a5c0-6634c3d9a003": [
						"Dog"
					],
					"fea9b266-3def-4d4e-89fd-824bfed902a3": "true"
				},
				"status": "pending",
				"profile": {
					"age": 66,
					"name": {
						"anglican": {
							"given": "John",
							"surname": "Doe"
						}
					},
					"emails": [
						{
							"email": "007@hotmail.com",
							"active": true,
							"primary": true
						},
						{
							"email": "licensetokill@hotmail.com",
							"active": true,
							"primary": false
						}
					],
					"gender": "m",
					"phones": [
						{
							"phone": "777.777.7007 x72507",
							"active": true,
							"primary": true,
							"phoneType": "mobile"
						},
						{
							"phone": "1-960-777-7777",
							"active": true,
							"primary": false,
							"phoneType": "mobile"
						}
					]
				},
				"primaryHouseholdId": "d2aa6679-62e2-40ec-aeb7-616ad3a3f77d"
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:30.718Z",
				"modified": "2019-04-03T18:55:30.718Z",
				"resource": "contacts",
				"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
				"isDeleted": false,
				"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		}
	],
	"errors": [
		{
			"name": "ConcurrencyError",
			"message": "The provided version does match the current value.",
			"data": {
				"position": 1
			}
		}
	]
}
```

### HTTP Request

`PATCH https://api.polisapp.com/v2/contacts/bulk`


## Update a contact

> Example Request

```http
PATCH /v2/contacts/{id} HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
{
	"data": [
		{
			"op": "replace",
			"path": "/profile/emails/0/email",
			"value": "abc@gmail.com"
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
	"id": "b7a9a3e2-e419-4c0a-9d03-4c8f280b2967",
	"data": {
		"fields": {
			"2438cc93-4395-4ded-99f0-0a4ac88e2577": 1,
			"510922c1-0a7e-40e1-b329-168b88c6cf3b": "laboriosam",
			"60a528b7-1b36-483a-9bdb-65c00b067e62": [
				"Snake"
			],
			"77227e62-d098-46b3-985b-a83e19a4850d": "House",
			"7e23f830-23a1-42dc-a33b-5617402cd880": "nemo",
			"83439622-cf55-4f0d-a7da-046862b73761": "true",
			"940f694b-d8d6-4b40-9f3d-efe9b6b110b5": "at",
			"b0f2bc7e-3089-401d-afb7-5e6659d0f1e6": "Deceased",
			"eb444550-4f38-43a2-a5c0-6634c3d9a003": [
				"Dog"
			],
			"fea9b266-3def-4d4e-89fd-824bfed902a3": "true"
		},
		"status": "pending",
		"profile": {
			"age": 66,
			"name": {
				"anglican": {
					"given": "John",
					"surname": "Doe"
				}
			},
			"emails": [
				{
					"email": "abc@gmail.com",
					"active": true,
					"primary": true
				},
				{
					"email": "licensetokill@hotmail.com",
					"active": true,
					"primary": false
				}
			],
			"gender": "m",
			"phones": [
				{
					"phone": "777.777.7007 x72507",
					"active": true,
					"primary": true,
					"phoneType": "mobile"
				},
				{
					"phone": "1-960-777-7777",
					"active": true,
					"primary": false,
					"phoneType": "mobile"
				}
			]
		},
		"primaryHouseholdId": "d2aa6679-62e2-40ec-aeb7-616ad3a3f77d"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:30.718Z",
		"modified": "2019-04-03T18:55:30.718Z",
		"resource": "contacts",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`PATCH https://api.polisapp.com/v2/contacts/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true	| ID of the contact being updated.
etag | true	| Current eTag value of the contact.
data | true	| Patch request following RFC 6902.


## Delete a contact

> Example Request

```http
DELETE /v2/contacts/{id} HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
```

### HTTP Request

`DELETE https://api.polisapp.com/v2/contacts/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id for the v3/contacts item.


## Delete a contact-household record

> Example Request

```http
DELETE /v2/contacts/{contactId}/households/{householdId} HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
```

### HTTP Request

`DELETE https://api.polisapp.com/v2/contacts/{contactId}/households/{householdId}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
contactId | true | The id of the contact
householdId | true | The id of the household


## Creates contact-household record

> Example Request

```http
PUT /v2/contacts/9c453ba8-106c-4fa5-ac49-e056aca7529b/households/904a4f4b-6c74-42a5-9437-15bd9728ffb9 HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"id": "3eba0ce4-3ab1-42c9-b3b8-015655137458",
	"data": {
		"contactId": "9c453ba8-106c-4fa5-ac49-e056aca7529b",
		"householdId": "904a4f4b-6c74-42a5-9437-15bd9728ffb9"
	},
	"meta": {
		"etag": "202-cM+xYVME1IsPAJSsCGT4XAPC7Gw",
		"created": "2019-04-22T20:38:49.919Z",
		"modified": "2019-04-22T20:38:49.919Z",
		"resource": "contact-households",
		"createdBy": "d1efa6f1-79fc-44fe-9ac2-b5faa35874bf",
		"isDeleted": false,
		"modifiedBy": "d1efa6f1-79fc-44fe-9ac2-b5faa35874bf"
	},
	"customerId": "23a9a81b-1ebc-4aac-954f-86482f271870",
	"securityGroupId": "f5909f51-3b8c-49ee-b3d9-b45eb2dc20fd"
}
```

### HTTP Request

`PUT https://api.polisapp.com/v2/contacts/{contactId}/households/{householdId}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
contactId | true | The id of the contact
householdId | true | The id of the household

