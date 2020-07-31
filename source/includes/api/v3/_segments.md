# Segments

## The segment object

```json
{
  "id": "f84ae4c4-e955-4049-bdff-f972afe48d29",
  "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
  "securityGroupId": "af2fba23-5fb4-4d14-b406-0aac501f00c8",
  "data": {
    "name": "My Segment",
    "criteria": {
      "filter": "any",
      "clauses": [
        {
          "value": "18",
          "source": "/data/profile/age",
          "operator": "gt"
        }
      ]
    },
    "surveyId": "e2f61e8e-129d-445f-a252-cd267cbce21f",
    "campaignId": "d012c895-4318-4725-9012-b1099e96643d",
    "precedence": 2
  },
  "meta": {
    "etag": "27d-nhGX43ixs4LwVlZq03E7K3NF2yE",
    "created": "2018-09-20T17:38:35.912Z",
    "modified": "2018-09-20T17:38:35.912Z",
    "resource": "segments",
    "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
    "isDeleted": false,
    "modifiedBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851"
  }
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
name | true | Name of the segment.
description | false | Description of the segment.
campaignId | true | Camapaign indentifier that this segment belongs to.
surveyId | true | Survey indentifier that this segment will use.
criteria | true | Object that defines the criteria used to analyze the contacts.[details](#data-criteria)
precedence | true | Level of precedence between segments.

### data/criteria

Attribute | Required? | Description
--------- | --------- | -----------
filter | true | Can be `any` or `all`.
clauses | true | Specifies something. Minimum 1 clause. [details](#data-criteria-clause)

### data/criteria/clause

Attribute | Required? | Description
--------- | --------- | -----------
source | true | Path to the contact attribute.
operator | true | Operator used to compare the value and the contact attribute retrieved using the source path. Can be `eq`, `neq`, `gt`, `gte`, `lt`, `lte` or `in`.
value | true | Value used for comparison.

### Note

The segment is created and deleted together with its respective survey.

### meta

[See documentation](#metadata-object).

## Retrieve a segment

> Example Request

```http
GET /v1/segments/f2636525-36d7-439c-924d-a2aaf3848716 HTTP/1.1
Host: api.beta.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "id": "f2636525-36d7-439c-924d-a2aaf3848716",
  "data": {
    "name": "Default Target",
    "criteria": {
      "filter": "any",
      "clauses": [
        {
          "value": "1",
          "source": "1",
          "operator": "eq"
        }
      ]
    },
    "surveyId": "27d64393-cfe8-45fa-8e54-6b914ce376a4",
    "campaignId": "e2f3837e-46ff-41c8-b0b5-91e01a846c72",
    "precedence": 1
  },
  "meta": {
    "etag": "270-IcLEYiDB4jNoq6+5H10UJwQ5WHI",
    "created": "2018-09-20T17:13:30.143Z",
    "modified": "2018-09-20T17:13:30.143Z",
    "resource": "segments",
    "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
    "isDeleted": false,
    "modifiedBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851"
  },
  "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
  "securityGroupId": "8e9363ba-215c-40cb-822f-639e6b957472"
}

```

Obtains a single segment object by ID.

### HTTP Request

`GET https://api.beta.polisapp.com/v1/segments/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | Unique identifier of the segment.

## Update a segment

> Example Request

```http
PATCH /v1/segments/f2636525-36d7-439c-924d-a2aaf3848716 HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
ETag: {etag_value}

{
  "data": [
    {
      "op": "replace",
      "path": "/name",
      "value": "My Segment Name Changed"
    }
  ]
}

```

> Example Response

```json
{
  "id": "f2636525-36d7-439c-924d-a2aaf3848716",
  "data": {
    "name": "My Segment Name Changed",
    "criteria": {
      "filter": "any",
      "clauses": [
        {
          "value": "m",
          "source": "/data/profile/gender",
          "operator": "eq"
        }
      ]
    },
    "surveyId": "e2f61e8e-129d-445f-a252-cd267cbce21f",
    "campaignId": "d012c895-4318-4725-9012-b1099e96643d",
    "precedence": 2
  },
  "meta": {
    "created": "2018-09-20T17:41:11.856Z",
    "modified": "2018-09-20T18:16:34.158Z",
    "resource": "segments",
    "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
    "isDeleted": false,
    "modifiedBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
    "etag": "27c-mmBrAJTWNTl9s1mSuSOEm7Qa/rE"
  },
  "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
  "securityGroupId": "af2fba23-5fb4-4d14-b406-0aac501f00c8"
}

```
<aside class="notice">
You can only patch attributes inside <b>data</b> key.
</aside>

[RFC 6902 - JavaScript Object Notation (JSON) Patch](https://tools.ietf.org/html/rfc6902)

### HTTP Request

`PATCH https://api.beta.polisapp.com/v1/segments/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | Unique identifier of the segment.

## Get many segments

> Example Request

```http
GET /v1/segments?filter=%2Fdata%2FcampaignId%20eq%20%22d012c895-4318-4725-9012-b1099e96643d%22&limit=100&skip=0&sort=%5B%22data%2Fname%22%2C%22ASC%22%5D HTTP/1.1
Host: api.beta.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "data": [
    {
      "id": "39b2c678-17ea-404f-8c72-1f7f6367b820",
      "data": {
        "name": "Default Target 2",
        "criteria": {
          "filter": "any",
          "clauses": [
            {
              "value": "1",
              "source": "1",
              "operator": "eq"
            }
          ]
        },
        "surveyId": "27d64393-cfe8-45fa-8e54-6b914ce376a4",
        "campaignId": "e2f3837e-46ff-41c8-b0b5-91e01a846c72",
        "precedence": 2
      },
      "meta": {
        "etag": "272-quEjhMx9oyLll0DOhdYu5/sXOx4",
        "created": "2018-09-20T19:00:22.476Z",
        "modified": "2018-09-20T19:00:22.476Z",
        "resource": "segments",
        "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
        "isDeleted": false,
        "modifiedBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851"
      },
      "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
      "securityGroupId": "8e9363ba-215c-40cb-822f-639e6b957472"
    },
    {
      "id": "8d2bc490-bbb0-4506-96be-8d59b1ed31d1",
      "data": {
        "name": "Default Target",
        "criteria": {
          "filter": "any",
          "clauses": [
            {
              "value": "1",
              "source": "1",
              "operator": "eq"
            }
          ]
        },
        "surveyId": "27d64393-cfe8-45fa-8e54-6b914ce376a4",
        "campaignId": "e2f3837e-46ff-41c8-b0b5-91e01a846c72",
        "precedence": 1
      },
      "meta": {
        "etag": "270-dEtct4eaEmoZfXvopHFiMi7wybg",
        "created": "2018-09-20T19:00:15.065Z",
        "modified": "2018-09-20T19:00:15.065Z",
        "resource": "segments",
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
`GET https://api.beta.polisapp.com/v1/segments?filter={filter}&limit={limit}&skip={skip}&sort={sort}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
fiter | false | Query to filter data. [See documentation](#filters).
limit | true | Limit results returned. Useful for pagination.
skip | true | Data offset index. Useful for pagination.
sort | true | Sort column. Ex.: `["id","ASC"]`

Filter Example: `/data/organizationId eq "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319" and /data/status eq "complete"`

## Swap precedences

Swap precedences of two segments.

> Example Request

```http
POST /v1/segments/swap-precedences HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
  "data": {
    "segments": [
      {
        "id": "b5792d25-8e70-4bec-8ac9-319260cedc26",
        "etag": "277-ZiR5elWikIT8dF9V8hS/O/LSLDU"
      },
      {
        "id": "f84ae4c4-e955-4049-bdff-f972afe48d29",
        "etag": "27d-nhGX43ixs4LwVlZq03E7K3NF2yE"
      }
    ]
  }
}
```

> Example Response

```json
[
  {
    "id": "b5792d25-8e70-4bec-8ac9-319260cedc26",
    "data": {
      "name": "My Segment 2",
      "criteria": {
        "filter": "any",
        "clauses": [
          {
            "value": "m",
            "source": "/data/profile/gender",
            "operator": "eq"
          }
        ]
      },
      "surveyId": "e2f61e8e-129d-445f-a252-cd267cbce21f",
      "campaignId": "d012c895-4318-4725-9012-b1099e96643d",
      "precedence": 2
    },
    "meta": {
      "created": "2018-09-20T17:41:11.856Z",
      "modified": "2018-09-20T17:55:40.825Z",
      "resource": "segments",
      "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
      "isDeleted": false,
      "modifiedBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
      "etag": "277-Sw81CIqtglhNs4g5Mf3JwDjfJVg"
    },
    "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
    "securityGroupId": "af2fba23-5fb4-4d14-b406-0aac501f00c8"
  },
  {
    "id": "f84ae4c4-e955-4049-bdff-f972afe48d29",
    "data": {
      "name": "My Segment",
      "criteria": {
        "filter": "any",
        "clauses": [
          {
            "value": "18",
            "source": "/data/profile/age",
            "operator": "gt"
          }
        ]
      },
      "surveyId": "e2f61e8e-129d-445f-a252-cd267cbce21f",
      "campaignId": "d012c895-4318-4725-9012-b1099e96643d",
      "precedence": 3
    },
    "meta": {
      "created": "2018-09-20T17:38:35.912Z",
      "modified": "2018-09-20T17:55:40.878Z",
      "resource": "segments",
      "createdBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
      "isDeleted": false,
      "modifiedBy": "13b6fc16-b84f-42a0-ad84-1135e12e0851",
      "etag": "273-ttH1rhbK7CHTgZH87+aZVwGUEMo"
    },
    "customerId": "f51b86dd-aaba-485e-b14d-65cbea28b8e4",
    "securityGroupId": "af2fba23-5fb4-4d14-b406-0aac501f00c8"
  }
]
```

### HTTP Request
`POST https://api.beta.polisapp.com/v1/segments/swap-precedences`
