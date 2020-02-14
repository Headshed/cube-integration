## Get sms data in CRM

The following request can be used to get sms data from Cube for a CRM:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/data_owners/{data_owner_id}/{crm_type}/sms/?from_date={YYYYMMDD}&to_date={YYYYMMDD}```

> HTTP Response: 200 OK

` {data_owner_id} ` is mandatory as a URL parameter. 
` {crm_type} ` is mandatory as a URL parameter. The crm type could be B2C or B2B.
` from_date` and ` to_date ` are optional query parameters. Will return data from "today" one of them are not specified.

## Get sms data in campaign

The following request can be used to get sms data from Cube for a campaign:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/campaigns/{campaign_id}/sms/?from_date={YYYYMMDD}&to_date={YYYYMMDD}```

> HTTP Response: 200 OK

`{campaign_id}` is a mandatory URL parameter.
` from_date` and ` to_date ` are optional query parameters. The request will return data from "today" if not both date parameters are specified.


### Example response:
Request example: https://xxx.headshed.com/api/v1/campaigns/15/sms/?from_date=20170101&to_date=20180401

```json  
{
  "count": 99,
  "next": "https://xxx.headshed.com/api/v1/campaigns/15/sms/?from_date=20170101&to_date=20180401/?page=2",
  "previous": null,
  "results": [
    {
            "crm__customer_id": "05029249275",
            "crm__name": "Lene Andersen",
            "crm__birth_date": "1992-02-05",
            "crm__gender": "Femail",
            "crm__need_to_know": "Kunde vil ha tilbud på forsikring",
            "crm__zone_name": "",
            "crm__address_street": "Osloveien",
            "crm__address_street_no": "3",
            "crm__address_entrance": "",
            "crm__zip_code": "0232",
            "crm__city": "Oslo",
            "crm__municipality": "",
            "crm__county": "",
            "crm__country": "",
            "crm__phone_1": "95499097",
            "crm__phone_2": "63952795",
            "crm__phone_3": "",
            "crm__email": "",
            "crm__last_updated": "2018-03-21",
            "crm__last_updated_by": "lene@headshed.no",
            "crm__last_update_method": "Import update",
            "crm__pseudonymized": "",
            "crm__extra__active_products_937": "Innbo",
            "crm__extra__Care_of_name_1816": "",
            "sms_submitted_by": "Auto",
            "sms_submitted_when": "2018-03-23 19:38",
            "sms_crm_customer_id": 1363063,
            "sms_customer_name": "Lene Andersen",
            "sms_campaign_id": 15,
            "sms_type": "Received SMS message",
            "sms_subtype": "Received SMS message",
            "sms_relevant_for_reporting": true,
            "sms_response_id": "",
            "sms_customer_number": "95499097",
            "sms_assignment_number": "3215647895",
            "sms_message": "Ok",
            "campaign__type": "Offer",
            "campaign__name": "Innboforsikring - Høst",
            "assignment__name": "Forsikringskunder",
            "client__short_name": "Selskap",
            "client__full_name": "Selskap"
        },
]
}
  ```
  




