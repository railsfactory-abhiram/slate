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

`POST https://connecticket.railsfactory.com/api/authorize`

### Query Parameters

Parameter | Description
--------- | -----------
api_key   | api_key got while registering the application with connect4health
api_secret| api_secret got while registering the application with connect4health

In Response, Access_token will be provided, with success message, this means that the app and user got authorized successfully.
This access token should be used in further requests along with api_key and api_secret.


# Tickets

## Get All Tickets

This endpoint retrieves all tickets.

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
}
```
### HTTP Request

`GET https://connecticket.railsfactory.com/api/<:access_token_got_from_authentication>/tickets`

### Query Parameters

Send the below parameters in Headers

Parameter | Description
--------- | -----------
api_key   | api_key got while registering the application with connect4health
api_secret| api_secret got while registering the application with connect4health
access_token| Should be sent through url

With the ***Access token*** provided in the url, the particular provider will be identified, and Residents of that particular
provider will be sent.

## Getting a specific Ticket

```shell
curl "http://connecticket.railsfactory.org/api/356kdpiamhkz7a43nu0e2ldr9/ticket_detail?id=201"
 In Headers:  api_key: "8eb68e28cda407158cf9a8064bdd5351"
              api_secret: "b19fszzt9e2z4wpu87r09zy58"
```

> The above command returns JSON structured like this:

```json
{
    "ticket_with_details": {
        "ticket_attachments": [],
        "ticket": {
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
        },
        "categories": {
            "6": {
                "comment378": {
                    "commented_by": "Sample",
                    "commented_on": "2016/02/12 03:00:34 -0800",
                    "title": "comment 1"
                },
                "status": "no issue",
                "title": "check now"
            },
            "7": {
                "comment379": {
                    "commented_by": "Sample",
                    "commented_on": "2016/02/12 03:00:34 -0800",
                    "title": "comment 2"
                },
                "status": "issue",
                "title": "yes add"
            }
        }
    }
}
```

This endpoint retrieves a specific ticket.

### HTTP Request

`GET http://connecticket.railsfactory.com/api/<:access_token_got_from_authentication>/ticket_detail

Parameter | Description
--------- | -----------
api_key | Should be sent in header
api_secret | Should be sent in header
id | Unique ID of the ticket
access_token| Should be sent through url



## Get All Residents

```shell
    "http://connecticket.railsfactory.com/api/356kdpiamhkz7a43nu0e2ldr9/all_residents"
  In Headers: api_key: "8eb68e28cda407158cf9a8064bdd5351"
              api_secret: "b19fszzt9e2z4wpu87r09zy58"
```

> The above command returns JSON structured like this:

```json
{
    "status": "Success",
    "residents": [
        {
            "fax_number": null,
            "caretracker_id": null,
            "resident_type_id": null,
            "provider_id": 72136196,
            "photo_content_type": "",
            "first_name": "Test Case (Provider Type)",
            "next_status_update": null,
            "id": 889283349,
            "state": "active",
            "photo_file_name": "",
            "creator_id": 0,
            "last_status_update": null,
            "home_zip": "534412",
            "in_home_care": false,
            "home_address2": "",
            "home_address1": "123 Mockingbird Lane",
            "email": null,
            "customer_number": null,
            "updated_at": "2016/02/07 02:57:51 -0800",
            "review_updates": null,
            "updater_id": 0,
            "location": "Assisted Living Apt. 204",
            "home_city": "New York",
            "photo_file_size": 0,
            "home_state": "NY",
            "dob": "1937/01/21",
            "last_name": null,
            "demo": false,
            "phone_number": null,
            "created_at": "2016/02/07 02:57:51 -0800",
            "account_number": null
        },
        {
            "fax_number": null,
            "caretracker_id": null,
            "resident_type_id": 1058366525,
            "provider_id": 72136196,
            "photo_content_type": "",
            "first_name": "Test Doctor",
            "next_status_update": null,
            "id": 501333996,
            "state": "active",
            "photo_file_name": "",
            "creator_id": 0,
            "last_status_update": null,
            "home_zip": "534412",
            "in_home_care": false,
            "home_address2": "",
            "home_address1": "123 Mockingbird Lane",
            "email": null,
            "customer_number": null,
            "updated_at": "2016/02/07 02:57:51 -0800",
            "review_updates": null,
            "updater_id": 0,
            "location": "Assisted Living Apt. 204",
            "home_city": "New York",
            "photo_file_size": 0,
            "home_state": "NY",
            "dob": "1937/01/21",
            "last_name": null,
            "demo": false,
            "phone_number": null,
            "created_at": "2016/02/07 02:57:51 -0800",
            "account_number": null
        }
    ]
}
```

This endpoint retrieves all Resident details of a particular provider.

### HTTP Request

`GET http://connecticket.railsfactory.com/api/<:access_token_got_from_authentication>/all_residents`

With the ***Access token*** provided in the url, the particular provider will be identified, and Residents of that particular
provider will be sent.

Parameter | Description
--------- | -----------
api_key | Should be sent in header
api_secret | Should be sent in header
access_token| Should be sent through url

## Get Categories

```shell
    "http://connecticket.railsfactory.com/api/356kdpiamhkz7a43nu0e2ldr9/provider_categories"
  In Headers: api_key: "8eb68e28cda407158cf9a8064bdd5351"
              api_secret: "b19fszzt9e2z4wpu87r09zy58"
```

> The above command returns JSON structured like this:

```json
{
    "status": "Success",
    "categories": [{"id": 3, "name": "Clinical Edit"},
                  {"id": 3, "name": "Emergency"},
                  {"id": 3, "name": "Activity Level"},
                  {"id": 3, "name": "Weight Gain"}]
 }
```

This endpoint will retrieve all the categories that comes under a particulan provider. These categories status needs to be set
while creating a ticket.

### HTTP Request

`GET http://connecticket.railsfactory.com/api/<:access_token_got_from_authentication>/provider_categories`

With the ***Access token*** provided in the url, the particular provider will be identified, and Categories of that particular
provider will be sent.

Parameter | Description
--------- | -----------
api_key | Should be sent in header
api_secret | Should be sent in header
access_token| Should be sent through url


## Update Status of a Ticket

```shell
    "http://connecticket.railsfactory.com/api/356kdpiamhkz7a43nu0e2ldr9/update_status?id=202&status=Reopen"
  In Headers: api_key: "8eb68e28cda407158cf9a8064bdd5351"
              api_secret: "b19fszzt9e2z4wpu87r09zy58"
```

> The above command returns JSON structured like this:

```json
{
    "status": "Success",
    "message": "Status Updated Successfully!!"
     }
```

This endpoint will retrieve all the categories that comes under a particulan provider. These categories status needs to be set
while creating a ticket.

### HTTP Request

`POST http://connecticket.railsfactory.com/api/<:access_token_got_from_authentication>/update_status`

With the ***Access token*** provided in the url, the particular provider will be identified, and Categories of that particular
provider will be sent.

Parameter | Description
--------- | -----------
api_key | Should be sent in header
api_secret | Should be sent in header
access_token| Should be sent through url
id | Ticket id 
status | status to be set for the ticket



## Create Ticket

```shell
    "http://connecticket.railsfactory.com/api/356kdpiamhkz7a43nu0e2ldr9/create_ticket"
  In Headers: api_key: "8eb68e28cda407158cf9a8064bdd5351"
              api_secret: "b19fszzt9e2z4wpu87r09zy58"
```

> The above command returns JSON structured like this:

```json
{
    "status": "Success",
    "ticket_id": 46,
    "message": "Ticket Created Successfully!!"
     }
```

This endpoint will create a ticket for a particular provider.

### HTTP Request

`GET http://connecticket.railsfactory.com/api/<:access_token_got_from_authentication>/provider_categories`

With the ***Access token*** provided in the url, the particular provider will be identified, and Categories of that particular
provider will be sent.

Parameter | Description
--------- | -----------
api_key | Should be sent in header
api_secret | Should be sent in header
access_token| Should be sent through url

Parameters to be sent: "title", "resident_id", "sms", "email", "state", "urgency_status","ticket_status".
Along with these parameters: Category status also should be set. Category details of a particular provider cant be fetched
from "Provider Categories" end point. Category status should be sent like below along with the parameters above.
Parameter | Status
--------- | -----------
category_19 | "Issue"
category_22| "No Issue"
category_33| "Potential Issue"

Once the above parameters sent to the above end point, ticket will be created and a success status will be sent.

