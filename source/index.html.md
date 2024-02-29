---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell
  - javascript

toc_footers:
  - <a href='https://aspireapp.com/contact-us'>Contact Us for a Developer Key</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Aspire Connect API
---

# Introduction

Aspire is the all-in-one finance operating system for new-age businesses. We help companies pay, manage, and earn smarter - by doing more than a bank, bookkeeper, or rewards program could ever do alone.

Aspire Connect is Aspire's API suite that allows our clients to automate their finance workflows. Clients can disburse funds, issue cards, and more using APIs. Read on to learn more.

# Authentication

Aspire Connect uses client credentials to authenticate requests.

Please get in touch with your account executive for help with client credentials & whitelisting your IP for utilizing the APIs.

The auth flow is as follows:

![auth flow](https://content.pstmn.io/d14b59a0-70bc-468f-bc82-e141b0f31a8f/U2NyZWVuc2hvdCAyMDIzLTExLTMwIGF0IDIuMjYuMzcgUE0ucG5n "Title")

> Example Request:

```shell
curl --location "https://api.aspireapp.com/public/v1/login" \
  --header 'Content-Type: application/json' \
  --data '[
      {   
          "grant_type" : "client_credentials",
          "client_id" : "SGLTTC-qXox2TAe1WHs7Erd",
          "client_secret" : "CkuDGSF1HCkei9ZEgthbor2suQAITZ36"
      }
  ]'
```

```javascript
import axios from 'axios';

let api = axios.post('https://api.aspireapp.com/public/v1/login');

axios.defaults.headers.common['Authorization'] = 'Bearer ' + ###
```

> Make sure to replace `###` with your API key.

The `/login` endpoint enables Aspire Connect clients to obtain an access token using their client credentials. This access token has a 30 minute expiry and serves as a bearer token in the Authorization request header for all subsequent calls to authorized endpoints.

Make sure to send query params in request body`

<aside class="notice">
You must replace <code>###</code> with your personal API key.
</aside>

# Kittens

## Get All Users

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
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
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

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
curl "http://example.com/api/kittens/2" \
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
curl "http://example.com/api/kittens/2" \
  -X DELETE \
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

