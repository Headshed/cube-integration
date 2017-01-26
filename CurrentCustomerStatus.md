We provide an API to retreive the current customer status for assignments, campaigns and individual customers.

To get the customer status for all customers in an assignment:
**GET** ```https://YOURACCOUNT.cube4sales.com/api/v1/assignments/{ASSIGNMENT_ID}/callflow_customers/```

> HTTP Response: 200 OK

` {campaign_id} ` is mandatory as a URL parameter.

### Pagination
As the result may contain many customers, we use Pagination to limit the number of results fetched in one go.
Read more about how the Pagination works [in the Readme](../blob/master/Readme).
The json response returned will have links (next/previous) you can use to navigate the results. These will be ```null```
when there are no more customers to fetch. The default pagination size is 50 (can be changed on request)


### Example response:

```json  
{
  "count": 15516,
  "next": "http://demo.cube4sales.com/api/v1/assignments/239/callflow_customers/?page=2",
  "previous": null,
  "results": [
    {
      "crm__zone_name": "",
      "crm__extra__1142": "550326-8947",
      "crm__address_street": "",
      "crm__customer_id": 1006967,
      "crm__last_updated": "2016-12-14",
      "crm__birth_date": "1955-03-26",
      "crm__address_entrance": "",
      "crm__zip_code": "",
      "callflow__recent_no_answers": "",
      "crm__county": "",
      "callflow__last_change__when": "2016-12-19 07:21",
      "client__short_name": "MyClientName",
      "callflow__zone_name": "",
      "crm__gender": "",
      "callflow__last_change__cause": "Segmentation",
      "crm__last_update_method": "Import update",
      "crm__last_updated_by": "torbjorn@headshed.no",
      "callflow__last_change__user": "torbjorn@headshed.no",
      "crm__name": "Ola Nordmann",
      "callflow__crm_customer_id": 1312869,
      "crm__city": "",
      "crm__municipality": "",
      "crm__email": "",
      "client__full_name": "MyClientName",
      "assignment__name": "Medlemmer",
      "crm__need_to_know": "",
      "campaign__name": "Bekreftelse av medlemsskap uke 51-52",
      "crm__phone_3": "40218008",
      "crm__phone_2": "97747430",
      "crm__phone_1": "90978457",
      "callflow__accumulated_attempts": "",
      "crm__care_of_name": "",
      "campaign__type": "Sales",
      "crm__address_street_no": "",
      "callflow__last_change__comment": "",
      "crm__country": "",
      "callflow__last_change__alternative": "Segmentation",
      "callflow__call_state_code": "To Call"
    },
]
}
  ```

