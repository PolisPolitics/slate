# Status-groups

## The status-group object

```json
{
  "id": "1033d9ec-e244-4210-b569-06d9f0029359", 
  "data": {
    "icon": "faCalendar:regular",
    "name": "Appointment",
    "pinColor": "#C8C8C8",
    "iconColor": "#01B5D6",
    "statusType": "appointment",
    "contactState": "appointment"
  },
  "meta": {
    "etag": "1c3-qK4WON+wwEzDcVWVND8Axzz14yQ",
    "created": "2019-01-04T11:40:08.221Z",
    "modified": "2019-01-04T11:40:08.221Z",
    "resource": "status-groups",
    "createdBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7",
    "isDeleted": false,
    "modifiedBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7"
  }
}
```

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Unique identifier for the object.
data | true | status-group data.

### data

Attribute | Required? | Description
--------- | --------- | -----------
icon | true | Name of the icon.
name | true | Name of the status-group.
pinColor | true | Hex code for the pin color.
iconColor | true | Hex code for the icon color.
statusType | true | Category of the status-group. Can be `successful`, `unsucessful`, `appointment`, `unavailable`, `list`.
contactState | true | Compatibility attribute that maps a status-group to an older version of statuses.

### meta

[See documentation](#metadata-object).

## Retrieve a status-group

> Example Request

```http
GET /status-groups/23b9f19d-fb96-404c-93ea-d9517abe8830 HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "id":"23b9f19d-fb96-404c-93ea-d9517abe8830",
  "data": {
    "contactState":"contacted-available-successful",
    "icon":"success",
    "iconColor":"#0000FF",
    "name":"StatusGroup",
    "pinColor":"#808080",
    "statusType":"successful"
  },
  "meta":{
    "created":"2019-01-04T17:40:18.074Z",
    "createdBy":"bac9a571-848b-46cb-bf3b-4518fc1c5c7b",
    "etag":"1c3-qK4WON+wwEzDcVWVND8Axzz14yQ",
    "isDeleted":false,
    "modified":"2019-01-04T17:40:18.074Z",
    "modifiedBy":"bac9a571-848b-46cb-bf3b-4518fc1c5c7b",
    "resource":"status-groups"
  }
}
```

Obtains a single status-group object by it's id.

### HTTP Request

`GET https://api.polisapp.com/status-groups/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | Unique identifier of the status-group.

## Get many status-groups

Retrieves a list of existing status-groups

> Example Request

```http
GET /status-groups?limit=10&skip=0&sort=%5B%22data%2Fname%22%2C%22ASC%22%5D HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "data": [
    {
      "id": "1033d9ec-e244-4210-b569-06d9f0029359",
      "data": {
        "icon": "faCalendar:regular",
        "name": "Appointment",
        "pinColor": "#C8C8C8",
        "iconColor": "#01B5D6",
        "statusType": "appointment",
        "contactState": "appointment"
      },
      "meta": {
        "etag": "1c3-+A8tftYDtDm1bESW/8P2PWBZm6c",
        "created": "2019-01-04T11:40:08.221Z",
        "modified": "2019-01-04T11:40:08.221Z",
        "resource": "status-groups",
        "createdBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7",
        "isDeleted": false,
        "modifiedBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7"
      },
    }
    {
      "id": "5b15e892-eb5c-4154-b75a-347554718cb1",
      "data": {
        "contactState":"not-contacted-high-priority",
        "icon":"faStar:solid",
        "iconColor":"#FFBE00",
        "name":"High Priority",
        "pinColor":"#FFBE00",
        "statusType":"list"
      },
      "meta": {
        "etag": "1c1-ZHoblhKhdlX+rpJo/FfcPuPQTwg",
        "created": "2019-01-04T11:40:08.221Z",
        "modified": "2019-01-04T11:40:08.221Z",
        "resource": "status-groups",
        "createdBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7",
        "isDeleted": false,
        "modifiedBy": "5a2c9e4b-7fec-4c91-a700-c36233b160e7"
      }
    }
  ],
  "meta": {
  }
}
```

### HTTP Request

`GET https://api.polisapp.com/status-groups?filter={filter}&limit={limit}&skip={skip}&sort={sort}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
fiter | false | Query to filter data. [See documentation](#filters).
limit | true | Limit results returned. Useful for pagination.
skip | true | Data offset index. Useful for pagination.
sort | true | Sort column. Ex.: `["data/name","ASC"]`
