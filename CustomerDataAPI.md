## Customer data API - Retrieving all customer records.
The following request can be used to get all customer data for an assignment in Cube:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/assignments/{ASSIGNMENT_ID}/customers/```

Cube will return > HTTP Response: 200 OK and a JSON containing a list of customer records similar to the example below.


## Example

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/assignments/9/customers/```

In this example, we have asked for all Customer records in assignment #9. What type of assignment this is can be seen in the Cube GUI. (We will add API support for listing assignment information).
Assignment #9 in this example have been configured as a B2C-assignment (Customer records are consumers), and 6 assignment specific extra information fields have been configured:

For standard customer data fields, the fields are shown (with `null` values when no data is registered)

**Paginated results**
As the result may contain thousands of customer records, we use Pagination to limit the number of results fetched in one go. The json response returned will have links (next/previous) you can use to navigate the results. These will be null when there are no more customers to fetch. 
The result records are is put in a list (results).

The default pagination size is 50 (can be changed on request).

```json  
{
  "count": 3909,
  "next": "http://YOURACCOUNT.headshed.com/api/v1/assignments/9/customers/?page=2",
  "previous": null,
  "results": [
    {
      "id": 971352,
      "customer_id": 793558,
      "assignment_id": 98,
      "name": "SOME CUSTOMER NAME",
      "gender": "",
      "birth_date": null,
      "need_to_know": "Startet 2000-04-12, termin 3 | OR",
      "care_of_name": "",
      "zone_name": "",
      "address_street": "SOME ROAD",
      "address_street_no": 21,
      "address_entrance": "",
      "zip_code": "3940",
      "city": "MIDDLE_OF_NOWHERE",
      "municipality": null,
      "county": "",
      "country": "",
      "phone_1": "99999999",
      "phone_2": "88888888",
      "phone_3": null,
      "email": "",
      "company": null,
      "active products": null,
      "gen info 1": "3.0",
      "gen info 2": null,
      "gen info 3": "OR",
      "gen info 5": "AGD_101215_update",
      "gen date 2": "2000-04-12"
    },
    {
      "id": 971486,
      "customer_id": 781284,
      "assignment_id": 98,
      "name": "ANOTHER CUSTOMER NAME",
      "gender": "",
      "birth_date": null,
      "need_to_know": "OR",
      "care_of_name": "",
      "zone_name": "",
      "address_street": "MIDDLE_OF_NOWHERE",
      "address_street_no": null,
      "address_entrance": "",
      "zip_code": "3870",
      "city": "FYRESDAL",
      "municipality": null,
      "county": "",
      "country": "",
      "phone_1": "48272265",
      "phone_2": "48272265",
      "phone_3": null,
      "email": "",
      "company": null,
      "active products": "3",
      "gen info 1": "Standard giro",
      "gen info 2": null,
      "gen info 3": "OR",
      "gen info 5": "AGD_101215_update",
      "gen date 2": "2015-06-12"
    }
  ]
}
  ```

## Reading paginated data from the API - example code in Python
The code below is an example on how you can use the pagination to retrieve all customers from an assignment.
```python
import requests

def read_customers_test():
    headers = {'Accept': 'application/json', 'Content-Type': 'application/json'}
    headers['Authorization'] = 'Basic YOUR_BASE64_ENCODED_STRING_HERE'
    url = 'https://XXXX.headshed.com/api/v1/assignments/240/customers/'
    customer_retrieved = []

    response = requests.get(url=url, headers=headers)
    customer_retrieved.extend(response.json().get('results'))

    while response.json().get('next') is not None:
        response = requests.get(url=response.json().get('next'), headers=headers)
        customer_retrieved.extend(response.json().get('results'))

    return customer_retrieved
```

## Customer data API - Retrieving a single customer record.
The following request can be used to get Customer data from Cube:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/assignments/{ASSIGNMENT_ID}/customers/{CUSTOMER_ID}```

The assignment_id and customer_id must be integers.
**NOTE:** The customer_id is the internal id ('id') for the customer record. (Do not use the 'external_customer_id')

The API will return a > HTTP Response: 200 OK, and a JSON response with all available customer data, including any extra information fields configured for the assignment.
### Example response:

```json  
{
  "id": 20101,
  "assignment_id": 246,
  "name": "Olas Reklameservice AS",
  "gender": "",
  "birth_date": null,
  "need_to_know": "500 mbps, 3990 kr",
  "care_of_name": null,
  "zone_name": "",
  "address_street": "My address",
  "address_street_no": 32,
  "address_entrance": "",
  "zip_code": "7000",
  "city": "Trondheim",
  "municipality": "",
  "county": "",
  "country": "",
  "phone_1": "90978457",
  "phone_2": "",
  "phone_3": "",
  "email": "ola@olasreklameservice.no",
  "Oppstartsdato": "2011-12-12",
  "Antall år": "6",
  "Pris på dagens avtale": "3990"
  "external_customer_id" : 999888
}
  ```


## Customer data API - Updating customer records.
The following request can be used to update Customer data records in Cube:

**PUT** ```https://YOURACCOUNT.headshed.com/api/v1/assignments/{ASSIGNMENT_ID}/customers/{CUSTOMER_ID}```

The PUT body must contain the fields you want to update, and MUST include assignment_id and customer_id.
**NOTE:** The customer_id is the internal id ('id') for the customer record. (Do not use the 'external_customer_id')

In the example below, we want to update ```gender```

```json 
{
    "gender": "Male"
}
```  

Once updated, we will send a ```HTTP Response: 200 OK``` and return all data for the updated customer record.


## Customer data API - Creating customer records. (NOT YET IMPLEMENTED)
The following request can be used to create Customer data records in Cube:

**POST** ```https://YOURACCOUNT.headshed.com/api/v1/assignments/{ASSIGNMENT_ID}/customers/{CUSTOMER_ID}```

To create a new customer record, you need to POST the following parameters. Mandatory parameters have a * next to them.

| Parameter     | Description |
| ------------- |-------------|
| customer_id *  | A unique customer ID (typically the id from your CRM system |
| assignment_id * | The id of the assignment where the customer should be placed |
| name          | Name of the customer |
| etc..         | We have a lot of fields - will add them later |


