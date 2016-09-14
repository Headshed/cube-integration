The following request can be used to get response data from Cube:
GET
```
https://YOURACCOUNT.cube4sales.com/responses?campaign_id={ID}&from={YYYYMMDD}&to={YYYYMMDD}
```
> HTTP Response: 200 OK
` campaign_id={ID} ` and ` from={YYYYMMDD} ` are mandatory.
The ` to=YYYYMMDD ` is optional (will use TODAY if not included)

## Example
(Add image to show configuration)
### Example response:

```json  
{
    {   "customer_id": 2488539,
        "name": "Lastname, Firstname",
        "updated": "2016-04-07",
        "updated_by": "magnus@headshed.no",
        "update_method": "Import new",
        "org_number": "989898981",
        "org_name": "Company GBH",
        "response_type": "Scheduled call",
        "scheduled_call_due_date": "28.02.2015",
        "comment": "Customer wanted to be contacted again nest week. Need to discuss offer with his CEO",
    }
    {
        "customer_id": 2488538,
        "name": "AnotherLastname, AnotherFirstname",
        "updated": "2016-04-07",
        "updated_by": "magnus@headshed.no",
        "update_method": "Response",
        "org_number": "777777777",
        "org_name": "Company AS",
        "response_type": "Completed with action",
        "comment": "Meeting accepted",
    }
    {
        "customer_id": 2488537,
        "name": "YetAnotherLastname, YetAnotherFirstname",
        "updated": "2016-04-07",
        "updated_by": "magnus@headshed.no",
        "update_method": "Import new",
        "org_number": "555555555",
        "org_name": "Company INC",
        "response_type": "Completed without action",
        "response_alternative": "Ingen ansatte å forsikre",
        "comment": "Customer do not want to be contacted about this again",
    }    
}
  ```

