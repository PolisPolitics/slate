# Interactions

## The interaction object

```json
{
  "customerId": "e3899af9-2b74-45dd-b2b1-d7be8ad47bae",
  "data": {
    "campaignId": "8b385b44-1618-4dce-bffc-8075002e29a0",
    "contactId": "7fbec30c-b576-42bb-b5ba-646972844253",
    "distance": 9.97,
    "listId": "2210d9ea-1870-4b8d-8803-ce426e33a96b",
    "location": {
      "confidence": 0,
      "lat": 42.3659207,
      "lng": -71.0587026
    },
    "successful": false,
    "survey": {
      "responses": {
        "6430c7c8-364c-4fa5-b145-9dbaa2795f7d": {
          "fields": {"dogliker": "true"},
          "questionId": "6430c7c8-364c-4fa5-b145-9dbaa2795f7d"
        },
        "789bb27d-101d-4021-ba8d-06b02eaf736f": {
          "fields": {"mothername": "Jane Doe"},
          "questionId": "789bb27d-101d-4021-ba8d-06b02eaf736f"
        },
        "ac3f2a70-c7b1-4d25-a5ea-135233c5437c": {
          "fields": {"available": "true"},
          "questionId": "ac3f2a70-c7b1-4d25-a5ea-135233c5437c"
        },
        "b21d978b-0a48-42c3-9c3a-c24fff0236f2": {
          "fields": {"bestpet": "Cat"},
          "questionId": "b21d978b-0a48-42c3-9c3a-c24fff0236f2"
        },
        "cd6d2a75-df61-407c-8763-8d2c407c8196": {
          "fields": {
            "buypet": [
              "Horse",
              "Snake"
            ]
          },
          "questionId": "cd6d2a75-df61-407c-8763-8d2c407c8196"
        },
        "f25a1d08-67c5-4970-87ac-21b17f1ed808": {
          "fields": {"catlikeness": 4},
          "questionId": "f25a1d08-67c5-4970-87ac-21b17f1ed808"
        }
      },
      "surveyId": "3e365fdb-4e7e-4107-9ea4-2d1904ef5404"
    },
    "timestamp": "2017-08-29T15:55:12.000Z",
    "unavailable": false
  },
  "id": "0b8c5147-45ab-47d2-b91f-5773034f1f6e",
  "meta": {
    "created": "2017-12-15T19:46:01.719Z",
    "createdBy": "11b78eab-8b3e-45e7-804c-4a94045367d4",
    "etag": "",
    "isDeleted": false,
    "modified": "2017-12-15T19:46:01.719Z",
    "modifiedBy": "11b78eab-8b3e-45e7-804c-4a94045367d4",
    "resource": "interactions"
  },
  "securityGroupId": "d4a1d326-a2c7-415c-bfea-dd9fc84f8d00"
}
```

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Unique identifier for the object.
customerId | true | Customer this resource belongs to.
securityGroupId | true | Security group of this resource.
listId | true | (Read-only field) List identifier this interaction belongs to.


### data

Attribute | Required? | Description
--------- | --------- | -----------
campaignId | true | Campaign identifier this interaction is associated with.
contactId | true | Contact identifier of this interaction.
distance | false | Distance measured in miles.
location | false | Location [details](#data-location).
successful | false | Flag indicating whether this interaction was successful.
survey | true | Survey [details](#data-survey).
timestamp | true | Date and time when this interaction occurred.
unavailable | true | Flag indicating whether the listed contact person was unavailable.
unavailableReason | false | The reason specifying why the listed contact person was unavailable.
walklistId | false | Route identifier this contact is reserved to.

### data/location

Attribute | Required? | Description
--------- | --------- | -----------
confidence | false | Quantitative accuracy of this location co-ordinate.
lat | false | Co-ordinate specifying the north–south position of this location on Earth.
lng | false | Co-ordinate specifying the east–west position of this location on Earth.

### data/survey

Attribute | Required? | Description
--------- | --------- | -----------
surveyId | true | Survey identifier that the interaction consists.
responses | false | Object containing all the responses for this survey.

### meta

[See documentation](#metadata-object).

## Create an interaction

> Example Request

```http
POST /v1/interactions HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

```json
{
  "campaignId":"d545b1e1-8f97-4ae4-a164-1b4a4a87bc07",
  "contactId":"3e591604-059a-4726-a0b9-0af6316adfa6",
  "timestamp":"2017-09-18T12:51:55.000Z",
  "survey":{
    "surveyId":"116473d5-0ebb-4554-a13c-a4ed965c9857",
    "responses":{
      "16a51c61-57b5-4a38-9a7d-2b5f56bfb835":{
        "fields":{},
        "questionId":"16a51c61-57b5-4a38-9a7d-2b5f56bfb835"
        },
      "6209002e-5921-4b62-83bb-35b4dbe62580":{
        "fields":{"available":"true"},
        "questionId":"6209002e-5921-4b62-83bb-35b4dbe62580"
        }
      }
    },
  "distance":2449.35,
  "location":{
    "lat":34.0687112,
    "lng":-118.3530776,
    "confidence":0
  },
  "unavailable":false
  }
  ```

  > Example Response

  ```json
  {
  "id":"019becde-9138-4e21-b1ba-6e817dd27c80",
  "data":{
    "listId":"dc8b5229-ef66-41cc-b774-4a8e6a39c60b",
    "campaignId":"d545b1e1-8f97-4ae4-a164-1b4a4a87bc07",
    "contactId":"3e591604-059a-4726-a0b9-0af6316adfa6",
    "timestamp":"2017-09-18T12:51:55.000Z",
    "survey":{
      "surveyId":"116473d5-0ebb-4554-a13c-a4ed965c9857",
      "responses":{
        "16a51c61-57b5-4a38-9a7d-2b5f56bfb835":{
          "fields":{},
          "questionId":"16a51c61-57b5-4a38-9a7d-2b5f56bfb835"
          },
        "6209002e-5921-4b62-83bb-35b4dbe62580":{
          "fields":{"available":"true"},
          "questionId":"6209002e-5921-4b62-83bb-35b4dbe62580"
          }
        }
      },
    "distance":2449.35,
    "location":{
      "lat":34.0687112,
      "lng":-118.3530776,
      "confidence":0
    },
    "unavailable":false
  },
  "meta":{
    "etag":"3e8-SIMIS22pStVskqOe/o51Wzx9bbk",
    "created":"2017-09-18T15:20:58.865Z",
    "modified":"2017-09-18T15:20:58.865Z",
    "resource":"interactions",
    "createdBy":"931596ea-8ac6-44c5-8aa7-e11456fca02c",
    "isDeleted":false,
    "modifiedBy":"931596ea-8ac6-44c5-8aa7-e11456fca02c"
    },
  "customerId":"15ecebe1-e92c-4d8e-893b-e961be3f482a",
  "securityGroupId":"f32cdf73-e257-44c9-8e70-3235952962a0"
  }
```

Creates a new interaction.

### HTTP Request

`POST https://api.polisapp.com/v1/interactions`

## Retrieve an interaction

> Example Request

```http
GET /v1/interactions/019becde-9138-4e21-b1ba-6e817dd27c80 HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "id": "019becde-9138-4e21-b1ba-6e817dd27c80",
  "data": {
    "listId": "dc8b5229-ef66-41cc-b774-4a8e6a39c60b",
    "survey": {
      "surveyId": "116473d5-0ebb-4554-a13c-a4ed965c9857",
      "responses": {
        "16a51c61-57b5-4a38-9a7d-2b5f56bfb835": {
          "fields": {},
          "questionId": "16a51c61-57b5-4a38-9a7d-2b5f56bfb835"
          },
        "6209002e-5921-4b62-83bb-35b4dbe62580": {
          "fields": {"available": "true"},
          "questionId": "6209002e-5921-4b62-83bb-35b4dbe62580"
          }
        }
      },
    "distance": 2449.35,
    "location": {
      "lat": 34.0687112,
      "lng": -118.3530776,
      "confidence": 0
      },
      "contactId": "3e591604-059a-4726-a0b9-0af6316adfa6",
      "timestamp": "2017-09-18T12:51:55.000Z",
      "campaignId": "d545b1e1-8f97-4ae4-a164-1b4a4a87bc07",
      "unavailable": false
  },
  "meta": {
    "etag": "3e8-SIMIS22pStVskqOe/o51Wzx9bbk",
    "created": "2017-09-18T15:20:58.865Z",
    "modified": "2017-09-18T15:20:58.865Z",
    "resource": "interactions",
    "createdBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
    "isDeleted": false,
    "modifiedBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c"
  },
  "customerId": "15ecebe1-e92c-4d8e-893b-e961be3f482a",
  "securityGroupId": "f32cdf73-e257-44c9-8e70-3235952962a0"
}
```

Obtains a single interaction object by ID.

### HTTP Request

`GET https://api.polisapp.com/v1/interactions/{interactionId}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
interactionId | true | Unique identifier of the interaction.

## Update an interaction

> Example Request

```http
PATCH /v1/interactions/019becde-9138-4e21-b1ba-6e817dd27c80 HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
ETag: {etag_value}
{
  "data": [
    {
      "op":"replace",
      "path":"/interactions",
      "value": "New Interaction Name"
    }
  ]
}
```

> Example Response

```json
{
  "id": "019becde-9138-4e21-b1ba-6e817dd27c80",
  "data": {
    "listId": "dc8b5229-ef66-41cc-b774-4a8e6a39c60b",
    "survey": {
      "surveyId": "116473d5-0ebb-4554-a13c-a4ed965c9857",
      "responses": {
        "16a51c61-57b5-4a38-9a7d-2b5f56bfb835": {
          "fields": {},
          "questionId": "16a51c61-57b5-4a38-9a7d-2b5f56bfb835"
        },
        "6209002e-5921-4b62-83bb-35b4dbe62580": {
          "fields": {"available": "true"},
          "questionId": "6209002e-5921-4b62-83bb-35b4dbe62580"
        }
      }
    },
    "distance": 2449.35,
    "location": {
      "lat": 34.0687112,
      "lng": -118.3530776,
      "confidence": 0
    },
    "contactId": "3e591604-059a-4726-a0b9-0af6316adfa6",
    "timestamp": "2017-09-18T12:51:55.000Z",
    "campaignId": "d545b1e1-8f97-4ae4-a164-1b4a4a87bc07",
    "unavailable": false
  },
  "meta": {
    "etag": "3e8-SIMIS22pStVskqOe/o51Wzx9bbk",
    "created": "2017-09-18T15:20:58.865Z",
    "modified": "2017-09-18T15:20:58.865Z",
    "resource": "interactions",
    "createdBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
    "isDeleted": false,
    "modifiedBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c"
  },
  "customerId": "15ecebe1-e92c-4d8e-893b-e961be3f482a",
  "securityGroupId": "f32cdf73-e257-44c9-8e70-3235952962a0"
}
```
<aside class="notice">
You can only patch attributes inside <b>data</b> key.
</aside>

[RFC 6902 - JavaScript Object Notation (JSON) Patch](https://tools.ietf.org/html/rfc6902)

### HTTP Request

`PATCH https://api.polisapp.com/v1/interactions/{interactionId}`



## Delete an interaction

### HTTP Request
`DELETE https://api.polisapp.com/v1/interactions/{interactionId}`

> Example Request

```http
DELETE https://api.polisapp.com/v1/interactions/019becde-9138-4e21-b1ba-6e817dd27c80
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

## Get all interactions

> Example Request

```http
GET /v1/interactions?limit=1&skip=9&sort=%5B%22id%22%2C%22ASC%22%5D HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "id": "019becde-9138-4e21-b1ba-6e817dd27c80",
  "data": {
    "listId": "dc8b5229-ef66-41cc-b774-4a8e6a39c60b",
    "survey": {
      "surveyId": "116473d5-0ebb-4554-a13c-a4ed965c9857",
      "responses": {
        "16a51c61-57b5-4a38-9a7d-2b5f56bfb835": {
          "fields": {},
          "questionId": "16a51c61-57b5-4a38-9a7d-2b5f56bfb835"
        },
        "6209002e-5921-4b62-83bb-35b4dbe62580": {
          "fields": {"available": "true"},
          "questionId": "6209002e-5921-4b62-83bb-35b4dbe62580"
        }
      }
    },
  "distance": 2449.35,
  "location": {
    "lat": 34.0687112,
    "lng": -118.3530776,
    "confidence": 0
  },
  "contactId": "3e591604-059a-4726-a0b9-0af6316adfa6",
  "timestamp": "2017-09-18T12:51:55.000Z",
  "campaignId": "d545b1e1-8f97-4ae4-a164-1b4a4a87bc07",
  "unavailable": false
  },
  "meta": {
    "etag": "3e8-SIMIS22pStVskqOe/o51Wzx9bbk",
    "created": "2017-09-18T15:20:58.865Z",
    "modified": "2017-09-18T15:20:58.865Z",
    "resource": "interactions",
    "createdBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
    "isDeleted": false,
    "modifiedBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c"
  },
  "customerId": "15ecebe1-e92c-4d8e-893b-e961be3f482a",
  "securityGroupId": "f32cdf73-e257-44c9-8e70-3235952962a0"
}
```

## Find the latest interactions

> Example Request

```http
GET /v1/interactions/latest/by-canvasser HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "data": [
    {
      "id": "019becde-9138-4e21-b1ba-6e817dd27c80",
      "data": {
        "listId": "dc8b5229-ef66-41cc-b774-4a8e6a39c60b",
        "survey": {
          "surveyId": "116473d5-0ebb-4554-a13c-a4ed965c9857",
          "responses": {
            "16a51c61-57b5-4a38-9a7d-2b5f56bfb835": {
              "fields": {},
              "questionId": "16a51c61-57b5-4a38-9a7d-2b5f56bfb835"
            },
            "6209002e-5921-4b62-83bb-35b4dbe62580": {
              "fields": {"available": "true"},
              "questionId": "6209002e-5921-4b62-83bb-35b4dbe62580"
            }
          }
        },
        "distance": 2449.35,
        "location": {
          "lat": 34.0687112,
          "lng": -118.3530776,
          "confidence": 0
        },
        "contactId": "3e591604-059a-4726-a0b9-0af6316adfa6",
        "timestamp": "2017-09-18T12:51:55.000Z",
        "campaignId": "d545b1e1-8f97-4ae4-a164-1b4a4a87bc07",
        "unavailable": false
    },
    "meta": {
      "etag": "3e8-SIMIS22pStVskqOe/o51Wzx9bbk",
      "created": "2017-09-18T15:20:58.865Z",
      "modified": "2017-09-18T15:20:58.865Z",
      "resource": "interactions",
      "createdBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
      "isDeleted": false,
      "modifiedBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c"
    },
    "customerId": "15ecebe1-e92c-4d8e-893b-e961be3f482a",
    "securityGroupId": "f32cdf73-e257-44c9-8e70-3235952962a0"
  },
  {
    "id": "01c9e50f-43b0-4033-9ef6-db49c1c51e3a",
    "data": {
      "listId": "d276761e-54cb-492b-be7a-3a257dad5903",
      "survey": {
        "surveyId": "85a638fe-63bf-4410-a90f-77a746487298",
        "responses": {
          "461a29dd-5d9c-4c6f-b13a-954b00db4c59": {
            "fields": {"available": "true"},
            "questionId": "461a29dd-5d9c-4c6f-b13a-954b00db4c59"
          },
          "53ac8a4e-9f4a-4349-a467-b639ca4fa1d3": {
            "fields": {"likeness": "true"},
            "questionId": "53ac8a4e-9f4a-4349-a467-b639ca4fa1d3"
          },
          "9ab4a264-47a7-45c8-be5f-6c454f665f45": {
            "fields": {"newphonenumberblabla": ""},
            "questionId": "9ab4a264-47a7-45c8-be5f-6c454f665f45"
          },
          "a49bb7e7-cc97-4c29-bd11-48e62d9751d8": {
            "fields": {"doglikeness": "true"},
            "questionId": "a49bb7e7-cc97-4c29-bd11-48e62d9751d8"
          }
        }
      },
      "distance": 4809.8449,
      "location": {
        "lat": -21.2198655,
        "lng": -47.8306027,
        "confidence": 0
      },
      "contactId": "6a43779f-94a8-450c-8ec9-d8c7dfc9ea6d",
      "timestamp": "2018-04-26T12:31:49.000Z",
      "campaignId": "bf374a20-37c0-4ca0-9e0b-b97cc42b0dfb",
      "successful": true,
      "walklistId": "237d47ad-d882-4abb-862c-19878f8423c7",
      "unavailable": false
      },
      "meta": {
        "etag": "540-xz3Ey5PC9Cz8tPAUCDecQFJjs8c",
        "created": "2018-04-26T15:31:48.763Z",
        "modified": "2018-04-26T15:31:48.763Z",
        "resource": "interactions",
        "createdBy": "20ebe78a-541b-42be-8800-cd7bd37054b4",
        "isDeleted": false,
        "modifiedBy": "20ebe78a-541b-42be-8800-cd7bd37054b4"
      },
      "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
      "securityGroupId": "7e4bc876-2c98-4674-9c37-bdbd52c90eb7"
    }
  ],
"meta": {}
}
```

Obtains the latest interactions for an organization's canvassers.

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
organizationId | true | Unique identifier of the organization.
startDate | true | Date after which interactions have occurred. 
endDate | true | Date before which interactions have occurred. 