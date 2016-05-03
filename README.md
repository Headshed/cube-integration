#Integration with Cube (WORK IN PROGRESS)

This is how you integrate with Cube, delivered by [Headshed](http://www.headshed.no)

## Authentication and Headers

Cube supports Basic Authentication and JSON format.
[Authentication and Headers] (https://github.com/Headshed/cube-integration/blob/master/AuthenticationAndHeaders.md)

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

[Response data API] (https://github.com/Headshed/cube-integration/blob/master/ResponseDataAPI.md)

