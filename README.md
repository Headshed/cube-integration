#Integration with Headshed (WORK IN PROGRESS)

This is how you integrate with the Headshed Cube REST API. 
Cube is delivered by [Headshed AS](http://www.headshed.no).

## Authentication and Headers

Cube supports Token based, and Basic Authentication and provides data in JSON format.
_We are open to implement other authentication methods upon client request._

See [Authentication and Headers] (https://github.com/Headshed/cube-integration/blob/master/AuthenticationAndHeaders.md) for details on setting up Authentication and correct request headers.

## Clients, Assignments and Campaigns
Cube operates with a hierarchy of Clients, Assignments and Campaigns that hold various parts of the configuration.
All Customers managed in Cube is imported and linked to an Assignment.
All Responses managed in Cube is linked to a Customer and Campaign.

To investigate the properties of your Clients/Assignment/Campaigns you can use the Cube web application or the 
[Clients-Assignments-Campaigns API] (https://github.com/Headshed/cube-integration/blob/master/Clients-Assignments-Campaigns.md)

## Importing customer data from _any_ CRM into Cube
Customer records are imported into an Assignment, and Customer records can be imported via the REST API for CRM data. We have a flexible/extensible data model where you can configure an Assignment to support any extra information fields you want to use.

[Customer data API] (CustomerDataAPI.md)

Imports of customer records from various CRM solutions can also be done in the Cube web application by the user of the CRM system via Excel spreadsheets. As mentioned, the import is very flexible and can support any model.(e.g. data from Microsoft Dynamics, Siebel, SAP, Hubspot etc.).

## Updating customer data from _any_ CRM into Cube
If you have updated CRM records you want the users in Cube to know about, you can update Customer records via the API.

[Customer data API] (CustomerDataAPI.md)

## Recieving updated CRM records from Cube
In a typical use-case scenario, Cube is used to register all contact with a customer. When in contact with the customer, the Cube user can update the Customer information in Cube with e.g. a new phone number, email address, changed last name etc. To retreive the updated CRM information, use the

[Customer data API] (CustomerDataAPI.md)

## Recieving updated Response-records from Cube
In a typical use-case scenario, Cube is used to register all contact with a customer. Configuration of extra response information fields is done pr. Campaign in Cube, and the data is grouped by Campaign.

[Response data API] (https://github.com/Headshed/cube-integration/blob/master/ResponseDataAPI.md)


## Example
This is an example of how you can use the API's to retrieve updated response- and customer data from Cube.

1. Get the campaign- and assignment id's you want to retrieve data for. You can find this in the Cube web-application, or you can use the [Clients-Assignments-Campaigns API] (https://github.com/Headshed/cube-integration/blob/master/Clients-Assignments-Campaigns.md) to look them up.
2. Iterate the list of Campaigns you want to see, gather the Response information you are looking for using the [Response data API] (https://github.com/Headshed/cube-integration/blob/master/ResponseDataAPI.md)
3. If you want more details on the Customer cards, retrieve the Customer data using the [Customer data API] (https://github.com/Headshed/cube-integration/blob/master/CustomerDataAPI.md). You will need the assignment_id. The Response-records and Customer-records will match on ` customer_id `
4. Transform and store the updated data in your CRM system

