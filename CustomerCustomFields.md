## Customer Custom Fields data API - Retrieving all customer custom fields records.
The following request can be used to get all crm customer custom fields for an assignment in Cube:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/assignments/{ASSIGNMENT_ID}/crm_custom_fields/```

Cube will return > HTTP Response: 200 OK and a JSON containing a list of customer custom field records similar to the example below.


## Example

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/assignments/9/crm_custom_fields/```

In this example, we have asked for all Customer Custom Field records in assignment #9. What type of assignment this is can be seen in the Cube GUI.
Assignment #9 in this example have been configured with 3 custom fields.
The result records are is put in a list:

```json  
[
    {
        "id": 1,
        "key": "active products",
        "type": "text",
        "max_length": 999,
        "hint": ""
    },
    {
        "id": 2,
        "key": "Previous bank",
        "type": "text",
        "max_length": 250,
        "hint": ""
    },
    {
        "id": 3,
        "key": "Bonus programme",
        "type": "text",
        "max_length": 250,
        "hint": ""
    }    
]
  ```
## Lookup for crm__custom_info__xx fields
You will typically find the values of the custom fields in other API's such as:
*  [CallOutcomesAPI](https://github.com/Headshed/cube-integration/blob/master/CallOutcomesAPI.md "Call Outcomes API")
*  [CurrentCustomerStatus](https://github.com/Headshed/cube-integration/blob/master/CurrentCustomerStatus.md "Current Customer Status")
*  [CustomerDataAPI](https://github.com/Headshed/cube-integration/blob/master/CustomerDataApi.md "Customer Data API")
