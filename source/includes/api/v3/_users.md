# Users

## The user object

```json
{
  "id": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
  "data": {
    "email": "user@test.com",
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
  },
  "meta": {
    "created": "2018-08-29T17:48:58.519Z",
    "modified": "2018-09-06T18:42:28.492Z",
    "resource": "users",
    "isDeleted": false,
    "modifiedBy": "08f35132-7b4f-44d9-b212-6e5fad31aad3",
    "etag": "1b1-6WwNjE79Gtf2NqviIKmYwsfjDWg"
  }
}
```

Attribute | Required? | Description
--------- | --------- | -----------
id | true | Unique identifier for the object.
data | true | User data.

### data

Attribute | Required? | Description
--------- | --------- | -----------
email | true | Email that will be used to login.
profile | false | Object containing the user personal information. [details](#data/profile)
privacy | false | Object with public info available. [details](#data/privacy)
status | false | Current status of the user. Can be `active`, `pending`, `inactive`. By default is set to `pending`.

### data/profile

Attribute | Required? | Description
--------- | --------- | -----------
name | true | User name.
phone | false | Array of phone numbers.
gender | false | User gender. Can be `d` for decline, `f` for female, `m` for male, `n` for non-binary or `o` for other.
languages | false | Array of languages that the user is familiar with. Check languages documentation for the full list.
birthdate | false | User birthdate.

### data/privacy

Attribute | Required? | Description
--------- | --------- | -----------
publicInfo | false | Array with available public info. Can have `email`, `phone`, `location`, `languages`, `gender` and `birthdate`. By default is set just to `[email]`.

### meta

[See documentation](#metadata-object).

## Create a user

> Example Request

```
http
POST /v1/users HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}

{
  "data": {
    "profile": {
      "name": {
        "anglican": {
          "given": "test",
          "surname": "user"
        }
      },
      "phone": [
        "123456789"
      ],
      "birthdate": "12/12/1993"
    },
    "status": "active",
    "email": "testapi@polisapp.com"
  },
  "params": {
    "password": "password123"
  }
}
```

> Example Response

```json
{
  "id": "9c6ce344-9ea9-49e7-95da-4cce67bd094c",
  "data": {
    "email": "testapi@polisapp.com",
    "status": "active",
    "privacy": {
      "publicInfo": [
        "email"
      ]
    },
    "profile": {
      "name": {
        "anglican": {
          "given": "TestApi",
          "surname": "TestApi"
        }
      },
      "phone": [
        "0937846"
      ],
      "birthdate": "1993-12-12T00:00:00.000Z"
    }
  },
  "meta": {
    "etag": "190-3txcvnZCq5spapPJPuCEeKLLlYM",
    "created": "2018-09-21T16:19:53.512Z",
    "modified": "2018-09-21T16:19:53.512Z",
    "resource": "users",
    "isDeleted": false
  }
}
```

Creates a new user.

### HTTP Request

`POST https://api.polisapp.com/v1/users`

## Update a user

> Example Request

```http
PATCH /v1/users/c153c65c-f51b-4caa-b6ca-f66d03583419 HTTP/1.1
Host: api.polisapp.com
Content-Type: application/json
Authorization: Bearer {access_token}
ETag: {etag_value}
{
  "data": [
    {
      "op": "replace",
      "path": "/profile/name/anglican/given",
      "value": "New First Name"
    },
    {
      "op": "replace",
      "path": "/profile/name/anglican/surname",
      "value": "New Last Name"
    }
  ]
}
```

> Example Response

```json
{
  "id": "c153c65c-f51b-4caa-b6ca-f66d03583419",
  "data": {
    "email": "testapi@polisapp.com",
    "status": "active",
    "privacy": {
      "publicInfo": [
        "email"
      ]
    },
    "profile": {
      "name": {
        "anglican": {
          "given": "New First Name",
          "surname": "New Last Name"
        }
      },
      "gender": "d"
    }
  },
  "meta": {
    "created": "2018-01-23T16:14:30.278Z",
    "modified": "2018-12-18T01:48:40.186Z",
    "resource": "users",
    "createdBy": "b80c41ad-37ad-4388-a587-14ab6e3b2c0c",
    "isDeleted": false,
    "modifiedBy": "b80c41ad-37ad-4388-a587-14ab6e3b2c0c",
    "etag": "1f4-uK48XPpi6Vp9sDge6U5xfoFnFZM"
  }
}
```
<aside class="notice">
You can only patch attributes inside <b>data</b> key.
</aside>

[RFC 6902 - JavaScript Object Notation (JSON) Patch](https://tools.ietf.org/html/rfc6902)

### HTTP Request

`PATCH https://api.polisapp.com/v1/users/{userId}`

