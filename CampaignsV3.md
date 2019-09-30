## Services related to Campaigns

### Campaigns API

The following request can be used to get information about Campaigns in Cube:

GET
```
https://YOURACCOUNT.headshed.com/api/v1/campaigns?include_inactive_campaigns=True
```
> HTTP Response: 200 OK

The `include_inactive_campaigns `parameter is optional and will be set to False of not included. (i.e. retrieving only active campaigns)

#### Example response:
```json  
{
    {
        "campaign__id": 8,
        "campaign__name": "My Offer with followup Campaign",
        "campaign__start_date": "2017-02-25",
        "campaign__end_date": "",
        "campaign__archived_date": "",
        "campaign__is_active": true,
        "crm_type__id": 3,
        "crm_type__name": "B2C",
        "data_owner__id": 2,
        "data_owner__name": "Demo Client"
    },
    {
        "campaign__id": 9,
        "campaign__name": "Offers B2C (ENG)",
        "campaign__start_date": "2017-03-24",
        "campaign__end_date": "",
        "campaign__archived_date": "",
        "campaign__is_active": true,
        "crm_type__id": 5,
        "crm_type__name": "B2B",
        "data_owner__id": 2,
        "data_owner__name": "Demo Client"
    },
}
  ```


