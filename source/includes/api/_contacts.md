# Contacts

## The contact object

```json
{
  "id": "0d011563-c7c6-4a09-8fde-f3b8c6f2b22d",
  "customerId": "e3899af9-2b74-45dd-b2b1-d7be8ad47bae",
  "securityGroupId": "d4a1d326-a2c7-415c-bfea-dd9fc84f8d00",
  "data": {
    "listId": "2210d9ea-1870-4b8d-8803-ce426e33a96b",
    "profile": {
      "name": {
        "first": "John",
        "last": "Snow",
        "title": "Mr"
      },
      "address": {
        "country": "United States of America",
        "position": {
          "type": "Point",
          "coordinates": [
            -71.067513,
            42.3520436
          ]
        },
        "formatted": "100 Boylseton Street, Boston, MA 02266, USA",
        "streetAddress": {
          "formatted": "100 Boylseton Street",
          "number": "100",
          "route": "Boylseton Street"
        },
        "postalCode": "02266",
        "state": "Massachusettes",
        "county": "Suffolk County",
        "city": "Boston",
        "neighborhood": "Downtown Boston"
      },
      "email": "john@testemail.com",
      "phone": [
        "9781234568",
        "3171234568",
        "2631234568"
      ],
      "gender": "m",
      "languages": [
        "en"
      ],
      "birthdate": "1987-09-03",
      "age": 30
    },
    "notes": "test notes",
    "fields": {
      "available": "true",
      "bestpet": "Cat",
      "buypet": [
        "Horse",
        "Snake"
      ],
      "mothername": "Jane Doe"
    },
    "integration": {
      "integrationId": "e5f5b8b9-9275-426d-ae52-3e684b6c7c76",
      "externalId": 1001,
    },
    "reservation": {
      "reserved": false
    },
    "contacted": true,
    "state": "contacted-unavailable-other",
    "statusId": "1e055231-e35e-4503-92ba-99fd496aea46"
  },
  "meta": {
    "created": "2017-12-15T19:46:01.594Z",
    "modified": "2017-12-15T19:46:02.219Z",
    "isDeleted": false,
    "resource": "contacts",
    "createdBy": "11b78eab-8b3e-45e7-804c-4a94045367d4",
    "modifiedBy": "11b78eab-8b3e-45e7-804c-4a94045367d4",
    "etag": "MTUxMzM2NzE2NTI3MzM3NDcyMA=="
  }
}
```

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Unique identifier for the object.
customerId | true | Customer this resource belongs to.
securityGroupId | true | Security group of this resource.
data | true | Contact data.

### data

Attribute | Required? | Description
--------- | --------- | -----------
listId | true | List identifier this contact belongs to.
profile | true | Contact profile [details](#data/profile).
notes | false | String with custom text (max length: 2048 characters).
fields | true | Custom fields [details](#data/fields).
integration | false | Integration information [details](#data/integration).
reservation | false | Route reservation [details](#data/reservation).
contacted | false | Flag indicating if the contact has ever been contacted.
state | false | Property that categorizes a contact by it's interaction [details](#data/state).
statusId | false | Id of a status object. [details](#data/statusId).

### data/profile

Attribute | Required? | Description
--------- | --------- | -----------
name | false | Contact name [details](#data/profile/name).
address | true | Contact address [details](#data/profile/address).
email | false | Email address of the contact.
phone | false | Array of phone numbers.
gender | false |  decline: 'd'<br/> female: 'f'<br/> male: 'm'<br/> nonbinary: 'n'<br/> other: 'o',
languages | false | [ISO 639-1 alpha-2](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) language code (i.e.: en, es, af).
birthdate | false | Birthdate in ISO-8601 format (YYYY-MM-DD).
age | false | Integer representing the age of the contact.

### data/profile/name

Attribute | Required? | Description
--------- | --------- | -----------
title | false | Name title.
first | true | First name.
middle | false | Middle name.
last | true | Last name.
suffix | false | Name suffix.

### data/profile/address

Attribute | Required? | Description
--------- | --------- | -----------
country | false | Country.
position | false | Coordinates in [GeoJSON](https://tools.ietf.org/html/rfc7946) format (only `Point` is supported).
formatted | false | Full address.
streetAddress | false | Street address decomposed.
postalCode | false | Postal code.
state | false | State.
county | false | Conty.
city | false | City.
neighborhood | false | Neighborhood.

### data/profile/address/streetAddress

Attribute | Required? | Description
--------- | --------- | -----------
formatted | true | Formatted street address.
route | true | Street name.
number | true | Street number.
unit | false | Unit number.
unitType | false | Unit type (e.g.: suite, unit, apartment).

### data/fields

This is a flat object that contains custom data for this contact.
Allowed values:

* `String`
* `Number`
* `Array` - not containing objects.
* `Boolean`

### data/integration

Attribute | Required? | Description
--------- | --------- | -----------
integrationId | false | Identifier of the integration this contact as pulled from.
externalId | false | Identifier that identifies this contact on an external platform. This can be either an integer or a string.

### data/reservation

Attribute | Required? | Description
--------- | --------- | -----------
reserved | true | Boolean indicating if this contact is reserved for some route.
walklistId | false | Route identifier this contact is reserved to.

### data/state

Allowed values:

* `'appointment'`
* `'not-contacted-high-priority'`
* `'not-contacted-do-not-knock'`
* `'not-contacted-normal'`
* `'contacted-available-successful'`
* `'contacted-available-not-successful'`
* `'contacted-unavailable-not-home'`
* `'contacted-unavailable-other'`
* `'come-back'`
* `'unknown'`

### data/statusId

The statusId property must point to the id property of a status object.
This status' `contactState` property must have the same value of the contact's `state` property, otherwise it's id will not be a valid statusId for the contact object.

### meta

[See documentation](#metadata-object).

## Create a contact

> Example Request

```http
POST /v1/contacts HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}

{
  "data": {
    "listId": "2210d9ea-1870-4b8d-8803-ce426e33a96b",
    "profile": {
      "name": {
        "first": "John",
        "last": "Snow",
        "title": "Mr"
      },
      "address": {
        "country": "United States of America",
        "position": {
          "type": "Point",
          "coordinates": [
            -71.067513,
            42.3520436
          ]
        },
        "formatted": "100 Boylseton Street, Boston, MA 02266, USA",
        "streetAddress": {
          "formatted": "100 Boylseton Street",
          "number": "100",
          "route": "Boylseton Street"
        },
        "postalCode": "02266",
        "state": "Massachusettes",
        "county": "Suffolk County",
        "city": "Boston",
        "neighborhood": "Downtown Boston"
      },
      "email": "john@testemail.com",
      "phone": [
        "9781234568",
        "3171234568",
        "2631234568"
      ],
      "gender": "m",
      "languages": [
        "en"
      ],
      "birthdate": "1987-09-03",
      "age": 30
    },
    "notes": "test notes",
    "fields": {
      "dogliker": "true",
      "bestpet": "Cat",
      "buypet": [
        "Horse",
        "Snake"
      ],
      "catlikeness": 4,
      "mothername": "Jane Doe"
    }
  }
}
```

> Example Response

```json
{
  "id": "0d011563-c7c6-4a09-8fde-f3b8c6f2b22d",
  "customerId": "e3899af9-2b74-45dd-b2b1-d7be8ad47bae",
  "securityGroupId": "d4a1d326-a2c7-415c-bfea-dd9fc84f8d00",
  "data": {
    "listId": "2210d9ea-1870-4b8d-8803-ce426e33a96b",
    "profile": {
      "name": {
        "first": "John",
        "last": "Snow",
        "title": "Mr"
      },
      "address": {
        "country": "United States of America",
        "position": {
          "type": "Point",
          "coordinates": [
            -71.067513,
            42.3520436
          ]
        },
        "formatted": "100 Boylseton Street, Boston, MA 02266, USA",
        "streetAddress": {
          "formatted": "100 Boylseton Street",
          "number": "100",
          "route": "Boylseton Street"
        },
        "postalCode": "02266",
        "state": "Massachusettes",
        "county": "Suffolk County",
        "city": "Boston",
        "neighborhood": "Downtown Boston"
      },
      "email": "john@testemail.com",
      "phone": [
        "9781234568",
        "3171234568",
        "2631234568"
      ],
      "gender": "m",
      "languages": [
        "en"
      ],
      "birthdate": "1987-09-03",
      "age": 30
    },
    "notes": "test notes",
    "fields": {
      "dogliker": "true",
      "bestpet": "Cat",
      "buypet": [
        "Horse",
        "Snake"
      ],
      "catlikeness": 4,
      "mothername": "Jane Doe"
    },
    "reservation": {
      "reserved": false
    },
    "contacted": false
  },
  "meta": {
    "created": "2017-12-15T19:46:01.594Z",
    "modified": "2017-12-15T19:46:02.219Z",
    "isDeleted": false,
    "resource": "contacts",
    "createdBy": "11b78eab-8b3e-45e7-804c-4a94045367d4",
    "modifiedBy": "11b78eab-8b3e-45e7-804c-4a94045367d4",
    "etag": "MTUxMzM2NzE2NTI3MzM3NDcyMA=="
  }
}
```

Creates a new contact in an list.

### HTTP Request

`POST https://api.polisapp.com/v1/contacts`

## Create multiple contacts

> Example Request

```http
POST /v1/contacts/bulk HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}

{
  "data": [
    {
      "data": {
        "listId": "2210d9ea-1870-4b8d-8803-ce426e33a96b",
        "profile": {
          "name": {
            "first": "John",
            "last": "Snow",
            "title": "Mr"
          },
          "address": {
            "country": "United States of America",
            "position": {
              "type": "Point",
              "coordinates": [
                -71.067513,
                42.3520436
              ]
            },
            "formatted": "100 Boylseton Street, Boston, MA 02266, USA",
            "streetAddress": {
              "formatted": "100 Boylseton Street",
              "number": "100",
              "route": "Boylseton Street"
            },
            "postalCode": "02266",
            "state": "Massachusettes",
            "county": "Suffolk County",
            "city": "Boston",
            "neighborhood": "Downtown Boston"
          },
          "email": "john@testemail.com",
          "phone": [
            "9781234568",
            "3171234568",
            "2631234568"
          ],
          "gender": "m",
          "languages": [
            "en"
          ],
          "birthdate": "1987-09-03",
          "age": 30
        },
        "notes": "test notes",
        "fields": {
          "dogliker": "true",
          "bestpet": "Cat",
          "buypet": [
            "Horse",
            "Snake"
          ],
          "catlikeness": 4,
          "mothername": "Jane Doe"
        }
      }
    }
  ]
}
```

> Example Response

```json
{
  "data": [
    {
      "id": "0d011563-c7c6-4a09-8fde-f3b8c6f2b22d",
      "customerId": "e3899af9-2b74-45dd-b2b1-d7be8ad47bae",
      "securityGroupId": "d4a1d326-a2c7-415c-bfea-dd9fc84f8d00",
      "data": {
        "listId": "2210d9ea-1870-4b8d-8803-ce426e33a96b",
        "profile": {
          "name": {
            "first": "John",
            "last": "Snow",
            "title": "Mr"
          },
          "address": {
            "country": "United States of America",
            "position": {
              "type": "Point",
              "coordinates": [
                -71.067513,
                42.3520436
              ]
            },
            "formatted": "100 Boylseton Street, Boston, MA 02266, USA",
            "streetAddress": {
              "formatted": "100 Boylseton Street",
              "number": "100",
              "route": "Boylseton Street"
            },
            "postalCode": "02266",
            "state": "Massachusettes",
            "county": "Suffolk County",
            "city": "Boston",
            "neighborhood": "Downtown Boston"
          },
          "email": "john@testemail.com",
          "phone": [
            "9781234568",
            "3171234568",
            "2631234568"
          ],
          "gender": "m",
          "languages": [
            "en"
          ],
          "birthdate": "1987-09-03",
          "age": 30
        },
        "notes": "test notes",
        "fields": {
          "dogliker": "true",
          "bestpet": "Cat",
          "buypet": [
            "Horse",
            "Snake"
          ],
          "catlikeness": 4,
          "mothername": "Jane Doe"
        },
        "reservation": {
          "reserved": false
        },
        "contacted": false
      },
      "meta": {
        "created": "2017-12-15T19:46:01.594Z",
        "modified": "2017-12-15T19:46:02.219Z",
        "isDeleted": false,
        "resource": "contacts",
        "createdBy": "11b78eab-8b3e-45e7-804c-4a94045367d4",
        "modifiedBy": "11b78eab-8b3e-45e7-804c-4a94045367d4",
        "etag": "MTUxMzM2NzE2NTI3MzM3NDcyMA=="
      }
    }
  ]
}
```

Creates multiple contacts in an list.

### HTTP Request

`POST https://api.polisapp.com/v1/contacts/bulk`

## Retrieve a Contact

### HTTP Request
`GET https://api.polisapp.com/v1/contacts/{contactsId}`

> Example Request

```http
GET /v1/contacts/bfced18e-1b90-433b-8f4e-d905d2406524 HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```



> Example Response

```json
{
    "id": "bfced18e-1b90-433b-8f4e-d905d2406524",
    "data": {
        "fields": {
            "likeness": false,
            "available": false
        },
        "listId": "81414d4e-e237-467e-81f1-80cbe6652231",
        "profile": {
            "name": {
                "first": "Wilber",
                "last": "Mertz"
            },
            "address": {
                "country": "US",
                "position": {
                    "type": "Point",
                    "coordinates": [
                        -74.07787,
                        40.70426
                    ]
                },
                "formatted": "53 Arlington Ave Apt 1  Jersey City NJ 7305",
                "streetAddress": {
                    "unit": "1",
                    "route": "Arlington Ave",
                    "number": "53",
                    "formatted": "53 Arlington Ave Apt 1"
                },
                "postalCode": "7305",
                "state": "NJ",
                "county": "Jersey City"
            },
            "age": 24,
            "email": "Marc.Monahan@yahoo.com",
            "phone": [
                "1-495-660-3830 x42618"
            ],
            "gender": "n"
        },
        "contacted": false,
        "reservation": {
            "reserved": false
        }
    },
    "meta": {
        "etag": "4dc-5aWkR+Lvoft7CAdRm6/R8X1IBvM",
        "created": "2018-03-28T16:09:43.028Z",
        "modified": "2018-03-28T16:09:43.028Z",
        "resource": "contacts",
        "createdBy": "a46d8825-3f9e-45f4-9db9-be5a77883e18",
        "isDeleted": false,
        "modifiedBy": "a46d8825-3f9e-45f4-9db9-be5a77883e18"
    },
    "customerId": "f0e2736d-31c5-461a-89d1-e64f697d9e98",
    "securityGroupId": "1bdf50d1-d3d5-4ecf-922c-f2541cd9ba37"
}
```

## Update a Contact

### HTTP Request
`PATCH https://api.polisapp.com/v1/contacts/{contactId}`

> Example Request

```http
PATCH /v1/contacts/bfced18e-1b90-433b-8f4e-d905d2406524 HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
ETag: {etag_value}
{
   "data":[
      {
         "op":"replace",
         "path":"/profile/email",
         "value":"abc@gmail.com"
      }
   ]
}
```

> Example Response

```json
{
    "id": "bfced18e-1b90-433b-8f4e-d905d2406524",
    "data": {
        "fields": {
            "likeness": false,
            "available": false
        },
        "listId": "81414d4e-e237-467e-81f1-80cbe6652231",
        "profile": {
            "name": {
                "first": "Wilber",
                "last": "Mertz"
            },
            "address": {
                "country": "US",
                "position": {
                    "type": "Point",
                    "coordinates": [
                        -74.07787,
                        40.70426
                    ]
                },
                "formatted": "53 Arlington Ave Apt 1  Jersey City NJ 7305",
                "streetAddress": {
                    "unit": "1",
                    "route": "Arlington Ave",
                    "number": "53",
                    "formatted": "53 Arlington Ave Apt 1"
                },
                "postalCode": "7305",
                "state": "NJ",
                "county": "Jersey City"
            },
            "age": 24,
            "email": "abc@gmail.com",
            "phone": [
                "1-495-660-3830 x42618"
            ],
            "gender": "n"
        },
        "contacted": false,
        "reservation": {
            "reserved": false
        }
    },
    "meta": {
        "etag": "4dc-5aWkR+Lvoft7CAdRm6/R8X1IBvM",
        "created": "2018-03-28T16:09:43.028Z",
        "modified": "2018-03-28T16:09:43.028Z",
        "resource": "contacts",
        "createdBy": "a46d8825-3f9e-45f4-9db9-be5a77883e18",
        "isDeleted": false,
        "modifiedBy": "a46d8825-3f9e-45f4-9db9-be5a77883e18"
    },
    "customerId": "f0e2736d-31c5-461a-89d1-e64f697d9e98",
    "securityGroupId": "1bdf50d1-d3d5-4ecf-922c-f2541cd9ba37"
}
```

## Update multiple contacts

> Example Request

```http
PATCH /v1/contacts/bulk HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"data": [
		{
			"id": "8e8c2e84-9c4f-490c-b8bc-81dd7e24c622",
			"etag": "4bb-1m+umYrN3hg8k/ds2fLTxdWH/Nw",
			"data": [
				{ "op": "replace", "path": "/profile/name/first", "value": "John" },
				{ "op": "replace", "path": "/profile/name/last", "value": "Doe" }
			]
		},
		{
			"id": "ba36519a-2468-4d0b-803a-fba678cebfd4",
			"etag": "4b5-a05nAD4wrRsbnVc/lNBlVCtyPSI",
			"data": [
				{ "op": "replace", "path": "/profile/name/first", "value": "John" },
				{ "op": "replace", "path": "/profile/name/last", "value": "Doe" }
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
            "id": "8e8c2e84-9c4f-490c-b8bc-81dd7e24c622",
            "data": {
                "fields": {},
                "listId": "a6abf2bf-5109-4237-a976-8267daa9db80",
                "profile": {
                    "name": {
                        "first": "John",
                        "last": "Doe"
                    },
                    "address": {
                        "country": "United States",
                        "position": {
                            "type": "Point",
                            "coordinates": [
                                -87.592017,
                                41.804027
                            ]
                        },
                        "formatted": "5006 S Dorchester Ave Chicago IL 60615",
                        "streetAddress": {
                            "route": "S Dorchester Ave",
                            "number": "5006",
                            "formatted": "5006 S Dorchester Ave"
                        },
                        "postalCode": "60615",
                        "state": "IL",
                        "city": "Chicago"
                    },
                    "age": 53,
                    "phone": [],
                    "gender": "d"
                },
                "contacted": false,
                "successful": false,
                "reservation": {
                    "reserved": false
                }
            },
            "meta": {
                "etag": "4bc-jQasVHl7NxorvkZb4wzIHQjmZu8",
                "created": "2018-07-11T18:47:41.917Z",
                "modified": "2018-12-27T13:27:17.990Z",
                "resource": "contacts",
                "createdBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
                "isDeleted": false,
                "modifiedBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851"
            },
            "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
            "securityGroupId": "f2baec89-8577-4f18-81e6-e99c5b77222d"
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

Update multiple contacts in an list.

### HTTP Request

`PATCH https://api.polisapp.com/v1/contacts/bulk`

### Request Body

The request body should have an array of patch requests under **data** key.
Each patch request can update multiple fields of each contact.

<aside class="notice">
You can only patch attributes inside <b>data</b> key.
</aside>

Parameter | Required | Description
--------- | -------- | -----------
id | true | ID of the contact being updated.
etag | true | Current ETag value of the contact.
data | true | Patch request following [RFC 6902](https://tools.ietf.org/html/rfc6902).

### Response

The response will contain:

Parameter | Description
--------- | -----------
data | Array of successfully updated contacts with its value updated.
errors | Array of error for unsuccessful updates. It contains the error message and error key for each contact that was not possible to update.

## Delete a Contact

### HTTP Request
`DELETE https://api.polisapp.com/v1/contacts/{contactId}`

> Example Request

```http
DELETE https://api.polisapp.com/v1/contacts/4155c6a9-f3fc-475f-a76e-df203d28f55a
Host: api.polisapp.com
Authorization: Bearer {access_token}
ETag: {etag_value}

```

## Get all Contacts
Retrieves a list of contacts filtered by a criteria

### HTTP Request
`GET https://api.polisapp.com/v1/contacts?filter={filter}&limit={limit}&skip={skip}&sort={sort}`

NOTE: This endpoint's filter query parameter ONLY supports `eq`. All other filter operations are not supported.

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | true | Query to filter data. Example filter : /data/listId = {listId}
limit | true | Limit results returned. Usefull for paggination.
skip | true | Data offset index. Usefull for paggination.
sort | true | Sort column. Ex.: `["id","ASC"]`

> Example Request

```http
GET /v1/contacts?filter=/data/listId+eq+"81414d4e-e237-467e-81f1-80cbe6652231"&limit=100&skip=0&sort=["id","ASC"] HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
   "data":[
      {
         "id":"02b88c4e-3901-4fd7-a580-79eaec83058a",
         "data":{
            "fields":{
               "likeness":false,
               "available":false
            },
            "listId":"81414d4e-e237-467e-81f1-80cbe6652231",
            "profile":{
               "name":{
                  "first":"Wilber",
                  "last":"Mertz"
               },
               "address":{
                  "country":"US",
                  "position":{
                     "type":"Point",
                     "coordinates":[
                        -74.07787,
                        40.70426
                     ]
                  },
                  "formatted":"53 Arlington Ave Apt 1  Jersey City NJ 7305",
                  "streetAddress":{
                     "unit":"1",
                     "route":"Arlington Ave",
                     "number":"53",
                     "formatted":"53 Arlington Ave Apt 1"
                  },
                  "postalCode":"7305",
                  "state":"NJ",
                  "county":"Jersey City"
               },
               "age":24,
               "email":"Marc.Monahan@yahoo.com",
               "phone":[
                  "1-495-660-3830 x42618"
               ],
               "gender":"n"
            },
            "contacted":false,
            "reservation":{
               "reserved":false
            }
         },
         "meta":{
            "etag":"4dc-5aWkR+Lvoft7CAdRm6/R8X1IBvM",
            "created":"2018-03-28T16:09:43.028Z",
            "modified":"2018-03-28T16:09:43.028Z",
            "resource":"contacts",
            "createdBy":"a46d8825-3f9e-45f4-9db9-be5a77883e18",
            "isDeleted":false,
            "modifiedBy":"a46d8825-3f9e-45f4-9db9-be5a77883e18"
         },
         "customerId":"f0e2736d-31c5-461a-89d1-e64f697d9e98",
         "securityGroupId":"1bdf50d1-d3d5-4ecf-922c-f2541cd9ba37"
      }
   ],
   "meta":{

   }
}
```
