#Integration with Cube

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

## Importing data from CRM into Cube
For now, imports of customer records from various CRM solutions is done by the user of the CRM system with Excel spreadsheets. The Excel import is very flexible and can support any model. We are looking into implementing more CRM specific import integrations (e.g. Microsoft Dynamics, Siebel etc.), so please feel free to contact support@headshed.no if you have a specific need, and we will look into it.

## Recieving updated CRM records from Cube
In a typical use-case scenario, Cube is used to register all contact with a customer. Whild doig this, the Cube user can update the Customer information in Cube with e.g. a new phone number, email address, changed last name etc.
Extra information may also be configured and updated in the customer.

The following post can be used to get Customer data from Cube:
GET
```
https://YOURACCOUNT.cube4sales.com/crm/customers?assignment_id={ID}
```
> HTTP Response: 200 OK

## Example
In this example, we have asked for all Customer records in assignment #9. What type of assignment this is can be seen in Cube. (TODO. Add REST API for listing Assignments)
Assignment #9 in this example have been configured as a B2B-assignment (Customer records are companies), and 6 assignment specific extra information fields have been configured:
(Add image to show configuration)
In the customer record shown below, only 3 if the assignment specific fields have data registered, and hence only these are displayed/included.
For other customer data, all fields are shown (with `null` values when no data is registered)

### Example response:

```json  
{
    "customer_id": 2488539,
    "name": "Lastname, Firstname",
    "gender": null,
    "birth_date": null,
    "assignment_id": 9,
    "care_of_name": null,
    "address_street": null,
    "address_street_no": null,
    "address_entrance": null,
    "zip_code": null,
    "city": "ELVERUM",
    "municipality": null,
    "county": "Hedmark",
    "country": null,
    "phone_1": "99999999",
    "phone_2": null,
    "phone_3": null,
    "email": null,
    "more_info_fields": {},
    "updated": "2016-04-07",
    "updated_by": "magnus@headshed.no",
    "update_method": "Import new",
    "org_number": "989898981",
    "org_number_main": "999911111",
    "org_name": "Company AS",
    "nace_code": null,
    "nace_text": "Utgivelse av blader og tidsskrifter",
    "number_of_employees": "6",
    "company_type": null,
    "established": null,
    "credit_rating": null,
    "need_to_know": null,
    "url": null,
    "company_email": "company@domain.no",
    "revenue": null,
    "po_box": null,
    "postal_address": null,
    "postal_zip": null,
    "postal_city": null,
    "Klassifisering": "C",
    "Landsforening": "XYZ",
    "Region": "Innlandet",
    "Hoved": "Ja"
  },
  ```
## Recieving updated Response-records from Cube
In a typical use-case scenario, Cube is used to register all contact with a customer. Configuration of extra response information fields is done pr. Campaign in Cube, and the data is grouped by Campaign.

The following request can be used to get response data from Cube:
GET
```
https://YOURACCOUNT.cube4sales.com/responses?from=YYYYMMDD&to=YYYYMMDD
```
> HTTP Response: 200 OK
The ` to=YYYYMMDD ` is optional (will use TODAY if not included)
You can also add an optional ` campaign_id={ID} ` argument if you want to limit the responses to only one campaign.

## Example
(Add image to show configuration)
### Example response:

```json  
{
"campaign_entry": {
        "client_name": "My Client Name",
        "client_id": 2,
        "assignment_name": "My Assignment Name",
        "assignment_id": 3,
        "campaign_name": "My Campaign Name",
        "campaign_id": 32,
        "response_entry": {
            "customer_id": 2488539,
            "name": "Lastname, Firstname",
            "updated": "2016-04-07",
            "updated_by": "magnus@headshed.no",
            "update_method": "Import new",
            "org_number": "989898981",
            "org_name": "Company GBH",
        }
        "response_entry": {
            "customer_id": 2488538,
            "name": "AnotherLastname, AnotherFirstname",
            "updated": "2016-04-07",
            "updated_by": "magnus@headshed.no",
            "update_method": "Import new",
            "org_number": "777777777",
            "org_name": "Company AS",
        }
        "response_entry": {
            "customer_id": 2488537,
            "name": "YetAnotherLastname, YetAnotherFirstname",
            "updated": "2016-04-07",
            "updated_by": "magnus@headshed.no",
            "update_method": "Import new",
            "org_number": "555555555",
            "org_name": "Company INC",
        }    
    }
    "campaign_entry": {
        "client_name": "My Client Name",
        "client_id": 2,
        "assignment_name": "My Assignment Name",
        "assignment_id": 3,
        "campaign_name": "Another Campaign Name",
        "campaign_id": 33,
        "response_entry": {
            "customer_id": 5488539,
            "name": "Lastname, Firstname",
            "updated": "2016-04-07",
            "updated_by": "magnus@headshed.no",
            "update_method": "Import new",
            "org_number": "779898981",
            "org_name": "Company XYX",
        }
        "response_entry": {
            "customer_id": 762488538,
            "name": "AnotherLastname, AnotherFirstname",
            "updated": "2016-04-07",
            "updated_by": "magnus@headshed.no",
            "update_method": "Import new",
            "org_number": "222222222",
            "org_name": "Company ABC",
        }
    }
}
  ```
