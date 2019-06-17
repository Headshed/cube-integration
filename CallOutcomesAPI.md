The following request can be used to get call outcomes data from Cube:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/campaigns/{campaign_id}/call_outcomes/?from_date={YYYYMMDD}&to_date={YYYYMMDD}```

> HTTP Response: 200 OK

` {campaign_id} ` is mandatory as a URL parameter.
` from_date` and ` to_date ` are optional query parameters. Will return data from "today" one of them are not specified.

### Pagination
As the result may contain many responses, we use Pagination to limit the number of results fetched in one go.
The json response returned will have links (next/previous) you can use to navigate the results. These will be ```null```
when there are no more customers to fetch. The default pagination size is 500 (can be changed on request)


### Example response:
Request example: https://xxx.headshed.com/api/v1/campaigns/926/call_outcomes/?from_date=20170101&to_date=20170131

```json  
{
    "count": 781,
    "next":   "https://xxxx.headshed.com/api/v1/campaigns/10/call_outcomes/from_date=20190101&page=2&to_date=2019033,
    "previous": null,
    "results": [
        {
            "crm__customer_id": "12345",
            "crm__standard_info__name": "Ola Nordmann",
            "crm__standard_info__phone_1": "99998888",
            "crm__standard_info__phone_2": "",
            "crm__standard_info__phone_3": "",
            "crm__standard_info__email": "",
            "crm__change_log__updated": "2019-03-01",
            "crm__change_log__updated_by": "torbjorn@headshed.com",
            "crm__change_log__update_method": "Manual update",
            "crm__custom_info__108": 100200.0,
            "crm__custom_info__29": "ABC",
            "call_outcome__submitted_by": "torbjorn@headshed.com",
            "call_outcome__submitted_when": "2019-03-01 08:47",
            "call_outcome__type": "No answer",
            "call_outcome__subtype": "No answer",
            "call_outcome__submitted_in_department": "Salgsteam ABC",
            "call_outcome__comment": "",
            "call_outcome__additional_input_text": "",
            "campaign__name": "My Campaign",
            "assignment__name": "My Assignment",
            "client__short_name": "My Client"
        },
    ........
]
}
  ```

## Note on data prefixes
As you see from the returned response, there are prefixed fields like crm__xxx and response__xxx.
These refer to different parts of the information. The customer information is from the Cube internal CRM (on Assignment), while the response data. 
The "crm__customer_id" is the imported customer_id field, and NOT the same as the internal "id" field in the [CustomerData API](https://github.com/Headshed/cube-integration/blob/master/CustomerDataAPI.md "CustomerData API")

## Lookup for crm__custom_info__xx fields
The crm__custom_info__108 and crm__custom_info__29 fields in this example are custom fields defined on the crm model for the assignment ("My Assignment" in this case).
If you need to know the label/name of this field, you can look it up in the [CustomerCustomFields](https://github.com/Headshed/cube-integration/blob/master/CustomerCustomFields.md "Customer Custom Fields")
