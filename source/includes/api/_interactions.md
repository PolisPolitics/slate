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
              "fields": {
                "dogliker": "true"
              },
              "questionId": "6430c7c8-364c-4fa5-b145-9dbaa2795f7d"
            },
            "789bb27d-101d-4021-ba8d-06b02eaf736f": {
              "fields": {
                "mothername": "Jane Doe"
              },
              "questionId": "789bb27d-101d-4021-ba8d-06b02eaf736f"
            },
            "ac3f2a70-c7b1-4d25-a5ea-135233c5437c": {
              "fields": {
                "available": "true"
              },
              "questionId": "ac3f2a70-c7b1-4d25-a5ea-135233c5437c"
            },
            "b21d978b-0a48-42c3-9c3a-c24fff0236f2": {
              "fields": {
                "bestpet": "Cat"
              },
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
              "fields": {
                "catlikeness": 4
              },
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