# Lists

## The list object

```json
{
  "id": "8c57eca4-68c1-4e8b-a83d-e34284121e9d",
  "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
  "securityGroupId": "7e4bc876-2c98-4674-9c37-bdbd52c90eb7",
  "contactsCount": 298,
  "data": {
    "name": "List 1",
    "organizationId": "118d0436-4243-4810-94e9-13713fdfa31c"
  },
  "meta": {
    "created": "2017-12-19T15:58:43.150Z",
    "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
    "etag": "MTUxMzY5OTcwNzQ2OTE2ODY0MA==",
    "isDeleted": false,
    "modified": "2017-12-19T15:58:43.150Z",
    "modifiedBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
    "resource": "lists"
  }
}
```

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Unique identifier for the object.
customerId | true | Customer this resource belongs to.
securityGroupId | true | Security group of this resource.
contactsCount | false | (Read only field) Total number of contacts within this list.

### data

Attribute | Required? | Description
--------- | --------- | -----------
name | true | List name.
organizationId | true | Organization owner of this list.

### meta

[See documentation](#metadata-object).

## Create a list

> Example Request

```http
POST /v1/lists HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}

{
  "data": {
    "name": "New List",
    "organizationId": "118d0436-4243-4810-94e9-13713fdfa31c"
  }
}
```

> Example Response

```json
{
  "id": "10b16a4f-32df-44c6-8946-bac870668f94",
  "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
  "securityGroupId": "7e4bc876-2c98-4674-9c37-bdbd52c90eb7",
  "data": {
    "name": "New List",
    "organizationId": "118d0436-4243-4810-94e9-13713fdfa31c"
  },
  "meta": {
    "etag": "MTUxNjE0NzUwOTQ2ODY1OTcxMg==",
    "created": "2018-01-16T23:53:59.758Z",
    "modified": "2018-01-16T23:53:59.758Z",
    "isDeleted": false,
    "resource": "lists",
    "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
    "modifiedBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851"
  }
}
```

Creates a new list in an organization.

### HTTP Request

`POST https://api.polisapp.com/v1/lists`


## Retrieve a list

> Example Request

```http
GET /v1/lists/8c57eca4-68c1-4e8b-a83d-e34284121e9d HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "id": "8c57eca4-68c1-4e8b-a83d-e34284121e9d",
  "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
  "securityGroupId": "7e4bc876-2c98-4674-9c37-bdbd52c90eb7",
  "contactsCount": 298,
  "data": {
    "name": "List 1",
    "organizationId": "118d0436-4243-4810-94e9-13713fdfa31c"
  },
  "meta": {
    "created": "2017-12-19T15:58:43.150Z",
    "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
    "etag": "MTUxMzY5OTcwNzQ2OTE2ODY0MA==",
    "isDeleted": false,
    "modified": "2017-12-19T15:58:43.150Z",
    "modifiedBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
    "resource": "lists"
  }
}
```

Obtains a single list object by ID.

### HTTP Request

`GET https://api.polisapp.com/v1/lists/{listId}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
listId | true | Unique identifier of the list.

## Update a list

> Example Request

```http
PATCH /v1/lists/8c57eca4-68c1-4e8b-a83d-e34284121e9d HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}

{
  "data": [
    {"op":"replace", "path":"/name", "value": "New List Name"}
  ]
}
```

> Example Response

```json
{
  "id": "8c57eca4-68c1-4e8b-a83d-e34284121e9d",
  "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
  "securityGroupId": "7e4bc876-2c98-4674-9c37-bdbd52c90eb7",
  "data": {
    "name": "New List Name",
    "organizationId": "118d0436-4243-4810-94e9-13713fdfa31c"
  },
  "meta": {
    "created": "2017-12-19T15:58:43.150Z",
    "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
    "etag": "MTUxNjE0ODQ5MjI2MDI3ODI3Mg==",
    "isDeleted": false,
    "modified": "2018-01-17T00:10:22.523Z",
    "modifiedBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
    "resource": "lists"
  }
}
```
<aside class="notice">
You can only patch attributes inside <b>data</b> key.
</aside>

[RFC 6902 - JavaScript Object Notation (JSON) Patch](https://tools.ietf.org/html/rfc6902)

### HTTP Request

`PATCH https://api.polisapp.com/v1/lists/{listId}`



## Delete a list

## Get all lists

> Example Request

```http
GET /v1/lists?filter=/data/organizationId+eq+"118d0436-4243-4810-94e9-13713fdfa31c"&limit=100&skip=0&sort=["data/name","ASC"] HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "data": [
    {
      "id": "8c57eca4-68c1-4e8b-a83d-e34284121e9d",
      "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
      "securityGroupId": "7e4bc876-2c98-4674-9c37-bdbd52c90eb7",
      "contactsCount": 298,
      "data": {
        "name": "List 1",
        "organizationId": "118d0436-4243-4810-94e9-13713fdfa31c"
      },
      "meta": {
        "created": "2017-12-19T15:58:43.150Z",
        "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
        "etag": "MTUxMzY5OTcwNzQ2OTE2ODY0MA==",
        "isDeleted": false,
        "modified": "2017-12-19T15:58:43.150Z",
        "modifiedBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
        "resource": "lists"
      }
    }
  ]
}
```

Retrieves a list of lists filtered by a criteria.

### HTTP Request

`GET https://api.polisapp.com/v1/lists?filter={filter}&limit={limit}&skip={skip}&sort={sort}`

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
* `/data/organizationId`
* `/data/name`

### Common filters queries

Filter by organization:

`/data/organizationId eq "{organizationId}"`
