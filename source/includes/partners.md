# Partners

REST endpoints that allow you to create, retrieve, update and delete partners.

## Partner Properties

| Property     | Type     | Required  | Description                                   |
| ------------ | ---------| ----------| --------------------------------------------- |
| \_id         | String   | Automatic <td style="width:100%;"> ID of this record  </td>
| email        | String   | Required  | The business email for this partner           |
| active       | Boolean  | Required  | Do you want to sync with them?                |
| invited      | Boolean  | Automatic | Have they been invited?                       |
| billing      | Boolean  | Optional  | Do you want to bill them here?                |
| priceList    | String   | Optional  | The name of their price list                  |
| relationship | String   | Required  | Relative to you: 'parent', 'child' or 'self'  |
| itemLookup   | Array    | Optional  | A reference of your item codes and theirs     |
| custom       | Array    | Optional  | Custom key/value pairs                        |
| live         | Boolean  | Automatic | True for live mode, false for test mode       |
| created      | Date     | Automatic | Date record was created (in ISO8601 format)   |
| updated      | Date     | Automatic | Date record was updated (in ISO8601 format)   |
| companyId    | String   | Automatic | Your company ID                               |

## Get Partner by ID

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "email": "capartner@example.com",
  "active": true,
  "invited": true,
  "billing": true,
  "itemLookup": [
    {
      "myId": "12345",
      "yourId": "ABC123"
    },
    {
      "myId": "56789",
      "yourId": "XYZ098"
    }
  ],
  "priceList": "Price List for Canada",
  "relationship": "child",
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "live": true,
  "companyId": "convictional-wholesale"
}
```

This endpoint returns a single partner by ID.

### Endpoint

`https://api.convictional.com/partners/:id`

### Request example

`GET https://api.convictional.com/partners/5a692f658f6d524e8282dac7`

## Get Partners by Query

> Returns (JSON):

```json
[
  {
    "_id": "5a692f658f6d524e8282dac7",
    "email": "capartner@example.com",
    "active": true,
    "invited": true,
    "billing": true,
    "itemLookup": [
      {
        "myId": "12345",
        "yourId": "ABC123"
      },
      {
        "myId": "56789",
        "yourId": "XYZ098"
      }
    ],
    "priceList": "Price List for Canada",
    "relationship": "child",
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "live": true,
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac7",
    "email": "uspartner@example.com",
    "active": true,
    "invited": true,
    "billing": true,
    "itemLookup": [
      {
        "myId": "12345",
        "yourId": "ABC123"
      },
      {
        "myId": "56789",
        "yourId": "XYZ098"
      }
    ],
    "priceList": "Price List for USA",
    "relationship": "child",
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "live": true,
    "companyId": "convictional-wholesale"
  }
]
```

This endpoint returns all your partners.

### Endpoint

`https://api.convictional.com/partners`

### Open example

`GET https://api.convictional.com/partners`

### Filtered example

`GET https://api.convictional.com/partners?createdBefore=2018-02-28T11:26:43.000-0500`

### Query Parameters

| Property      | Type      | Required  | Description                                       |
| ------------  | --------- | ----------| --------------------------------------------------|
| fields        | String    | Optional  | Return only the specified fields, comma separated |
| page          | Number    | Optional  | Return only records on a specific page            |
| limit         | Number    | Optional  | Return up to this number of records               |
| count         | Boolean   | Optional  | Return a count of documents, defaults to false    |
| active        | Boolean   | Optional  | Filter by active status (true or false)           |
| invited       | Boolean   | Optional  | Filter by invited status (true or false)          |
| relationship  | String    | Optional  | Filter by relationship (child, self or parent)    |
| createdBefore | Date      | Optional  | Filter records created before this date (ISO8601) |
| createdAfter  | Date      | Optional  | Filter records created after this date (ISO8601)  |
| updatedBefore | Date      | Optional  | Filter records updated before this date (ISO8601) |
| updatedAfter  | Date      | Optional  | Filter records updated after this date (ISO8601)  |
| live          | Boolean   | Optional  | Filter by live mode status (true or false)        |

## Create Partner

> Request Body (JSON):

```json
{
  "email": "capartner@example.com",
  "priceList": "Price List for Canada",
  "relationship": "child"
}
```

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
    "email": "capartner@example.com",
    "active": true,
    "invited": true,
    "billing": true,
  "itemLookup": [
    {
      "myId": "12345",
      "yourId": "ABC123"
    },
    {
      "myId": "56789",
      "yourId": "XYZ098"
    }
  ],
  "priceList": "Price List for Canada",
  "relationship": "child",
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "live": true,
  "companyId": "convictional-wholesale"
}
```

This endpoint creates a new partner.

### Endpoint

`https://api.convictional.com/partners`

### Request example

`POST https://api.convictional.com/partners`

## Update Partner

> Request Body (JSON):

```json
{
  "active": false
}
```

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "email": "capartner@example.com",
  "active": true,
  "invited": true,
  "billing": true,
  "itemLookup": [
    {
      "myId": "12345",
      "yourId": "ABC123"
    },
    {
      "myId": "56789",
      "yourId": "XYZ098"
    }
  ],
  "priceList": "Price List for Canada",
  "relationship": "child",
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "live": true,
  "companyId": "convictional-wholesale"
}
```

This endpoint updates a single partner by ID.

### Endpoint

`https://api.convictional.com/partners/:id`

### Request example

`PUT https://api.convictional.com/partners/5a692f658f6d524e8282dac7`

## Bulk Update/Create

> Request Body (JSON):

```json
{
  "partners": [
    {
      "email": "capartner@example.com",
      "priceList": "Price List for Canada",
      "relationship": "child",
    },
    {
      "email": "uspartner@example.com",
      "priceList": "Price List for USA",
      "relationship": "child",
    }
  ]
}
```

> Returns (JSON):

```json
{
  "updated": 2
}
```

This endpoint updates (or creates) partners. If the email matches an existing record, it will update. Otherwise, it will create. Maximum is 100 records, above that please send multiple requests to this endpoint.

### Endpoint

`https://api.convictional.com/partners`

### Request example

`PUT https://api.convictional.com/partners`

## Delete Partner

> Returns (JSON):

```json
{
  "deleted": 1
}
```

This endpoint deletes a single partner by ID.

### Endpoint

`https://api.convictional.com/partners/:id`

### Request example

`DELETE https://api.convictional.com/partners/5a692f658f6d524e8282dac7`