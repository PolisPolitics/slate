# Households

## The Household object

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Identifier of this record.
securityGroupId | true | Identifier of the associated security group.
customerId | true | Identifier of the associated customer.
data | true | Household data. Should be either [addressId](#addressId) OR [fullAddress](#fullAddress).

### addressId

Attribute | Required? | Description
--------- | --------- | -----------
unitNum | true | The unit number.
addressId | true | Identifier of a address.

### fullAddress

Attribute | Required? | Description
--------- | --------- | -----------
address | true | [Address](#address) with an identifier.

### address

Attribute | Required? | Description
--------- | --------- | -----------
address | true | Full address.
streetName | true | Name of the street.
city | true | Name of the city.
country | false | Name of the country.
county | false | Name of the county.
neighborhood | false | Name of the neighborhood.
state | false | Name of the state.
postalCode | false | Name of the postalCode.
coords | false | Name of the coords.

### data/coords

Attribute | Required? | Description
--------- | --------- | -----------
lat | true | Latitude.
lng | true | Longitude.
confidence | true | GPS Accuracy.

### meta

[See documentation](#metadata-object)



```json
{
	"id": "1b6e3e26-511c-48c5-ab38-1317072f7276",
	"data": {
		"unitNum": "Apt. 2",
		"addressId": "d58ff153-ddd4-4b91-9f80-07de095b1b19"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:30.088Z",
		"modified": "2019-04-03T18:55:30.088Z",
		"resource": "households",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

## Get many households

> Example Request

```http
GET /v2/households?filter%5B%2FcustomerId%5D=286d1af1-c2c5-4069-a19d-3987fdacc0d6&skip=0&limit=9007199254740991&sort=id&sort=ASC HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"data": [
		{
			"id": "1b6e3e26-511c-48c5-ab38-1317072f7276",
			"data": {
				"unitNum": "Apt. 2",
				"addressId": "d58ff153-ddd4-4b91-9f80-07de095b1b19"
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:30.088Z",
				"modified": "2019-04-03T18:55:30.088Z",
				"resource": "households",
				"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
				"isDeleted": false,
				"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		},
		{
			"id": "b810c49b-9585-46a3-9e62-77b48c293d88",
			"data": {
				"unitNum": "Apt. 1",
				"addressId": "3a2be50d-a8bc-47b4-833f-1962ef197751"
			},
			"meta": {
				"etag": "",
				"created": "2019-04-03T18:55:30.088Z",
				"modified": "2019-04-03T18:55:30.088Z",
				"resource": "households",
				"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
				"isDeleted": false,
				"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
			},
			"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
			"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
		}
	],
	"meta": {}
}
```

### HTTP Request

`GET https://api.beta.polisapp.com/v2/households`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
filter | false | Query to filter data. `/customerId eq "eb4dfe83-f1fd-46dd-a69d-b7cf7b566319"`
limit | true | Limits number of result-rows. Should be a positive integer. Useful for pagination.
skip | true | Offset data by given number. Useful for pagination.
sort | true | Sort the column in `ASC` or `DESC` e.g. ['id', 'ASC']


### Allowed attributes

List of attributes that are allowed to be used in a filter query.

* `/customerId`
* `/data/unitNum`
* `/data/addressId`


## Get a household

> Example Request

```http
GET /v2/households/1b6e3e26-511c-48c5-ab38-1317072f7276 HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
```

> Example Response

```json
{
	"id": "1b6e3e26-511c-48c5-ab38-1317072f7276",
	"data": {
		"unitNum": "Apt. 2",
		"addressId": "d58ff153-ddd4-4b91-9f80-07de095b1b19"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:30.088Z",
		"modified": "2019-04-03T18:55:30.088Z",
		"resource": "households",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`GET https://api.beta.polisapp.com/v2/households/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the household to be retrieved.


## Create a household

> Example Request

```http
POST /v2/households HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
{
	"data": {
		"unitNum": "Apt. 2",
		"address": {
			"data": {
				"number": "1",
				"streetName": "Morris Stream",
				"city": "North Vincefurt",
				"coords": {
					"lat": 42.3795514,
					"lng": -71.2525621
				},
				"country": "USA",
				"county": null,
				"neighborhood": null,
				"state": "Idaho",
				"postalCode": "25079-7079"
			}
		}
	},
	"customerId": "b1b101cf-646c-4ad2-86e7-9683209b1633"
}
```

> Example Response

```json
{
	"id": "1b6e3e26-511c-48c5-ab38-1317072f7276",
	"data": {
		"unitNum": "Apt. 2",
		"addressId": "d58ff153-ddd4-4b91-9f80-07de095b1b19"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:30.088Z",
		"modified": "2019-04-03T18:55:30.088Z",
		"resource": "households",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`POST https://api.beta.polisapp.com/v2/households`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
customerId | true | The id of the customer to which this resoruce belongs
data | true | The data of household to be created


## Update a household

> Example Request

```http
PATCH /v2/households/1b6e3e26-511c-48c5-ab38-1317072f7276 HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
{
	"data": [
		{
			"op": "replace",
			"path": "/unitNum",
			"value": "Apt. 3"
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
	"id": "1b6e3e26-511c-48c5-ab38-1317072f7276",
	"data": {
		"unitNum": "Apt. 3",
		"addressId": "d58ff153-ddd4-4b91-9f80-07de095b1b19"
	},
	"meta": {
		"etag": "",
		"created": "2019-04-03T18:55:30.088Z",
		"modified": "2019-04-04T19:35:30.088Z",
		"resource": "households",
		"createdBy": "cff4a05f-2612-471d-821d-8782627d42aa",
		"isDeleted": false,
		"modifiedBy": "cff4a05f-2612-471d-821d-8782627d42aa"
	},
	"customerId": "286d1af1-c2c5-4069-a19d-3987fdacc0d6",
	"securityGroupId": "3b825553-4f43-4893-a960-b642ba676fa0"
}
```

### HTTP Request

`PATCH https://api.beta.polisapp.com/v2/households/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the household to be updated
data | true | The patch data 


## Delete an item from households

> Example Request

```http
DELETE /v2/households/1b6e3e26-511c-48c5-ab38-1317072f7276 HTTP/1.1
Host: api.beta.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
etag: etag_value
```

### HTTP Request

`DELETE https://api.beta.polisapp.com/v2/households/{id}`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
id | true | The id of the household to be deleted.


## Create Many Households

> Example Request

```http
POST /v2/households/bulk HTTP/1.1
Host: api.beta.polisapp.com
Contact-Type: application/json
Authorization: Bearar {access_token}
{
  "data": [
    {
      "data": {
        "unitNum": "Apt. 2L",
        "address": {
          "data": {
            "number": "1",
            "streetName": "Daphney Knoll",
            "city": "Rempelfurt",
            "coords": {
              "lat": 42.3795514,
              "lng": -71.2525621
            },
            "country": "",
            "county": null,
            "neighborhood": null,
            "state": "Massachusetts",
            "postalCode": "69864-4637"
          }
        },
        "formattedAddress": "1 Daphney Knoll #Apt. 2L Rempelfurt  69864-4637"
      },
      "customerId": "36ab287b-567d-4fea-a001-297991db46cb"
    },
    
    {
      "data": {
        "unitNum": "Apt. 1",
        "address": {
          "data": {
            "number": "1",
            "streetName": "Mathilde Unions",
            "city": "North Pinkietown",
            "coords": {
              "lat": 42.3795514,
              "lng": -71.2525621
            },
            "country": "",
            "county": null,
            "neighborhood": null,
            "state": "Maryland",
            "postalCode": "48828"
          }
        },
        "formattedAddress": "1 Mathilde Unions #Apt. 1 North Pinkietown  48828"
      },
      "customerId": "36ab287b-567d-4fea-a001-297991db46cb"
    }
  ]
}

```

> Example Response

```json
{
  "data": [
     {
       "id": "11289ba8-3a58-468f-afe4-f048971a7a10",
       "data": {
         "address": {
           "id": "7596674d-3aa5-49d3-a9d1-b7ef81e4a9b3",
           "data": {
             "city": "Rempelfurt",
             "state": "Massachusetts",
             "coords": {
               "lat": 42.3795514,
               "lng": -71.2525621
             },
             "number": "1",
             "country": "",
             "postalCode": "69864-4637",
             "streetName": "Daphney Knoll"
           }
         },
         "unitNum": "Apt. 2L",
         "formattedAddress": "1 Daphney Knoll #Apt. 2L Rempelfurt  69864-4637"
       },
       "meta": {
         "etag": "21e-FmBn+WqCu6/TxglSKS0qQWwO4zM",
         "created": "2020-02-04T14:08:46.514Z",
         "modified": "2020-02-04T14:08:46.514Z",
         "resource": "households",
         "createdBy": "54b43387-1235-4fca-b37c-deecee83c80e",
         "isDeleted": false,
         "modifiedBy": "54b43387-1235-4fca-b37c-deecee83c80e"
       },
       "customerId": "36ab287b-567d-4fea-a001-297991db46cb",
       "securityGroupId": "cf344bd5-1ab9-4e50-8818-741fc1c0eeb2"
     },
     {
       "id": "c2722281-dbac-421e-b465-9000e5216259",
       "data": {
         "address": {
           "id": "1c32714e-9190-40b5-a44a-b8309f187f41",
           "data": {
             "city": "North Pinkietown",
             "state": "Maryland",
             "coords": {
               "lat": 42.3795514,
               "lng": -71.2525621
             },
             "number": "1",
             "country": "",
             "postalCode": "48828",
             "streetName": "Mathilde Unions"
           }
         },
         "unitNum": "Apt. 1",
         "formattedAddress": "1 Mathilde Unions #Apt. 1 North Pinkietown  48828"
       },
       "meta": {
         "etag": "21f-gDxPlK+jBKBa64RyIbM2quMRX6M",
         "created": "2020-02-04T14:08:46.515Z",
         "modified": "2020-02-04T14:08:46.515Z",
         "resource": "households",
         "createdBy": "54b43387-1235-4fca-b37c-deecee83c80e",
         "isDeleted": false,
         "modifiedBy": "54b43387-1235-4fca-b37c-deecee83c80e"
       },
       "customerId": "36ab287b-567d-4fea-a001-297991db46cb",
       "securityGroupId": "cf344bd5-1ab9-4e50-8818-741fc1c0eeb2"
     }
  ],
  "meta": {}
}
```

### HTTP Request

`POST https://api.beta.polisapp.com/v2/households/bulk`



