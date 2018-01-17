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
        "location": {
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
    "status": "pending",
    "fields": {
      "available": "true",
      "bestpet": "Cat",
      "buypet": [
        "Horse",
        "Snake"
      ],
      "mothername": "Jane Doe"
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
status | false | Contact status.
fields | true | Custom fields [details](#data-fields).
reservation | false | Route reservation []().
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
location | false | Coordinates in [GeoJSON](https://tools.ietf.org/html/rfc7946) format (only `Point` is supported).
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
        "coordinates": {
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
        "coordinates": {
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
    "status": "pending",
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


