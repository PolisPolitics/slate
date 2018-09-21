# Roles

## The role object

```json
{
  "id": "d188e998-dee9-45a9-8f97-92a71f3cee9b",
  "data": {
    "name": "Canvasser",
    "description": "Canvasser",
    "permissions": [
      "read@authentications",
      "read@roles",
      "read@user-roles",
      "read@users",
      "read@customers",
      "modify@invitations",
      "read@invitations",
      "insert@memberships",
      "read@memberships",
      "insert@notifications-history",
      "read@organizations",
      "insert@organization-descendants",
      "read@organization-descendants",
      "insert@field-sets",
      "modify@field-sets",
      "read@field-sets",
      "insert@payments",
      "modify@payments",
      "read@campaigns",
      "modify@campaigns",
      "read@contacts",
      "insert@contacts",
      "modify@contacts",
      "insert@interactions",
      "modify@interactions",
      "read@interactions",
      "read@integrations",
      "read@lists",
      "insert@lists",
      "modify@lists",
      "read@segments",
      "read@surveys",
      "read@turfs",
      "read@turf-assignments",
      "read@walklists",
      "insert@walklists",
      "modify@walklists",
      "insert@walklist-share-requests",
      "modify@walklist-share-requests",
      "read@walklist-share-requests",
      "read@analytics::doors-knocked"
    ]
  },
  "meta": {
    "etag": "531-xSHEwJwswdDT3Qx0ikixl+ZBfzE",
    "created": "2017-08-18T18:52:19.556Z",
    "modified": "2017-08-18T18:52:19.556Z",
    "resource": "roles",
    "createdBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
    "isDeleted": false,
    "modifiedBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c"
  },
  "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
  "securityGroupId": "65ab5050-0942-4343-9ca2-866987a07f09"
}
```

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Unique identifier for the object.
customerId | true | Customer this resource belongs to.
securityGroupId | true | Security group of this resource.
data | true | Role data.

### data

Attribute | Required? | Description
--------- | --------- | -----------
name | true | Name of the role.
description | false | Descriptions of the role.
permissions | false | Array of permissions allowed to that role.

### meta

[See documentation](#metadata-object).

## Get many roles


> Example Request

```http
GET /roles?filter=%2FcustomerId%20eq%20%22f51b86dd-aaba-485e-b14d-65cbea28b8e4%22&limit=100&skip=0&sort=%5B%22data%2Fname%22%2C%22ASC%22%5D HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "data": [
    {
      "id": "d188e998-dee9-45a9-8f97-92a71f3cee9b",
      "data": {
        "name": "Canvasser",
        "description": "Canvasser",
        "permissions": [
          "read@authentications",
          "read@roles",
          "read@user-roles",
          "read@users",
          "read@customers",
          "modify@invitations",
          "read@invitations",
          "insert@memberships",
          "read@memberships",
          "insert@notifications-history",
          "read@organizations",
          "insert@organization-descendants",
          "read@organization-descendants",
          "insert@field-sets",
          "modify@field-sets",
          "read@field-sets",
          "insert@payments",
          "modify@payments",
          "read@campaigns",
          "modify@campaigns",
          "read@contacts",
          "insert@contacts",
          "modify@contacts",
          "insert@interactions",
          "modify@interactions",
          "read@interactions",
          "read@integrations",
          "read@lists",
          "insert@lists",
          "modify@lists",
          "read@segments",
          "read@surveys",
          "read@turfs",
          "read@turf-assignments",
          "read@walklists",
          "insert@walklists",
          "modify@walklists",
          "insert@walklist-share-requests",
          "modify@walklist-share-requests",
          "read@walklist-share-requests",
          "read@analytics::doors-knocked"
        ]
      },
      "meta": {
        "etag": "531-xSHEwJwswdDT3Qx0ikixl+ZBfzE",
        "created": "2017-08-18T18:52:19.556Z",
        "modified": "2017-08-18T18:52:19.556Z",
        "resource": "roles",
        "createdBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
        "isDeleted": false,
        "modifiedBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c"
      },
      "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
      "securityGroupId": "65ab5050-0942-4343-9ca2-866987a07f09"
    },
    {
      "id": "17394ade-7903-470d-8525-6ddcf12be0af",
      "data": {
        "name": "Manager",
        "description": "Manager",
        "permissions": [
          "read@customers",
          "destroy@invitations",
          "insert@invitations",
          "modify@invitations",
          "read@invitations",
          "destroy@memberships",
          "insert@memberships",
          "modify@memberships",
          "read@memberships",
          "destroy@join-requests",
          "insert@join-requests",
          "modify@join-requests",
          "read@join-requests",
          "destroy@notifications-history",
          "insert@notifications-history",
          "modify@notifications-history",
          "read@notifications-history",
          "destroy@organizations",
          "insert@organizations",
          "modify@organizations",
          "read@organizations",
          "destroy@organization-descendants",
          "insert@organization-descendants",
          "modify@organization-descendants",
          "read@organization-descendants",
          "destroy@field-sets",
          "insert@field-sets",
          "modify@field-sets",
          "read@field-sets",
          "destroy@exports",
          "insert@exports",
          "modify@exports",
          "read@exports",
          "destroy@imports",
          "insert@imports",
          "modify@imports",
          "read@imports",
          "destroy@import-configs",
          "insert@import-configs",
          "modify@import-configs",
          "read@import-configs",
          "destroy@integrations",
          "insert@integrations",
          "modify@integrations",
          "read@integrations",
          "destroy@integration-request",
          "insert@integration-request",
          "modify@integration-request",
          "read@integration-request",
          "destroy@payments",
          "insert@payments",
          "modify@payments",
          "read@payments",
          "destroy@campaigns",
          "insert@campaigns",
          "modify@campaigns",
          "read@campaigns",
          "destroy@contacts",
          "insert@contacts",
          "modify@contacts",
          "read@contacts",
          "destroy@interactions",
          "insert@interactions",
          "modify@interactions",
          "read@interactions",
          "destroy@lists",
          "insert@lists",
          "modify@lists",
          "read@lists",
          "destroy@segments",
          "insert@segments",
          "modify@segments",
          "read@segments",
          "destroy@surveys",
          "insert@surveys",
          "modify@surveys",
          "read@surveys",
          "destroy@turfs",
          "insert@turfs",
          "modify@turfs",
          "read@turfs",
          "destroy@turf-assignments",
          "insert@turf-assignments",
          "modify@turf-assignments",
          "read@turf-assignments",
          "destroy@walklists",
          "insert@walklists",
          "modify@walklists",
          "read@walklists",
          "destroy@walklist-share-requests",
          "insert@walklist-share-requests",
          "modify@walklist-share-requests",
          "read@walklist-share-requests",
          "read@unassigned-turf-data",
          "read@authentications",
          "read@roles",
          "read@security-groups",
          "insert@security-groups",
          "read@user-roles",
          "read@users",
          "modify@user-credentials",
          "read@user-credentials",
          "read@analytics::responses",
          "read@analytics::doors-knocked"
        ]
      },
      "meta": {
        "etag": "ab1-Sg+bBsaSdNKIorPe65+VLqq2n/g",
        "created": "2017-08-18T18:52:19.558Z",
        "modified": "2017-08-18T18:52:19.558Z",
        "resource": "roles",
        "createdBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c",
        "isDeleted": false,
        "modifiedBy": "931596ea-8ac6-44c5-8aa7-e11456fca02c"
      },
      "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
      "securityGroupId": "65ab5050-0942-4343-9ca2-866987a07f09"
    }
  ],
  "meta": {}
}
```

### HTTP Request
`GET https://api.polisapp.com/roles?filter={filter}&limit={limit}&skip={skip}&sort={sort}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
fiter | false | Query to filter data. [See documentation](#filters).
limit | true | Limit results returned. Useful for pagination.
skip | true | Data offset index. Useful for pagination.
sort | true | Sort column. Ex.: `["data/name","ASC"]`

Filter Example: `/customerId eq "f51b86dd-aaba-485e-b14d-65cbea28b8e4"`
