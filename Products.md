## Get all product registrations for a specific CRM

The following request can be used to get all call outcomes registered in a CRM in Cube:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/data_owners/{data_owner_id}/crm/{crm_type}/product_registrations/?from_date={YYYYMMDD}&to_date={YYYYMMDD}```

> HTTP Response: 200 OK

` {data_owner_id} ` is mandatory as a URL integer parameter. 
` {crm_type} ` is mandatory as a URL parameter. The crm type could be B2C or B2B.
` from_date` and ` to_date ` are optional query parameters. Will return data from "today" one of them are not specified.


### Example response:
Request example: https://xxx.headshed.com/api/v1/data_owners/2/crm/B2C/product_registrations/?from_date=20180102&to_date=20200102

```json  
{
    "count": 781,
    "next":   "https://xxxx.headshed.com/api/v1/data_owners/2/crm/B2C/call_outcomes/?from_date=20200212&to_date=20200212,
    "previous": null,
    "results": [
                {
            "crm__customer_id": "22120292930",
            "crm__standard_info__name": "Elias Olsen",
            "crm__standard_info__phone_1": "90978457",
            "crm__standard_info__phone_2": "97747430",
            "crm__standard_info__phone_3": "40218008",
            "crm__standard_info__email": "EliasOlsen@dayrep.com",
            "crm__change_log__updated": "2017-12-07",
            "crm__change_log__updated_by": "anders@headshed.com",
            "crm__change_log__update_method": "Import new",
            "crm__custom_info__64": "Kleivane 70",
            "crm__custom_info__221": "",
            "crm__custom_info__62": 36,
            "crm__custom_info__61": "1981-08-13",
            "crm__custom_info__34": "A+",
            "crm__custom_info__39": "",
            "crm__custom_info__66": "STORD",
            "crm__custom_info__67": "Kleivane 70, 5416 STORD",
            "crm__custom_info__63": "male",
            "crm__custom_info__68": "Ordnance handling expert at Today's Man",
            "crm__custom_info__65": "5416",
            "product__code": "MPC",
            "product__title": "My Product C",
            "product__price": 599,
            "product__extra__Example checkbox": "False",
            "product__extra__Example date": "",
            "product__extra__Example dropdown alternatives": "",
            "call_outcome__comment": "",
            "call_outcome__report_as__submitted_by": "lene@headshed.com",
            "call_outcome__report_as__submitted_in_department": "Default",
            "call_outcome__type": "Booked",
            "call_outcome__subtype": "Book",
            "call_outcome__report_as__submitted_when": "2018-11-27 09:24",
            "call_outcome__extra__Innhentet samtykke for TM": "",
            "call_outcome__extra__Leveransedato": "",
            "call_outcome__extra__Lol": "",
            "call_outcome__extra__Kunnskap": "",
            "call_outcome__additional_input_text": "Followup time: Between 28.11.2018 08:00 and 28.11.2018 21:00 \nMeeting: 28-11-2018 10:00 - 12:00 with lene@headshed.com  \n",
            "campaign__name": "My Booking Campaign",
            "campaign__crm_type": "B2C",
            "data_owner__name": "Demo Client",
            "segment__name": "Default segment"
        },
    ........
]
}
  ```
  
  
  ## Get all product registrations for a campaign

The following request can be used to get all call outcomes registered in a CRM in Cube:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/campaigns/{campaign_id}/product_registrations/?from_date={YYYYMMDD}&to_date={YYYYMMDD}```

> HTTP Response: 200 OK

` {campaign_id} ` is mandatory as a URL integer parameter. 
` from_date` and ` to_date ` are optional query parameters. Will return data from "today" one of them are not specified.


### Example response:
Request example: https://xxx.headshed.com/api/v1/campaigns/20/product_registrations/?from_date=20180102&to_date=20200102

```json  
{
    "count": 781,
    "next":   "https://xxxx.headshed.com/api/v1/data_owners/2/crm/B2C/call_outcomes/?from_date=20200212&to_date=20200212,
    "previous": null,
    "results": [
        {
            "crm__customer_id": "",
            "crm__standard_info__name": "Anonymized",
            "crm__standard_info__phone_1": "",
            "crm__standard_info__phone_2": "",
            "crm__standard_info__phone_3": "",
            "crm__standard_info__email": "",
            "crm__change_log__updated": "",
            "crm__change_log__updated_by": "",
            "crm__change_log__update_method": "",
            "crm__custom_info__64": "",
            "crm__custom_info__221": "",
            "crm__custom_info__62": "",
            "product__code": "ProdC",
            "product__title": "Product C",
            "product__price": 399,
            "call_outcome__comment": "",
            "call_outcome__report_as__submitted_by": "torbjorn+2@headshed.com",
            "call_outcome__report_as__submitted_in_department": "Default",
            "call_outcome__type": "Sale",
            "call_outcome__subtype": "Written confirmation received",
            "call_outcome__report_as__submitted_when": "2018-01-29 23:04",
            "call_outcome__additional_input_text": "",
            "campaign__name": "My Demo Campaign",
            "campaign__crm_type": "B2C",
            "data_owner__name": "Demo Client",
            "segment__name": "Default segment"
        },
    ........
]
}
  ```