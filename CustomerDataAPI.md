## Customer data API - Retrieving all customer records.
The following request can be used to get all customer data for an assignment in Cube:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/assignments/{ASSIGNMENT_ID}/customers/```

Cube will return > HTTP Response: 200 OK and a JSON containing a list of customer records similar to the example below.


## Example

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/assignments/9/customers/```

In this example, we have asked for all Customer records in assignment #9. What type of assignment this is can be seen in the Cube GUI.
Assignment #9 in this example have been configured as a B2C-assignment (Customer records are consumers), and 6 customer custom fields have been configured:

For standard customer fields, the fields are shown (with `null` values when no data is registered)

**Paginated results**
As the result may contain thousands of customer records, we use Pagination to limit the number of results fetched in one go. The json response returned will have links (next/previous) you can use to navigate the results. These will be null when there are no more customers to fetch. 
The result records are is put in a list (results).

The default pagination size is 500 (can be changed on request).

```json  
{
    "count": 701,
    "next": "http://YOURDOMAIN.headshed.com/api/v1/assignments/1/customers/?page=2",
    "previous": null,
    "results": [
        {
            "crm__customer_id": "9120011999",
            "crm__standard_info__name": "Olas Produksjon AS",
            "crm__standard_info__phone_1": "90909090",
            "crm__standard_info__phone_2": "",
            "crm__standard_info__phone_3": "",
            "crm__standard_info__email": "olan@produksjon.no",
            "crm__custom_info__17": "A",
            "crm__custom_info__388": "Olaveien 2",
            "crm__custom_info__225": "",
            "crm__custom_info__390": "ASKIM",
            "crm__custom_info__78": "",
            "crm__custom_info__253": 233,
            "crm__custom_info__79": "",
            "crm__custom_info__103": "",
            "crm__custom_info__101": "",
            "crm__custom_info__102": "",
            "crm__custom_info__104": "",
            "crm__custom_info__100": "",
            "crm__custom_info__387": "99988899",
            "crm__custom_info__385": "Per Olsen",
            "crm__custom_info__391": "Olaveien 2, 1832 ASKIM",
            "crm__custom_info__24": "1948-01-01",
            "crm__custom_info__18": "PRODUKSJON",
            "crm__custom_info__19": "BNL",
            "crm__custom_info__20": "1281847542.0",
            "crm__custom_info__21": "233.0",
            "crm__custom_info__386": "Klassifisering A",
            "crm__custom_info__389": "1832"
        },
        {
            "crm__customer_id": "9120011888",
            "crm__standard_info__name": "Pers Hårklipperi AS",
            "crm__standard_info__phone_1": "90909088",
            "crm__standard_info__phone_2": "",
            "crm__standard_info__phone_3": "",
            "crm__standard_info__email": "per@klipperiet.no",
            "crm__custom_info__17": "A",
            "crm__custom_info__388": "Perveien 2",
            "crm__custom_info__225": "",
            "crm__custom_info__390": "ASKIM",
            "crm__custom_info__78": "",
            "crm__custom_info__253": 233,
            "crm__custom_info__79": "",
            "crm__custom_info__103": "",
            "crm__custom_info__101": "",
            "crm__custom_info__102": "",
            "crm__custom_info__104": "",
            "crm__custom_info__100": "",
            "crm__custom_info__387": "99988899",
            "crm__custom_info__385": "Per Olsen",
            "crm__custom_info__391": "Perveien 2, 1832 ASKIM",
            "crm__custom_info__24": "1973-01-01",
            "crm__custom_info__18": "FRISØR",
            "crm__custom_info__19": "BNL",
            "crm__custom_info__20": "1281847542.0",
            "crm__custom_info__21": "233.0",
            "crm__custom_info__386": "Klassifisering A",
            "crm__custom_info__389": "1832"
        },
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

The API will return a > HTTP Response: 200 OK, and a JSON response with all available customer data, including any cuistom fields configured for the assignment.
### Example response:

```json  
{
            "crm__customer_id": "9120011888",
            "crm__standard_info__name": "Pers Hårklipperi AS",
            "crm__standard_info__phone_1": "90909088",
            "crm__standard_info__phone_2": "",
            "crm__standard_info__phone_3": "",
            "crm__standard_info__email": "per@klipperiet.no",
            "crm__custom_info__17": "A",
            "crm__custom_info__388": "Perveien 2",
            "crm__custom_info__225": "",
            "crm__custom_info__390": "ASKIM",
            "crm__custom_info__78": "",
            "crm__custom_info__253": 233,
            "crm__custom_info__79": "",
            "crm__custom_info__103": "",
            "crm__custom_info__101": "",
            "crm__custom_info__102": "",
            "crm__custom_info__104": "",
            "crm__custom_info__100": "",
            "crm__custom_info__387": "99988899",
            "crm__custom_info__385": "Per Olsen",
            "crm__custom_info__391": "Perveien 2, 1832 ASKIM",
            "crm__custom_info__24": "1973-01-01",
            "crm__custom_info__18": "FRISØR",
            "crm__custom_info__19": "BNL",
            "crm__custom_info__20": "1281847542.0",
            "crm__custom_info__21": "233.0",
            "crm__custom_info__386": "Klassifisering A",
            "crm__custom_info__389": "1832"
        }
  ```
## Lookup for crm__custom_info__xx fields
The crm__custom_info__17 and crm__custom_info__388 fields in this example are custom fields defined on the crm model for the assignment.
If you need to know the label/key of this field, you can look it up in the [CustomerCustomFields](https://github.com/Headshed/cube-integration/blob/master/CustomerCustomFields.md "Customer Custom Fields")

## Customer data API - Updating customer records. (NOT YET IMPLEMENTED)
The following request can be used to update Customer data records in Cube:

**PUT** ```https://YOURACCOUNT.headshed.com/api/v1/assignments/{ASSIGNMENT_ID}/customers/{CUSTOMER_ID}```

The PUT body must contain the fields you want to update, and MUST include assignment_id and customer_id.

In the example below, we want to update ```gender```

```json 
{
    "crm__standard_info__phone_2": "90978457"
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


