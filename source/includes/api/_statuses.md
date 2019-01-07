# Statuses

## The status object

```json
{
  "id": "1114c59b-a3bd-4bd7-aa26-fbe0ebaf891f",
  "data": {
    "icon": "faTimes:solid",
    "name": "Inaccessible",
    "pinColor": "#C8C8C8",
    "iconColor": "#E95C41",
    "contactState": "contacted-unavailable-other",
    "defaultStatus": false,
    "statusGroupId": "a9f9e8bb-246f-4127-a9c7-83d151c95415"
  },
  "meta": {
    "etag": "264-2ZTRcL3W5ySJvg29c8WkF9Klwe8",
    "created": "2019-01-04T11:40:08.812Z",
    "modified": "2019-01-04T11:40:08.812Z",
    "resource": "statuses",
    "createdBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7",
    "isDeleted": false,
    "modifiedBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7"
  },
  "customerId": "28ea23c0-1b1e-4778-8cb5-be02e13b60d9",
  "securityGroupId": "75b37065-f7bd-4b1b-afff-c9ded1776f25"
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
icon | true | Name of the icon.
name | true | Name of the status-group.
pinColor | true | Hex code for the pin color.
iconColor | true | Hex code for the icon color.
contactState | true | Compatibility attribute that maps a status to an older version of statuses.
defaultStatus | false | Boolean that determines if this is a default status. Defaults value is `false`
statusGroupId | true | Id of the status-group that a status belongs to.

### meta

[See documentation](#metadata-object).

## Create a status

> Example Request

```http
POST /v1/statuses HTTP/1.1
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
    "statusGroupId": "a9f9e8bb-246f-4127-a9c7-83d151c95415"
  },
  "customerId": "28ea23c0-1b1e-4778-8cb5-be02e13b60d9"
}
```

> Example Response

```json
{
  "id": "1114c59b-a3bd-4bd7-aa26-fbe0ebaf891f",
  "data": {
    "icon": "faTimes:solid",
    "name": "Inaccessible",
    "pinColor": "#C8C8C8",
    "iconColor": "#E95C41",
    "contactState": "contacted-unavailable-other",
    "defaultStatus": true,
    "statusGroupId": "a9f9e8bb-246f-4127-a9c7-83d151c95415"
  },
  "meta": {
    "etag": "264-2ZTRcL3W5ySJvg29c8WkF9Klwe8",
    "created": "2019-01-04T11:40:08.812Z",
    "modified": "2019-01-04T11:40:08.812Z",
    "resource": "statuses",
    "createdBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7",
    "isDeleted": false,
    "modifiedBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7"
  },
  "customerId": "28ea23c0-1b1e-4778-8cb5-be02e13b60d9",
  "securityGroupId": "75b37065-f7bd-4b1b-afff-c9ded1776f25"
}
```

Creates a new status for a customer.

### HTTP Request

`POST https://api.polisapp.com/v1/statuses`

## Retrieve a status

> Example Request

```http
GET /v1/statuses/1114c59b-a3bd-4bd7-aa26-fbe0ebaf891f HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "id": "1114c59b-a3bd-4bd7-aa26-fbe0ebaf891f",
  "data": {
    "icon": "faTimes:solid",
    "name": "Inaccessible",
    "pinColor": "#C8C8C8",
    "iconColor": "#E95C41",
    "contactState": "contacted-unavailable-other",
    "defaultStatus": true,
    "statusGroupId": "a9f9e8bb-246f-4127-a9c7-83d151c95415"
  },
  "meta": {
    "etag": "264-2ZTRcL3W5ySJvg29c8WkF9Klwe8",
    "created": "2019-01-04T11:40:08.812Z",
    "modified": "2019-01-04T11:40:08.812Z",
    "resource": "statuses",
    "createdBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7",
    "isDeleted": false,
    "modifiedBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7"
  },
  "customerId": "28ea23c0-1b1e-4778-8cb5-be02e13b60d9",
  "securityGroupId": "75b37065-f7bd-4b1b-afff-c9ded1776f25"
}
```

Obtains a single status object by ID.

### HTTP Request

`GET https://api.polisapp.com/v1/statuses/{statusId}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
statusId | true | Unique identifier of the status.

## Update a status

> Example Request

```http
PATCH /v1/statuses/1114c59b-a3bd-4bd7-aa26-fbe0ebaf891f HTTP/1.1
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
  "id": "1114c59b-a3bd-4bd7-aa26-fbe0ebaf891f",
  "data": {
    "icon": "faTimes:solid",
    "name": "New Status Name",
    "pinColor": "#C8C8C8",
    "iconColor": "#E95C41",
    "contactState": "contacted-unavailable-other",
    "defaultStatus": true,
    "statusGroupId": "a9f9e8bb-246f-4127-a9c7-83d151c95415"
  },
  "meta": {
    "etag": "MTUxNjE0ODQ5MjI2MDI3ODI3Mg==",
    "created": "2019-01-04T11:40:08.812Z",
    "modified": "2019-01-04T11:40:08.812Z",
    "resource": "statuses",
    "createdBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7",
    "isDeleted": false,
    "modifiedBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7"
  },
  "customerId": "28ea23c0-1b1e-4778-8cb5-be02e13b60d9",
  "securityGroupId": "75b37065-f7bd-4b1b-afff-c9ded1776f25"
}
```
<aside class="notice">
You can only patch attributes inside <b>data</b> key.
</aside>

[RFC 6902 - JavaScript Object Notation (JSON) Patch](https://tools.ietf.org/html/rfc6902)

### HTTP Request

`PATCH https://api.polisapp.com/v1/statuses/{statusId}`



## Delete a status

### HTTP Request
`DELETE https://api.polisapp.com/v1/statuses/{statusId}`

> Example Request

```http
DELETE https://api.polisapp.com/v1/statuses/1114c59b-a3bd-4bd7-aa26-fbe0ebaf891f
Host: api.polisapp.com
Authorization: Bearer {access_token}
```


## Get all statuses

> Example Request

```http
GET /v1/statuses?filter=/customerId+eq+""28ea23c0-1b1e-4778-8cb5-be02e13b60d9""&limit=100&skip=0&sort=["data/name","ASC"] HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "data": [
    {
      "id": "1114c59b-a3bd-4bd7-aa26-fbe0ebaf891f",
      "data": {
        "icon": "faTimes:solid",
        "name": "New Status Name",
        "pinColor": "#C8C8C8",
        "iconColor": "#E95C41",
        "contactState": "contacted-unavailable-other",
        "defaultStatus": true,
        "statusGroupId": "a9f9e8bb-246f-4127-a9c7-83d151c95415"
      },
      "meta": {
        "etag": "MTUxNjE0ODQ5MjI2MDI3ODI3Mg==",
        "created": "2019-01-04T11:40:08.812Z",
        "modified": "2019-01-04T11:40:08.812Z",
        "resource": "statuses",
        "createdBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7",
        "isDeleted": false,
        "modifiedBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7"
      },
      "customerId": "28ea23c0-1b1e-4778-8cb5-be02e13b60d9",
      "securityGroupId": "75b37065-f7bd-4b1b-afff-c9ded1776f25"
    }
  ]
}
```

Retrieves a list of statuses filtered by a criteria.

### HTTP Request

`GET https://api.polisapp.com/v1/statuses?filter={filter}&limit={limit}&skip={skip}&sort={sort}`

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

```http
PUT /campaigns/2cf2bdd2-3a84-43cc-8171-aad0f4433f89/statuses/27c2f041-971c-4446-9d88-eebabfc44ab8 HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "id": "35004149-a941-4955-9b99-2572962d66a3",
  "data": {
    "campaignId": "2cf2bdd2-3a84-43cc-8171-aad0f4433f89",
    "statusId": "27c2f041-971c-4446-9d88-eebabfc44ab8"
  },
  "meta": {
    "created": "2019-01-07T13:07:47.948Z",
    "createdBy": "32981f31-0c1f-4469-bcd8-930576593013",
    "etag": "1fd-LbLNJ8jMZgewKlGyhtUQ02IsILQ",
    "isDeleted": false,
    "modified": "2019-01-07T13:07:47.948Z",
    "modifiedBy": "32981f31-0c1f-4469-bcd8-930576593013",
    "resource": "status-campaign"
  },
  "customerId": "1a525718-c0df-4d26-90c3-a25c6e5bd2eb",
  "securityGroupId": "b5680128-fc63-4ce0-9c0b-2a22ea3a70bf",
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

```http
GET /campaigns/:campaignId/statuses HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "data": [
    {
      "id": "1114c59b-a3bd-4bd7-aa26-fbe0ebaf891f",
      "data": {
        "icon": "faTimes:solid",
        "name": "New Status Name",
        "pinColor": "#C8C8C8",
        "iconColor": "#E95C41",
        "contactState": "contacted-unavailable-other",
        "defaultStatus": true,
        "statusGroupId": "a9f9e8bb-246f-4127-a9c7-83d151c95415"
      },
      "meta": {
        "etag": "MTUxNjE0ODQ5MjI2MDI3ODI3Mg==",
        "created": "2019-01-04T11:40:08.812Z",
        "modified": "2019-01-04T11:40:08.812Z",
        "resource": "statuses",
        "createdBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7",
        "isDeleted": false,
        "modifiedBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7"
      },
      "customerId": "28ea23c0-1b1e-4778-8cb5-be02e13b60d9",
      "securityGroupId": "75b37065-f7bd-4b1b-afff-c9ded1776f25"
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

```http
DELETE /campaigns/:campaignId/statuses/:statusId HTTP/1.1
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