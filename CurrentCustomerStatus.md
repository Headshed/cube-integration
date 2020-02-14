We provide an API to retreive the current customer status for campaigns and individual customers.

To get the customer status for all customers in a data owner:
**GET** ```https://YOURACCOUNT.headshed.com/api/v1/data_owners/{DATA_OWNER_ID}/crm/{CRM_TYPE}/callflow_customers/```

> HTTP Response: 200 OK

` {DATA_OWNER_ID} ` is an integer representing the id of the data owner you want to access.

` {CRM_TYPE} ` is a string representing the name of the crm type you want to access (Available: B2B or B2C).

To get the customer status for all customers in a campaign:
**GET** ```https://YOURACCOUNT.headshed.com/api/v1/campaigns/{CAMPAIGN_ID}/callflow_customers/```

> HTTP Response: 200 OK

` {CAMPAIGN_ID} ` is an integer representing the id of the campaign you want to access.


To get the customer status for all customers in a campaign with a speific call state:
**GET** ```https://YOURACCOUNT.headshed.com/api/v1/campaigns/{CAMPAIGN_ID}/callflow_customers/?call_state={CALL_STATE_CODE}/```

> HTTP Response: 200 OK

` {CAMPAIGN_ID} ` is an integer representing the id of the campaign you want to access.
` {CALL_STATE_CODE} ` parameter is a string with the specific call_state you would like to filter on.


Example: ```https://YOURACCOUNT.headshed.com/api/v1/campaigns/998/callflow_customers/?call_state=Sale```


### Pagination
As the result may contain many customers, we use Pagination to limit the number of results fetched in one go.
Read more about how our Pagination works [in the Readme](README.md).

### Example response:

```json  
{
    "count": 2925,
    "next": "https://demotest.headshed.com/api/v1/data_owners/2/crm/B2B/callflow_customers/?page=2",
    "previous": null,
    "results": [
        {
            "crm__customer_id": "833819",
            "crm__standard_info__name": "Headshed AS",
            "crm__standard_info__phone_1": "90978457",
            "crm__standard_info__phone_2": "97747430",
            "crm__standard_info__phone_3": "40218008",
            "crm__standard_info__email": "mail@headshed.no",
            "crm__change_log__updated": "2017-06-14",
            "crm__change_log__updated_by": "demo@headshed.no",
            "crm__change_log__update_method": "Import new",
            "crm__custom_info__104": "Dyrmyrgata 35",
            "crm__custom_info__22": "Kongsberg",
            "crm__custom_info__24": "Produksjon av komponenter",
            "crm__custom_info__106": "OSLO",
            "crm__custom_info__38": "",
            "crm__custom_info__42": "AS",
            "crm__custom_info__49": "",
            "crm__custom_info__43": "mail@headshed.no",
            "crm__custom_info__48": "",
            "crm__custom_info__40": "26110",
            "crm__custom_info__41": "Produksjon av komponenter",
            "crm__custom_info__111": "",
            "crm__custom_info__47": "",
            "crm__custom_info__103": "992513624",
            "crm__custom_info__44": "Bakkegate 35",
            "crm__custom_info__46": "OSLO",
            "crm__custom_info__45": "3611",
            "crm__custom_info__113": "",
            "crm__custom_info__110": "",
            "crm__custom_info__114": "",
            "crm__custom_info__108": "Bakkegate 35, 3611 OSLO, Oslo",
            "crm__custom_info__112": "",
            "crm__custom_info__23": "A",
            "crm__custom_info__107": "Oslo",
            "crm__custom_info__109": "Ola Hansen",
            "crm__custom_info__25": "AS",
            "crm__custom_info__105": "3611",
            "callflow__attempts_status__attempts": "",
            "callflow__callstate__name": "Ready",
            "callflow__last_change__user": "manual",
            "callflow__last_change__when": "2017-09-13 09:24",
            "callflow__last_change__cause": "Make To Call",
            "callflow__last_change__alternative": "Make To Call",
            "callflow__last_change__comment": "",
            "campaign__name": "Tilbud - salg - oppfølging",
            "assignment__name": "B2B",
            "data_owner__name": "Demo Client",
            "segment__name": "Default segment",
            "meeting__agent": "",
            "meeting__time__from_date_time": "",
            "meeting__time__to_date_time": "",
            "product__MPC": "",
            "product__MPA": "",
            "product__T1": "",
            "product__STR1": ""
        },
]
}
  ```
