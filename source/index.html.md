---
title: API Reference

language_tabs:
  - shell
  - ruby
  - python

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

```shell
# With shell, you can just pass the correct header with each request
 "https://connecticket.railsfactory.com/api/authorize"
  In Headers: api_key: "8eb68e28cda407158cf9a8064bdd5351"
              api_secret: "b19fszzt9e2z4wpu87r09zy58"
```

> The above command returns JSON structured like this:

```
    {
      "status": true,
      "message": "Authorized Successfully, Use the Provided Access Token for Future Requests. Thanks for connecting with Example Provider",
      "access_token": "356kdpiamhkz7a43nu0e2ldr9"
    }
```


Register the Application with connect4health and get your API_KEY and API_SECRET. With the api_key and api_secret send a request like below,

### HTTP Request

`GET https://connecticket.railsfactory.com/api/authorize`

### Query Parameters

Send the below parameters in Headers

Parameter | Description
--------- | -----------
api_key   | api_key got while registering the application with connect4health
api_secret| api_secret got while registering the application with connect4health

In Response, Access_token will be provided, with success message, this means that the app and user got authorized successfully.
This access token should be used in further requests along with api_key and api_secret.


# Tickets

## Get All Tickets

```shell
    "https://connecticket.railsfactory.com/api/356kdpiamhkz7a43nu0e2ldr9/tickets"
  In Headers: api_key: "8eb68e28cda407158cf9a8064bdd5351"
              api_secret: "b19fszzt9e2z4wpu87r09zy58"
```

> The above command returns JSON structured like this:

```json
{
    "status": "Success",
    "ticket": [
        {
            "start_date": null,
            "sentsent_to_primary": null,
            "urgency_status_id": 3,
            "ticket_type": null,
            "resident_id": 75474618,
            "updated_at": "2016/02/12 03:00:34 -0800",
            "created_at": "2016/02/12 03:00:25 -0800",
            "email": null,
            "sent_to_healthcare_pro": null,
            "state": false,
            "sms": null,
            "id": 202,
            "end_date": null,
            "ticket_status": "New",
            "sent_to_family": null,
            "title": "Ticket  commment",
            "employee_id": 81987870
        }
    ]
}```

This endpoint retrieves all tickets.

### HTTP Request

`GET https://connecticket.railsfactory.com/api/<:access_token_got_from_authentication>/tickets`


## Getting a specific Ticket

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

