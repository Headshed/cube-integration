# Integration with Headshed

This is how you integrate with the Headshed Cube REST API. 
Cube is delivered by [Headshed AS](http://www.headshed.no).

## Authentication and Headers

Cube supports Token, and Basic Authentication and provides data results in JSON format.
_We are open to implement other authentication methods upon client request._

See [Authentication and Headers](https://github.com/Headshed/cube-integration/blob/master/AuthenticationAndHeaders.md) for details on setting up Authentication and correct request headers.

## Data Owners and Campaigns
Cube operates with a hierarchy of Data Owners and Campaigns that hold various parts of the configuration.
All Customers managed in Cube is imported and linked to a data owner. 
All call outcomes managed in Cube is linked to a Customer and Campaign.

To investigate the properties of your Data Owners and Campaigns you can use the Cube web application or the 
[Data Owner-Campaigns API](https://github.com/Headshed/cube-integration/blob/master/CampaignStructure.md)


## Recieving updated CRM records from Cube
In a typical use-case scenario, Cube is used to register all contact with a customer. When in contact with the customer, the Cube user can update the Customer information in Cube with e.g. a new phone number, email address, changed last name etc. To retreive the updated CRM information, use the

[Customer data API](CustomerData.md)

## Recieving updated Call Outcome-records from Cube
In a typical use-case scenario, Cube is used to register all contact with a customer. Configuration of custom information fields is done pr. Campaign in Cube, and the data is grouped by Campaign.

[Call outcome data API](https://github.com/Headshed/cube-integration/blob/master/CallOutcomeData.md)

## Pagination of GET responses
Since the result of a GET request for may contain thousands of records, we use Pagination to limit the number of results fetched in one go. The json response returned will have links (next/previous) you can use to navigate the results. The ``next`` link will be null when there are no more customers to fetch. The result records are is put in a list (``results``).

The default pagination size is 50, meaning that only 50 records will be retrevied in each response.
The example response below show how this works. We see that there is a total number of 1200 records here, but only the 50 first are retreived in the ``results`` list. The customer records in the example have been reduced to only show an 'id' and only 2 of the 50 records.

```json
{
  "count": 1200,
  "next": "https://XXX.headshed.com/api/v1/campaigns/17/callflow_customers/?page=2",
  "previous": null,
  "results": [
    {
      "id": 11772,
    },
    {
      "id": 11773,
    },    
   ]
}   
```



The example code i Python below show how you can use the pagination links to retreive the complete list (of Customer records for a Campaign in this case)
```python
import requests

def read_customers_test():
    headers = {'Accept': 'application/json', 'Content-Type': 'application/json'}
    headers['Authorization'] = 'Basic bGlwcGUuc2xvcmRhbAAAAAAAAAAAAAAmQwOQ=='
    url = 'https://demo.headshed.com/api/v1/campaigns/100/callflow_customers/'
    customer_retrieved = []

    response = requests.get(url=url, headers=headers)
    customer_retrieved.extend(response.json().get('results'))

    while response.json().get('next') is not None:
        response = requests.get(url=response.json().get('next'), headers=headers)
        customer_retrieved.extend(response.json().get('results'))

    return customer_retrieved
```
## Example
This is an example flow to use the API's to retrieve updated response- and customer data from Cube.

1. Get the campaign id's you want to retrieve data for. You can find this in the Cube web-application, or you can use the [DataOwners-Campaigns API](https://github.com/Headshed/cube-integration/blob/master/CampaignStructure.md) to look them up.
2. Iterate the list of Campaigns you want to see, gather the Call outcome information you are looking for using the [Call outcome data API](https://github.com/Headshed/cube-integration/blob/master/CallOutcomeData.md)
3. If you want more details on the Customer cards, retrieve the Customer data using the [Customer data API](https://github.com/Headshed/cube-integration/blob/master/CustomerData.md). The Call outcome-records and Customer-records will match on ` customer_id `
4. Transform and store the updated data in your CRM system
