# cube-integration
Integration with Cube

This is how you integrate with Cube, delivered by [Headshed](http://www.headshed.no)

Authentication

HTTP Basic Authentication

HTTP Basic authentication is the simplest way of interacting with the Harvest API. Requests require a username and password. HTTPS is required for accessing the API.

Making A Request
Here’s an example of interacting with Harvest via JSON. To make requests in JSON, specify application/json for your Content-Type and Accept headers. A simple example with curl:

`curl -H 'Content-Type: application/json' -H 'Accept: application/json' -u "user@example.com:password" https://example.cube4sales.com/account/who_am_i`

Successful requests return HTTP response code 200. Other response codes indicate a failed request or missing resource, in which case an error message may be returned.

Headers
Request headers need to be set up with the following:
`
Accept: application/json
Content-Type: application/json
Authorization: Basic (insert your authentication string here)`
Your authentication string is a base64 encoded version of your credentials. You can generate this in Python:

`base64.b64encode("myemail@example.com:password")`

Or in JavaScript:

`btoa("myemail@example.com:password")`


Importing data from CRM into Cube
For now, imports of customer records from various CRM solutions is done by the user of the CRM system with Excel spreadsheets. The Excel import is very flexible and can support any model. We are looking into implementing more CRM specific import integrations (e.g. Microsoft Dynamics, Siebel etc.), so please feel free to contact support@headshed.no if you have a specific need, and we will look into it.

Recieving updated CRM records from Cube
In a typical use-case scenario, Cube is used to register all contact with a customer. Whild donig this, the Cube user can updated the Customer information in Cube with e.g. a new phone number, email address, changed last name etc.
In these cases you can import

