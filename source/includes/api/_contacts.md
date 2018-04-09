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
    "contacted": true
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
profile | true | Contact profile [details](#data-profile).
notes | false | String with custom text (max length: 2048 characters).
fields | true | Custom fields [details](#data-fields).
integration | false | Integration information [details](#data-integration).
reservation | false | Route reservation [details](#data-reservation).
contacted | false | Flag indicating if the contact has ever been contacted.

### data/profile

Attribute | Required? | Description
--------- | --------- | -----------
name | false | Contact name [details](#data-profile-name).
address | true | Contact address [details](#data-profile-address).
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
   "id":"bfced18e-1b90-433b-8f4e-d905d2406524",
   "data":{
      "fields":{

      },
      "listId":"504f3788-f2e0-4b0e-acbe-cb06d9f51923",
      "status":"pending",
      "profile":{
         "age":26,
         "name":{
            "anglican":{
               "given":"Jon",
               "title":"Mr",
               "surname":"Doe",
               "middlename":"M"
            }
         },
         "email":"jondoe@gmail.com",
         "phone":[
            "9538295457"
         ],
         "gender":"m",
         "location":{
            "coords":{
               "lat":42.3530125,
               "lng":-71.1285818
            },
            "country":{
               "abbr":"us",
               "name":"United States"
            },
            "locality":{
               "abbr":"Boston",
               "name":"Boston",
               "type":"locality"
            },
            "formatted":"66 Chester St, Boston, MA 02134, USA",
            "statoid01":{
               "abbr":"MA",
               "name":"Massachusetts",
               "type":"state"
            },
            "statoid02":{
               "abbr":"Suffolk County",
               "name":"Suffolk County",
               "type":"county"
            },
            "statoid03":{
               "abbr":"Boston",
               "name":"Boston",
               "type":"city"
            },
            "statoid04":{
               "abbr":"Allston",
               "name":"Allston",
               "type":"neighborhood"
            },
            "postalCode":"02134",
            "streetAddress":{
               "unit":"1",
               "route":"Chester Street",
               "number":"66",
               "formatted":"66 Chester Street 1"
            }
         },
         "birthdate":"1992-01-25T00:00:00.000Z",
         "languages":[
            "en"
         ]
      },
      "contacted":false,
      "reservation":{
         "reserved":false
      }
   },
   "meta":{
      "created":"2018-03-01T22:06:25.079Z",
      "modified":"2018-03-08T18:59:10.185Z",
      "resource":"contacts",
      "createdBy":"ac18d844-309b-40ea-ba23-1828870f2a85",
      "isDeleted":false,
      "modifiedBy":"ac18d844-309b-40ea-ba23-1828870f2a85",
      "etag":"55a-cx8KC3r7sKhkY48vp3wJiJSH8bc"
   },
   "customerId":"eb95a33f-80f3-4776-8c4c-f3bd6a7b4349",
   "securityGroupId":"924cbcbc-fe4c-4e74-b7e5-62d87bb7fc04"
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
   "id":"bfced18e-1b90-433b-8f4e-d905d2406524",
   "data":{
      "fields":{

      },
      "listId":"504f3788-f2e0-4b0e-acbe-cb06d9f51923",
      "status":"pending",
      "profile":{
         "age":26,
         "name":{
            "anglican":{
               "given":"Jon",
               "title":"Mr",
               "surname":"Doe",
               "middlename":"M"
            }
         },
         "email":"abc@gmail.com",
         "phone":[
           "9538295457"
         ],
         "gender":"m",
         "location":{
            "coords":{
               "lat":42.3530125,
               "lng":-71.1285818
            },
            "country":{
               "abbr":"us",
               "name":"United States"
            },
            "locality":{
               "abbr":"Boston",
               "name":"Boston",
               "type":"locality"
            },
            "formatted":"66 Chester St, Boston, MA 02134, USA",
            "statoid01":{
               "abbr":"MA",
               "name":"Massachusetts",
               "type":"state"
            },
            "statoid02":{
               "abbr":"Suffolk County",
               "name":"Suffolk County",
               "type":"county"
            },
            "statoid03":{
               "abbr":"Boston",
               "name":"Boston",
               "type":"city"
            },
            "statoid04":{
               "abbr":"Allston",
               "name":"Allston",
               "type":"neighborhood"
            },
            "postalCode":"02134",
            "streetAddress":{
               "unit":"1",
               "route":"Chester Street",
               "number":"66",
               "formatted":"66 Chester Street 1"
            }
         },
         "birthdate":"1992-01-25T00:00:00.000Z",
         "languages":[
            "en"
         ]
      },
      "contacted":false,
      "reservation":{
         "reserved":false
      }
   },
   "meta":{
      "created":"2018-03-01T22:06:25.079Z",
      "modified":"2018-04-09T22:26:55.349Z",
      "resource":"contacts",
      "createdBy":"ac18d844-309b-40ea-ba23-1828870f2a85",
      "isDeleted":false,
      "modifiedBy":"3d90f333-82d6-48c1-9287-da3da756b263",
      "etag":"540-pTcXJbpXMAU0PcsoVd/tPHdehRs"
   },
   "customerId":"eb95a33f-80f3-4776-8c4c-f3bd6a7b4349",
   "securityGroupId":"924cbcbc-fe4c-4e74-b7e5-62d87bb7fc04"
}
```

## Delete a Contact

### HTTP Request
`DELETE https://api.polisapp.com/v1/contacts/{contactId}`

> Example Request

```http
DELETE https://api.polisapp.com/v1/contacts/4155c6a9-f3fc-475f-a76e-df203d28f55a
Host: api.polisapp.com
Authorization: Bearer {access_token}

```

## Get all Contacts
Retrieves a list of contacts filtered by a criteria

### HTTP Request
`GET https://api.polisapp.com/v1/contacts?filter={filter}&limit={limit}&skip={skip}&sort={sort}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | true | Query to filter data. Example filter : /data/listId = {listId}
limit | true | Limit results returned. Usefull for paggination.
skip | true | Data offset index. Usefull for paggination.
sort | true | Sort column. Ex.: `["data/name","ASC"]`

> Example Request

```http
GET /v1/contacts?filter=/data/listId+eq+"504f3788-f2e0-4b0e-acbe-cb06d9f51923"&limit=100&skip=0&sort=["data/name","ASC"] HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
   "data":[
      {
         "id":"bfced18e-1b90-433b-8f4e-d905d2406524",
         "data":{
            "fields":{

            },
            "listId":"504f3788-f2e0-4b0e-acbe-cb06d9f51923",
            "status":"pending",
            "profile":{
               "age":26,
               "name":{
                  "anglican":{
                     "given":"Jon",
                     "title":"Mr",
                     "surname":"Doe",
                     "middlename":"M"
                  }
               },
               "email":"abc@gmail.com",
               "phone":[

               ],
               "gender":"m",
               "location":{
                  "coords":{
                     "lat":42.3530125,
                     "lng":-71.1285818
                  },
                  "country":{
                     "abbr":"us",
                     "name":"United States"
                  },
                  "locality":{
                     "abbr":"Boston",
                     "name":"Boston",
                     "type":"locality"
                  },
                  "formatted":"66 Chester St, Boston, MA 02134, USA",
                  "statoid01":{
                     "abbr":"MA",
                     "name":"Massachusetts",
                     "type":"state"
                  },
                  "statoid02":{
                     "abbr":"Suffolk County",
                     "name":"Suffolk County",
                     "type":"county"
                  },
                  "statoid03":{
                     "abbr":"Boston",
                     "name":"Boston",
                     "type":"city"
                  },
                  "statoid04":{
                     "abbr":"Allston",
                     "name":"Allston",
                     "type":"neighborhood"
                  },
                  "postalCode":"02134",
                  "streetAddress":{
                     "unit":"1",
                     "route":"Chester Street",
                     "number":"66",
                     "formatted":"66 Chester Street 1"
                  }
               },
               "birthdate":"1992-01-25T00:00:00.000Z",
               "languages":[
                  "en"
               ]
            },
            "contacted":false,
            "reservation":{
               "reserved":false
            }
         },
         "meta":{
            "created":"2018-03-01T22:06:25.079Z",
            "modified":"2018-04-09T22:26:55.349Z",
            "resource":"contacts",
            "createdBy":"ac18d844-309b-40ea-ba23-1828870f2a85",
            "isDeleted":false,
            "modifiedBy":"3d90f333-82d6-48c1-9287-da3da756b263",
            "etag":"540-pTcXJbpXMAU0PcsoVd/tPHdehRs"
         },
         "customerId":"eb95a33f-80f3-4776-8c4c-f3bd6a7b4349",
         "securityGroupId":"924cbcbc-fe4c-4e74-b7e5-62d87bb7fc04"
      }
   ],
   "meta":{

   }
}
```