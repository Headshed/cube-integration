## Get all call outcomes for a specific CRM

The following request can be used to get all call outcomes registered in a CRM in Cube:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/data_owners/{data_owner_id}/crm/{crm_type}/call_outcomes/?from_date={YYYYMMDD}&to_date={YYYYMMDD}```

> HTTP Response: 200 OK

` {data_owner_id} ` is mandatory as a URL parameter. 
` {crm_type} ` is mandatory as a URL parameter. The crm type could be B2C or B2B.
` from_date` and ` to_date ` are optional query parameters. Will return data from "today" one of them are not specified.


### Example response:
Request example: https://xxx.headshed.com/api/v1/data_owners/2/crm/B2C/call_outcomes/?from_date=20200212&to_date=20200212

```json  
{
    "count": 781,
    "next":   "https://xxxx.headshed.com/api/v1/data_owners/2/crm/B2C/call_outcomes/?from_date=20200212&to_date=20200212,
    "previous": null,
    "results": [
        {
            "crm__customer_id": "1231316464",
            "crm__standard_info__name": "Adam Svennestad",
            "crm__standard_info__phone_1": "004795499097",
            "crm__standard_info__phone_2": "90978457",
            "crm__standard_info__phone_3": "41042165",
            "crm__standard_info__email": "adam@hotmail.com",
            "crm__change_log__updated": "2020-02-12",
            "crm__change_log__updated_by": "lene@headshed.com",
            "crm__change_log__update_method": "Manual update",
            "crm__custom_info__1": "Bekkelia 50 C",
            "crm__custom_info__20": "Aktiv",
            "crm__custom_info__220": 56,
            "crm__custom_info__21": "Hund",
            "crm__custom_info__224": "Enebolig",
            "crm__custom_info__223": "0235",
            "crm__custom_info__222": "Oslo",
            "call_outcome__comment": "Please call this customer, and say hello from Lene!",
            "call_outcome__report_as__submitted_by": "lene@headshed.com",
            "call_outcome__report_as__submitted_in_department": "TestingSS",
            "call_outcome__type": "Call back later",
            "call_outcome__subtype": "Call back later",
            "call_outcome__report_as__submitted_when": "2020-02-12 10:27",
            "call_outcome__additional_input_text": "",
            "campaign__name": "Vinter 2020",
            "campaign__crm_type": "B2C",
            "data_owner__name": "Demo Client",
            "segment__name": "Default segment"
        },
    ........
]
}
  ```
  

## Get all call outcomes in a Campaign

The following request can be used to get all call outcomes registered in a Campaign in Cube:

**GET** ```https://YOURACCOUNT.headshed.com/api/v1/campaigns/{campaign_id}/call_outcomes/?from_date={YYYYMMDD}&to_date={YYYYMMDD}```

> HTTP Response: 200 OK

` {campaign_id} ` is mandatory as a URL parameter.
` from_date` and ` to_date ` are optional query parameters. Will return data from "today" one of them are not specified.


### Example response:
Request example: https://xxx.headshed.com/api/v1/campaigns/140/call_outcomes/?from_date=20200212&to_date=20200212

```json  
{
    "count": 781,
    "next":   "https://xxxx.headshed.com/api/v1/campaigns/140/call_outcomes/?from_date=20200212&to_date=20200212,
    "previous": null,
    "results": [
        {
            "crm__customer_id": "1231316464",
            "crm__standard_info__name": "Adam Svennestad",
            "crm__standard_info__phone_1": "004795499097",
            "crm__standard_info__phone_2": "90978457",
            "crm__standard_info__phone_3": "41042165",
            "crm__standard_info__email": "adam@hotmail.com",
            "crm__change_log__updated": "2020-02-12",
            "crm__change_log__updated_by": "lene@headshed.com",
            "crm__change_log__update_method": "Manual update",
            "crm__custom_info__1": "Bekkelia 50 C",
            "crm__custom_info__20": "Aktiv",
            "crm__custom_info__220": 56,
            "crm__custom_info__21": "Hund",
            "crm__custom_info__224": "Enebolig",
            "crm__custom_info__223": "0235",
            "crm__custom_info__222": "Oslo",
            "call_outcome__comment": "Please call this customer, and say hello from Lene!",
            "call_outcome__report_as__submitted_by": "lene@headshed.com",
            "call_outcome__report_as__submitted_in_department": "TestingSS",
            "call_outcome__type": "Call back later",
            "call_outcome__subtype": "Call back later",
            "call_outcome__report_as__submitted_when": "2020-02-12 10:27",
            "call_outcome__additional_input_text": "",
            "campaign__name": "Vinter 2020",
            "campaign__crm_type": "B2C",
            "data_owner__name": "Demo Client",
            "segment__name": "Default segment"
        },
    ........
]
}
  ```
  

## Note on data prefixes
As you see from the returned response, there are prefixed fields like crm xxx and call_outcome__xxx.
These refer to different parts of the information model. The customer information is from the Cube CRM, while the call outcome data is related to the current campaign. 
[CRMCustomerData](https://github.com/Headshed/cube-integration/blob/master/CRMCustomerData.md "CustomerData API")

## Lookup for crm custom info fields
The crm custom fields are custom fields defined on the CRM of your selected Data Owner.
If you need to know the label/name of this field, you can look it up in the [CustomerCustomFields](https://github.com/Headshed/cube-integration/blob/master/CustomerCustomFields.md "Customer Custom Fields")
