The following request can be used to get response data from Cube:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/campaigns/{campaign_id}/responses/?from_date={YYYYMMDD}&to_date={YYYYMMDD}&response_type=Sale```

> HTTP Response: 200 OK

` {campaign_id} ` is mandatory as a URL parameter.
` from_date` and ` to_date ` are mandatory query parameters
`response_type` is an optional parameter to filter the result to a specific response type (e.g. Sale, Offer etc.) 

### Pagination
As the result may contain many responses, we use Pagination to limit the number of results fetched in one go.
The json response returned will have links (next/previous) you can use to navigate the results. These will be ```null```
when there are no more customers to fetch. The default pagination size is 50 (can be changed on request)


### Example response:
Request example: https://xxx.headshed.com/api/v1/campaigns/926/responses/?from_date=20170101&to_date=20170131&response_type=Sale

```json  
{
  "count": 207,
  "next": "https://xxx.headshed.com/api/v1/campaigns/926/responses/?from_date=20170101&to_date=20170131&response_type=Sale/?page=2",
  "previous": null,
  "results": [
    {
      "submitted_by": "someone@callcenter.no",
      "submitted_when": "2017-01-01T13:55:20.257789Z",
      "crm_customer_id": 1286928,
      "customer_name": "CUSTOMER NAME",
      "campaign_id": 926,
      "type": "Sale",
      "subtype": "Betaler tilsendt faktura",
      "comment": "",
      "external_customer_id": 971352
    },
    {
      "submitted_by": "someone@callcenter.no",
      "submitted_when": "2017-01-01T13:53:16.450388Z",
      "crm_customer_id": 1286937,
      "customer_name": "ANOTHER CUSTOMER NAME",
      "campaign_id": 926,
      "type": "Sale",
      "subtype": "Betaler tilsendt faktura",
      "comment": "",
      "external_customer_id": 971353
    }
 
]
}
  ```

## Note on customer_id's
As you see from the response, there are two id fields: A "crm_customer_id" and a "external_customer_id".
The "crm_customer_id" is the internal/unique id for the customer record in Cube. 
The "exteral_customer_id" is the id set by the external system on import. This field is optional in Headshed Cube (depending on assignment configuration), but may be what you need to link the response record to a customer in your system.

The "crm_customer_id" refers to the "id" field in the [CustomerData API](https://github.com/Headshed/cube-integration/blob/master/CustomerDataAPI.md "Go to CustomerData API")
