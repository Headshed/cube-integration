The following request can be used to get response data from Cube:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/campaigns/{campaign_id}/call_outcomes/?from_date={YYYYMMDD}&to_date={YYYYMMDD}&call_outcome_type=Sale```

> HTTP Response: 200 OK

` {campaign_id} ` is mandatory as a URL parameter.
` from_date` and ` to_date ` are optional query parameters. Will return data from "today" one ofthem are not specified.
`call_outcome_type` is an optional parameter to filter the result to a specific call outcome type (e.g. Sale, Offer etc.) 

### Pagination
As the result may contain many responses, we use Pagination to limit the number of results fetched in one go.
The json response returned will have links (next/previous) you can use to navigate the results. These will be ```null```
when there are no more customers to fetch. The default pagination size is 500 (can be changed on request)


### Example response:
Request example: https://xxx.headshed.com/api/v1/campaigns/926/call_outcomes/?from_date=20170101&to_date=20170131&call_outcome_type=Sale

```json  
{
  "count": 207,
  "next": "https://xxx.headshed.com/api/v1/campaigns/926/responses/?from_date=20170101&to_date=20170131&response_type=Sale/?page=2",
  "previous": null,
  "results": [
    {
     "crm__address_street": "Hinnavågen 2001",
     "crm__customer_id": "355116",
     "crm__last_updated": "2017-10-13",
     "crm__zip_code": "4707",
     "crm__name": "Ola Nordmann",
     "crm__city": "Vennesla",
     "crm__email": "xxx@hotmail.com",
     "crm__extra__Opprinnelig_lånebeløp_1324": "121911",
     "crm__phone_3": "40218008",
     "crm__phone_2": "97747430",
     "crm__phone_1": "90978457",
     "crm__extra__Resterende_nedbetalingstid_1358": "5,92 år",
     "crm__extra__Lånebeløp_utbetalt_1320": "2017-09-28",
     "client__short_name": "MyClient",
     "client__full_name": "MyClient",
     "assignment__name": "New sales",
     "campaign__name": "Produktsalg 2017",
     "campaign__type": "Sales",
     "response_comment": ""
     "response_subtype": "Ja - Salg",
     "response_submitted_when": "2017-01-01 12:24",
     "response_type": "Sale",
     "response_submitted_by": "someone@callcenter.no"
    },
    ........
]
}
  ```

## Note on data prefixes
As you see from the returned response, there are prefixed fields like crm__xxx and response__xxx.
These refer to different parts of the information. The customer information is from the Cube internal CRM (on Assignment), while the response data. 
The "crm__customer_id" is the imported customer_id field, and NOT the same as the internal "id" field in the [CustomerData API](https://github.com/Headshed/cube-integration/blob/master/CustomerDataAPI.md "CustomerData API")
