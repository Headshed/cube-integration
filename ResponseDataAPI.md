The following request can be used to get call outcomes data from Cube:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/campaigns/{campaign_id}/call_outcomes/?from_date={YYYYMMDD}&to_date={YYYYMMDD}&call_outcomes=Sale```

> HTTP Response: 200 OK

` {campaign_id} ` is mandatory as a URL parameter.
` from_date` and ` to_date ` are optional query parameters. Will return data from "today" one ofthem are not specified.
`call_outcomes` is an optional parameter to filter the result to a specific call outcome type (e.g. Sale, Offer etc.) 

### Pagination
As the result may contain many call outcomes, we use Pagination to limit the number of results fetched in one go.
The json response returned will have links (next/previous) you can use to navigate the results. These will be ```null```
when there are no more customers to fetch. The default pagination size is 50 (can be changed on request)


### Example response:
Request example: https://xxx.headshed.com/api/v1/campaigns/926/call_outcomes/?from_date=20170101&to_date=20170131&call_outcomes_type=Sale

```json  
{
    "count": 2,
    "next": null,
    "previous": null,
    "results": [
        {
            "crm__customer_id": "1186",
            "crm__standard_info__name": "Torbjørn Slørdal",
            "crm__standard_info__phone_1": "90978457",
            "crm__standard_info__phone_2": "97747430",
            "crm__standard_info__phone_3": "40218008",
            "crm__standard_info__email": "torbjorn@headshed.com",
            "crm__change_log__updated": "2019-01-14",
            "crm__change_log__updated_by": "lene@headshed.com",
            "crm__change_log__update_method": "Manual update",
            "crm__custom_info__115": "",
            "crm__custom_info__30": "",
            "crm__custom_info__29": "",
            "crm__custom_info__166": "",
            "crm__custom_info__117": "",
            "crm__custom_info__123": "",
            "crm__custom_info__122": "",
            "crm__custom_info__31": "",
            "crm__custom_info__118": "",
            "crm__custom_info__120": "",
            "crm__custom_info__28": "",
            "crm__custom_info__27": "",
            "crm__custom_info__121": "",
            "crm__custom_info__119": "",
            "crm__custom_info__116": "",
            "call_outcome__submitted_by": "lene@headshed.com",
            "call_outcome__submitted_when": "2019-10-01 10:22",
            "call_outcome__type": "Call back later",
            "call_outcome__subtype": "Call back later",
            "call_outcome__submitted_in_department": "TestingSS",
            "call_outcome__comment": "",
            "call_outcome__extra__jjj": "",
            "call_outcome__extra__iuu": "",
            "call_outcome__extra__aeaer-aeraer": "",
            "call_outcome__extra__Studielån88": "",
            "call_outcome__extra__aefaef": "",
            "call_outcome__extra__ID": "",
            "call_outcome__additional_input_text": "Followup time: Between 02.10.2019 08:00 and 02.10.2019 21:00 \n",
            "campaign__name": "Sjekk av assignment fields",
            "crm_type__name": "Lenes CSI test",
            "data_owner__name": "Client",
            "segment__name": "Default segment"
        },
    ........
]
}
  ```

## Note on data prefixes
As you see from the response, there are prefixed fields like crm__xxx and call_outcome__xxx.
These refer to different parts of the information. The customer information is from the Cube internal CRM.
The "crm__customer_id" is the imported customer_id field, and NOT the same as the internal "id" field in the [CustomerData API](https://github.com/Headshed/cube-integration/blob/master/CustomerDataAPI.md "CustomerData API")
