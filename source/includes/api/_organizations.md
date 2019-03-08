# Organizations

## The organization object

```json
{
  "id": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319",
  "data": {
    "name": "Organization Test",
    "token": "FZsvUJCzCS",
    "parentId": "28a699ee-342d-4bae-af37-c07924c0e23e",
    "description": "Organization Test",
    "discoverable": false,
    "editOldTurfs": true,
    "viewUnassignedData": true,
    "requireSignUpConfirmation": true
  },
  "meta": {
    "etag": "27d-wlAWROPGf7xiGd2BZNuoSaeMLlE",
    "created": "2018-09-18T21:10:45.619Z",
    "modified": "2018-09-18T21:10:45.619Z",
    "resource": "organizations",
    "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
    "isDeleted": false,
    "modifiedBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851"
  },
  "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
  "securityGroupId": "8e9363ba-215c-40cb-822f-639e6b957472"
}
```

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Unique identifier for the object.
customerId | true | Customer this resource belongs to.
securityGroupId | true | Security group of this resource.
data | true | Organization data.

### data

Attribute | Required? | Description
--------- | --------- | -----------
name | true | Name of the organization.
description | false | Descriptions of the role.
permissions | false | Array of permissions allowed to that role.
token | false | Token used to join an organization.
parentId | false | Id of the parent Organization.
discoverable | false | Defines if the organization is public. Default `false`.
editOldTurfs | false | Enables editting old turfs. Default `true`.
viewUnassignedData | false | Enables canvassers to view unassigned data. Default `true`.
requireSignUpConfirmation | false | Joining organization by link, if `false`, doesn't need to be approved by a manager. Default `true`.

### meta

[See documentation](#metadata-object).

## Retrieve an organization

> Example Request

```http
GET /v1/organizations/eb4dfe83-f1fd-46dd-a69d-b7cf7b566319 HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "id": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319",
  "data": {
    "name": "Organization Test",
    "token": "FZsvUJCzCS",
    "parentId": "28a699ee-342d-4bae-af37-c07924c0e23e",
    "description": "Organization Test",
    "discoverable": false,
    "editOldTurfs": true,
    "viewUnassignedData": true,
    "requireSignUpConfirmation": true
  },
  "meta": {
    "etag": "27d-wlAWROPGf7xiGd2BZNuoSaeMLlE",
    "created": "2018-09-18T21:10:45.619Z",
    "modified": "2018-09-18T21:10:45.619Z",
    "resource": "organizations",
    "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
    "isDeleted": false,
    "modifiedBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851"
  },
  "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
  "securityGroupId": "8e9363ba-215c-40cb-822f-639e6b957472"
}
```

### HTTP Request
`GET https://api.polisapp.com/v1/organizations/{id}`

## Get many organizations

> Example Request

```http
GET /v1/organizations?filter=%2FcustomerId%20eq%20%22f51b86dd-aaba-485e-b14d-65cbea28b8e4%22&limit=100&skip=0&sort=%5B%22data%2Fname%22%2C%22ASC%22%5D HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "data": [
    {
      "id": "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319",
      "data": {
        "name": "Org 1",
        "token": "bMaCCFePb1",
        "parentId": "28a699ee-342d-4bae-af37-c07924c0e23e",
        "description": "org 1",
        "discoverable": false,
        "editOldTurfs": true,
        "viewUnassignedData": true,
        "requireSignUpConfirmation": false
      },
      "meta": {
        "created": "2018-03-19T18:10:17.034Z",
        "modified": "2018-09-07T15:28:45.555Z",
        "resource": "organizations",
        "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
        "isDeleted": false,
        "modifiedBy": "20ebe78a-541b-42be-8800-cd7bd37054b4",
        "etag": "25a-u7VJCxnC5OEpb9j3lYzrEQ33v6E"
      },
      "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
      "securityGroupId": "5595590b-2e06-4177-99ae-3133f811df62"
    },
    {
      "id": "23efbafa-6375-476d-814e-4cdc71a02ca8",
      "data": {
        "name": "Org 2",
        "token": "FZsvUJCzCS",
        "parentId": "28a699ee-342d-4bae-af37-c07924c0e23e",
        "description": "org 2",
        "discoverable": false,
        "editOldTurfs": true,
        "viewUnassignedData": true,
        "requireSignUpConfirmation": true
      },
      "meta": {
        "etag": "27d-wlAWROPGf7xiGd2BZNuoSaeMLlE",
        "created": "2018-09-18T21:10:45.619Z",
        "modified": "2018-09-18T21:10:45.619Z",
        "resource": "organizations",
        "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
        "isDeleted": false,
        "modifiedBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851"
      },
      "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
      "securityGroupId": "8e9363ba-215c-40cb-822f-639e6b957472"
    }
  ],
  "meta": {}
}

```

### HTTP Request
`GET https://api.polisapp.com/v1/organizations?filter={filter}&limit={limit}&skip={skip}&sort={sort}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
fiter | false | Query to filter data. [See documentation](#filters).
limit | true | Limit results returned. Useful for pagination.
skip | true | Data offset index. Useful for pagination.
sort | true | Sort column. Ex.: `["id","ASC"]`

Filter Example: `/customerId eq "f51b86dd-aaba-485e-b14d-65cbea28b8e4"`
