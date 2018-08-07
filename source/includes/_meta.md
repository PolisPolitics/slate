# Metadata object

```json
{
  ...
  "meta": {
    "created": "2017-12-15T19:46:01.594Z",
    "modified": "2017-12-15T19:46:02.219Z",
    "resource": "contacts",
    "createdBy": "11b78eab-8b3e-45e7-804c-4a94045367d4",
    "modifiedBy": "11b78eab-8b3e-45e7-804c-4a94045367d4",
    "etag": "MTUxMzM2NzE2NTI3MzM3NDcyMA==",
    "isDeleted": false
  }
}
```

Attribute | Description
--------- | -----------
etag | HTTP ETag for cache control.
created | Date this resource was created.
createdBy | Identifier of user who created this resource.
modified | Date this resource was last modified.
modifiedBy | Identifier of user who last modified this resource.
resource | Resource name (e.g.: lists, contacts)
isDeleted | Flag indicating if the resource has been deleted.