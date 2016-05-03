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
    }
    {
        "customer_id": 2488538,
        "name": "AnotherLastname, AnotherFirstname",
        "updated": "2016-04-07",
        "updated_by": "magnus@headshed.no",
        "update_method": "Import new",
        "org_number": "777777777",
        "org_name": "Company AS",
    }
    {
        "customer_id": 2488537,
        "name": "YetAnotherLastname, YetAnotherFirstname",
        "updated": "2016-04-07",
        "updated_by": "magnus@headshed.no",
        "update_method": "Import new",
        "org_number": "555555555",
        "org_name": "Company INC",
    }    
}
  ```

