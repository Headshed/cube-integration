We provide an API to retreive the current customer status for assignments, campaigns and individual customers.

To get the customer status for all customers in an assignment:
**GET** ```https://YOURACCOUNT.headshed.com/api/v1/assignments/{ASSIGNMENT_ID}/callflow_customers/```

> HTTP Response: 200 OK

` {ASSIGNMENT_ID} ` is an integer representing the id of the assignment you want to access.

To get the customer status for all customers in a campaign:
**GET** ```https://YOURACCOUNT.headshed.com/api/v1/campaigns/{CAMPAIGN_ID}/callflow_customers/```

> HTTP Response: 200 OK

` {CAMPAIGN_ID} ` is an integer representing the id of the campaign you want to access.


To get the customer status for all customers in a campaign with a speific call state:
**GET** ```https://YOURACCOUNT.headshed.com/api/v1/campaigns/{CAMPAIGN_ID}/callflow_customers/?call_state={CALL_STATE_CODE}/```

> HTTP Response: 200 OK

` {CAMPAIGN_ID} ` is an integer representing the id of the campaign you want to access.
` {CALL_STATE_CODE} ` parameter is a string with the specific call_state you would like to filter on. The call_state is defined on your Campaigns.

Example: ```https://YOURACCOUNT.headshed.com/api/v1/campaigns/998/callflow_customers/?call_state=Completed - Yes```


### Pagination
As the result may contain many customers, we use Pagination to limit the number of results fetched in one go.
Read more about how our Pagination works [in the Readme](README.md).

### Example response:

```json  
{
  "count": 15516,
  "next": "http://demo.headshed.com/api/v1/assignments/239/callflow_customers/?page=2",
  "previous": null,
  "results": [
    {
            "crm__customer_id": "481846",
            "crm__standard_info__name": "STIORI BJØRR",
            "crm__standard_info__phone_1": "",
            "crm__standard_info__phone_2": "11223344",
            "crm__standard_info__phone_3": "",
            "crm__standard_info__email": "ingen@epost.com",
            "crm__change_log__updated": "2016-02-22",
            "crm__change_log__updated_by": "admin",
            "crm__change_log__update_method": "import new",
            "crm__custom_info__1": "",
            "crm__custom_info__87": "",
            "crm__custom_info__78": "PRESTEVN",
            "crm__custom_info__79": 375,
            "crm__custom_info__76": 38,
            "crm__custom_info__75": "1979-09-27",
            "crm__custom_info__81": "INGENMANNSLAND",
            "crm__custom_info__50": "",
            "crm__custom_info__74": "923609016",
            "crm__custom_info__73": "STIORI BJØRR",
            "crm__custom_info__84": "LAND",
            "crm__custom_info__83": "FYLKE",
            "crm__custom_info__85": "PRESTEVN 375, 5555 INGENMANNSLAND FYLKE, KOMMUNE, LAND",
            "crm__custom_info__7": "2013-06-04",
            "crm__custom_info__8": "2012-06-15",
            "crm__custom_info__86": "",
            "crm__custom_info__2": "Alder: 52 år",
            "crm__custom_info__3": "BT",
            "crm__custom_info__4": "",
            "crm__custom_info__5": "4.0",
            "crm__custom_info__6": "Passive_210915_update",
            "crm__custom_info__82": "KOMMUNE",
            "crm__custom_info__77": "Stoppet 2013-06-04, termin 4",
            "crm__custom_info__10": "",
            "crm__custom_info__80": "5555",
            "crm__custom_info__88": "",
            "callflow__attempts_status__attempts": "",
            "callflow__callstate__name": "Ready",
            "callflow__last_change__user": "manual",
            "callflow__last_change__when": "2016-11-07 10:38",
            "callflow__last_change__cause": "Segmentation",
            "callflow__last_change__alternative": "Segmentation",
            "callflow__last_change__comment": "",
            "campaign__name": "Bookingkampanje - TEST",
            "assignment__name": "Assignment",
            "client__short_name": "Client",
            "meeting__agent": "",
            "meeting__time__from_date_time": "",
            "meeting__time__to_date_time": "",
            "product__PROD1": "",
            "product__PROD2": "",
            "product__p": ""
    },
]
}
  ```

## Lookup for crm__custom_info__xx fields
The crm__custom_info__1 and crm__custom_info__87 fields in this example are custom fields defined on the crm model for the assignment.
If you need to know the label/name of this field, you can look it up in the [CustomerCustomFields](https://github.com/Headshed/cube-integration/blob/master/CustomerCustomFields.md "Customer Custom Fields")
