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

# Search

## Search all transfers

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
curl "http://api.paymints.dev/api/search/all-transfers"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```
> Request body:

```json
{
    "email": "",
    "firstName": "",
    "lastName": "",
    "propertyAddress1": "",
    "propertyAddress2": "",
    "propertyZipcode": "",
    "propertyState": "",
    "propertyCity": "",
    "purpose": "",
    "amount": {
      "min": 0,
      "max": 100000
    },
    "tenantGUID": ""
  }
```

> The above command returns:

```json
{
    "search transfer info"
}
```

This endpoint searches transfers filtering by tenantGUID. Amount max and min optional defaults to 0-100,000. TenantGUID is required and all other fields are optional.

### HTTP Request

`POST /search/all-transfers`

## Search all clients

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
curl "http://api.paymints.dev/api/search/all-clients"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```
> Request body:

```json
{
    "email": "",
    "firstName": "",
    "lastName": "",
    "propertyAddress1": "",
    "propertyAddress2": "",
    "propertyZipcode": "",
    "propertyState": "",
    "propertyCity": "",
    "purpose": "",
    "amount": {
      "min": 0,
      "max": 100000
    },
    "tenantGUID": ""
  }
```

> The above command returns:

```json
{
    "search client info"
}
```

This endpoint searches clients filtering by tenantGUID. Amount max and min optional defaults to 0-100,000. TenantGUID is required and all other fields are optional.

### HTTP Request

`POST /search/all-clients`

# Users

## Adding new users

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
curl "http://api.paymints.dev/api/users"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```
> Request body:

```json
{
    "create_user": {
      "email": "hiller.stuart+3@gmail.com",
      "name": "agent hiller3",
      "connection":"email"
    },
    "new_user_role": "paymints_tenant",
    "role": "paymints_admin"
  }
```

> The above command returns:

```json
{
    "created user info"
}
```

This endpoint adds the list of users. User info passed in must contain email, name, connection. Newly created users will be assigned a role and associted with tenantGUID.

### HTTP Request

`POST /users`

## Get all users of a tenant

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
curl "http://api.paymints.dev/api/users/**********"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns:

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

This endpoint returns the list of users associated with tenant_GUID. 

### HTTP Request

`GET /users/{tenant_GUID}`

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
curl "http://api.paymints.dev/api/users/**********/**********"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns:

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

This endpoint retrieves a specific user from a specific tenant.

### HTTP Request

`GET /users/{tenant_GUID}/{user_GUID}`

### URL Parameters

Parameter | Description
--------- | -----------
tenant_GUID | The ID of the tenant to retrieve his users.
user_GUID   | The ID of the specific user of the tenant with ID tenant_GUID.

## Updates specific user for a tenant

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
curl "http://api.paymints.dev/api/users/:tenant_GUID/:user_GUID"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns:

```json
{
  
}
```

This endpoint updates specific user.

### HTTP Request

`PATCH /users/{tenant_GUID}/{user_GUID}`

### URL Parameters

Parameter | Description
--------- | -----------
tenant_GUID | The ID of the tenant to retrieve his users.
user_GUID   | The ID of the specific user of the tenant with ID tenant_GUID.

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
curl "http://api.paymints.dev/api/account/auth/create-client"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns:

```json
{
    "success": true,
    "bankAccountId": "5f112bc579eaf938a65ffc92"
}
```


This endpoint will add a verified customer to dwolla, with a funding source, and save dwolla/plaid attributes to the database.

<aside class="success">
This route can also be used for adding a bank account to a customer that already has other bank accounts. (and is already in Dwolla). The following values must be saved to the Client in the DB prior to the API call: ssn, DateOfBirth, email.
</aside>

### HTTP Request

`POST /account/auth/create-client`

### Request Parameters

Name | Description
--------- | -----------
Id | Client ID in database
plaidAccountId | Account ID from plaid onSuccess
publicToken | Public token from plaid onSuccess

### Responses

Name | Description
--------- | -----------
successful:200 | success:true, bankAccountId 
unsuccessful:400   | route, error, success:false

## Creating an EscrowAccount

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
curl "http://api.paymints.dev/api/account/auth/:tenant_ID/escrow"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns:

```json
{
  "success": true, 
  "escrowAccountId": "5ee7c544aa79d44d5f396c46"
}
```

This endpoint adds a tenant, bank account to plaid/dwolla. Creates a EscrowAccount with the given information. This route can also be used to add a bank account to a tenant already added.

<aside class="success">
The following values must be saved in the DB prior to the API call: businessType (llc, corporation, soleProprietorship), address1, address2 (optional), city, state, zipcode, name, ein (9 digit number).
</aside>

### HTTP Request

`POST /account/auth/{tenant_ID}/escrow`

### Request Parameters

Name | Description
--------- | -----------
agent_ID | Agent database ID
plaidAccountId | Account ID from plaid onSuccess
publicToken | Public token from plaid onSuccess

### Responses

Name | Description
--------- | -----------
successful 201 | success:true, escrowAccountId: ID
unsuccessful:400   | success:false, error: error, route: '/account/auth/create-tenant'


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
curl "http://api.paymints.dev/api/account/client-accounts/:id"
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
      "id": "************************", 
      "balance": 200, 
      "institutionCode": "ins_4" , 
      "bankDisplayName": "Citi Savings" ,
      "dwollaFundingURL": "https://api-sandbox.dwolla.com/funding-sources/12345" } 
    ]
}
```

This endpoint finds connected bank accounts for specific customer, returns information on these accounts to be displayed on front end. Saves the balance & balanceDateTime to the database.

### HTTP Request

`GET /account/client-accounts/{ID}`

### Request Parameters

Name | Description
--------- | -----------
ID | Database ID of customer

### Responses

Name | Description
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
curl "http://api.paymints.dev/api/account/tenant-accounts/:id"
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

`GET /account/tenant-accounts/{ID}`

### Request Parameters

Name | Description
--------- | -----------
ID | Database ID of tenant

### Responses

Name | Description
--------- | -----------
successful:200 | accounts: []
unsuccessful:400 | accounts: [], error:err, route: '/account/tenant-accounts/{ID}'

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
curl "http://api.paymints.dev/api/account/auth/:tenant_ID/billing"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns:

```json
{
  "success": true, 
  "billingAccountId": "5ed130372ad1c17318779c9e"
}
```

This endpoint subscribes a tenant to be billed monthly & adds a Billing Account. Authenticates account and creates new billing account connected to tenant, adds subscription to Tenant.

<aside class="success">
This route has the same Tenant, Agent, and Tenant Exec requirements as /account/auth/{tenant_ID}/escrow
</aside>

### HTTP Request

`POST /account/auth/{tenant_ID}/billing`

### Request Parameters

Name | Description
--------- | -----------
tenant_ID | Tenant database ID
plaidAccountId | Account ID from plaid onSuccess
publictoken | Public token from plaid onSuccess
subscriptionId | Subscription ID
agentId | Angent ID

### Responses

Namer | Description
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
curl "http://api.paymints.dev/api/transfer/start"
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
  "success": true
}
```

This endpoint is the primary route for initiating a transfer. Will initiate an ACH transfer, save dwollaStatus, dwollaSourceURL.

### HTTP Request

`POST /transfer/start`

### Request Parameters

Name | Description
--------- | -----------
bankAccountID | database ID of Bank Account that will send money
escrowAccountID | database ID of Escrow Account that will receive money
transferID | database ID of transfer, which will be updated with dwollaStatus, dwollaResourceURL, dwollaDestinationURL, dwollaTransferURL

### Responses

Name | Description
--------- | -----------
successful:201 | success: true
unsuccessful:400 | success:false, error: error, route: 'transfer/start'


## Saving a document to client in preparation for transfer > $150000

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
curl "http://api.paymints.dev/api/transfer/document/5ee8063e6c1f3346b6adc9fe"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns:

```json 
{
  "success" : true,
  "documentUrl" : "https://api-sandbox.dwolla.com/transfers/df8740c5-edbb-ea11-8125-fd127c7b5ea8"
}
```

This endpoint saves a document to client in preparation for transfer > $150000. 

### HTTP Request

`GET /transfer/document/{transferId}`

### Request Parameters

Name | Description
--------- | -----------
documentType | Type of document: ( 'passport', 'license' )
assetId | Corresponding asset ID in file service
documentUrl | Unique document URL for uploaded document in Dwolla. Returned from this route

### Responses

Name | Description
--------- | -----------
successful:200 | success: true, {documentUrl}
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
curl "http://api.paymints.dev/account"
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

This endpoint deactivates a client bank account in Plaid/Dwolla. 

### HTTP Request

`DELETE /account/`

### Request Parameters

Name | Description
--------- | ------------
bankAccountId | Client bank account ID

### Responses

Name | Description
--------- | -----------
successful:204 | success: true 
unsuccessful:400 | success: false, route 'DELETE/account/', erroe: err

# Email-service
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
curl "http://api.paymints.dev/api/email/receipt"
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

This endpoint send the transfer receipt with attached asset. Uses S3GetObject to fetch attachment with key /TENANT_GUID/CLIENT_GUID/TRANSFER_GUID/ASSET_GUID. Uses CLIENT_GUID and TRANSFER_GUID to fetch transfer objects and dynamically populate email. 


### HTTP Request

`POST /email/receipt`

### Request Parameters

Name | Description
--------- | -----------
Transfer_GUID | "########################", // required
emailRecipients | ["test.test@gmail.com", "test.test+2@gmail.com"] // required (atleast 1 email)
emailFrom | 'test@gmail.com'

# File-service
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
curl "http://api.paymints.dev/api/assets/public/imgs"
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns:

```json
{
  "bucket content": {
        "IsTruncated": true,
        "Marker": "",
         "Contents": [
            {
                "Key": "**********/branding/Screen Shot 2020-06-09 at 1.36.26 PM.png",
                "LastModified": "2020-06-16T17:10:48.000Z",
                "ETag": "\"**********\"",
                "Size": 590020,
                "StorageClass": "STANDARD",
                "Owner": {
                    "DisplayName": "ashish",
                    "ID": "**********"
                }
            },

            {
                "Key": "**********/logo/Screen Shot 2020-06-11 at 10.07.33 AM.png",
                "LastModified": "2020-06-16T20:18:38.000Z",
                "ETag": "\"**********\"",
                "Size": 1245030,
                "StorageClass": "STANDARD",
                "Owner": {
                    "DisplayName": "ashish",
                    "ID": "**********"
                }
            },
            {},
            {}
         ]
      }
}
```

This endpoint gets all images in public img bucket. 

### HTTP Request

`GET /assets/public/imgs`

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
curl "http://api.paymints.dev/api/assets/public
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns:

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

This endpoint uploads images to public img bucket. Expects multi-form payload. First & second needs to be field text (required). Second field is a file with key = 'logo'. Third field is a file with key = 'backgroundImage'. After s3 upload server updates paymint.io graphql server tenant { branding { logoURL backgroundImageURL } }.

### HTTP Request

`POST /assets/public`

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
curl "http://api.paymints.dev/api/assets/private
  -H "Authorization: your-api-key"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns:

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

This endpoint uploads images to private img bucket. First three forms should be TENANT_GUID, CLIENT_GUID, and TRANSFER_GUID(required). Forms 4 through 6 will be the files labeled, escrow-agreement, receipt, id-copy 

### HTTP Request

`POST /assets/private`

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

> The above command returns file list as array objects like this:

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

`GET /assets/private/{TENANT_GUID}/{CLIENT_GUID}/{TRANSFER_GUID}`

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
curl "http://api.paymints.dev/api/assets/private/**********/**********/**********/
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
    "s3Assets": []
}
```

This endpoint response streams file back to client associated with tenant, client and transfer GUID. This endpoint is the key response from GET(/assets/private/:TENANT_GUID/:CLIENT_GUID/:TRANSFER_GUID)

### HTTP Request

`GET /assets/private/{TENANT_GUID}/{CLIENT_GUID}/{TRANSFER_GUID}/{ASSET_GUID}`

