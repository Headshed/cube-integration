## CRM Customer data
The following request can be used to get all customer data for a CRM in Cube:

**GET** ```https://xxx.headshed.com/api/v1/data_owners/{data_owner_id}/{crm_type}/customers/```

> HTTP Response: 200 OK

` {data_owner_id} ` is mandatory as a URL integer parameter. 
` {crm_type} ` is mandatory as a URL string parameter. The crm type could be B2C or B2B.


### Example response:

Request example: https://xxx.headshed.com/api/v1/data_owners/2/B2C/customers/

```json  
{
    "count": 701,
    "next": "http://YOURDOMAIN.headshed.com/api/v1/data_owners/2/B2C/customers/",
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
  ```

### Reading paginated data from the API - example code in Python
The code below is an example on how you can use the pagination to retrieve all customers from an assignment.
```python
import requests

def read_customers_test():
    headers = {'Accept': 'application/json', 'Content-Type': 'application/json'}
    headers['Authorization'] = 'Basic YOUR_BASE64_ENCODED_STRING_HERE'
    url = 'https://XXXX.headshed.com/api/v1/data_owners/2/B2C/customers/'
    customer_retrieved = []

    response = requests.get(url=url, headers=headers)
    customer_retrieved.extend(response.json().get('results'))

    while response.json().get('next') is not None:
        response = requests.get(url=response.json().get('next'), headers=headers)
        customer_retrieved.extend(response.json().get('results'))

    return customer_retrieved
```

## Retrieving a single customer record
The following request can be used to get Customer data from Cube:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/data_owners/{data_owner_id}/{crm_type}/customers/{customer_id}```

> HTTP Response: 200 OK

` {data_owner_id} ` is mandatory as a URL integer parameter. 
` {crm_type} ` is mandatory as a URL string parameter. The crm type could be B2C or B2B.
` {customer_id} ` is mandatory as a URL integer parameter. 


### Example response:

Request example: https://xxx.headshed.com/api/v1/data_owners/2/B2C/customers/9120011888

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



