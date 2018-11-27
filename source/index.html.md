---
title: Hackwagon API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascsript

toc_footers:
  - <a href='mailto:hello@hackwagon.com'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Hackwagon API! You can use our API to access Hackwagon API endpoints, which currently only allows our approved partners to access certain protected endpoints. More to come soon.

We have language bindings in REST for now only, and more to come. You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

The API endpoint for Hackwagon's API follows the following structure: [https://api.hackwagon.com/v1/](https://api.hackwagon.com/v1/)

<!-- This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation. -->

# Authentication

> Example API call with embedded API key:

```javascript
fetch('https://api.hackwagon.com/v1/example', {
  method: "POST",
  headers: {
    'Content-Type': 'application/json',
    'X-API-Key': 'sk_superawesomesecretkey',
    'X-App-Id': 'randomappid'
  },
  body: JSON.stringify({
    key: 'value'
  })
}).then(function(response) {
  return response.json()
}).catch(function(ex) {
  console.log('parsing failed', ex)
})
```

> Make sure to replace `sk_superawesomesecretkey` with your API key, and `randomappid` with your Application id.

Hackwagon uses API keys and Application Ids to allow access to the API. You can register a new Hackwagon API key by contacting us at [hello@hackwagon.com](mailto:hello@hackwagon.com).

Hackwagon expects for the API key and Application Id to be included in all API requests to the server in the header that looks like the following:

`X-API-Key: sk_superawesomesecretkey`

`X-App-Id: randomappid`

From here on it is expected that all requests contain the API key and application Id header.

<aside class="notice">
You must replace <code>sk_superawesomesecretkey</code> with your personal API key, and <code>randomappid</code> with your personal Application Id.
</aside>

# Queue System

## Appending Queue Number

> Example API call:

```javascript
fetch('https://api.hackwagon.com/v1/company_queue', {
  method: "POST",
  body: JSON.stringify({
    merchantId: 'value',
    number: '010',
  })
}).then(function(response) {
  return response.json()
}).catch(function(ex) {
  console.log('parsing failed', ex)
})
```

> Request Body:

```json
{
  "merchantId": "string",
  "number": "string"
}
```

> Expected response structure:

```json
{
  "status": "success|failed",
  "message": "A message detailing the success or error message"
}
```

This endpoint appends a new queue number to be displayed in our physical devices located around Singapore. By specifying a `merchantId`, you'll be able to target a specific device. The `number` is the queue number you wish to display on the device (try to keep it to 3 characters or less).

### HTTP Request

`POST http://api.hackwagon.com/v1/company_queue`

### Query Parameters

Parameter | Expects | Description
--------- | ------- | -----------
merchantId | string | This is the Id you assign to your own merchants in your own applications. This key will be stored by us, so your application can identify the physical device.
number | string | This number is supposed to be taken in as a string. Keep it to 3 characters or less.

<aside class="notice">
The <code>merchantId</code> must be provided to Hackwagon's team so we can assign it to each unique physical device for your identification.
</aside>

### Response Parameters

Parameter | Possible Value(s) | Description
--------- | ------- | -----------
status | success,failed | This describes whether your API call was a success or failure
message | string | This is a success/error description

<!-- ## Get a Specific Kitten

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
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
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

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

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
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
 -->
