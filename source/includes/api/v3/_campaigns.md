# Campaigns

## The Campaign object

```json
{
  "id": "f2636525-36d7-439c-924d-a2aaf3848716",
  "data": {
    "name": "My Campaign",
    "lists": [
      {
        "type": "high-priority",
        "listId": "ffd8bd17-eafc-45ec-a975-23ecda1fa2e6"
      },
      {
        "type": "normal",
        "listId": "d276761e-54cb-492b-be7a-3a257dad5903"
      },
      {
        "type": "do-not-knock",
        "listId": "770f0e3e-4351-4f4c-85f5-484201d1de94"
      },
      {
        "listId": "887ad4c6-93d8-4d9e-bcf6-72a188751d23"
      },
    ],
    "fields": [
      [
        {
          "path": "/data/profile/location/formatted",
          "type": "field"
        },
        {
          "path": "/data/profile/name/anglican/middlename",
          "type": "field"
        },
        {
          "path": "/data/profile/location/streetAddress/route",
          "type": "field"
        },
      ],
      [
        {
          "path": "/data/profile/name/anglican/title",
          "type": "field"
        },
        {
          "path": "/data/profile/name/anglican/given",
          "type": "field"
        },
        {
          "type": "separator",
          "value": ","
        },
        {
          "path": "/data/profile/location/statoid01/abbr",
          "type": "field"
        }
      ],
    ],
    "status": "started",
    "description": "test",
    "organizationId": "118d0436-4243-4810-94e9-13713fdfa31c"
  },
  "meta": {
    "created": "2017-12-19T16:24:59.992Z",
    "modified": "2018-09-18T14:26:03.243Z",
    "resource": "campaigns",
    "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
    "isDeleted": false,
    "modifiedBy": "20ebe78a-541b-42be-8800-cd7bd37054b4",
    "etag": "4ad-oh4PUy35/GfsofxZMU6gEGZq/hE"
  },
  "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
  "securityGroupId": "7e4bc876-2c98-4674-9c37-bdbd52c90eb7",
  "ended": true
}
```

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Unique identifier for the object.
customerId | true | Customer this resource belongs to.
securityGroupId | true | Security group of this resource.
data | true | Campaign data.

### data

Attribute | Required? | Description
--------- | --------- | -----------
name | true | Name of the Campaign.
lists | false | Array of lists of contacts associated with the campaign. [details](#data-lists)
fields | false | Information available to a canvasser about the contact on the mobile app. [details](#data-fields)
status | true | Current status of this campaign. Can be `pending`, `started` or `complete`.
description | false | Description of the campaign.
organizationId | true | Organization indentifier that this campaign belongs to.
ended | false | Timestamp of when the campaign was ended.

### data/lists

Attribute | Required? | Description
--------- | --------- | -----------
listId | true | List identifier of a list of contacts.
type | false | Priority of the list. Can be `do-not-knock`, `high-priority` or `normal`.

### data/fields

Contains an array that represents each line of the displayed values to the canvassers on the mobile app.
Each value of this array can be a `field` or a `separator`.
A `field` is an attribute of the contact.
A `separator` is a string value used to separate fields.

#### data/fields/field
Attribute | Required? | Description
--------- | --------- | -----------
type | true | Field type. Can be `field` or `separator`.
path | true | Path of a contact attribute.

#### data/fields/separator
Attribute | Required? | Description
--------- | --------- | -----------
type | true | Field type. Can be `field` or `separator`.
value | true | String value used to separate other fields.

### meta

[See documentation](#metadata-object).

## Create a campaign

> Example Request

```
http
POST /v1/campaigns HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}

  {
    "data": {
      "status": "started",
      "organizationId": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319",
      "name": "My Campaign",
      "description": "My Campaign Description"
    }
  }
```

> Example Response

```json
{
  "id": "f2636525-36d7-439c-924d-a2aaf3848716",
  "data": {
    "name": "My Campaign",
    "fields": [
      [
        {
          "path": "/data/profile/name/anglican/title",
          "type": "field"
        },
        {
          "path": "/data/profile/name/anglican/given",
          "type": "field"
        },
        {
          "path": "/data/profile/name/anglican/surname",
          "type": "field"
        },
        {
          "path": "/data/profile/name/anglican/suffix",
          "type": "field"
        }
      ],
      [
        {
          "path": "/data/profile/age",
          "type": "field"
        },
        {
          "type": "separator",
          "value": ","
        },
        {
          "path": "/data/profile/gender",
          "type": "field"
        }
      ],
      [
        {
        "path": "/data/notes",
        "type": "field"
        }
      ]
    ],
    "status": "started",
    "description": "My Campaign Description",
    "organizationId": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319"
  },
  "meta": {
    "etag": "3bf-MM03Q4w6jFS3ZUJ/3DBUV4M27Ow",
    "created": "2018-09-18T20:12:46.771Z",
    "modified": "2018-09-18T20:12:46.771Z",
    "resource": "campaigns",
    "createdBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
    "isDeleted": false,
    "modifiedBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3"
  },
  "customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466",
  "securityGroupId": "3453b386-60b5-4e58-b7f6-46b4977791ad"
}
```

Creates a new campaign.

<aside class="warning">
You must create a Default Survey and a Default Target for new campaigns.
Check Surveys and Segments documentations.
</aside>

### HTTP Request

`POST https://api.beta.polisapp.com/v1/campaigns`

## Retrieve a campaign

> Example Request

```http
GET /v1/campaigns/f2636525-36d7-439c-924d-a2aaf3848716 HTTP/1.1
Host: api.beta.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "id": "f2636525-36d7-439c-924d-a2aaf3848716",
  "data": {
    "name": "My Campaign",
    "lists": [
      {
        "type": "high-priority",
        "listId": "ffd8bd17-eafc-45ec-a975-23ecda1fa2e6"
      },
      {
        "type": "normal",
        "listId": "d276761e-54cb-492b-be7a-3a257dad5903"
      },
      {
        "listId": "770f0e3e-4351-4f4c-85f5-484201d1de94"
      },
      {
        "listId": "887ad4c6-93d8-4d9e-bcf6-72a188751d23"
      },
      {
        "listId": "fd1cc88a-d040-4d0e-81ac-e81028fccfcd"
      }
    ],
    "fields": [
      [
        {
          "path": "/data/profile/location/formatted",
          "type": "field"
        },
        {
          "path": "/data/profile/name/anglican/middlename",
          "type": "field"
        },
        {
          "path": "/data/profile/location/streetAddress/route",
          "type": "field"
        },
      ],
      [
        {
          "path": "/data/profile/name/anglican/title",
          "type": "field"
        },
        {
          "path": "/data/profile/name/anglican/given",
          "type": "field"
        },
        {
          "path": "/data/profile/location/statoid01/abbr",
          "type": "field"
        }
      ],
    ],
    "status": "started",
    "description": "test",
    "organizationId": "118d0436-4243-4810-94e9-13713fdfa31c"
  },
  "meta": {
    "created": "2017-12-19T16:24:59.992Z",
    "modified": "2018-09-18T14:26:03.243Z",
    "resource": "campaigns",
    "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
    "isDeleted": false,
    "modifiedBy": "20ebe78a-541b-42be-8800-cd7bd37054b4",
    "etag": "4ad-oh4PUy35/GfsofxZMU6gEGZq/hE"
  },
  "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
  "securityGroupId": "7e4bc876-2c98-4674-9c37-bdbd52c90eb7",
  "ended": true
}
```

Obtains a single campaign object by ID.

### HTTP Request

`GET https://api.beta.polisapp.com/v1/campaigns/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | Unique identifier of the campaign.

## Update a campaign

> Example Request

```http
PATCH /v1/campaigns/f2636525-36d7-439c-924d-a2aaf3848716 HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
ETag: {etag_value}
{
  "data": [
    {
      "op": "replace",
      "path": "/name",
      "value": "My Campaign Changed"
    },
    {
      "op": "replace",
      "path": "/description",
      "value": "My Campaign Description"
    },
    {
      "op": "replace",
      "path": "/lists",
      "value": [
        {
          "listId": "ea19c3ab-3526-4709-b027-3e3c1d1851b2"
        }
      ]
    }
  ]
}
```

> Example Response

```json
{
  "id": "f2636525-36d7-439c-924d-a2aaf3848716",
  "data": {
    "name": "My Campaign Changed",
    "lists": [
      {
        "listId": "ea19c3ab-3526-4709-b027-3e3c1d1851b2"
      }
    ],
    "fields": [
      [
        {
          "path": "/data/profile/name/anglican/title",
          "type": "field"
        },
        {
          "path": "/data/profile/name/anglican/given",
          "type": "field"
        },
        {
          "path": "/data/profile/name/anglican/surname",
          "type": "field"
        },
        {
          "path": "/data/profile/name/anglican/suffix",
          "type": "field"
        }
      ],
      [
        {
          "path": "/data/profile/age",
          "type": "field"
        },
        {
          "type": "separator",
          "value": ","
        },
        {
          "path": "/data/profile/gender",
          "type": "field"
        }
      ],
      [
        {
          "path": "/data/notes",
          "type": "field"
        }
      ]
    ],
    "status": "started",
    "description": "My Campaign Description",
    "organizationId": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319"
  },
  "meta": {
    "created": "2018-09-18T20:12:46.771Z",
    "modified": "2018-09-18T20:26:20.585Z",
    "resource": "campaigns",
    "createdBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
    "isDeleted": false,
    "modifiedBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
    "etag": "3f9-GfHHOhHMrNV4MJZqHKqzmXVNI10"
  },
  "customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466",
  "securityGroupId": "3453b386-60b5-4e58-b7f6-46b4977791ad"
}
```
<aside class="notice">
You can only patch attributes inside <b>data</b> key.
</aside>

[RFC 6902 - JavaScript Object Notation (JSON) Patch](https://tools.ietf.org/html/rfc6902)

### HTTP Request

`PATCH https://api.beta.polisapp.com/v1/campaigns/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | Unique identifier of the campaign.

## Delete a campaign

> Example Request

```http
DELETE https://api.beta.polisapp.com/v1/campaigns/f2636525-36d7-439c-924d-a2aaf3848716
Host: api.beta.polisapp.com
Authorization: Bearer {access_token}
ETag: {etag_value}
```

### HTTP Request
`DELETE https://api.beta.polisapp.com/v1/campaigns/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | Unique identifier of the campaign.


## Get many campaigns


> Example Request

```http
GET /v1/campaigns?filter=%2Fdata%2ForganizationId%20eq%20%22eb4dfe83-f1fd-46dd-a69d-b7cf7b566319%22%20and%20%2Fdata%2Fstatus%20eq%20%22complete%22&limit=10&skip=0&sort=%5B%22data%2Fname%22%2C%22ASC%22%5D HTTP/1.1
Host: api.beta.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "data": [
    {
      "id": "a2167f5e-2529-48d1-a1e8-b008a8f0c546",
      "data": {
        "name": "First Campaign",
        "lists": [
          {
            "type": "high-priority",
            "listId": "b701a705-2dec-4b43-a9dc-eefb9926de64"
          },
          {
            "listId": "7310c2b1-b49f-4aeb-bfa4-8963e397fbb1"
          }
        ],
        "fields": [
          [
            {
              "path": "/data/profile/name/anglican/title",
              "type": "field"
            },
            {
              "path": "/data/profile/name/anglican/given",
              "type": "field"
            },
            {
              "path": "/data/profile/name/anglican/surname",
              "type": "field"
            },
            {
              "path": "/data/profile/name/anglican/suffix",
              "type": "field"
            }
          ],
          [
            {
              "path": "/data/profile/age",
              "type": "field"
            },
            {
              "type": "separator",
              "value": ","
            },
            {
              "path": "/data/profile/gender",
              "type": "field"
            }
          ],
          [
            {
              "path": "/data/notes",
              "type": "field"
            }
          ]
        ],
        "status": "complete",
        "description": "First Campaign Description",
        "organizationId": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319"
      },
      "meta": {
        "created": "2018-08-29T17:50:03.623Z",
        "modified": "2018-09-18T19:31:25.307Z",
        "resource": "campaigns",
        "createdBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
        "isDeleted": false,
        "modifiedBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
        "etag": "439-wpTJLSrdLG9ldsF+aFeVJweEXdI"
      },
      "customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466",
      "securityGroupId": "3453b386-60b5-4e58-b7f6-46b4977791ad"
    },
    {
      "id": "4f1e6e72-630f-4ff2-b089-4359f4b2a8de",
      "data": {
        "name": "Second Campaign",
        "lists": [
          {
            "listId": "ea19c3ab-3526-4709-b027-3e3c1d1851b2"
          }
        ],
        "fields": [
          [
            {
              "path": "/data/profile/name/anglican/title",
              "type": "field"
            },
            {
              "path": "/data/profile/name/anglican/given",
              "type": "field"
            },
            {
              "path": "/data/profile/name/anglican/surname",
              "type": "field"
            },
            {
              "path": "/data/profile/name/anglican/suffix",
              "type": "field"
            }
          ],
          [
            {
              "path": "/data/profile/age",
              "type": "field"
            },
            {
              "type": "separator",
              "value": ","
            },
            {
              "path": "/data/profile/gender",
              "type": "field"
            }
          ],
          [
            {
              "path": "/data/notes",
              "type": "field"
            }
          ]
        ],
        "status": "complete",
        "description": "Second Campaign Description",
        "organizationId": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319"
      },
      "meta": {
        "created": "2018-09-18T20:12:46.771Z",
        "modified": "2018-09-18T20:39:11.309Z",
        "resource": "campaigns",
        "createdBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
        "isDeleted": false,
        "modifiedBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
        "etag": "3fa-SPGxUzCOevknzfLhaMU2ZJ7Ofjo"
      },
      "customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466",
      "securityGroupId": "3453b386-60b5-4e58-b7f6-46b4977791ad"
    }
  ],
  "meta": {}
}
```

### HTTP Request
`GET https://api.beta.polisapp.com/v1/campaigns?filter={filter}&limit={limit}&skip={skip}&sort={sort}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
fiter | false | Query to filter data. [See documentation](#filters).
limit | true | Limit results returned. Useful for pagination.
skip | true | Data offset index. Useful for pagination.
sort | true | Sort column. Ex.: `["id","ASC"]`

Filter Example: `/data/organizationId eq "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319" and /data/status eq "complete"`


## Get contact household campaign record

Get the contact household campaign document associated with a contact ,household and a campaign. This document has 
the status information related to the contact household in a campaign. This information is equivalent to the contact's
status if you used the v1 contact endpoints.
> Example Request

```http
GET /v1/campaigns/c92162c6-f604-4caf-a964-d668d8bf67c8/contacts/cc20ab46-6233-491d-82ac-94c7ba6a8997/households/e50be735-cfe3-49db-8fca-e03f630d4a7e/status HTTP/1.1
Host: api.beta.polisapp.com
Authorization: Bearer {access_token}
``` 

> Example Response

```json
{
    "id": "00001820-1329-490c-b07c-2071c29329de",
    "data": {
        "contacted": false,
        "campaignId": "c92162c6-f604-4caf-a964-d668d8bf67c8",
        "successful": false,
        "reservation": {
            "reserved": false
        },
        "availability": {
            "available": false,
            "unavailableReason": null
        },
        "contactHouseholdId": "b66e4452-5fcd-4b79-bb1c-068ed7353192",
        "state": "not-contacted-normal",
        "statusId": "54aa7cef-877a-44ec-b2c5-442b43f5d758"
    },
    "meta": {
        "etag": "295-1n/IqPXKKnZp0KmvaPoq7YWAIUI",
        "created": "2019-09-05T20:54:33.580Z",
        "modified": "2019-09-05T20:54:33.580Z",
        "resource": "contact-household-campaigns",
        "createdBy": "f7db3e84-e0f0-4b8b-94b2-2e5675ddddaa",
        "isDeleted": false,
        "modifiedBy": "f7db3e84-e0f0-4b8b-94b2-2e5675ddddaa"
    },
    "customerId": "bd4b51e6-804c-497d-8f60-cf7b12c56e06",
    "securityGroupId": "2e61dbbc-02f2-4084-b36e-c3d1d39ed495"
}
```
### HTTP Request

`GET https://api.beta.polisapp.com/v1/campaigns/{campaignId}/contacts/{contactId}/households/{householdId}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
campaignId | true | The identifier of a campaign.
contactId | true | The identifier of a contact.
householdId | true | The identifier of a household.

## Update a contact household campaign record

> Example Request

```http
PATCH /v1/campaigns/c92162c6-f604-4caf-a964-d668d8bf67c8/contacts/cc20ab46-6233-491d-82ac-94c7ba6a8997/households/e50be735-cfe3-49db-8fca-e03f630d4a7e/status HTTP/1.1
Host: api.beta.polisapp.com
Authorization: Bearer {access_token}
etag {etag value}
{
    "data": [
        {
        	 "op": "replace", "path": "/statusId", "value": "53a18d44-54f0-400e-b9cd-dd0bd32ae904" 
        },
        {
        	"op": "replace", "path" : "/state", "value": "contacted-unavailable-not-home"
        },
        {
        	"op": "replace", "path" : "/contacted", "value": true
        }
    ]
}
```

> Example Response

```json
{
    "id": "00001820-1329-490c-b07c-2071c29329de",
    "data": {
        "state": "contacted-unavailable-not-home",
        "statusId": "53a18d44-54f0-400e-b9cd-dd0bd32ae904",
        "contacted": true,
        "campaignId": "c92162c6-f604-4caf-a964-d668d8bf67c8",
        "successful": false,
        "reservation": {
            "reserved": false
        },
        "availability": {
            "available": false,
            "unavailableReason": null
        },
        "contactHouseholdId": "b66e4452-5fcd-4b79-bb1c-068ed7353192"
    },
    "meta": {
        "created": "2019-09-05T20:54:33.580Z",
        "modified": "2020-05-26T21:07:31.802Z",
        "resource": "contact-household-campaigns",
        "createdBy": "f7db3e84-e0f0-4b8b-94b2-2e5675ddddaa",
        "isDeleted": false,
        "modifiedBy": "ccce05b9-ddad-44e0-bc4e-7e9fe37edb4a",
        "etag": "2e5-DCRtzEum5wZhZGFCH6Spy7M8nUE"
    },
    "customerId": "bd4b51e6-804c-497d-8f60-cf7b12c56e06",
    "securityGroupId": "2e61dbbc-02f2-4084-b36e-c3d1d39ed495"
}
```

### HTTP Request

`PATCH https://api.beta.polisapp.com/v1/campaigns/{campaignId}/contacts/{contactId}/households/{householdId}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
campaignId | true | The identifier of a campaign.
contactId | true | The identifier of a contact.
householdId | true | The identifier of a household.

## Update or create new contact household campaign record

> Example Request

```http
PUT /v1/campaigns/c92162c6-f604-4caf-a964-d668d8bf67c8/contacts/cc20ab46-6233-491d-82ac-94c7ba6a8997/households/e50be735-cfe3-49db-8fca-e03f630d4a7e/status HTTP/1.1
Host: api.beta.polisapp.com
Authorization: Bearer {access_token}
{
    "data": {
    	"availability": {
    		"available": false,
    		"unavailableReason": "Not Home"
    	}
    }
        
}
```

> Example Response

```json
{
    "id": "00001820-1329-490c-b07c-2071c29329de",
    "data": {
        "contacted": false,
        "campaignId": "c92162c6-f604-4caf-a964-d668d8bf67c8",
        "successful": false,
        "reservation": {
            "reserved": false,
            "walklistId": null
        },
        "availability": {
            "available": false,
            "unavailableReason": "Not Home"
        },
        "contactHouseholdId": "b66e4452-5fcd-4b79-bb1c-068ed7353192"
    },
    "meta": {
        "created": "2019-09-05T20:54:33.580Z",
        "modified": "2020-05-26T22:05:03.442Z",
        "resource": "contact-household-campaigns",
        "createdBy": "f7db3e84-e0f0-4b8b-94b2-2e5675ddddaa",
        "isDeleted": false,
        "modifiedBy": "ccce05b9-ddad-44e0-bc4e-7e9fe37edb4a",
        "etag": "2a3-NWxUWrbVIRmWaHKOPWIcYA5G0jg"
    },
    "customerId": "bd4b51e6-804c-497d-8f60-cf7b12c56e06",
    "securityGroupId": "2e61dbbc-02f2-4084-b36e-c3d1d39ed495"
}
```

### HTTP Request

`PUT https://api.beta.polisapp.com/v1/campaigns/{campaignId}/contacts/{contactId}/households/{householdId}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
campaignId | true | The identifier of a campaign.
contactId | true | The identifier of a contact.
householdId | true | The identifier of a household.
