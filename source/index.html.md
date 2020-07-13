---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the Paymints API! You can use our API to access Paymints API endpoints.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Paymints uses API keys to allow access to the API. You can register a new API key.

Paymints expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: your-api-key`

<aside class="notice">
You must replace <code>your-api-key</code> with your personal API key.
</aside>

# Users

## Get All Users

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/users"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  
]
```

This endpoint returns the list of users.

### HTTP Request

`GET http://example.com/api/users`


<aside class="success">
Remember — a happy user is an authenticated user!
</aside>

## Get All Users for a tenant

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/users/**********"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "users" : [
      {
        "created_at": "2020-06-04T19:07:11.523Z",
        "email": "XXXXXXX@gmail.com",
        "email_verified": false,
        "identities": [
            {
                "connection": "email",
                "user_id": "5ed9465f580a1d9af47e7ffa",
                "provider": "email",
                "isSocial": false
            }
        ],
        "name": "XXXXX XXXXXX",
        "nickname": "XXXX",
        "picture": "https://s.gravatar.com/avatar/048a48bd768f393614278f49a788446c?s=480&r=pg&d=https%3A%2F%2Fcdn.auth0.com%2Favatars%2Fah.png",
        "updated_at": "2020-06-04T19:36:08.944Z",
        "user_id": "email|5ed9465f580a1d9af47e7ffa",
        "user_metadata": {
            "tenant_GUID": "**********"
        }
      } , 

      {
      "created_at": "2020-06-04T14:56:15.245Z",
      "email": "XXXXXXXX@gmail.com",
      "email_verified": false,
      "identities": [
          {
              "connection": "email",
              "user_id": "5ed90b8f580a1d9af4bb7381",
              "provider": "email",
              "isSocial": false
          }
      ],
      "name": "XXXX XXXXX",
      "nickname": "XXXXX",
      "picture": "https://s.gravatar.com/avatar/5a82333368f8ae9dd46f3d8658423862?s=480&r=pg&d=https%3A%2F%2Fcdn.auth0.com%2Favatars%2Fah.png",
      "updated_at": "2020-07-08T22:57:49.700Z",
      "user_id": "email|5ed90b8f580a1d9af4bb7381",
      "user_metadata": {
          "tenant_GUID": "**********"
      }
  }

  ]
}
```

This endpoint retrieves a specific user.

### HTTP Request

`GET http://example.com/users/:tenant_GUID`

### URL Parameters

Parameter | Description
--------- | -----------
tenant_GUID | The ID of the tenant to retrieve his users.

## Get specific user for a tenant

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/users/**********/********"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
    "user": {
        "created_at": "2020-07-08T23:14:26.608Z",
        "email": "XXXXXXXXXXXXX@gmail.com",
        "email_verified": false,
        "identities": [
            {
                "connection": "email",
                "user_id": "********",
                "provider": "email",
                "isSocial": false
            }
        ],
        "name": "XXXX XXXXX",
        "nickname": "XXXXX",
        "picture": "https://s.gravatar.com/avatar/36a3afa8492137799859713f94fa9c4c?s=480&r=pg&d=https%3A%2F%2Fcdn.auth0.com%2Favatars%2Fah.png",
        "updated_at": "2020-07-11T00:33:59.412Z",
        "user_id": "********",
        "user_metadata": {
            "tenant_GUID": "**********"
        }
    }
}
```

This endpoint retrieves a specific user.

### HTTP Request

`GET http://example.com/users/:tenant_GUID/:user_GUID`

### URL Parameters

Parameter | Description
--------- | -----------
tenant_GUID | The ID of the tenant to retrieve his users.
user_GUID   | The ID of the specific user of the tenant with ID tenant_GUID.

## Adding new users

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/users/"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```
> Information needed for adding new users

```json
{
    "create_user": {
      "email": "XXXXXXXXX@gmail.com",
      "name": "XXXXX XXXXXX",
      "connection":"email"
    },
    "new_user_role": "paymints_tenant",
    "role": "paymints_admin"
}
```

> The above command returns JSON structured like this:

```json
{
    "created user info"
}
```

This endpoint adds new users. User info passed in must contain email, name, connection

### HTTP Request

`POST http://example.com/users/`

# Transfer-service (Plaid And Dwolla API Services)

## Adding verified customer to Dwolla

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/account/auth/create-client"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```


This endpoint will add a verified customer to dwolla, with a funding source, and save dwolla/plaid attributes to the database. {id, plaidAccountId, publicToken} => {success:boolean, bankAccountId}

<aside class="success">
This route can also be used for adding a bank account to a customer that already has other bank accounts. (and is already in Dwolla).
</aside>

### HTTP Request

`POST http://example.com/api/account/auth/create-client`

### URL Parameters

Parameter | Description
--------- | -----------
Id | client Id in database
plaidAccountId   | account id from plaid onSuccess
publicToken   | public token from plaid onSuccess

The following values must be saved to the Client in the DB prior to the API call: ssn, DateOfBirth, email

### Responses

Parameter | Description
--------- | -----------
successful:200 | success:true, bankAccountId
unsuccessful:400   | route, error, success:false


## Creating an EscrowAccount by adding a tenant, bank account to Plaid/Dwolla

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/account/auth/:tenant_ID/escrow"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

This endpoint adds a tenant, bank account to plaid/dwolla. Creates a EscrowAccount with the given information. This route can also be used to add a bank account to a tenant already added. { agentId, plaidAccountId, publicToken } => { success, escrowAccountId }

### HTTP Request

`POST http://example.com/account/auth/:tenant_ID/escrow`

### URL Parameters

Parameter | Description
--------- | -----------
tenant_ID | Tenant database ID
agent_ID | Agent database ID
plaidAccountId | account id from plaid onSuccess
publicToken | public token from plaid onSuccess

### Responses

Parameter | Description
--------- | -----------
successful 201 | success:true, escrowAccountId: ID
unsuccessful:400   | success:false, error: error, route: '/account/auth/create-tenant'

## Subscribing a tenant for billing

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/account/auth/:tenant_ID/billing"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

This endpoint subscribes a tenant to be billed monthly & adds a Billing Account. Authenticates account and creates new billing account connected to tenant, adds subscription to Tenant. { plaidAccountId, publictoken, subscriptionId, agentId } => { success, billingAccountId }

<aside class="success">
This route has the same Tenant, Agent, and Tenant Exec requirements as /account/auth/:tenant_ID/escrow
</aside>

### HTTP Request

`POST http://example.com/account/auth/:tenantID/billing`

### URL Parameters

Parameter | Description
--------- | -----------
tenant_ID | Tenant database ID

### Responses

Parameter | Description
--------- | -----------
successful:201 | success: true, billingAccountId: ID
unsuccessful:400 | success:false, error: error, route: '/account/auth/create-tenant'

## Initiating a transfer

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/transfer/start"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:


This endpoint is the primary route for initiating a transfer. Will initiate an ACH transfer, save dwollaStatus, dwollaSourceURL. { bankAccountId, escrowAccountId, transferId } => { success(boolean) }

### HTTP Request

`POST http://example.com/transfer/start`

### URL Parameters

Parameter | Description
--------- | -----------
bankAccountID | database ID of Bank Account that will send money
escrowAccountID | database ID of Escrow Account that will receive money
transferID | database ID of transfer, which will be updated with dwollaStatus, dwollaResourceURL, dwollaDestinationURL, dwollaTransferURL

### Responses

Parameter | Description
--------- | -----------
successful:201 | success: true
unsuccessful:400 | success:false, error: error, route: 'transfer/start'

## Finding connected Bank Accounts for a specific customer

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/account/client-accounts/5ee3ad5cbdcb012345678910"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "accounts": [ 
    { "name": "Silver Standard 0.1% Interest Saving", 
      "bankName": "Citi", 
      "accountNumber": "1111", 
      "id": "5ee3ad5cbdcb012345678910", 
      "balance": 200, 
      "institutionCode": "ins_4" , 
      "bankDisplayName": "Citi Savings" ,
      "dwollaFundingURL": "https://api-sandbox.dwolla.com/funding-sources/12345" } 
    ]
}
```

This endpoint finds connected bank accounts for specific customer, returns information on these accounts to be displayed on front end. Saves the balance & balanceDateTime to the database.

### HTTP Request

`GET http://example.com/account/client-accounts/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | database ID of customer

### Responses

Parameter | Description
--------- | -----------
successful:200 | accounts: []

## Finding connected Bank Accounts for a specific tenant

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/account/tenant-accounts/5ee3ad5cbdcb012345678910"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "accounts": [
    {
        "name": "Silver Standard 0.1% Interest Saving",
        "bankName": "Citi",
        "accountNumber": "1111",
        "id": "5ee3ad5cbdcb012345678910",
        "balance": 200,
        "institutionCode": "ins_4",
        "dwollaFundingURL": "https://api-sandbox.dwolla.com/funding-sources/12345",
        "bankDisplayName": "Citi Savings" ,
        "type": "escrow"
    }
  ]
}
```

This endpoint finds connected bank accounts for specific tenant, returns information on these accounts to be displayed on front end.

### HTTP Request

`GET http://example.com/account/tenant-accounts/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | database ID of tenant

### Responses

Parameter | Description
--------- | -----------
successful:200 | accounts: []
unsuccessful:400 | accounts: [], error:err, route: '/account/tenant-accounts/:id'

## saves a document to client in preparation for transfer > $5000

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/transfer/document/:transferId"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:


This endpoint saves a document to client in preparation for transfer > $5000. { documentType, assetId }

### HTTP Request

`GET http://example.com/transfer/document/:transferId`

### URL Parameters

Parameter | Description
--------- | -----------
documentType | type of document: ( 'passport', 'license' )
assetId | corresponding asset ID in file service
documentUrl | unique document URL for uploaded document in Dwolla. Returned from this route

### Responses

Parameter | Description
--------- | -----------
successful:200 | success: true, documentUrl
unsuccessful:400 | success: false, route, error


## Delete an account

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/account"
  -X DELETE
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "success" : true
}
```

This endpoint deactivates a client bank account in Plaid/Dwolla. { bankAccountId } => { success (boolean) }

### HTTP Request

`DELETE http://example.com/account/`

### Responses

Parameter | Description
--------- | -----------
successful:204 | success: true 
unsuccessful:400 | success: false, route 'DELETE/account/', erroe: err

# Email-service

## Get API version

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/email/version"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "API version ****"
  }
]
```

This endpoint returns API version.

### HTTP Request

`GET http://example.com/api/email/version`


## Sending transfer receipt with attached asset

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/email/receipt"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> Request.body example:

```json
{
  "TENANT_GUID" : "########################", // required
    "CLIENT_GUID" : "########################", // required
    "TRANSFER_GUID" : "########################", // required
    "ASSET_GUID" : "########################.jpg", // required
    "emailRecipients": ["test.test@gmail.com", "test.test+2@gmail.com"] // required
}
```

> The above command returns JSON structured like this:

```json
{
  "response": [
      {
          "statusCode": 202,
          "body": "",
          "headers": {
              "server": "nginx",
              "date": "Thu, 25 Jun 2020 22:48:24 GMT",
              "content-length": "0",
              "connection": "close",
              "x-message-id": "********",
              "access-control-allow-origin": "https://sendgrid.api-docs.io",
              "access-control-allow-methods": "POST",
              "access-control-allow-headers": "Authorization, Content-Type, On-behalf-of, x-sg-elas-acl",
              "access-control-max-age": "600",
              "x-no-cors-reason": "https://sendgrid.com/docs/Classroom/Basics/API/cors.html"
          }
      },
      ""
  ]
}
```

This endpoint send the transfer receipt with attached asset. Uses S3GetObject to fetch attachment with key /TENANT_GUID/CLIENT_GUID/TRANSFER_GUID/ASSET_GUID. emailRecipients is an array and has to contain at least 1 email. uses CLIENT_GUID and TRANSFER_GUID to fetch transfer objects and dynamically populate email. 


### HTTP Request

`GET http://example.com/email/receipt`

# File-service

## Get API version

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/assets/version"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  "API version ****"
]
```

This endpoint returns API version.

### HTTP Request

`GET http://example.com/api/assets/version`


## Getting images in public img bucket

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/assets/public/imgs"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint gets all images in public img bucket. 

### HTTP Request

`GET http://example.com/assets/public/imgs`

## Uploading images to public img bucket

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/assets/public
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "s3-assets": {
          "logo": {
              "ETag": "\"****\"",
              "ServerSideEncryption": "******",
              "VersionId": "**********",
              "Location": "https://**********.s3.amazonaws.com/**********/logo/S**********.png",
              "key": "**********/logo/**********",
              "Key": "**********/logo/**********",
              "Bucket": "******"
          },
          "backgroundImage": {
              "ETag": "\"****\"",
              "ServerSideEncryption": "******",
              "VersionId": "***********",
              "Location": "https://**********.s3.amazonaws.com/**********/backgroundImage/**********.png",
              "key": "**********/backgroundImage/**********",
              "Key": "**********/backgroundImage/**********",
              "Bucket": "******"
          }
      }
}
```

This endpoint uploads images to public img bucket.  

### HTTP Request

`POST http://example.com/assets/public`

## Uploading images to private img bucket

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/assets/private
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "s3-assets": {
        "escrow-agreement": {
            "ETag": "\"**********\"",
            "Location": "https://**********.s3.amazonaws.com/**********/**********/**********/escrow-agreement-**********",
            "key": "**********/**********/**********/escrow-agreement-**********",
            "Key": "**********/**********/**********/escrow-agreement-**********",
            "Bucket": "**********"
        },
        "receipt": {
            "ETag": "\"**********\"",
            "Location": "**********.s3.amazonaws.com/**********/**********/**********/receipt-**********",
            "key": "**********/**********/**********/receipt-**********",
            "Key": "**********/**********/**********/receipt-**********",
            "Bucket": "**********"
        }
    }
}
```

This endpoint uploads images to private img bucket.  

### HTTP Request

`POST http://example.com/assets/private`

## Getting list of files associated with tenant, client and transfer GUID

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/assets/private/:TENANT_GUID/:CLIENT_GUID/:TRANSFER_GUID
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "Key": "********/********/********/*********",
      "LastModified": "2020-06-18T22:47:33.000Z",
      "ETag": "\"**********\"",
      "Size": 6550,
      "StorageClass": "STANDARD",
      "Owner": {
          "DisplayName": "ashish",
          "ID": "**********"
      }
}
```

This endpoint gets list of all files associated with tenant, client and transfer GUID.

### HTTP Request

`GET /assets/private/:TENANT_GUID/:CLIENT_GUID/:TRANSFER_GUID`

## Response streams file back to client

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/assets/private/:TENANT_GUID/:CLIENT_GUID/:TRANSFER_GUID/:ASSET_GUID
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  
}
```

This endpoint response streams file back to client associated with tenant, client and transfer GUID. This endpoint is the key response from GET(/assets/private/:TENANT_GUID/:CLIENT_GUID/:TRANSFER_GUID)

### HTTP Request

`GET /assets/private/:TENANT_GUID/:CLIENT_GUID/:TRANSFER_GUID/:ASSET_GUID`

