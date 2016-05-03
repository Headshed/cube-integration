#Integration with Cube (WORK IN PROGRESS)

This is how you integrate with Cube, delivered by [Headshed](http://www.headshed.no)

## Authentication

## HTTP Basic Authentication

HTTP Basic authentication is the simplest way of interacting with the Cube API. Requests require a username and password. HTTPS is required for accessing the API.

## Making A Request
Here’s an example of interacting with Cube via JSON. To make requests in JSON, specify application/json for your Content-Type and Accept headers. A simple example with curl:

`curl -H 'Content-Type: application/json' -H 'Accept: application/json' -u "user@example.com:password" https://YOURACCOUNT.cube4sales.com/account/who_am_i`

Successful requests return HTTP response code 200. Other response codes indicate a failed request or missing resource, in which case an error message may be returned.

### Headers
Request headers need to be set up with the following:
```
Accept: application/json
Content-Type: application/json
Authorization: Basic (insert your authentication string here)
```
Your authentication string is a base64 encoded version of your credentials. You can generate this in Python:
`base64.b64encode("myemail@example.com:password")`

Or in JavaScript:
`btoa("myemail@example.com:password")`


## Clients, Assignments and Campaigns
Cube operates with a hierarchy of Clients, Assignments and Campaigns that hold various parts of the configuration.
All Customers managed in Cube is linked to an Assignment.
All Responses managed in Cube is linked to a Campaign.

[Clients-Assignments-Campaigns API] (https://github.com/Headshed/cube-integration/blob/master/Clients-Assignments-Campaigns.md)

## Importing data from CRM into Cube
For now, imports of customer records from various CRM solutions is done by the user of the CRM system with Excel spreadsheets. The Excel import is very flexible and can support any model. We are looking into implementing more CRM specific import integrations (e.g. Microsoft Dynamics, Siebel etc.), so please feel free to contact support@headshed.no if you have a specific need, and we will look into it.

## Recieving updated CRM records from Cube
In a typical use-case scenario, Cube is used to register all contact with a customer. When in contact with the customer, the Cube user can update the Customer information in Cube with e.g. a new phone number, email address, changed last name etc.

[Customer data API] (https://github.com/Headshed/cube-integration/blob/master/CustomerDataAPI.md)

## Recieving updated Response-records from Cube
In a typical use-case scenario, Cube is used to register all contact with a customer. Configuration of extra response information fields is done pr. Campaign in Cube, and the data is grouped by Campaign.

The following request can be used to get response data from Cube:
GET
```
https://YOURACCOUNT.cube4sales.com/responses?campaign_id={ID}&from={YYYYMMDD}&to={YYYYMMDD}
```
> HTTP Response: 200 OK
` campaign_id={ID} ` and ` from={YYYYMMDD} ` are mandatory.
The ` to=YYYYMMDD ` is optional (will use TODAY if not included)

## Example
(Add image to show configuration)
### Example response:

```json  
{
    {   "customer_id": 2488539,
        "name": "Lastname, Firstname",
        "updated": "2016-04-07",
        "updated_by": "magnus@headshed.no",
        "update_method": "Import new",
        "org_number": "989898981",
        "org_name": "Company GBH",
    }
    {
        "customer_id": 2488538,
        "name": "AnotherLastname, AnotherFirstname",
        "updated": "2016-04-07",
        "updated_by": "magnus@headshed.no",
        "update_method": "Import new",
        "org_number": "777777777",
        "org_name": "Company AS",
    }
    {
        "customer_id": 2488537,
        "name": "YetAnotherLastname, YetAnotherFirstname",
        "updated": "2016-04-07",
        "updated_by": "magnus@headshed.no",
        "update_method": "Import new",
        "org_number": "555555555",
        "org_name": "Company INC",
    }    
}
  ```
