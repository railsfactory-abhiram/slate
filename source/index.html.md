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

### Getting Started

  This session inducts the steps you need to take when you use the Connect4healthcare API. Registering in Connect4healthcare application is mandatory to use the REST APIs provided

### Process
  General procedure involved in using Connect4healthcare API is very simple. Follow the below steps.

  * Get the authorization. Do the necessary user login steps.
  * Set up parameters. Decide which parameters you are passing to API and set their values or retrieve those values as input from the user of your application.
  * Build the request to the API. The request consists of the full URL to the API resource itself, the parameters and their values.
  * Make the request. You should invoke each request with its appropriate HTTP method: GET, PUT, DELETE, or POST.
  * Get the response and parse it for the data you need. Some of the data may be contained directly within the response, marked by appropriate tags, and some data may appear in the form of links to other resources.
  * Use the response data to do further operations. 
  * The Connect4healthcare API will return the error code for the failed request or actions which helps the developers to know the exact reason for the failure.

### Response Format
  The response returned can be in either JSON or XML. Each format specifies a way of encoding name-value pairs which comprise the response data. Each format has an associated mime-type which must be returned in the Content-type header along with the response.

### Request Format
  Access tokens are similar to session tokens. Authorization can be performed with an access token that is submitted with every secure request. Make sure that the Access token is stored securely and make every request with the access token. For every request access_token is sent as an extra parameter. 


# Authentication

```shell
# With shell, you can just pass the correct header with each request
 "http://connecticket.railsfactory.com/api/authorize"
  In Headers: api_key: "8eb68e28cda407158cf9a8064bdd5351"
              api_secret: "b19fszzt9e2z4wpu87r09zy58"
```

> The above command returns JSON structured like this:

```
Success Response:

    {
      "status": true,
      "message": "Authorized Successfully, Use the Provided Access Token for Future Requests. Thanks for connecting with Example Provider",
      "access_token": "356kdpiamhkz7a43nu0e2ldr9"
    }
```

```
Error Response:

    {
      "status": false,
      "message": "Invalid API key or API secret",
    }
```



### Authentication on all endpoints
We require applications to authenticate all of their requests with Access Token. This visibility allows us to prevent abusive behavior, and it also helps us to further understand how categories of applications are using the API. We apply this understanding to better meet the needs of developers as we continue to evolve the platform. Register the Application with Connect4health and get your API_KEY and API_SECRET. With the api_key and api_secret send a request like below,

### Resource URL

`http://connecticket.railsfactory.com/api/authorize`

### Verb:
POST

<!-- ### Resource Information -->
Resource | Information
--------- | -----------
Response formats        | JSON
Requires authentication?| Yes

### Query Parameters

Parameter | Description | Required/Optional
--------- | ----------- |------------------
api_key   | api_key got while registering the application with Connect4health | Required
          | Example API Key: 8eb68e28cda407158cf9a8064bdd5351
api_secret| api_secret got while registering the application with Connect4health | Required
          | Example API Secret: b19fszzt9e2z4wpu87r09zy58

In Response, Access_token will be provided, with success message, this means that the app and user has been authorized successfully.
This access token should be used in further requests along with api_key and api_secret.


# Tickets

## Get All Tickets

This endpoint retrieves all the tickets created by the provider.

```shell
    "http://connecticket.railsfactory.com/api/356kdpiamhkz7a43nu0e2ldr9/tickets"
  In Headers: api_key: "8eb68e28cda407158cf9a8064bdd5351"
              api_secret: "b19fszzt9e2z4wpu87r09zy58"
```

> The above command returns JSON structured like this:

```
  Success response:

    {
        "status": true,
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

```
Error Response:

    {
      "status": false,
      "message": "Invalid Credentials",
    }

```
### Resource URL

`http://connecticket.railsfactory.com/api/<:access_token_got_from_authentication>/tickets`

### Verb:
GET

Resource | Information
--------- | -----------
Response formats        | JSON
Requires authentication?| Yes

### Query Parameters

Send the below parameters in Headers

Parameter | Description | Required/Optional
--------- | ----------- | -----------------
api_key   | api_key got while registering the application with connect4health    |  Required
          | Example API Key: 8eb68e28cda407158cf9a8064bdd5351
api_secret| api_secret got while registering the application with connect4health |  Required
          | Example API Secret: b19fszzt9e2z4wpu87r09zy58
access_token| Should be sent through url  |  Required
          | Example Access Token: ssdfsdf7s87878sd878d87fd

With the ***Access token*** provided in the url, the particular provider will be identified, and all the tickets created by the 
provider will be sent.

## Getting a specific Ticket

```shell
curl "http://connecticket.railsfactory.org/api/356kdpiamhkz7a43nu0e2ldr9/ticket_detail?id=201"
 In Headers:  api_key: "8eb68e28cda407158cf9a8064bdd5351"
              api_secret: "b19fszzt9e2z4wpu87r09zy58"
```

> The above command returns JSON structured like this:

```
Success response:

    {
        "status": true,
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
```
Error Response:

  Response 1:
    {
      "status": false,
      "message": "Invalid Credentials",
    }
  Response 2:
    {
      "status": false,
      "message": "Invalid Ticket ID",
    }

```
This endpoint retrieves a specific ticket created by the provider.

### Resource URL

`http://connecticket.railsfactory.com/api/<:access_token_got_from_authentication>/ticket_detail`

### Verb:
GET

Resource | Information
--------- | -----------
Response formats        | JSON
Requires authentication?| Yes

Parameter | Description | Required/Optional
--------- | ----------- | -----------------
api_key   | api_key got while registering the application with connect4health    |  Required
          | Example API Key: 8eb68e28cda407158cf9a8064bdd5351
api_secret| api_secret got while registering the application with connect4health |  Required
          | Example API Secret: b19fszzt9e2z4wpu87r09zy58
access_token| Should be sent through url  |  Required
          | Example Access Token: ssdfsdf7s87878sd878d87fd
id | Unique ID of the ticket  |   Required
   | Example ID: 12

Access Token helps in identifying the respective provider. The Ticket ID helps in displaying the respective ticket.  


## Get All Residents

```shell
    "http://connecticket.railsfactory.com/api/356kdpiamhkz7a43nu0e2ldr9/all_residents"
  In Headers: api_key: "8eb68e28cda407158cf9a8064bdd5351"
              api_secret: "b19fszzt9e2z4wpu87r09zy58"
```

> The above command returns JSON structured like this:

```
Success Response:
    {
        "status": true,
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
```
Error Response:

    {
      "status": false,
      "message": "Invalid Credentials",
    }

```
This endpoint retrieves the details of all the Residents of a particular provider.

### Resource URL

`http://connecticket.railsfactory.com/api/<:access_token_got_from_authentication>/all_residents`

### Verb:
GET

Resource | Information
--------- | -----------
Response formats        | JSON
Requires authentication?| Yes


Parameter | Description | Required/Optional
--------- | ----------- | -----------------
api_key   | api_key got while registering the application with connect4health    |  Required
          | Example API Key: 8eb68e28cda407158cf9a8064bdd5351
api_secret| api_secret got while registering the application with connect4health |  Required
          | Example API Secret: b19fszzt9e2z4wpu87r09zy58
access_token| Should be sent through url  |  Required
          | Example Access Token: ssdfsdf7s87878sd878d87fd

With the ***Access token*** provided in the url, the particular provider will be identified, and Residents of that particular
provider will be sent in response.
## Get Categories

```shell
    "http://connecticket.railsfactory.com/api/356kdpiamhkz7a43nu0e2ldr9/provider_categories"
  In Headers: api_key: "8eb68e28cda407158cf9a8064bdd5351"
              api_secret: "b19fszzt9e2z4wpu87r09zy58"
```

> The above command returns JSON structured like this:

```
Success Response"
{
    "status": true,
    "categories": [{"id": 3, "name": "Clinical Edit"},
                  {"id": 3, "name": "Emergency"},
                  {"id": 3, "name": "Activity Level"},
                  {"id": 3, "name": "Weight Gain"}]
 }
```
```
Error Response:

    {
      "status": false,
      "message": "Invalid Credentials",
    }
  
```

This endpoint will retrieve all the ticket categories created by particular provider. These categories have three status that needs to be set
while creating a ticket.

### Resource URL

`http://connecticket.railsfactory.com/api/<:access_token_got_from_authentication>/provider_categories`

### Verb:
GET

Resource | Information
--------- | -----------
Response formats        | JSON
Requires authentication?| Yes


Parameter | Description | Required/Optional
--------- | ----------- | -----------------
api_key   | api_key got while registering the application with connect4health    |  Required
          | Example API Key: 8eb68e28cda407158cf9a8064bdd5351
api_secret| api_secret got while registering the application with connect4health |  Required
          | Example API Secret: b19fszzt9e2z4wpu87r09zy58
access_token| Should be sent through url  |  Required
          | Example Access Token: ssdfsdf7s87878sd878d87fd

With the ***Access token*** provided in the url, the particular provider will be identified, and Categories of that particular
provider will be sent.

## Create Ticket

```shell
    "http://connecticket.railsfactory.com/api/356kdpiamhkz7a43nu0e2ldr9/create_ticket"
  In Headers: api_key: "8eb68e28cda407158cf9a8064bdd5351"
              api_secret: "b19fszzt9e2z4wpu87r09zy58"
```

> The above command returns JSON structured like this:

```
  Success Response:
  
  Response 1:
  {
    "status": true,
    "ticket_id": 46,
    "message": "Ticket Created Successfully!!"
  }

  
  Error Response:

  Response 1:
  {
    "status": false,
    "message": "Invalid ticket id!!"
  }

  Response 2:
  {
    "status": false,
    "message": "title/regarding required"
  }

  Response 3:
  {
    "status": false,
    "message": "Message cannot be created <:respective error message will be shown here>"
  }

```

This endpoint will create a ticket for a particular provider.

### Resource URL

`GET http://connecticket.railsfactory.com/api/<:access_token_got_from_authentication>/create_ticket`

### Verb:
GET

Resource | Information
--------- | -----------
Response formats        | JSON
Requires authentication?| Yes

Parameter | Description | Required/Optional
--------- | ----------- | -----------------
api_key   | api_key got while registering the application with connect4health    |  Required
          | Example API Key: 8eb68e28cda407158cf9a8064bdd5351
api_secret| api_secret got while registering the application with connect4health |  Required
          | Example API Secret: b19fszzt9e2z4wpu87r09zy58
access_token| Should be sent through url  |  Required
          | Example Access Token: ssdfsdf7s87878sd878d87fd
title     | title of ticket   | Required
          | Example Title: new test ticket
resident_id | id of the particular subscriber whom the ticket is created | Required
            | Example Resident ID: 34333
sms   | sms notification for the recipient  | optional
      | Example sms: true
email | email notification for the recipient  | optional
      | Example email: true
state |   | optional
      | Example state: true
urgency_status | urgency status of the ticket  | Required
               | Example Urgency Status: No Issue / Exception
ticket_status  | status of the ticket   | Required
               | Example Ticket Status: New
general_comments | general comments of the ticket | Optional
                 | Example general comments: Hi welcome!
attachment[:attachment_id]  | Add the attachment like attachment_1 = #<File:/tmp/RackMultipart20160223-10206-8nvy6z-0>, attachment_2 = #<File:/tmp/RackMultipart20160223-10206-8nvy6z-0>...etc.

Along with the above parameters: Category status also should be set. Category details of a particular provider can be fetched
from "Provider Categories" end point. Category status should be sent like below along with the category parameters(parameters we got from provider categories end point).

Parameter | Description
--------- | -----------
category_[:id] | Status of the category
            | Example Category ID : category_12 => "Issue"
category_comments_[:id]  | Comment for this category
                      | Example Category Comments ID  : category_comments_12 => "There are few comments."
category_[:id] | Status of the category
            | Example Category ID : category_13 => " No Issue"
category_comments_[:id]  | Comment for this category
                      | Example Category Comments ID  : category_comments_13 => "There are less comments."
category_[:id] | Status of the category
            | Example Category ID : category_16 => "Potential Issue"
category_comments_[:id]  | Comment for this category
                      | Example Category Comments ID  : category_comments_16 => "There are no comments."
Once the parameters are sent to the end point, ticket will be created and a success status will be sent.

## Ticket status update

```shell
    "http://connecticket.railsfactory.com/api/356kdpiamhkz7a43nu0e2ldr9/update_status?id=202&status=Reopen"
  In Headers: api_key: "8eb68e28cda407158cf9a8064bdd5351"
              api_secret: "b19fszzt9e2z4wpu87r09zy58"
```

> The above command returns JSON structured like this:

```
Success Response:
  {
    "status": true,
    "message": "Status Updated Successfully!!"
  }

Error Response:

  Response 1:
    {
      "status": false,
      "message": "Invalid Credentials",
    }

  Response 2:
    {
      "status": false,
      "message": "Invalid Ticket ID/ <:respective error message will appear here>",
    }
```
This end point updates the status of the ticket changed by the provider. 


### Resource URL

`http://connecticket.railsfactory.com/api/<:access_token_got_from_authentication>/update_status`

### Verb:
POST

Resource | Information
--------- | -----------
Response formats        | JSON
Requires authentication?| Yes


Parameter | Description | Required/Optional
--------- | ----------- | -----------------
api_key   | api_key got while registering the application with connect4health    |  Required
          | Example API Key: 8eb68e28cda407158cf9a8064bdd5351
api_secret| api_secret got while registering the application with connect4health |  Required
          | Example API Secret: b19fszzt9e2z4wpu87r09zy58
access_token| Should be sent through url  |  Required
          | Example Access Token: ssdfsdf7s87878sd878d87fd
id | Unique ID of the ticket  |   Required
   | Example ID: 12
status | status to be set for the ticket | Required
       | Example status: In Progress


With the respective Ticket ID, the status of the ticket updates.

## Create General Comment

```shell
    "http://connecticket.railsfactory.com/api/356kdpiamhkz7a43nu0e2ldr9/update_status?id=202&status=Reopen"
  In Headers: api_key: "8eb68e28cda407158cf9a8064bdd5351"
              api_secret: "b19fszzt9e2z4wpu87r09zy58"
```

> The above command returns JSON structured like this:

```
Success Response:
  {
    "status": true,
    "message": "Comment created Successfully!!"
  }
```
```
Error Response:

  Response 1:
    {
      "status": false,
      "message": "Invalid Credentials",
    }
  Response 2:
    {
      "status": false,
      "message": "Invalid Ticket ID",
    }
```
This end point is used to create comment for ticket. 

### Resource URL

`http://connecticket.railsfactory.com/api/<:access_token_got_from_authentication>/create_comment`

### Verb:
POST

Resource | Information
--------- | -----------
Response formats        | JSON
Requires authentication?| Yes


Parameter | Description | Required/Optional
--------- | ----------- | -----------------
api_key   | api_key got while registering the application with connect4health    |  Required
          | Example API Key: 8eb68e28cda407158cf9a8064bdd5351
api_secret| api_secret got while registering the application with connect4health |  Required
          | Example API Secret: b19fszzt9e2z4wpu87r09zy58
access_token| Should be sent through url  |  Required
          | Example Access Token: ssdfsdf7s87878sd878d87fd
ticket_id | Unique ID of the ticket  |   Required
   | Example Ticket ID: 12
comment | comment given by provider | Required
       | Example comment: Hi! Welcome!

Comment for this particular ticket is created by the above parameters.

## Create Category Comment

```shell
    "http://connecticket.railsfactory.com/api/356kdpiamhkz7a43nu0e2ldr9/update_status?id=202&status=Reopen"
  In Headers: api_key: "8eb68e28cda407158cf9a8064bdd5351"
              api_secret: "b19fszzt9e2z4wpu87r09zy58"
```

> The above command returns JSON structured like this:

```
Success Response:
  {
    "status": true,
    "message": "Comment created Successfully!!"
  }
```
```
Error Response:

  Response 1:
    {
      "status": false,
      "message": "Invalid Credentials",
    }
  Response 2:
    {
      "status": false,
      "message": "Invalid Ticket ID",
    }
```
This end point is used to create comment for a particular category. 

### Resource URL

`http://connecticket.railsfactory.com/api/<:access_token_got_from_authentication>/create_comment`

### Verb:
POST

Resource | Information
--------- | -----------
Response formats        | JSON
Requires authentication?| Yes


Parameter | Description | Required/Optional
--------- | ----------- | -----------------
api_key   | api_key got while registering the application with connect4health    |  Required
          | Example API Key: 8eb68e28cda407158cf9a8064bdd5351
api_secret| api_secret got while registering the application with connect4health |  Required
          | Example API Secret: b19fszzt9e2z4wpu87r09zy58
access_token| Should be sent through url  |  Required
          | Example Access Token: ssdfsdf7s87878sd878d87fd
ticket_id | Unique ID of the ticket  |   Required
   | Example Ticket ID: 12
comment | comment given by provider | Required
       | Example comment: Hi! Welcome!
category_id | Unique ID of the category | Required
            | Example category ID: 2

Comment for this particular category is created by the above parameters.

