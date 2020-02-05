# Interactions

## The Interaction object

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Unique identifier for this object.
securityGroupId | true | Security group of this resource.
customerId | true | Customer to which this resource belongs.
data | true | Interaction data.

### data

Attribute | Required? | Description
--------- | --------- | -----------
campaignId | true | Identifier of the campaign with which this interaction is associated.
contactId | true | Identifier of the contact with whom this interaction occurred.
householdId | true | Identifier of the household where this interaction occurred.
contactHouseholdId | true | Identifier of the contact-household.
timestamp | true | Timestamp of this interaction.
survey | true | The survey data. [details](#data-survey)
location | false | Location data. [details](#data-location)
successful | false | Flag indicating whether this interaction was successful.
unavailable | true | Flag indicating whether the contact was unavailable.
unavailableReason | false | Reason specifying why the contact was unavailable.
distance | false | Distance between canvasser's location and household location in miles. For fraud detection.
statusId | false | Identifier of the status of this interaction.
walklistId | false | Identifier of the walklist route under which the contact was reserved.

### data/survey

Attribute | Required? | Description
--------- | --------- | -----------
surveyId | true | Identifier of the survey.
responses | false | Response recorded for the suvey questions.

### data/location

Attribute | Required? | Description
--------- | --------- | -----------
lat | false | Coordinate specifying north-south position of this location on Earth.
lng | false | Coordinate specifying east-west position of this location on Earth.
confidence | false | Quantitative accuracy of the location coordinates.

### meta

[See documentation](#metadata-object)



```json
{
	"id": "7da76f74-7951-423a-be41-85a2551d16e7",
	"data": {
		"survey": {
			"surveyId": "375d437b-3b47-4940-b43d-be8daec4afff",
			"responses": {
				"9826940d-76a8-4700-8c92-5743ce7bb728": {
					"fields": {
						"available": "false"
					},
					"questionId": "9826940d-76a8-4700-8c92-5743ce7bb728"
				},
				"f386f88a-61f1-4f0d-b3d9-ba97e8238444": {
					"fields": {
						"dogliker": "true"
					},
					"questionId": "f386f88a-61f1-4f0d-b3d9-ba97e8238444"
				}
			}
		},
		"distance": 936.2361,
		"location": {
			"lat": 33.43174362182617,
			"lng": -84.18405151367188,
			"confidence": 0
		},
		"contactId": "0478dbbf-b6eb-4168-afa9-5ebab6fef4b6",
		"timestamp": "2018-07-17T18:40:53.526Z",
		"campaignId": "61fbfbaa-5de8-4d17-ac2b-c47f2376265a",
		"successful": true,
		"householdId": "c15e3515-aabf-42da-8d1b-31679f738eae",
		"unavailable": true,
		"unavailableReason": "Come Back",
		"contactHouseholdId": "d070b1dc-9611-4f29-9300-a32160d21baa"
	},
	"meta": {
		"etag": "47a-h6vIm4ttg8qp/cFMmsY+JtWtBsc",
		"created": "2019-04-22T19:43:06.475Z",
		"modified": "2019-04-22T19:43:06.475Z",
		"resource": "interactions",
		"createdBy": "0651e380-d556-49bd-acdd-2bd813b16430",
		"isDeleted": false,
		"modifiedBy": "0651e380-d556-49bd-acdd-2bd813b16430"
	},
	"customerId": "cfa8df1b-baf1-446b-b06c-3177063faed7",
	"securityGroupId": "e822d07f-5972-4ff2-bc75-dbd68d6d79bf"
}
```


## Get many interactions

> Example Request

```http
GET /v2/interactions?filter%5B%2Fdata%2FcampaignId%5D=61fbfbaa-5de8-4d17-ac2b-c47f2376265a&skip=0&limit=9007199254740991&sort=%2Fdata%2Fid&sort=ASC HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"data": [
		{
			"id": "7da76f74-7951-423a-be41-85a2551d16e7",
			"data": {
				"survey": {
					"surveyId": "375d437b-3b47-4940-b43d-be8daec4afff",
					"responses": {
						"9826940d-76a8-4700-8c92-5743ce7bb728": {
							"fields": {
								"available": "false"
							},
							"questionId": "9826940d-76a8-4700-8c92-5743ce7bb728"
						},
						"f386f88a-61f1-4f0d-b3d9-ba97e8238444": {
							"fields": {
								"dogliker": "true"
							},
							"questionId": "f386f88a-61f1-4f0d-b3d9-ba97e8238444"
						}
					}
				},
				"distance": 936.2361,
				"location": {
					"lat": 33.43174362182617,
					"lng": -84.18405151367188,
					"confidence": 0
				},
				"contactId": "0478dbbf-b6eb-4168-afa9-5ebab6fef4b6",
				"timestamp": "2018-07-17T18:40:53.526Z",
				"campaignId": "61fbfbaa-5de8-4d17-ac2b-c47f2376265a",
				"successful": true,
				"householdId": "c15e3515-aabf-42da-8d1b-31679f738eae",
				"unavailable": true,
				"unavailableReason": "Come Back",
				"contactHouseholdId": "d070b1dc-9611-4f29-9300-a32160d21baa"
			},
			"meta": {
				"etag": "47a-h6vIm4ttg8qp/cFMmsY+JtWtBsc",
				"created": "2019-04-22T19:43:06.475Z",
				"modified": "2019-04-22T19:43:06.475Z",
				"resource": "interactions",
				"createdBy": "0651e380-d556-49bd-acdd-2bd813b16430",
				"isDeleted": false,
				"modifiedBy": "0651e380-d556-49bd-acdd-2bd813b16430"
			},
			"customerId": "cfa8df1b-baf1-446b-b06c-3177063faed7",
			"securityGroupId": "e822d07f-5972-4ff2-bc75-dbd68d6d79bf"
		},
		{
			"id": "2f79b11e-e23c-4305-ba72-32d97311d053",
			"data": {
				"survey": {
					"surveyId": "375d437b-3b47-4940-b43d-be8daec4afff",
					"responses": {
						"9826940d-76a8-4700-8c92-5743ce7bb728": {
							"fields": {
								"available": "true"
							},
							"questionId": "9826940d-76a8-4700-8c92-5743ce7bb728"
						},
						"f386f88a-61f1-4f0d-b3d9-ba97e8238444": {
							"fields": {
								"dogliker": "true"
							},
							"questionId": "f386f88a-61f1-4f0d-b3d9-ba97e8238444"
						}
					}
				},
				"distance": 936.2361,
				"location": {
					"lat": 33.43174362182617,
					"lng": -84.18405151367188,
					"confidence": 0
				},
				"contactId": "0478dbbf-b6eb-4168-afa9-5ebab6fef4b6",
				"timestamp": "2018-07-18T18:40:53.526Z",
				"campaignId": "61fbfbaa-5de8-4d17-ac2b-c47f2376265a",
				"successful": true,
				"householdId": "c15e3515-aabf-42da-8d1b-31679f738eae",
				"unavailable": false,
				"unavailableReason": "Come Back",
				"contactHouseholdId": "d070b1dc-9611-4f29-9300-a32160d21baa"
			},
			"meta": {
				"etag": "47a-wHD832ZEORk838ByTovnIQVEMrA",
				"created": "2019-04-22T19:45:44.659Z",
				"modified": "2019-04-22T19:45:44.659Z",
				"resource": "interactions",
				"createdBy": "0651e380-d556-49bd-acdd-2bd813b16430",
				"isDeleted": false,
				"modifiedBy": "0651e380-d556-49bd-acdd-2bd813b16430"
			},
			"customerId": "cfa8df1b-baf1-446b-b06c-3177063faed7",
			"securityGroupId": "e822d07f-5972-4ff2-bc75-dbd68d6d79bf"
		}
	],
	"meta": {}
}
```

### HTTP Request

`GET https://api.beta.polisapp.com/v2/interactions`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | false | Query to filter data. <br/> e.g. '"/data/contactId": "0478dbbf-b6eb-4168-afa9-5ebab6fef4b6"'
limit | true | Limits number of result-rows. Should be a positive integer. Useful for pagination.
skip | true | Offset data by given number. Useful for pagination.
sort | true | Sort the column in `ASC` or `DESC` e.g. ['id', 'ASC']


## Get an interaction

> Example Request

```http
GET /v2/interactions/7da76f74-7951-423a-be41-85a2551d16e7 HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"id": "7da76f74-7951-423a-be41-85a2551d16e7",
	"data": {
		"survey": {
			"surveyId": "375d437b-3b47-4940-b43d-be8daec4afff",
			"responses": {
				"9826940d-76a8-4700-8c92-5743ce7bb728": {
					"fields": {
						"available": "false"
					},
					"questionId": "9826940d-76a8-4700-8c92-5743ce7bb728"
				},
				"f386f88a-61f1-4f0d-b3d9-ba97e8238444": {
					"fields": {
						"dogliker": "true"
					},
					"questionId": "f386f88a-61f1-4f0d-b3d9-ba97e8238444"
				}
			}
		},
		"distance": 936.2361,
		"location": {
			"lat": 33.43174362182617,
			"lng": -84.18405151367188,
			"confidence": 0
		},
		"contactId": "0478dbbf-b6eb-4168-afa9-5ebab6fef4b6",
		"timestamp": "2018-07-17T18:40:53.526Z",
		"campaignId": "61fbfbaa-5de8-4d17-ac2b-c47f2376265a",
		"successful": true,
		"householdId": "c15e3515-aabf-42da-8d1b-31679f738eae",
		"unavailable": true,
		"unavailableReason": "Come Back",
		"contactHouseholdId": "d070b1dc-9611-4f29-9300-a32160d21baa"
	},
	"meta": {
		"etag": "47a-h6vIm4ttg8qp/cFMmsY+JtWtBsc",
		"created": "2019-04-22T19:43:06.475Z",
		"modified": "2019-04-22T19:43:06.475Z",
		"resource": "interactions",
		"createdBy": "0651e380-d556-49bd-acdd-2bd813b16430",
		"isDeleted": false,
		"modifiedBy": "0651e380-d556-49bd-acdd-2bd813b16430"
	},
	"customerId": "cfa8df1b-baf1-446b-b06c-3177063faed7",
	"securityGroupId": "e822d07f-5972-4ff2-bc75-dbd68d6d79bf"
}
```

### HTTP Request

`GET https://api.beta.polisapp.com/v2/interactions/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the interaction to be retrieved.


## Post to interactions

> Example Request

```http
POST /v2/interactions HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"campaignId": "61fbfbaa-5de8-4d17-ac2b-c47f2376265a",
	"contactId": "0478dbbf-b6eb-4168-afa9-5ebab6fef4b6",
	"householdId": "c15e3515-aabf-42da-8d1b-31679f738eae",
	"contactHouseholdId": "d070b1dc-9611-4f29-9300-a32160d21baa",
	"timestamp": "2018-07-17T18:40:53.526Z",
	"unavailable": true,
	"unavailableReason": "Come Back",
	"successful": false,
	"survey": {
		"responses": {
			"9826940d-76a8-4700-8c92-5743ce7bb728": {
				"fields": {
					"available": "false"
				},
				"questionId": "9826940d-76a8-4700-8c92-5743ce7bb728"
			},
			"f386f88a-61f1-4f0d-b3d9-ba97e8238444": {
				"fields": {
					"dogliker": "true"
				},
				"questionId": "f386f88a-61f1-4f0d-b3d9-ba97e8238444"
			}
		},
		"surveyId": "375d437b-3b47-4940-b43d-be8daec4afff"
	},
	"location": {
		"lat": 33.43174362182617,
		"lng": -84.18405151367188,
		"confidence": 0
	}
}
```

> Example Response

```json
{
	"id": "7da76f74-7951-423a-be41-85a2551d16e7",
	"data": {
		"survey": {
			"surveyId": "375d437b-3b47-4940-b43d-be8daec4afff",
			"responses": {
				"9826940d-76a8-4700-8c92-5743ce7bb728": {
					"fields": {
						"available": "false"
					},
					"questionId": "9826940d-76a8-4700-8c92-5743ce7bb728"
				},
				"f386f88a-61f1-4f0d-b3d9-ba97e8238444": {
					"fields": {
						"dogliker": "true"
					},
					"questionId": "f386f88a-61f1-4f0d-b3d9-ba97e8238444"
				}
			}
		},
		"distance": 936.2361,
		"location": {
			"lat": 33.43174362182617,
			"lng": -84.18405151367188,
			"confidence": 0
		},
		"contactId": "0478dbbf-b6eb-4168-afa9-5ebab6fef4b6",
		"timestamp": "2018-07-17T18:40:53.526Z",
		"campaignId": "61fbfbaa-5de8-4d17-ac2b-c47f2376265a",
		"successful": true,
		"householdId": "c15e3515-aabf-42da-8d1b-31679f738eae",
		"unavailable": true,
		"unavailableReason": "Come Back",
		"contactHouseholdId": "d070b1dc-9611-4f29-9300-a32160d21baa"
	},
	"meta": {
		"etag": "47a-h6vIm4ttg8qp/cFMmsY+JtWtBsc",
		"created": "2019-04-22T19:43:06.475Z",
		"modified": "2019-04-22T19:43:06.475Z",
		"resource": "interactions",
		"createdBy": "0651e380-d556-49bd-acdd-2bd813b16430",
		"isDeleted": false,
		"modifiedBy": "0651e380-d556-49bd-acdd-2bd813b16430"
	},
	"customerId": "cfa8df1b-baf1-446b-b06c-3177063faed7",
	"securityGroupId": "e822d07f-5972-4ff2-bc75-dbd68d6d79bf"
}
```

### HTTP Request

`POST https://api.beta.polisapp.com/v2/interactions`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
data | true | Data of interaction to be created


## Patch an item from interactions

> Example Request

```http
PATCH /v2/interactions/7da76f74-7951-423a-be41-85a2551d16e7 HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
{
	"data": [
		{
			"op": "replace",
			"path": "/data/successful",
			"value": false
		},
		{
			"op": "replace",
			"path": "/data/unavailable",
			"value": false
		}
	]
}
```


<aside class='notice'>
You can only patch attributes inside <b>data</b> key.
</aside>

> Example Response

```json
{
	"id": "7da76f74-7951-423a-be41-85a2551d16e7",
	"data": {
		"survey": {
			"surveyId": "375d437b-3b47-4940-b43d-be8daec4afff",
			"responses": {
				"9826940d-76a8-4700-8c92-5743ce7bb728": {
					"fields": {
						"available": "false"
					},
					"questionId": "9826940d-76a8-4700-8c92-5743ce7bb728"
				},
				"f386f88a-61f1-4f0d-b3d9-ba97e8238444": {
					"fields": {
						"dogliker": "true"
					},
					"questionId": "f386f88a-61f1-4f0d-b3d9-ba97e8238444"
				}
			}
		},
		"distance": 936.2361,
		"location": {
			"lat": 33.43174362182617,
			"lng": -84.18405151367188,
			"confidence": 0
		},
		"contactId": "0478dbbf-b6eb-4168-afa9-5ebab6fef4b6",
		"timestamp": "2018-07-17T18:40:53.526Z",
		"campaignId": "61fbfbaa-5de8-4d17-ac2b-c47f2376265a",
		"successful": false,
		"householdId": "c15e3515-aabf-42da-8d1b-31679f738eae",
		"unavailable": false,
		"unavailableReason": "Come Back",
		"contactHouseholdId": "d070b1dc-9611-4f29-9300-a32160d21baa"
	},
	"meta": {
		"etag": "47a-h6vIm4ttg8qp/cFMmsY+JtWtBsc",
		"created": "2019-04-22T19:43:06.475Z",
		"modified": "2019-04-22T19:43:06.475Z",
		"resource": "interactions",
		"createdBy": "0651e380-d556-49bd-acdd-2bd813b16430",
		"isDeleted": false,
		"modifiedBy": "0651e380-d556-49bd-acdd-2bd813b16430"
	},
	"customerId": "cfa8df1b-baf1-446b-b06c-3177063faed7",
	"securityGroupId": "e822d07f-5972-4ff2-bc75-dbd68d6d79bf"
}
```

### HTTP Request

`PATCH https://api.beta.polisapp.com/v2/interactions/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the interaction to be updated.
data | true | The patch data in [JSONPatch Format](https://tools.ietf.org/html/rfc6902).


## Delete an interactions

> Example Request

```http
DELETE /v2/interactions/7da76f74-7951-423a-be41-85a2551d16e7 HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
```

### HTTP Request

`DELETE https://api.beta.polisapp.com/v2/interactions/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the interaction to be deleted.

