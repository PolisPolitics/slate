# Roles

## The Role object

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Identifier of this record.
securityGroupId | true | Identifier of the associated security group.
customerId | true | Identifier of the associated customer.
data | true | Role data.

### data

Attribute | Required? | Description
--------- | --------- | -----------
name | true | Name of the role.
description | false | Descriptions of the role.
permissions | false | Array of permissions allowed to that role.

### meta

[See documentation](#metadata-object)



```json
{
	"id": "d16c892e-91b8-4d8b-ae03-deb9890f71e1",
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
			"read@industries",
			"insert@field-sets",
			"modify@field-sets",
			"read@field-sets",
			"insert@payments",
			"modify@payments",
			"read@countries",
			"modify@countries",
			"insert@countries",
			"read@regions",
			"modify@regions",
			"insert@regions",
			"read@region-descendants",
			"modify@region-descendants",
			"insert@region-descendants",
			"read@addresses",
			"modify@addresses",
			"insert@addresses",
			"read@households",
			"modify@households",
			"insert@households",
			"insert@contact-households",
			"modify@contact-households",
			"read@contact-households",
			"read@campaigns",
			"modify@campaigns",
			"read@campaign-survey",
			"read@contacts",
			"insert@contacts",
			"modify@contacts",
			"insert@contact-integrations",
			"modify@contact-integrations",
			"read@contact-integrations",
			"insert@contact-household-campaigns",
			"modify@contact-household-campaigns",
			"read@contact-household-campaigns",
			"insert@contact-household-lists",
			"modify@contact-household-lists",
			"read@contact-household-lists",
			"insert@interactions",
			"modify@interactions",
			"read@interactions",
			"insert@answers",
			"modify@answers",
			"read@answers",
			"destroy@answers",
			"insert@answer-option",
			"modify@answer-option",
			"read@answer-option",
			"destroy@answer-option",
			"read@question-options",
			"read@integrations",
			"read@lists",
			"insert@lists",
			"modify@lists",
			"read@questions",
			"insert@notes",
			"modify@notes",
			"read@notes",
			"read@segments",
			"read@surveys",
			"read@status-campaign",
			"read@statuses",
			"read@status-groups",
			"read@turfs",
			"read@turf-assignments",
			"insert@turf-assignments",
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
		"etag": "",
		"created": "2019-04-03T18:55:25.305Z",
		"modified": "2019-04-03T18:55:25.305Z",
		"resource": "roles",
		"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
		"isDeleted": false,
		"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```


## Get many roles

> Example Request

```http
GET /v1/roles?filter%5B%2FcustomerId%5D=286d1af1-c2c5-4069-a19d-3987fdacc0d6&skip=0&limit=9007199254740991&sort=id&sort=ASC HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"data": [
		{
			"id": "d16c892e-91b8-4d8b-ae03-deb9890f71e1",
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
					"read@industries",
					"insert@field-sets",
					"modify@field-sets",
					"read@field-sets",
					"insert@payments",
					"modify@payments",
					"read@countries",
					"modify@countries",
					"insert@countries",
					"read@regions",
					"modify@regions",
					"insert@regions",
					"read@region-descendants",
					"modify@region-descendants",
					"insert@region-descendants",
					"read@addresses",
					"modify@addresses",
					"insert@addresses",
					"read@households",
					"modify@households",
					"insert@households",
					"insert@contact-households",
					"modify@contact-households",
					"read@contact-households",
					"read@campaigns",
					"modify@campaigns",
					"read@campaign-survey",
					"read@contacts",
					"insert@contacts",
					"modify@contacts",
					"insert@contact-integrations",
					"modify@contact-integrations",
					"read@contact-integrations",
					"insert@contact-household-campaigns",
					"modify@contact-household-campaigns",
					"read@contact-household-campaigns",
					"insert@contact-household-lists",
					"modify@contact-household-lists",
					"read@contact-household-lists",
					"insert@interactions",
					"modify@interactions",
					"read@interactions",
					"insert@answers",
					"modify@answers",
					"read@answers",
					"destroy@answers",
					"insert@answer-option",
					"modify@answer-option",
					"read@answer-option",
					"destroy@answer-option",
					"read@question-options",
					"read@integrations",
					"read@lists",
					"insert@lists",
					"modify@lists",
					"read@questions",
					"insert@notes",
					"modify@notes",
					"read@notes",
					"read@segments",
					"read@surveys",
					"read@status-campaign",
					"read@statuses",
					"read@status-groups",
					"read@turfs",
					"read@turf-assignments",
					"insert@turf-assignments",
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
				"etag": "",
				"created": "2019-04-03T18:55:25.305Z",
				"modified": "2019-04-03T18:55:25.305Z",
				"resource": "roles",
				"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
				"isDeleted": false,
				"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		},
		{
			"id": "ba192430-14b5-44f7-abcf-fc6b9aa35813",
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
					"destroy@countries",
					"insert@countries",
					"modify@countries",
					"read@countries",
					"destroy@regions",
					"insert@regions",
					"modify@regions",
					"read@regions",
					"destroy@region-descendants",
					"insert@region-descendants",
					"modify@region-descendants",
					"read@region-descendants",
					"destroy@addresses",
					"insert@addresses",
					"modify@addresses",
					"read@addresses",
					"destroy@households",
					"insert@households",
					"modify@households",
					"read@households",
					"destroy@contact-households",
					"insert@contact-households",
					"modify@contact-households",
					"read@contact-households",
					"destroy@campaigns",
					"insert@campaigns",
					"modify@campaigns",
					"read@campaigns",
					"destroy@campaign-survey",
					"insert@campaign-survey",
					"modify@campaign-survey",
					"read@campaign-survey",
					"destroy@contacts",
					"insert@contacts",
					"modify@contacts",
					"read@contacts",
					"destroy@contact-household-campaigns",
					"insert@contact-household-campaigns",
					"modify@contact-household-campaigns",
					"read@contact-household-campaigns",
					"insert@contact-integrations",
					"modify@contact-integrations",
					"read@contact-integrations",
					"destroy@contact-integrations",
					"destroy@contact-household-lists",
					"insert@contact-household-lists",
					"modify@contact-household-lists",
					"read@contact-household-lists",
					"destroy@interactions",
					"insert@interactions",
					"modify@interactions",
					"read@interactions",
					"destroy@answers",
					"insert@answers",
					"modify@answers",
					"read@answers",
					"destroy@answer-option",
					"insert@answer-option",
					"modify@answer-option",
					"read@answer-option",
					"destroy@question-options",
					"insert@question-options",
					"modify@question-options",
					"read@question-options",
					"destroy@lists",
					"insert@lists",
					"modify@lists",
					"read@lists",
					"destroy@questions",
					"insert@questions",
					"modify@questions",
					"read@questions",
					"destroy@notes",
					"insert@notes",
					"modify@notes",
					"read@notes",
					"destroy@segments",
					"insert@segments",
					"modify@segments",
					"read@segments",
					"destroy@surveys",
					"insert@surveys",
					"modify@surveys",
					"read@surveys",
					"destroy@statuses",
					"insert@statuses",
					"modify@statuses",
					"read@statuses",
					"destroy@status-campaign",
					"insert@status-campaign",
					"modify@status-campaign",
					"read@status-campaign",
					"read@status-groups",
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
					"modify@users",
					"modify@user-credentials",
					"read@user-credentials",
					"read@analytics::responses",
					"read@analytics::doors-knocked"
				]
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:25.356Z",
				"modified": "2019-04-03T18:55:25.356Z",
				"resource": "roles",
				"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
				"isDeleted": false,
				"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		}
	],
	"meta": {}
}
```

### HTTP Request

`GET https://api.polisapp.com/v1/roles`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | false | Query to filter data. e.g. `/customerId eq "f51b86dd-aaba-485e-b14d-65cbea28b8e4"`
limit | true | Limits number of result-rows. Should be a positive integer. Useful for pagination.
skip | true | Offset data by given number. Useful for pagination.
sort | true | Sort the column in `ASC` or `DESC` e.g. ['id', 'ASC']


## Get a role

> Example Request

```http
GET /v1/roles/d16c892e-91b8-4d8b-ae03-deb9890f71e1 HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"id": "d16c892e-91b8-4d8b-ae03-deb9890f71e1",
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
			"read@industries",
			"insert@field-sets",
			"modify@field-sets",
			"read@field-sets",
			"insert@payments",
			"modify@payments",
			"read@countries",
			"modify@countries",
			"insert@countries",
			"read@regions",
			"modify@regions",
			"insert@regions",
			"read@region-descendants",
			"modify@region-descendants",
			"insert@region-descendants",
			"read@addresses",
			"modify@addresses",
			"insert@addresses",
			"read@households",
			"modify@households",
			"insert@households",
			"insert@contact-households",
			"modify@contact-households",
			"read@contact-households",
			"read@campaigns",
			"modify@campaigns",
			"read@campaign-survey",
			"read@contacts",
			"insert@contacts",
			"modify@contacts",
			"insert@contact-integrations",
			"modify@contact-integrations",
			"read@contact-integrations",
			"insert@contact-household-campaigns",
			"modify@contact-household-campaigns",
			"read@contact-household-campaigns",
			"insert@contact-household-lists",
			"modify@contact-household-lists",
			"read@contact-household-lists",
			"insert@interactions",
			"modify@interactions",
			"read@interactions",
			"insert@answers",
			"modify@answers",
			"read@answers",
			"destroy@answers",
			"insert@answer-option",
			"modify@answer-option",
			"read@answer-option",
			"destroy@answer-option",
			"read@question-options",
			"read@integrations",
			"read@lists",
			"insert@lists",
			"modify@lists",
			"read@questions",
			"insert@notes",
			"modify@notes",
			"read@notes",
			"read@segments",
			"read@surveys",
			"read@status-campaign",
			"read@statuses",
			"read@status-groups",
			"read@turfs",
			"read@turf-assignments",
			"insert@turf-assignments",
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
		"etag": "",
		"created": "2019-04-03T18:55:25.305Z",
		"modified": "2019-04-03T18:55:25.305Z",
		"resource": "roles",
		"createdBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f",
		"isDeleted": false,
		"modifiedBy": "aa0c23a0-9e12-4397-9218-46065ae2ae8f"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`GET https://api.polisapp.com/v1/roles/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the role to be retrieved.

