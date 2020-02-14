##Current Customer Status

We provide an API to retreive the current customer status for CRM, Campaigns and individual customers.

###Current customer Status in CRM

To get the customer status for all customers in a CRM:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/data_owners/{DATA_OWNER_ID}/crm/{CRM_TYPE}/callflow_customers/```

> HTTP Response: 200 OK

`{DATA_OWNER_ID}` is an integer representing the id of the data owner you want to access.

`{CRM_TYPE}` is a string representing the name of the crm type you want to access (Available: B2B or B2C).


###Current Customer Status in Campaign

To get the customer status for all customers in a campaign:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/campaigns/{CAMPAIGN_ID}/callflow_customers/?call_state={CALL_STATE_CODE}/```

> HTTP Response: 200 OK

` {CAMPAIGN_ID} ` is an integer representing the id of the campaign you want to access.
` call_state ` is an optional string you could use, if you only want status of customer with a specific call_state.


### Example response:

```json  
{
    "count": 2925,
    "next": "https://xxx.headshed.com/api/v1/data_owners/2/crm/B2B/callflow_customers/?page=2",
    "previous": null,
    "results": [
        {
            "crm__customer_id": "1245659854",
            "crm__standard_info__name": "Kari Olsen",
            "crm__standard_info__phone_1": "+4795499097",
            "crm__standard_info__phone_2": "+4797747430",
            "crm__standard_info__phone_3": "",
            "crm__standard_info__email": "kari.olsen@hotmail.com",
            "crm__change_log__updated": "2020-02-12",
            "crm__change_log__updated_by": "lene@headshed.com",
            "crm__change_log__update_method": "Manual update",
            "crm__custom_info__64": "",
            "crm__custom_info__221": "Nordre Berggate 2",
            "crm__custom_info__62": "",
            "crm__custom_info__20": "Aktiv",
            "crm__custom_info__220": 22,
            "crm__custom_info__21": "Hund",
            "crm__custom_info__26": "",
            "crm__custom_info__224": "Leilighet",
            "crm__custom_info__33": "A",
            "crm__custom_info__69": "",
            "crm__custom_info__68": "",
            "crm__custom_info__223": "7035",
            "crm__custom_info__222": "Trondheim",
            "crm__custom_info__15": "",
            "crm__custom_info__65": "",
            "crm__custom_info__72": "",
            "callflow__attempts_status__attempts": 9,
            "callflow__callstate__name": "Ready",
            "callflow__last_change__user": "lene@headshed.com",
            "callflow__last_change__when": "2020-02-12 10:25",
            "callflow__last_change__cause": "Manually add",
            "callflow__last_change__alternative": "",
            "callflow__last_change__comment": "",
            "campaign__name": "Vinter 2020",
            "campaign__crm_type": "B2C",
            "data_owner__name": "Demo Client",
            "segment__name": "Default segment",
            "product__ProdB": ""
        },
]
}
  ```
