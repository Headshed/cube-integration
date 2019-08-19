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
            "crm__customer_id": "999988887777",
            "crm__standard_info__name": "Kari Nordnmann",
            "crm__standard_info__phone_1": "90978457",
            "crm__standard_info__phone_2": "97747430",
            "crm__standard_info__phone_3": "40218008",
            "crm__standard_info__email": "kari_nordmann@online.no",
            "crm__custom_info__3900": "Olavegen 20",
            "crm__custom_info__3902": "TROLLSTIGEN",
            "crm__custom_info__1405": "9999723623",
            "crm__custom_info__1410": "TM",
            "crm__custom_info__1406": "2019-07-26",
            "crm__custom_info__3901": "3520",
            "call_outcome__submitted_by": "selger@selskap.no",
            "call_outcome__submitted_when": "2019-08-14 09:34",
            "call_outcome__type": "Sale",
            "call_outcome__subtype": "Ja - Salg",
            "call_outcome__submitted_in_department": "Trondheim",
            "call_outcome__comment": "",
            "call_outcome__extra__Innkommende samtale": "",
            "call_outcome__extra__Fast ansatt over 50 %": true,
            "call_outcome__additional_input_text": "",
            "campaign__name": "Forsikringskampanje 2019",
            "assignment__name": "Nysalg-privatkunder",
            "client__short_name": "NorgesForsikring AS"
        },
    ........
]
}
  ```

## Note on data prefixes
As you see from the returned response, there are prefixed fields like crm__xxx and call_outcome__xxx.
These refer to different parts of the information model. The customer information is from the Cube internal CRM (we have one dataset pr. Assignment), while the call outcome data is related to the current campaign. 
The "crm__customer_id" is the imported customer_id field, and NOT the same as the internal "id" field in the [CustomerData API](https://github.com/Headshed/cube-integration/blob/master/CustomerDataAPI.md "CustomerData API")

## Lookup for crm__custom_info__xx fields
The crm__custom_info__108 and crm__custom_info__3900 fields in this example are custom fields defined on the crm model for the assignment ("Nysalg-privatkunder" in this case).
If you need to know the label/name of this field, you can look it up in the [CustomerCustomFields](https://github.com/Headshed/cube-integration/blob/master/CustomerCustomFields.md "Customer Custom Fields")
