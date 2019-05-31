---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript

toc_footers:
  - <a href='https://www.finqware.com/joinalpha'>Sign Up for our alpha testing program</a>

includes:
  - errors

search: true
---

# Quick start

Welcome to the Finqware API!

This alpha program is about learning and testing various Open Banking APIs.

1. <a href='https://www.finqware.com/joinalpha'>Register</a> yourself (personal or company) as a `servicer`
2. Register a tenant app with your servicer and get your API keys
3. Go through the skills catalog and check what you want to implement
4. Write the code, use the sandbox mode for each _skill_ for test & dev

# Overview

## Skills

### Concept

Open Banking is about _opening_ access for businesses to create value on top of financial services provided via APIs.

Each API that we integrate into our middleware is a `skill`. Examples: an account information API from Bank X is a skill, a payment initiation service from Bank Y is another skill.

With the initial releases, we'll focus on three skill types: account information, payment initiation and marketplace.

Each skill comes in two flavors: production and sandbox. Test & dev tenants will use sandbox skills.

### Account information

These skills are mainly based on PSD2 AISP APIs from various banks.

Use cases: wallet applications or enterprise systems that need to query for bank accounts and transaction reports.

### Payment initiation

Based on PSD2 PISP APIs from various banks.

Use cases: merchants willing to accept payments through a direct account-to-account transfer bypassing classic payment schemes.

### Marketplace

Based on custom connectors that we're building with our partner servicers.

Use cases: marketplaces interested in selling financial products without the hassle of a direct integration with banks, insurance providers etc.

## Servicers

A `servicer` is a partner company registered with Finqware.

It may be a bank or an insurance company providing skills into the middleware, or a fintech that consumes the Finqware API.

Or even both: a bank may be providing its own APIs into the middleware and at the same time it may implement a multi-banking experience on top of Finqware.

From a Finqware API consumer standpoint, a servicer may register multiple `tenant` apps.

A servicer has a number of developers/users with credentials on our developer's portal.

## Tenants

A `tenant` is your software, consuming the Finqware API. It usually has two components:

- a client-side application (eg: a mobile and/or a web front-end)
- a server. This is where you run the business logic, the user database etc.

It's important to make a clear distinction between the two. There are specific data items (i.e. tokens, secrets) that you can safely store in your client app, and others that we recommend to be used only in a server-to-Finqware communication.

A servicer may register multiple tenant apps for different business cases or just for technical reasons (eg: test & prod apps).

For a granular access control and reporting, each tenant is required to register the list of skills it connects to.

## Security model

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
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require("kittn");

let api = kittn.authorize("meowmeowmeow");
```

> Make sure to replace `meowmeowmeow` with your API key.

Finqware uses API keys to allow access to the API. You can register for a test API key [here](https://www.finqware.com/joinalpha).

`Authorization: test`

<aside class="notice">
You must replace <code>test</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

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
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require("kittn");

let api = kittn.authorize("meowmeowmeow");
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

| Parameter    | Default | Description                                                                      |
| ------------ | ------- | -------------------------------------------------------------------------------- |
| include_cats | false   | If set to true, the result will also include cats.                               |
| available    | true    | If set to false, the result will include kittens that have already been adopted. |

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
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require("kittn");

let api = kittn.authorize("meowmeowmeow");
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

| Parameter | Description                      |
| --------- | -------------------------------- |
| ID        | The ID of the kitten to retrieve |

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
const kittn = require("kittn");

let api = kittn.authorize("meowmeowmeow");
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted": ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

| Parameter | Description                    |
| --------- | ------------------------------ |
| ID        | The ID of the kitten to delete |
