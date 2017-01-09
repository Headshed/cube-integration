The following request can be used to get response data from Cube:

**GET** ```https://YOURACCOUNT.cube4sales.com/api/v1/campaigns/{campaign_id}/responses/?from_date={YYYYMMDD}&to_date={YYYYMMDD}```

> HTTP Response: 200 OK

` {campaign_id} ` is mandatory as a URL parameter.
Both ` from_date` and ` to_date ` are optional query parameters (will use TODAY as default)

### Pagination
As the result may contain many responses, we use Pagination to limit the number of results fetched in one go.
The json response returned will have links (next/previous) you can use to navigate the results. These will be ```null```
when there are no more customers to fetch. The default pagination size is 50 (can be changed on request)


### Example response:

```json  
{
  "count": 207,
  "next": "http://XXX.cube4sales.com/api/v1/campaigns/926/responses?from_date=20160924/?page=2",
  "previous": null,
  "results": [
    {
      "submitted_by": "someone@callcenter.no",
      "submitted_when": "2016-12-02T13:55:20.257789Z",
      "crm_customer_id": 1286928,
      "customer_name": "CUSTOMER NAME",
      "campaign_id": 926,
      "type": "Completed - No",
      "subtype": "Ville ikke kontaktes",
      "comment": "",
      "external_customer_id": 971352
    },
    {
      "submitted_by": "someone@callcenter.no",
      "submitted_when": "2016-12-02T13:53:16.450388Z",
      "crm_customer_id": 1286937,
      "customer_name": "ANOTHER CUSTOMER NAME",
      "campaign_id": 926,
      "type": "Completed - Yes",
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

The "crm_customer_id" refers to the "id" field in the [CustomerData API] (https://github.com/Headshed/cube-integration/blob/master/CustomerDataAPI.md "Go to CustomerData API")
