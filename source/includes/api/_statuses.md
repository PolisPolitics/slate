# Statuses

## The status object

```json
{
  "id": "91baec90-6c55-4fe6-8234-f8a4d5ee8d3d",
  "data": {
      "icon": "faCalendar:regular",
      "name": "Appointment",
      "pinColor": "#C8C8C8",
      "iconColor": "#01B5D6",
      "contactState": "appointment",
      "defaultStatus": true,
      "statusGroupId": "3239be67-199f-4cef-a30b-faea8ea48785"
  },
  "meta": {
      "etag": "255-ZPNmy2TEWvLE5Uag2uh1tSvts9E",
      "created": "2019-01-14T18:32:35.236Z",
      "modified": "2019-01-14T18:32:35.236Z",
      "resource": "statuses",
      "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
      "isDeleted": false,
      "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
  },
  "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
  "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
}
```

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Unique identifier for the object.
customerId | true | Customer this resource belongs to.
securityGroupId | true | Security group of this resource.

### data

Attribute | Required? | Description
--------- | --------- | -----------
icon | true | Name of the icon to be displayed [details](#icon-property-naming-rules)
name | true | Name of the status-group.
pinColor | true | Hex code for the pin color.
iconColor | true | Hex code for the icon color.
contactState | true | Compatibility attribute that maps a status to the state property of a contact instance.
defaultStatus | false | Boolean that determines if this is a default status. Defaults value is `false`
statusGroupId | true | Id of the status-group that a status belongs to.

### meta

[See documentation](#metadata-object).

### icon property naming rules

The icon property determines the displayed icon for a status.
We support all Free and Pro [Font Awesome's](https://fontawesome.com/icons?d=gallery) icons.

The following naming rules must be applied from Font Awesome's icon names to status icon property values:

1. status icon property values must start with the constant `fa`
2. Convert Font Awesome's icon name from dash-case to PascalCase
3. status icon property values must end with `:icon-style` where `icon-style` stands for one of the four Font Awesome's packages. Possible values: (`solid`, `regular`, `light` or `brands`)

> icon naming example

* Font Awesome's book-open icon from Light Style package.
* status' icon value: `'faBookOpen:light'`

## Create a status

> Example Request

```https
POST /statuses HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}

{
"data": {
  "icon": "faTimes:solid",
    "name": "Inaccessible",
    "pinColor": "#C8C8C8",
    "iconColor": "#E95C41",
    "contactState": "contacted-unavailable-other",
    "statusGroupId": "3239be67-199f-4cef-a30b-faea8ea48785"
},
"customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4"
}
```

> Example Response

```json
{
    "id": "f575fbc6-e3b9-4025-ada9-97d97a9e6a11",
    "data": {
        "icon": "faTimes:solid",
        "name": "Inaccessible",
        "pinColor": "#C8C8C8",
        "iconColor": "#E95C41",
        "contactState": "contacted-unavailable-other",
        "defaultStatus": false,
        "statusGroupId": "3239be67-199f-4cef-a30b-faea8ea48785"
    },
    "meta": {
        "etag": "262-SPYO6M3cY8znD5ujnOzxw/9WNhw",
        "created": "2019-01-14T19:06:25.104Z",
        "modified": "2019-01-14T19:06:25.104Z",
        "resource": "statuses",
        "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
        "isDeleted": false,
        "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
    },
    "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
    "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
}
```

Creates a new status for a customer.

### HTTP Request

`POST https://api.polisapp.com/statuses`

## Retrieve a status

> Example Request

```https
GET /statuses/f575fbc6-e3b9-4025-ada9-97d97a9e6a11 HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
    "id": "f575fbc6-e3b9-4025-ada9-97d97a9e6a11",
    "data": {
        "icon": "faTimes:solid",
        "name": "Inaccessible",
        "pinColor": "#C8C8C8",
        "iconColor": "#E95C41",
        "contactState": "contacted-unavailable-other",
        "defaultStatus": false,
        "statusGroupId": "3239be67-199f-4cef-a30b-faea8ea48785"
    },
    "meta": {
        "etag": "262-SPYO6M3cY8znD5ujnOzxw/9WNhw",
        "created": "2019-01-14T19:06:25.104Z",
        "modified": "2019-01-14T19:06:25.104Z",
        "resource": "statuses",
        "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
        "isDeleted": false,
        "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
    },
    "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
    "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
}
```

Obtains a single status object by ID.

### HTTP Request

`GET https://api.polisapp.com/statuses/{statusId}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
statusId | true | Unique identifier of the status.

## Update a status

> Example Request

```https
PATCH /statuses/f575fbc6-e3b9-4025-ada9-97d97a9e6a11 HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
ETag: {etag_value}
{
  "data": [
    {"op":"replace", "path":"/name", "value": "New Status Name"}
  ]
}
```

> Example Response

```json
{
    "id": "f575fbc6-e3b9-4025-ada9-97d97a9e6a11",
    "data": {
        "icon": "faTimes:solid",
        "name": "New Status Name",
        "pinColor": "#C8C8C8",
        "iconColor": "#E95C41",
        "contactState": "contacted-unavailable-other",
        "defaultStatus": false,
        "statusGroupId": "3239be67-199f-4cef-a30b-faea8ea48785"
    },
    "meta": {
        "created": "2019-01-14T19:06:25.104Z",
        "modified": "2019-01-14T19:10:24.296Z",
        "resource": "statuses",
        "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
        "isDeleted": false,
        "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
        "etag": "25b-flAkp9bnfXpUJxNTeMXblec9VpI"
    },
    "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
    "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
}
```
<aside class="notice">
You can only patch attributes inside <b>data</b> key.
</aside>

[RFC 6902 - JavaScript Object Notation (JSON) Patch](https://tools.ietf.org/html/rfc6902)

### HTTP Request

`PATCH https://api.polisapp.com/statuses/{statusId}`



## Delete a status

### HTTP Request
`DELETE https://api.polisapp.com/statuses/{statusId}`

> Example Request

```https
DELETE https://api.polisapp.com/statuses/f575fbc6-e3b9-4025-ada9-97d97a9e6a11
Host: api.polisapp.com
Authorization: Bearer {access_token}
```


## Get all statuses

> Example Request

```https
GET /statuses?filter=/customerId+eq+"cc34e52f-5bfa-42ee-ac72-d331ac97b5c4"&limit=100&skip=0&sort=["data/name","ASC"] HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
    "data": [
        {
            "id": "91baec90-6c55-4fe6-8234-f8a4d5ee8d3d",
            "data": {
                "icon": "faCalendar:regular",
                "name": "Appointment",
                "pinColor": "#C8C8C8",
                "iconColor": "#01B5D6",
                "contactState": "appointment",
                "defaultStatus": true,
                "statusGroupId": "3239be67-199f-4cef-a30b-faea8ea48785"
            },
            "meta": {
                "etag": "255-ZPNmy2TEWvLE5Uag2uh1tSvts9E",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "2579d3bf-6ee0-44f4-ab34-d40dc6a077c7",
            "data": {
                "icon": "faRedo:solid",
                "name": "Come Back",
                "pinColor": "#C8C8C8",
                "iconColor": "#01B5D6",
                "contactState": "come-back",
                "defaultStatus": true,
                "statusGroupId": "c75a45d6-67cc-434c-b5b5-9a2bd2cee860"
            },
            "meta": {
                "etag": "24b-3lJP37fqrMTQ7Sc86H1L4JeUInw",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "e228ff1a-d5bd-4496-ae66-73023412016e",
            "data": {
                "icon": "faTimes:solid",
                "name": "Deceased",
                "pinColor": "#C8C8C8",
                "iconColor": "#E95C41",
                "contactState": "contacted-unavailable-other",
                "defaultStatus": true,
                "statusGroupId": "40d81142-39ad-4390-b94f-dadc2c3ecc36"
            },
            "meta": {
                "etag": "25d-yDVThi3oEQ/cA1qoHchWI8mspgs",
                "created": "2019-01-14T18:32:35.237Z",
                "modified": "2019-01-14T18:32:35.237Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "4af5d1ae-fc9b-4cb8-b30f-e210240c9ca4",
            "data": {
                "icon": "faHome:solid",
                "name": "Default",
                "pinColor": "#01B5D6",
                "iconColor": "#01B5D6",
                "contactState": "not-contacted-normal",
                "defaultStatus": true,
                "statusGroupId": "423de88d-1f38-4c4b-98a5-329e446423ea"
            },
            "meta": {
                "etag": "254-XXuuobYVggZ7UFfTTEDB8+MDmqg",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "1f11979f-fe62-4bfa-b286-90701519d855",
            "data": {
                "icon": "faTimes:solid",
                "name": "Do Not Knock",
                "pinColor": "#E95C41",
                "iconColor": "#E95C41",
                "contactState": "not-contacted-do-not-knock",
                "defaultStatus": true,
                "statusGroupId": "c81320a3-238c-4d4b-b2af-120f55161f0e"
            },
            "meta": {
                "etag": "260-9tmmlmQW8FcbeF7iLDxqJDJO6WQ",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "8a7007e8-3a5a-4d05-81d4-b2fc4940e802",
            "data": {
                "icon": "faStar:solid",
                "name": "High Priority",
                "pinColor": "#FFBE00",
                "iconColor": "#FFBE00",
                "contactState": "not-contacted-high-priority",
                "defaultStatus": true,
                "statusGroupId": "1a64b38d-63da-437e-ab87-e30879d70c7a"
            },
            "meta": {
                "etag": "261-zdVq0UojIuLCbw3nrXWEnAgrtMI",
                "created": "2019-01-14T18:32:35.235Z",
                "modified": "2019-01-14T18:32:35.235Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "1e055231-e35e-4503-92ba-99fd496aea46",
            "data": {
                "icon": "faTimes:solid",
                "name": "Inaccessible",
                "pinColor": "#C8C8C8",
                "iconColor": "#E95C41",
                "contactState": "contacted-unavailable-other",
                "defaultStatus": true,
                "statusGroupId": "40d81142-39ad-4390-b94f-dadc2c3ecc36"
            },
            "meta": {
                "etag": "261-oFqgT5pn108rZXF1xeLE9IF+ocY",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "220fa738-df12-430a-83ce-2ec1ff44c02e",
            "data": {
                "icon": "faTimes:solid",
                "name": "Moved",
                "pinColor": "#C8C8C8",
                "iconColor": "#E95C41",
                "contactState": "contacted-unavailable-other",
                "defaultStatus": true,
                "statusGroupId": "40d81142-39ad-4390-b94f-dadc2c3ecc36"
            },
            "meta": {
                "etag": "25a-XzCTE6MK4Zvob32E7rIa96zd1TY",
                "created": "2019-01-14T18:32:35.237Z",
                "modified": "2019-01-14T18:32:35.237Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "7c0516db-9948-4b93-9782-14d2c0cf2cd0",
            "data": {
                "icon": "polisNotHome",
                "name": "Not Home",
                "pinColor": "#C8C8C8",
                "iconColor": "#C8C8C8",
                "contactState": "contacted-unavailable-not-home",
                "defaultStatus": true,
                "statusGroupId": "b9ed5a4a-8bd0-4734-98cf-78b1fe693982"
            },
            "meta": {
                "etag": "25f-JCMkkex0GIxICChH/qtemPeAEB8",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "3d2e5861-de08-4090-95f7-68aa186497c6",
            "data": {
                "icon": "faThumbsDown:solid",
                "name": "Not Successful",
                "pinColor": "#C8C8C8",
                "iconColor": "#E95C41",
                "contactState": "contacted-available-not-successful",
                "defaultStatus": true,
                "statusGroupId": "756585bf-57e3-41e4-8345-6e29b16894bf"
            },
            "meta": {
                "etag": "26f-wiovWHU8KOprVHAnTQFKVoOB744",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "490f9437-17f6-40e3-9956-33e0acfb4691",
            "data": {
                "icon": "faTimes:solid",
                "name": "Other Language",
                "pinColor": "#C8C8C8",
                "iconColor": "#E95C41",
                "contactState": "contacted-unavailable-other",
                "defaultStatus": true,
                "statusGroupId": "40d81142-39ad-4390-b94f-dadc2c3ecc36"
            },
            "meta": {
                "etag": "263-N2Rd6ufFnJRBTx2c+UbiDkLBVR0",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "88784604-034c-47cf-a83c-56b93e2ed911",
            "data": {
                "icon": "faTimes:solid",
                "name": "Refused",
                "pinColor": "#C8C8C8",
                "iconColor": "#E95C41",
                "contactState": "contacted-unavailable-other",
                "defaultStatus": true,
                "statusGroupId": "5c0d3183-c1cb-461a-ae0f-7ac2f52e6206"
            },
            "meta": {
                "etag": "25c-6E9Cy8UiVDBCeygMz6LKgNazG0M",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "955b2213-c31f-490b-8004-27d4568865b1",
            "data": {
                "icon": "faThumbsUp:solid",
                "name": "Successful",
                "pinColor": "#C8C8C8",
                "iconColor": "#73C1B1",
                "contactState": "contacted-available-successful",
                "defaultStatus": true,
                "statusGroupId": "7cba7113-f214-440d-9e2f-6f11fca47740"
            },
            "meta": {
                "etag": "265-eXQzUr9FDo+GS+UU2+0Y6Ri+WJU",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        }
    ],
    "meta": {}
}
```

Retrieves a list of statuses filtered by a criteria.

### HTTP Request

`GET https://api.polisapp.com/statuses?filter={filter}&limit={limit}&skip={skip}&sort={sort}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | true | Query to filter data. [See documentation](#filters).
limit | true | Limit results returned. Usefull for paggination.
skip | true | Data offset index. Usefull for paggination.
sort | true | Sort column. Ex.: `["data/name","ASC"]`

### Allowed attributes

List of attributes that are allowed to be used in a filter query.

* `/customerId`


## Add a status to a campaign

> Example Request

```https
PUT /campaigns/e660c056-ea61-4a2f-8bf4-ef9280413e0a/statuses/41eecffe-5b6a-4499-a7b9-70e93f35d78b HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
    "id": "eb7cedad-cba2-4ed4-86c4-ebecbc2b34a0",
    "data": {
        "statusId": "41eecffe-5b6a-4499-a7b9-70e93f35d78b",
        "campaignId": "e660c056-ea61-4a2f-8bf4-ef9280413e0a"
    },
    "meta": {
        "etag": "1fd-DZUtKhWFxo+Uj8aQcLuoNNTW2Ec",
        "created": "2019-01-14T19:20:37.553Z",
        "modified": "2019-01-14T19:20:37.553Z",
        "resource": "status-campaign",
        "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
        "isDeleted": false,
        "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
    },
    "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
    "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
}
```

Add a status to a campaign.

### HTTP Request

`PUT https://api.polisapp.com/campaigns/{campaignId}/statuses/{statusId}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
campaignId | true | Unique identifier of the campaign.
statusId | true | Unique identifier of the status.

## Get all statuses linked to campaign

> Example Request

```https
GET /campaigns/e660c056-ea61-4a2f-8bf4-ef9280413e0a/statuses HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
    "data": [
        {
            "id": "8a7007e8-3a5a-4d05-81d4-b2fc4940e802",
            "data": {
                "icon": "faStar:solid",
                "name": "High Priority",
                "pinColor": "#FFBE00",
                "iconColor": "#FFBE00",
                "contactState": "not-contacted-high-priority",
                "defaultStatus": true,
                "statusGroupId": "1a64b38d-63da-437e-ab87-e30879d70c7a"
            },
            "meta": {
                "etag": "261-zdVq0UojIuLCbw3nrXWEnAgrtMI",
                "created": "2019-01-14T18:32:35.235Z",
                "modified": "2019-01-14T18:32:35.235Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "4af5d1ae-fc9b-4cb8-b30f-e210240c9ca4",
            "data": {
                "icon": "faHome:solid",
                "name": "Default",
                "pinColor": "#01B5D6",
                "iconColor": "#01B5D6",
                "contactState": "not-contacted-normal",
                "defaultStatus": true,
                "statusGroupId": "423de88d-1f38-4c4b-98a5-329e446423ea"
            },
            "meta": {
                "etag": "254-XXuuobYVggZ7UFfTTEDB8+MDmqg",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "3d2e5861-de08-4090-95f7-68aa186497c6",
            "data": {
                "icon": "faThumbsDown:solid",
                "name": "Not Successful",
                "pinColor": "#C8C8C8",
                "iconColor": "#E95C41",
                "contactState": "contacted-available-not-successful",
                "defaultStatus": true,
                "statusGroupId": "756585bf-57e3-41e4-8345-6e29b16894bf"
            },
            "meta": {
                "etag": "26f-wiovWHU8KOprVHAnTQFKVoOB744",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "91baec90-6c55-4fe6-8234-f8a4d5ee8d3d",
            "data": {
                "icon": "faCalendar:regular",
                "name": "Appointment",
                "pinColor": "#C8C8C8",
                "iconColor": "#01B5D6",
                "contactState": "appointment",
                "defaultStatus": true,
                "statusGroupId": "3239be67-199f-4cef-a30b-faea8ea48785"
            },
            "meta": {
                "etag": "255-ZPNmy2TEWvLE5Uag2uh1tSvts9E",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "955b2213-c31f-490b-8004-27d4568865b1",
            "data": {
                "icon": "faThumbsUp:solid",
                "name": "Successful",
                "pinColor": "#C8C8C8",
                "iconColor": "#73C1B1",
                "contactState": "contacted-available-successful",
                "defaultStatus": true,
                "statusGroupId": "7cba7113-f214-440d-9e2f-6f11fca47740"
            },
            "meta": {
                "etag": "265-eXQzUr9FDo+GS+UU2+0Y6Ri+WJU",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "490f9437-17f6-40e3-9956-33e0acfb4691",
            "data": {
                "icon": "faTimes:solid",
                "name": "Other Language",
                "pinColor": "#C8C8C8",
                "iconColor": "#E95C41",
                "contactState": "contacted-unavailable-other",
                "defaultStatus": true,
                "statusGroupId": "40d81142-39ad-4390-b94f-dadc2c3ecc36"
            },
            "meta": {
                "etag": "263-N2Rd6ufFnJRBTx2c+UbiDkLBVR0",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "220fa738-df12-430a-83ce-2ec1ff44c02e",
            "data": {
                "icon": "faTimes:solid",
                "name": "Moved",
                "pinColor": "#C8C8C8",
                "iconColor": "#E95C41",
                "contactState": "contacted-unavailable-other",
                "defaultStatus": true,
                "statusGroupId": "40d81142-39ad-4390-b94f-dadc2c3ecc36"
            },
            "meta": {
                "etag": "25a-XzCTE6MK4Zvob32E7rIa96zd1TY",
                "created": "2019-01-14T18:32:35.237Z",
                "modified": "2019-01-14T18:32:35.237Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "1f11979f-fe62-4bfa-b286-90701519d855",
            "data": {
                "icon": "faTimes:solid",
                "name": "Do Not Knock",
                "pinColor": "#E95C41",
                "iconColor": "#E95C41",
                "contactState": "not-contacted-do-not-knock",
                "defaultStatus": true,
                "statusGroupId": "c81320a3-238c-4d4b-b2af-120f55161f0e"
            },
            "meta": {
                "etag": "260-9tmmlmQW8FcbeF7iLDxqJDJO6WQ",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "e228ff1a-d5bd-4496-ae66-73023412016e",
            "data": {
                "icon": "faTimes:solid",
                "name": "Deceased",
                "pinColor": "#C8C8C8",
                "iconColor": "#E95C41",
                "contactState": "contacted-unavailable-other",
                "defaultStatus": true,
                "statusGroupId": "40d81142-39ad-4390-b94f-dadc2c3ecc36"
            },
            "meta": {
                "etag": "25d-yDVThi3oEQ/cA1qoHchWI8mspgs",
                "created": "2019-01-14T18:32:35.237Z",
                "modified": "2019-01-14T18:32:35.237Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "2579d3bf-6ee0-44f4-ab34-d40dc6a077c7",
            "data": {
                "icon": "faRedo:solid",
                "name": "Come Back",
                "pinColor": "#C8C8C8",
                "iconColor": "#01B5D6",
                "contactState": "come-back",
                "defaultStatus": true,
                "statusGroupId": "c75a45d6-67cc-434c-b5b5-9a2bd2cee860"
            },
            "meta": {
                "etag": "24b-3lJP37fqrMTQ7Sc86H1L4JeUInw",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "1e055231-e35e-4503-92ba-99fd496aea46",
            "data": {
                "icon": "faTimes:solid",
                "name": "Inaccessible",
                "pinColor": "#C8C8C8",
                "iconColor": "#E95C41",
                "contactState": "contacted-unavailable-other",
                "defaultStatus": true,
                "statusGroupId": "40d81142-39ad-4390-b94f-dadc2c3ecc36"
            },
            "meta": {
                "etag": "261-oFqgT5pn108rZXF1xeLE9IF+ocY",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "7c0516db-9948-4b93-9782-14d2c0cf2cd0",
            "data": {
                "icon": "polisNotHome",
                "name": "Not Home",
                "pinColor": "#C8C8C8",
                "iconColor": "#C8C8C8",
                "contactState": "contacted-unavailable-not-home",
                "defaultStatus": true,
                "statusGroupId": "b9ed5a4a-8bd0-4734-98cf-78b1fe693982"
            },
            "meta": {
                "etag": "25f-JCMkkex0GIxICChH/qtemPeAEB8",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        },
        {
            "id": "88784604-034c-47cf-a83c-56b93e2ed911",
            "data": {
                "icon": "faTimes:solid",
                "name": "Refused",
                "pinColor": "#C8C8C8",
                "iconColor": "#E95C41",
                "contactState": "contacted-unavailable-other",
                "defaultStatus": true,
                "statusGroupId": "5c0d3183-c1cb-461a-ae0f-7ac2f52e6206"
            },
            "meta": {
                "etag": "25c-6E9Cy8UiVDBCeygMz6LKgNazG0M",
                "created": "2019-01-14T18:32:35.236Z",
                "modified": "2019-01-14T18:32:35.236Z",
                "resource": "statuses",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            },
            "customerId": "cc34e52f-5bfa-42ee-ac72-d331ac97b5c4",
            "securityGroupId": "8fa2a8d3-104f-48ce-9f00-c6795013edca"
        }
    ]
}
```

Retrieves all statuses linked to a campaign

### HTTP Request

`GET https://api.polisapp.com/campaigns/{campaignId}/statuses`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
campaignId | true | Unique identifier of the campaign.

## Remove a status from campaign

> Example Request

```https
DELETE /campaigns/e660c056-ea61-4a2f-8bf4-ef9280413e0a/statuses/41eecffe-5b6a-4499-a7b9-70e93f35d78b HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

Removes a status from a campaign.

### HTTP Request

`DELETE https://api.polisapp.com/campaigns/{campaignId}/statuses/{statusId}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
campaignId | true | Unique identifier of the campaign.
statusId | true | Unique identifier of the status.