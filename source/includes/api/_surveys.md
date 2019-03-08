# Surveys

## The survey object

```json
{
  "id": "07d8e307-a545-4ff8-9698-41776e27ad3c",
  "customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466",
  "securityGroupId": "3453b386-60b5-4e58-b7f6-46b4977791ad",
  "data": {
    "name": "My Survey",
    "questions": [
      {
        "tag": "available",
        "text": "availability",
        "type": "availability",
        "options": [
          {
            "icon": "no",
            "text": "Unavailable",
            "value": "false",
            "action": {
              "type": "question",
              "questionId": "901f6503-a0b7-40a2-85a6-d582cbde346b"
            },
            "success": false
          },
          {
            "icon": "yes",
            "text": "Available",
            "value": "true",
            "action": {
              "type": "question",
              "questionId": "2a61c99a-6c37-48f0-9b0c-ea25ba4bc5e5"
            },
            "success": false
          }
        ],
        "required": false,
        "questionId": "349b5655-67eb-4898-b70b-c9097d0f300a"
      },
      {
        "tag": "unavailable_reason",
        "text": "Why were they unavailable?",
        "type": "multi-choice",
        "options": [
          {
            "text": "Not Home",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Refused",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Inaccessible",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Moved",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Other Language",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Deceased",
            "action": {
              "type": "end"
            },
            "success": false
          }
        ],
        "required": false,
        "questionId": "901f6503-a0b7-40a2-85a6-d582cbde346b"
      },
      {
        "tag": "yes-no",
        "text": "Yes/No Example",
        "type": "multi-choice",
        "options": [
          {
            "tag": "yes-no_Yes",
            "icon": "yes",
            "text": "Yes",
            "value": "true",
            "action": {
              "type": "question",
              "questionId": "4a729102-7f54-4b46-8025-1095dfbb6a3c"
            },
            "success": true
          },
          {
            "tag": "yes-no_No",
            "icon": "yes",
            "text": "No",
            "value": "false",
            "action": {
              "type": "end"
            },
            "success": false
          }
        ],
        "required": false,
        "questionId": "2a61c99a-6c37-48f0-9b0c-ea25ba4bc5e5"
      },
      {
        "tag": "select-q",
        "text": "Select q",
        "type": "multi-select",
        "choices": [
          {
            "tag": "select-q_select1",
            "text": "select1",
            "success": false
          },
          {
            "tag": "select-q_select2",
            "text": "select2",
            "success": false
          }
        ],
        "options": [
          {
            "tag": "select-q_Submit",
            "icon": "yes",
            "text": "Submit",
            "action": {
              "type": "end"
            },
            "success": false
          }
        ],
        "required": false,
        "questionId": "14fafa64-9976-4f4b-a41a-cf018ee7d6c1"
      }
    ],
    "campaignId": "0cb2dc71-73ba-4eca-977c-548085328521",
    "discoverable": false,
  },
  "meta": {
    "created": "2018-09-19T13:32:05.413Z",
    "modified": "2018-09-19T14:05:51.234Z",
    "resource": "surveys",
    "createdBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
    "isDeleted": false,
    "modifiedBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
    "etag": "1337-5aJR1+zTeNml3uPDvBIhCZjsYm4"
  }
}
```

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Unique identifier for the object.
customerId | true | Customer this resource belongs to.
securityGroupId | true | Security group of this resource.
data | true | Survey data.

### data

Attribute | Required? | Description
--------- | --------- | -----------
campaignId | true | Identifier of the campaign that this survey belongs to.
discoverable | false | Boolean value that allow a survey to be shared between organizations. Default value is `false`.
name | true | Name of the survey.
questions | false | Array of questions.

### data/questions

Attribute | Required? | Description
--------- | --------- | -----------
questionId | false | Identifier of the question. By default a new id is generated.
text | true | Text of the question.
tag | true | Question tag.
options | true | Array of options. The option object depends on the type.
type | true | Type of a question. Can be `availability`, `multi-choice`, `multi-select`, `payment`, `pdf`, `scale`, `text`, `verification`or `youtube`.

For each type of question the option object will change and it may be that more attributes are added to the option.

Types:
#### availability

Attribute | Required? | Description
--------- | --------- | -----------
options | true | Array of possible options. Minimum of 2 options.

#### multi-choice

Attribute | Required? | Description
--------- | --------- | -----------
options | true | Array of possible options. Minimum of 2 options.

#### multi-select
Attribute | Required? | Description
--------- | --------- | -----------
options | true | Array of possible options. Minimum of 1 options.
choices | true | Array of possible choices. Minimum of 1 choice.

#### payment
Attribute | Required? | Description
--------- | --------- | -----------
options | true | Array of possible options. Minimum of 2 options.

#### pdf
Attribute | Required? | Description
--------- | --------- | -----------
options | true | Array of possible options. Must be 2 options.
url | true | String containing the url to the pdf.

#### scale
Attribute | Required? | Description
--------- | --------- | -----------
options | true | Array of possible options. Must be 5 options.

#### text
Attribute | Required? | Description
--------- | --------- | -----------
options | true | Array of possible options. Must be 2 options.
multiline | false | Defines if the text input is multiline. Default value is `false`.
max | false | Max size of the input string. Default `256`.
keyboard | false | Type of input. Can be `text`, `email`, `number`. Default value is `text`.
placeholder | false | Input placeholder. Default is an empty string.

#### verification
Attribute | Required? | Description
--------- | --------- | -----------
options | true | Array of possible options. Minimum of 1 options and maximum of 2 options.

#### youtube
Attribute | Required? | Description
--------- | --------- | -----------
options | true | Array of possible options. Minimum of 1 options and maximum of 2 options.
url | true | String containing the url to the youtube video.

### Option Object

The `icon` or `text` is required.

Attribute | Required? | Description
--------- | --------- | -----------
text | false | Description text of the option.
icon | false | Icon that will appear on the app. Can be `face-neutral`, `face-happy`, `face-sad`, `face-happiest`, `face-saddest`, `yes`, `no` or `questionmark`.
tag | false | Tag of the option.
success | false | Makes this option a success if `true`. By default is set to `false`.
value | false | Value of the option.
action | false | Action executed if the option is selected.

### Action Object

The action object is used to define the order of questions of a survey.
When an option of a question is selected, if it's action equals to `question` then next question will be called and if it's action type equals to `end`, the survey will finish.

Attribute | Required? | Description
--------- | --------- | -----------
type | false | Type of action that will be executed. Can be `question` or `end`.
questionId | false | Identifier of the next question.

### meta

[See documentation](#metadata-object).

## Create a survey

> Default Survey Example Request

```
http
POST /surveys HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
  "data": {
    "name": "My Survey",
    "campaignId": "0cb2dc71-73ba-4eca-977c-548085328521",
    "questions": [
      {
        "questionId": "349b5655-67eb-4898-b70b-c9097d0f300a",
        "text": "availability",
        "type": "availability",
        "tag": "available",
        "options": [
          {
            "text": "Unavailable",
            "icon": "no",
            "value": "false",
            "action": {
              "type": "question",
              "questionId": "901f6503-a0b7-40a2-85a6-d582cbde346b"
            }
          },
          {
            "text": "Available",
            "icon": "yes",
            "value": "true",
            "action": {
              "type": "end"
            }
          }
        ]
      },
      {
        "questionId": "901f6503-a0b7-40a2-85a6-d582cbde346b",
        "text": "Why were they unavailable?",
        "type": "multi-choice",
        "tag": "unavailable_reason",
        "options": [
          {
            "text": "Not Home",
            "action": {
              "type": "end"
            }
          },
          {
            "text": "Refused",
            "action": {
              "type": "end"
            }
          },
          {
            "text": "Inaccessible",
            "action": {
              "type": "end"
            }
          },
          {
            "text": "Moved",
            "action": {
              "type": "end"
            }
          },
          {
            "text": "Other Language",
            "action": {
              "type": "end"
            }
          },
          {
            "text": "Deceased",
            "action": {
              "type": "end"
            }
          }
        ]
      }
    ]
  }
}
```

> Example Response

```json
{
  "id": "07d8e307-a545-4ff8-9698-41776e27ad3c",
  "customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466",
  "securityGroupId": "3453b386-60b5-4e58-b7f6-46b4977791ad",
  "data": {
    "name": "My Survey",
    "questions": [
      {
        "tag": "available",
        "text": "availability",
        "type": "availability",
        "options": [
          {
            "icon": "no",
            "text": "Unavailable",
            "value": "false",
            "action": {
              "type": "question",
              "questionId": "901f6503-a0b7-40a2-85a6-d582cbde346b"
            },
            "success": false
          },
          {
            "icon": "yes",
            "text": "Available",
            "value": "true",
            "action": {
              "type": "end"
            },
            "success": false
          }
        ],
        "required": false,
        "questionId": "349b5655-67eb-4898-b70b-c9097d0f300a"
      },
      {
        "tag": "unavailable_reason",
        "text": "Why were they unavailable?",
        "type": "multi-choice",
        "options": [
          {
            "text": "Not Home",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Refused",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Inaccessible",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Moved",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Other Language",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Deceased",
            "action": {
              "type": "end"
            },
            "success": false
          }
        ],
        "required": false,
        "questionId": "901f6503-a0b7-40a2-85a6-d582cbde346b"
      }
    ],
    "campaignId": "0cb2dc71-73ba-4eca-977c-548085328521",
    "discoverable": false
  },
  "meta": {
    "etag": "58d-WRUgjR0jOoXcOLr8v2hd3n7p69E",
    "created": "2018-09-19T13:32:05.413Z",
    "modified": "2018-09-19T13:32:05.413Z",
    "resource": "surveys",
    "createdBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
    "isDeleted": false,
    "modifiedBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3"
  }
}
```

Creates a new survey.

### HTTP Request

`POST https://api.polisapp.com/surveys`

## Retrieve a survey

> Example Request

```http
GET /surveys/07d8e307-a545-4ff8-9698-41776e27ad3c HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "id": "07d8e307-a545-4ff8-9698-41776e27ad3c",

  "customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466",
  "securityGroupId": "3453b386-60b5-4e58-b7f6-46b4977791ad",
  "data": {
    "name": "My Survey",
    "questions": [
      {
        "tag": "available",
        "text": "availability",
        "type": "availability",
        "options": [
          {
            "icon": "no",
            "text": "Unavailable",
            "value": "false",
            "action": {
              "type": "question",
              "questionId": "901f6503-a0b7-40a2-85a6-d582cbde346b"
            },
            "success": false
          },
          {
            "icon": "yes",
            "text": "Available",
            "value": "true",
            "action": {
              "type": "question",
              "questionId": "2a61c99a-6c37-48f0-9b0c-ea25ba4bc5e5"
            },
            "success": false
          }
        ],
        "required": false,
        "questionId": "349b5655-67eb-4898-b70b-c9097d0f300a"
      },
      {
        "tag": "unavailable_reason",
        "text": "Why were they unavailable?",
        "type": "multi-choice",
        "options": [
          {
            "text": "Not Home",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Refused",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Inaccessible",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Moved",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Other Language",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Deceased",
            "action": {
              "type": "end"
            },
            "success": false
          }
        ],
        "required": false,
        "questionId": "901f6503-a0b7-40a2-85a6-d582cbde346b"
      },
    ],
    "campaignId": "0cb2dc71-73ba-4eca-977c-548085328521",
    "discoverable": false,
  },
  "meta": {
    "created": "2018-09-19T13:32:05.413Z",
    "modified": "2018-09-19T14:05:51.234Z",
    "resource": "surveys",
    "createdBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
    "isDeleted": false,
    "modifiedBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
    "etag": "1337-5aJR1+zTeNml3uPDvBIhCZjsYm4"
  }
}
```

Obtains a single survey object by it's id.

### HTTP Request

`GET https://api.polisapp.com/surveys/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | Unique identifier of the survey.

## Update a survey

To add a new question you have to include it with the other questions and send a patch request like in the example.
Make sure that the actions are properly set to order your questions survey flow correctly.

<aside class="notice">
You can only patch attributes inside <b>data</b> key.
</aside>

[RFC 6902 - JavaScript Object Notation (JSON) Patch](https://tools.ietf.org/html/rfc6902)

> Example Request

```http
PATCH /surveys/f2636525-36d7-439c-924d-a2aaf3848716 HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
ETag: {etag_value}
{
  "data": [
    {
      "op": "replace",
      "path": "/questions",
      "value": [
        {
          "tag": "available",
          "text": "availability",
          "type": "availability",
          "options": [
            {
              "icon": "no",
              "text": "Unavailable",
              "value": "false",
              "action": {
                "type": "question",
                "questionId": "901f6503-a0b7-40a2-85a6-d582cbde346b"
              },
              "success": false
            },
            {
              "icon": "yes",
              "text": "Available",
              "value": "true",
              "action": {
                "type": "question",
                "questionId": "2a61c99a-6c37-48f0-9b0c-ea25ba4bc5e5"
              },
              "success": false
            }
          ],
          "required": false,
          "questionId": "349b5655-67eb-4898-b70b-c9097d0f300a"
        },
        {
          "tag": "unavailable_reason",
          "text": "Why were they unavailable?",
          "type": "multi-choice",
          "options": [
            {
              "text": "Not Home",
              "action": {
                "type": "end"
              },
              "success": false
            },
            {
              "text": "Refused",
              "action": {
                "type": "end"
              },
              "success": false
            },
            {
              "text": "Inaccessible",
              "action": {
                "type": "end"
              },
              "success": false
            },
            {
              "text": "Moved",
              "action": {
                "type": "end"
              },
              "success": false
            },
            {
              "text": "Other Language",
              "action": {
                "type": "end"
              },
              "success": false
            },
            {
              "text": "Deceased",
              "action": {
                "type": "end"
              },
              "success": false
            }
          ],
          "required": false,
          "questionId": "901f6503-a0b7-40a2-85a6-d582cbde346b"
        },
        {
          "tag": "yes-no",
          "text": "Yes/No Example",
          "type": "multi-choice",
          "options": [
            {
              "tag": "yes-no_Yes",
              "icon": "yes",
              "text": "Yes",
              "value": "true",
              "action": {
                "type": "end"
              },
              "success": true
            },
            {
              "tag": "yes-no_No",
              "icon": "yes",
              "text": "No",
              "value": "false",
              "action": {
                "type": "end"
              },
              "success": false
            }
          ],
          "required": false,
          "questionId": "2a61c99a-6c37-48f0-9b0c-ea25ba4bc5e5"
        }
      ]
    }
  ]
}
```

> Example Response

```json
{
  "id": "07d8e307-a545-4ff8-9698-41776e27ad3c",
  "data": {
    "name": "My Survey",
    "questions": [
      {
        "tag": "available",
        "text": "availability",
        "type": "availability",
        "options": [
          {
            "icon": "no",
            "text": "Unavailable",
            "value": "false",
            "action": {
              "type": "question",
              "questionId": "901f6503-a0b7-40a2-85a6-d582cbde346b"
            },
            "success": false
          },
          {
            "icon": "yes",
            "text": "Available",
            "value": "true",
            "action": {
              "type": "question",
              "questionId": "2a61c99a-6c37-48f0-9b0c-ea25ba4bc5e5"
            },
            "success": false
          }
        ],
        "required": false,
        "questionId": "349b5655-67eb-4898-b70b-c9097d0f300a"
      },
      {
        "tag": "unavailable_reason",
        "text": "Why were they unavailable?",
        "type": "multi-choice",
        "options": [
          {
            "text": "Not Home",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Refused",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Inaccessible",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Moved",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Other Language",
            "action": {
              "type": "end"
            },
            "success": false
          },
          {
            "text": "Deceased",
            "action": {
              "type": "end"
            },
            "success": false
          }
        ],
        "required": false,
        "questionId": "901f6503-a0b7-40a2-85a6-d582cbde346b"
      },
      {
        "tag": "yes-no",
        "text": "Yes/No Example",
        "type": "multi-choice",
        "options": [
          {
            "tag": "yes-no_Yes",
            "icon": "yes",
            "text": "Yes",
            "value": "true",
            "action": {
              "type": "question",
              "questionId": "4a729102-7f54-4b46-8025-1095dfbb6a3c"
            },
            "success": true
          },
          {
            "tag": "yes-no_No",
            "icon": "yes",
            "text": "No",
            "value": "false",
            "action": {
              "type": "end"
            },
            "success": false
          }
        ],
        "required": false,
        "questionId": "2a61c99a-6c37-48f0-9b0c-ea25ba4bc5e5"
      },
    ],
    "campaignId": "0cb2dc71-73ba-4eca-977c-548085328521",
    "discoverable": false,
  },
  "meta": {
    "created": "2018-09-19T13:32:05.413Z",
    "modified": "2018-09-19T14:05:51.234Z",
    "resource": "surveys",
    "createdBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
    "isDeleted": false,
    "modifiedBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
    "etag": "1337-5aJR1+zTeNml3uPDvBIhCZjsYm4"
  },
  "customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466",
  "securityGroupId": "3453b386-60b5-4e58-b7f6-46b4977791ad"
}

```

### HTTP Request

`PATCH https://api.polisapp.com/surveys/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | Unique identifier of the survey.

## Delete a survey

> Example Request

```http
DELETE https://api.polisapp.com/surveys/f2636525-36d7-439c-924d-a2aaf3848716
Host: api.polisapp.com
Authorization: Bearer {access_token}
ETag: {etag_value}
```

### HTTP Request
`DELETE https://api.polisapp.com/surveys/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | Unique identifier of the survey.

## Get many surveys

Retrieved two surveys from the same campaign.

> Example Request

```http
GET /surveys?filter=%2Fdata%2FcampaignId%20eq%20%220cb2dc71-73ba-4eca-977c-548085328521%22&limit=10&skip=0&sort=%5B%22data%2Fname%22%2C%22ASC%22%5D HTTP/1.1
Host: api.polisapp.com
Authorization: Bearer {access_token}
```

> Example Response

```json
{
  "data": [
    {
      "id": "f2cf5cad-fff3-496d-9e28-e5333fe22268",
      "data": {
        "name": "Default Survey",
        "questions": [],
        "campaignId": "0cb2dc71-73ba-4eca-977c-548085328521",
        "discoverable": false
      },
      "meta": {
        "etag": "1ff-fnZHGuU/MMY7ug7UKZ/4uI8cLbQ",
        "created": "2018-09-19T13:30:42.760Z",
        "modified": "2018-09-19T13:30:42.760Z",
        "resource": "surveys",
        "createdBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
        "isDeleted": false,
        "modifiedBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3"
      },
      "customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466",
      "securityGroupId": "3453b386-60b5-4e58-b7f6-46b4977791ad"
    },
    {
      "id": "07d8e307-a545-4ff8-9698-41776e27ad3c",
      "data": {
        "name": "My Survey",
        "questions": [
          {
            "tag": "available",
            "text": "availability",
            "type": "availability",
            "options": [
              {
                "icon": "no",
                "text": "Unavailable",
                "value": "false",
                "action": {
                  "type": "question",
                  "questionId": "901f6503-a0b7-40a2-85a6-d582cbde346b"
                },
                "success": false
              },
              {
                "icon": "yes",
                "text": "Available",
                "value": "true",
                "action": {
                  "type": "question",
                  "questionId": "2a61c99a-6c37-48f0-9b0c-ea25ba4bc5e5"
                },
                "success": false
              }
            ],
            "required": false,
            "questionId": "349b5655-67eb-4898-b70b-c9097d0f300a"
          },
          {
            "tag": "unavailable_reason",
            "text": "Why were they unavailable?",
            "type": "multi-choice",
            "options": [
              {
                "text": "Not Home",
                "action": {
                  "type": "end"
                },
                "success": false
              },
              {
                "text": "Refused",
                "action": {
                  "type": "end"
                },
                "success": false
              },
              {
                "text": "Inaccessible",
                "action": {
                  "type": "end"
                },
                "success": false
              },
              {
                "text": "Moved",
                "action": {
                  "type": "end"
                },
                "success": false
              },
              {
                "text": "Other Language",
                "action": {
                  "type": "end"
                },
                "success": false
              },
              {
                "text": "Deceased",
                "action": {
                  "type": "end"
                },
                "success": false
              }
            ],
            "required": false,
            "questionId": "901f6503-a0b7-40a2-85a6-d582cbde346b"
          },
          {
            "tag": "yes-no",
            "text": "Yes/No Example",
            "type": "multi-choice",
            "options": [
              {
                "tag": "yes-no_Yes",
                "icon": "yes",
                "text": "Yes",
                "value": "true",
                "action": {
                  "type": "question",
                  "questionId": "bcf7cea1-99c4-486b-90a3-11611f043666"
                },
                "success": true
              },
              {
                "tag": "yes-no_No",
                "icon": "yes",
                "text": "No",
                "value": "false",
                "action": {
                  "type": "question",
                  "questionId": "bcf7cea1-99c4-486b-90a3-11611f043666"
                },
                "success": false
              }
            ],
            "required": false,
            "questionId": "2a61c99a-6c37-48f0-9b0c-ea25ba4bc5e5"
          },
          {
            "tag": "select-q",
            "text": "Select q",
            "type": "multi-select",
            "choices": [
              {
                "tag": "select-q_select1",
                "text": "select1",
                "success": false
              },
              {
                "tag": "select-q_select2",
                "text": "select2",
                "success": false
              }
            ],
            "options": [
              {
                "tag": "select-q_Submit",
                "icon": "yes",
                "text": "Submit",
                "action": {
                  "type": "end"
                },
                "success": false
              }
            ],
            "required": false,
            "questionId": "14fafa64-9976-4f4b-a41a-cf018ee7d6c1"
          }
        ],
        "campaignId": "0cb2dc71-73ba-4eca-977c-548085328521",
        "discoverable": true,
      },
      "meta": {
        "created": "2018-09-19T13:32:05.413Z",
        "modified": "2018-09-19T18:03:59.373Z",
        "resource": "surveys",
        "createdBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
        "isDeleted": false,
        "modifiedBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
        "etag": "a5c-UyhPHXG3X5oU8UUJo+ySk0oJg1g"
      },
      "customerId": "d94d4ae9-1221-4fea-90ae-41c1c65ff466",
      "securityGroupId": "3453b386-60b5-4e58-b7f6-46b4977791ad"
    }
  ],
  "meta": {}
}
```

### HTTP Request
`GET https://api.polisapp.com/surveys?filter={filter}&limit={limit}&skip={skip}&sort={sort}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
fiter | false | Query to filter data. [See documentation](#filters).
limit | true | Limit results returned. Useful for pagination.
skip | true | Data offset index. Useful for pagination.
sort | true | Sort column. Ex.: `["data/name","ASC"]`

Filter Example: `/data/campaignId eq "0cb2dc71-73ba-4eca-977c-548085328521"`
