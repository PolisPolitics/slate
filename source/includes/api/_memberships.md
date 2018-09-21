# Memberships

## The membership object

```json
{
  "data": [
    {
      "id": "c10cbd70-5a2f-440d-9e0d-7b9ea23daf3b",
      "data": {
        "roleId": "187e61d8-7571-46c6-a384-19aa700cf6af",
        "status": "active",
        "userId": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
        "notifications": {
          "dailySummary": true
        },
        "organizationId": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319",
        "organization": {
          "name": "user test",
          "token": "S3VIZA24Hp",
          "discoverable": true,
          "editOldTurfs": true,
          "viewUnassignedData": true,
          "requireSignUpConfirmation": true
        },
        "user": {
          "email": "usert@test.com",
          "status": "active",
          "privacy": {
            "publicInfo": [
              "email"
            ]
          },
          "profile": {
            "name": {
              "anglican": {
                "given": "user",
                "surname": "test"
              }
            },
            "phone": [],
            "birthdate": "1993-12-12T00:00:00.000Z"
          }
        }
      },
      "meta": {
        "etag": "263-3CJDoL9rmOq8CUidGEfKccJE4Eg",
        "created": "2018-08-29T17:49:22.075Z",
        "modified": "2018-08-29T17:49:22.075Z",
        "resource": "memberships",
        "createdBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
        "isDeleted": false,
        "modifiedBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c"
      },
      "customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466",
      "securityGroupId": "3453b386-60b5-4e58-b7f6-46b4977791ad"
    }
  ],
  "meta": {}
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
organizationId | true | Organization indentifier that this membership belongs to.
userId | true | User indentifier of this membership. On Get the the object for `user` is retrieved instead of the id.
roleId | true | Role indentifier of this membership.
status | false | Current status of this membership. Can be `active`, `disabled`, `unconfirmed` or `invited`. By default is set to `unconfirmed`.
notifications | false | Object with notification types. Default `{dailySummary: true}`.

#### data/notifications

Attribute | Required? | Description
--------- | --------- | -----------
dailySummary | false | If `true` the membership will receive a daily summary about the campaign on the e-mail. Default `true`.

### meta

[See documentation](#metadata-object).

## Create a membership

> Example Request

```
http
POST /memberships HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}

{
  "data": {
    "organizationId": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319",
    "userId": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
    "roleId": "187e61d8-7571-46c6-a384-19aa700cf6af"
  },
  "customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466"
}
```

> Example Response

```json
{
  "id": "ec15c251-01d9-4146-8957-68debc821588",
  "data": {
    "roleId": "187e61d8-7571-46c6-a384-19aa700cf6af",
    "status": "unconfirmed",
    "userId": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
    "notifications": {
      "dailySummary": true
    },
    "organizationId": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319"
  },
  "meta": {
    "etag": "268-77iKRUrM3zlu3FHeZ1lJ5S9XJoM",
    "created": "2018-09-21T17:07:26.676Z",
    "modified": "2018-09-21T17:07:26.676Z",
    "resource": "memberships",
    "createdBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
    "isDeleted": false,
    "modifiedBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c"
  },
  "customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466",
  "securityGroupId": "3453b386-60b5-4e58-b7f6-46b4977791ad"
}
```

Creates a new membership.

<aside class="warning">
You must create a User, get a Role id and an Organization id before creating a new membership.
Check Users, Roles and Organizations documentation.
</aside>

### HTTP Request

`POST https://api.polisapp.com/memberships`

## Retrieve a membership

> Example Request

```http
GET /memberships/c10cbd70-5a2f-440d-9e0d-7b9ea23daf3b HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "data": [
    {
      "id": "c10cbd70-5a2f-440d-9e0d-7b9ea23daf3b",
      "data": {
        "roleId": "187e61d8-7571-46c6-a384-19aa700cf6af",
        "status": "active",
        "userId": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
        "notifications": {
          "dailySummary": true
        },
        "organizationId": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319",
        "organization": {
          "name": "user test",
          "token": "S3VIZA24Hp",
          "discoverable": true,
          "editOldTurfs": true,
          "viewUnassignedData": true,
          "requireSignUpConfirmation": true
        },
        "user": {
          "email": "usert@test.com",
          "status": "active",
          "privacy": {
            "publicInfo": [
              "email"
            ]
          },
          "profile": {
            "name": {
              "anglican": {
                "given": "user",
                "surname": "test"
              }
            },
            "phone": [],
            "birthdate": "1993-12-12T00:00:00.000Z"
          }
        }
      },
      "meta": {
        "etag": "263-3CJDoL9rmOq8CUidGEfKccJE4Eg",
        "created": "2018-08-29T17:49:22.075Z",
        "modified": "2018-08-29T17:49:22.075Z",
        "resource": "memberships",
        "createdBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
        "isDeleted": false,
        "modifiedBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c"
      },
      "customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466",
      "securityGroupId": "3453b386-60b5-4e58-b7f6-46b4977791ad"
    }
  ],
  "meta": {}
}
```

Obtains a single membership object by ID.

### HTTP Request

`GET https://api.polisapp.com/memberships/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | Unique identifier of the membership.

## Update a membership

Updating membership status example.

> Example Request

```http
PATCH /membership/c10cbd70-5a2f-440d-9e0d-7b9ea23daf3b HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
ETag: {etag_value}
{
  "data": [
    {
      "op": "replace",
      "path": "/status",
      "value": "disabled"
    }
  ]
}
```

> Example Response

```json
{
  "id": "c10cbd70-5a2f-440d-9e0d-7b9ea23daf3b",
  "data": {
    "roleId": "187e61d8-7571-46c6-a384-19aa700cf6af",
    "status": "disabled",
    "userId": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
    "notifications": {
      "dailySummary": true
    },
    "organizationId": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319"
  },
  "meta": {
    "created": "2018-09-06T20:30:03.814Z",
    "modified": "2018-09-21T13:55:39.585Z",
    "resource": "memberships",
    "createdBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
    "isDeleted": false,
    "modifiedBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
    "etag": "259-9+Mx7Lrcv/isujI22nAW0qVaHx4"
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

`PATCH https://api.polisapp.com/memberships/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | Unique identifier of the membership.

## Update a membership role

> Example Request

```http
PATCH /membership/c10cbd70-5a2f-440d-9e0d-7b9ea23daf3b HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
ETag: {etag_value}
{
  "params": {
    "roleId": "187e61d8-7571-46c6-a384-19aa700cf6af",
    "action": "changeRole"
  },
  "data": []
}
```

> Example Response

```json
{
  "id": "c10cbd70-5a2f-440d-9e0d-7b9ea23daf3b",
  "data": {
    "roleId": "187e61d8-7571-46c6-a384-19aa700cf6af",
    "status": "active",
    "userId": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
    "notifications": {
      "dailySummary": true
    },
    "organizationId": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319"
  },
  "meta": {
    "created": "2018-09-06T20:30:03.814Z",
    "modified": "2018-09-21T13:55:39.585Z",
    "resource": "memberships",
    "createdBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
    "isDeleted": false,
    "modifiedBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
    "etag": "259-9+Mx7Lrcv/isujI22nAW0qVaHx4"
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

`PATCH https://api.polisapp.com/memberships/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | Unique identifier of the membership.

## Delete a membership

> Example Request

```http
DELETE https://api.polisapp.com/memberships/c10cbd70-5a2f-440d-9e0d-7b9ea23daf3b
Host: api.polisapp.com
Authorization: Bearer {access_token}
ETag: {etag_value}
```

### HTTP Request
`DELETE https://api.polisapp.com/memberships/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | Unique identifier of the membership.


## Get many memberships

> Example Request

```http
GET /memberships?filter=%2Fdata%2FuserId%20eq%20%2208f35132-7b4f-44d9-b212-6e5fad31aad3%22%20and%20%2Fdata%2Fstatus%20eq%20%22active%22&limit=9007199254740991&skip=0&sort=%5B%22id%22%2C%22ASC%22%5D HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "data": [
    {
      "id": "c10cbd70-5a2f-440d-9e0d-7b9ea23daf3b",
      "data": {
        "roleId": "187e61d8-7571-46c6-a384-19aa700cf6af",
        "status": "active",
        "userId": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
        "notifications": {
          "dailySummary": true
        },
        "organizationId": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319",
        "organization": {
          "name": "user test",
          "token": "S3VIZA24Hp",
          "discoverable": true,
          "editOldTurfs": true,
          "viewUnassignedData": true,
          "requireSignUpConfirmation": true
        },
        "user": {
          "email": "usert@test.com",
          "status": "active",
          "privacy": {
            "publicInfo": [
              "email"
            ]
          },
          "profile": {
            "name": {
              "anglican": {
                "given": "user",
                "surname": "test"
              }
            },
            "phone": [],
            "birthdate": "1993-12-12T00:00:00.000Z"
          }
        }
      },
      "meta": {
        "etag": "263-3CJDoL9rmOq8CUidGEfKccJE4Eg",
        "created": "2018-08-29T17:49:22.075Z",
        "modified": "2018-08-29T17:49:22.075Z",
        "resource": "memberships",
        "createdBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
        "isDeleted": false,
        "modifiedBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c"
      },
      "customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466",
      "securityGroupId": "3453b386-60b5-4e58-b7f6-46b4977791ad"
    }
  ],
  "meta": {}
}
```

### HTTP Request
`GET https://api.polisapp.com/memberships?filter={filter}&limit={limit}&skip={skip}&sort={sort}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
fiter | false | Query to filter data. [See documentation](#filters).
limit | true | Limit results returned. Useful for pagination.
skip | true | Data offset index. Useful for pagination.
sort | true | Sort column. Ex.: `["id","ASC"]`

Filter Example: `/data/userId eq "08f35132-7b4f-44d9-b212-6e5fad31aad3" and /data/status eq "active"`
