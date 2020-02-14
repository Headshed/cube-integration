## Customer Custom Fields
The following request can be used to get all crm customer custom fields for a CRM in Cube:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/data_owners/{data_owner_id}/{crm_type}/crm_custom_fields/```

> HTTP Response: 200 OK

` {data_owner_id} ` is mandatory as a URL parameter. 
` {crm_type} ` is mandatory as a URL parameter. The crm type could be B2C or B2B.


## Example response:

Request example: https://xxx.headshed.com/api/v1/data_owners/2/B2C/crm_custom_fields/


```json  
[
    {
        "id": 64,
        "key": "Address street",
        "type": "text",
        "max_length": 250,
        "hint": "",
        "lookup__id": "crm__custom_info__64"     
    },
    {
        "id": 221,
        "key": "Adresse",
        "type": "text",
        "max_length": 200,
        "hint": "",
        "lookup__id": "crm__custom_info__221"
    },
    }    
]
  ```
## Lookup for crm__custom_info__xx fields
You will typically find the values of the custom fields in other API's such as:
*  [CallOutcomesAPI](https://github.com/Headshed/cube-integration/blob/master/CallOutcomes.md "Call Outcomes")
*  [CurrentCustomerStatus](https://github.com/Headshed/cube-integration/blob/master/CurrentCustomerStatus.md "Current Customer Status")
*  [CustomerDataAPI](https://github.com/Headshed/cube-integration/blob/master/CustomerData.md "Customer Data")
