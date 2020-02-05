# Status-groups

## The status-group object

```json
{
    "id": "3239be67-199f-4cef-a30b-faea8ea48785",
    "data": {
        "icon": "faCalendar:regular",
        "name": "Appointment",
        "pinColor": "#C8C8C8",
        "iconColor": "#01B5D6",
        "statusType": "appointment",
        "contactState": "appointment"
    },
    "meta": {
        "etag": "1bc-5enwzbhdhBgW9Uq/8W5AxwAoSj8",
        "created": "2019-01-14T18:32:34.187Z",
        "modified": "2019-01-14T18:32:34.187Z",
        "resource": "status-groups",
        "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
        "isDeleted": false,
        "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
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

```https
GET /v1/status-groups/3239be67-199f-4cef-a30b-faea8ea48785 HTTP/1.1
Host: api.beta.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
    "id": "3239be67-199f-4cef-a30b-faea8ea48785",
    "data": {
        "icon": "faCalendar:regular",
        "name": "Appointment",
        "pinColor": "#C8C8C8",
        "iconColor": "#01B5D6",
        "statusType": "appointment",
        "contactState": "appointment"
    },
    "meta": {
        "etag": "1bc-5enwzbhdhBgW9Uq/8W5AxwAoSj8",
        "created": "2019-01-14T18:32:34.187Z",
        "modified": "2019-01-14T18:32:34.187Z",
        "resource": "status-groups",
        "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
        "isDeleted": false,
        "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
    }
}
```

Obtains a single status-group object by it's id.

### HTTP Request

`GET https://api.beta.polisapp.com/v1/status-groups/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | Unique identifier of the status-group.

## Get many status-groups

Retrieves a list of existing status-groups

> Example Request

```http
GET /v1/status-groups?limit=100&skip=0&sort=["id","ASC"] HTTP/1.1
Host: api.beta.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
    "data": [
        {
            "id": "3239be67-199f-4cef-a30b-faea8ea48785",
            "data": {
                "icon": "faCalendar:regular",
                "name": "Appointment",
                "pinColor": "#C8C8C8",
                "iconColor": "#01B5D6",
                "statusType": "appointment",
                "contactState": "appointment"
            },
            "meta": {
                "etag": "1bc-5enwzbhdhBgW9Uq/8W5AxwAoSj8",
                "created": "2019-01-14T18:32:34.187Z",
                "modified": "2019-01-14T18:32:34.187Z",
                "resource": "status-groups",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            }
        },
        {
            "id": "40d81142-39ad-4390-b94f-dadc2c3ecc36",
            "data": {
                "icon": "faTimes:solid",
                "name": "Bad Contact Info",
                "pinColor": "#C8C8C8",
                "iconColor": "#E95C41",
                "statusType": "unavailable",
                "contactState": "contacted-unavailable-other"
            },
            "meta": {
                "etag": "1cc-5kPJw112Bo07yGNwe/VSr6Fpkks",
                "created": "2019-01-14T18:32:34.161Z",
                "modified": "2019-01-14T18:32:34.161Z",
                "resource": "status-groups",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            }
        },
        {
            "id": "c75a45d6-67cc-434c-b5b5-9a2bd2cee860",
            "data": {
                "icon": "faRedo:solid",
                "name": "Come Back",
                "pinColor": "#C8C8C8",
                "iconColor": "#01B5D6",
                "statusType": "unavailable",
                "contactState": "come-back"
            },
            "meta": {
                "etag": "1b2-8ZEVVqsW3EObYyq+yEZuusP0dbw",
                "created": "2019-01-14T18:32:34.196Z",
                "modified": "2019-01-14T18:32:34.196Z",
                "resource": "status-groups",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            }
        },
        {
            "id": "423de88d-1f38-4c4b-98a5-329e446423ea",
            "data": {
                "icon": "faHome:solid",
                "name": "Default",
                "pinColor": "#01B5D6",
                "iconColor": "#01B5D6",
                "statusType": "list",
                "contactState": "not-contacted-normal"
            },
            "meta": {
                "etag": "1b4-3lq19W9GKj5wQ8IHqvr0iYS2Hgs",
                "created": "2019-01-14T18:32:34.197Z",
                "modified": "2019-01-14T18:32:34.197Z",
                "resource": "status-groups",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            }
        },
        {
            "id": "c81320a3-238c-4d4b-b2af-120f55161f0e",
            "data": {
                "icon": "faTimes:solid",
                "name": "Do Not Knock",
                "pinColor": "#E95C41",
                "iconColor": "#E95C41",
                "statusType": "list",
                "contactState": "not-contacted-do-not-knock"
            },
            "meta": {
                "etag": "1c0-ZXgeEWNAicSyNn4eWht0DRBD71U",
                "created": "2019-01-14T18:32:34.197Z",
                "modified": "2019-01-14T18:32:34.197Z",
                "resource": "status-groups",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            }
        },
        {
            "id": "1a64b38d-63da-437e-ab87-e30879d70c7a",
            "data": {
                "icon": "faStar:solid",
                "name": "High Priority",
                "pinColor": "#FFBE00",
                "iconColor": "#FFBE00",
                "statusType": "list",
                "contactState": "not-contacted-high-priority"
            },
            "meta": {
                "etag": "1c1-jMdRPz/xL/vMMULMXybONAzKlRc",
                "created": "2019-01-14T18:32:34.197Z",
                "modified": "2019-01-14T18:32:34.197Z",
                "resource": "status-groups",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            }
        },
        {
            "id": "b9ed5a4a-8bd0-4734-98cf-78b1fe693982",
            "data": {
                "icon": "polisNotHome",
                "name": "Not Home",
                "pinColor": "#C8C8C8",
                "iconColor": "#C8C8C8",
                "statusType": "unavailable",
                "contactState": "contacted-unavailable-not-home"
            },
            "meta": {
                "etag": "1c6-RljukdOcr2FL3LREd20nZNTBsqY",
                "created": "2019-01-14T18:32:34.161Z",
                "modified": "2019-01-14T18:32:34.161Z",
                "resource": "status-groups",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            }
        },
        {
            "id": "756585bf-57e3-41e4-8345-6e29b16894bf",
            "data": {
                "icon": "faThumbsDown:solid",
                "name": "Not Successful",
                "pinColor": "#C8C8C8",
                "iconColor": "#E95C41",
                "statusType": "unsuccessful",
                "contactState": "contacted-available-not-successful"
            },
            "meta": {
                "etag": "1d7-l3FztA7p5U725UR4rLvOuGRLpFo",
                "created": "2019-01-14T18:32:34.161Z",
                "modified": "2019-01-14T18:32:34.161Z",
                "resource": "status-groups",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            }
        },
        {
            "id": "5c0d3183-c1cb-461a-ae0f-7ac2f52e6206",
            "data": {
                "icon": "faTimes:solid",
                "name": "Refused",
                "pinColor": "#C8C8C8",
                "iconColor": "#E95C41",
                "statusType": "unavailable",
                "contactState": "contacted-unavailable-other"
            },
            "meta": {
                "etag": "1c3-Hm/j51heYK4nAeBI4ZOues+iDck",
                "created": "2019-01-14T18:32:34.176Z",
                "modified": "2019-01-14T18:32:34.176Z",
                "resource": "status-groups",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            }
        },
        {
            "id": "7cba7113-f214-440d-9e2f-6f11fca47740",
            "data": {
                "icon": "faThumbsUp:solid",
                "name": "Successful",
                "pinColor": "#C8C8C8",
                "iconColor": "#73C1B1",
                "statusType": "successful",
                "contactState": "contacted-available-successful"
            },
            "meta": {
                "etag": "1cb-WsWYvLl/2CDMJ9JbqrGvYJ5VEcs",
                "created": "2019-01-14T18:32:34.177Z",
                "modified": "2019-01-14T18:32:34.177Z",
                "resource": "status-groups",
                "createdBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be",
                "isDeleted": false,
                "modifiedBy": "01c312cc-5d3b-4d2f-a594-0ecd100411be"
            }
        }
    ],
    "meta": {}
}
```

### HTTP Request

`GET https://api.beta.polisapp.com/v1/status-groups?filter={filter}&limit={limit}&skip={skip}&sort={sort}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
fiter | false | Query to filter data. [See documentation](#filters).
limit | true | Limit results returned. Useful for pagination.
skip | true | Data offset index. Useful for pagination.
sort | true | Sort column. Ex.: `["id","ASC"]`
