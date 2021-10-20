## List all campaigns in Cube

The following request can be used to get information about all Campaigns in Cube:

GET
```
https://YOURACCOUNT.headshed.com/api/v1/campaigns
```
> HTTP Response: 200 OK


### Example response:
```json  
[
    {
        "campaign__id": 1,
        "campaign__name": "My first campaign",
        "campaign__start_date": "2018-02-14",
        "campaign__end_date": "",
        "campaign__archived_date": "2020-01-30",
        "campaign__is_active": "",
        "campaign__crm_type": "B2C",
        "data_owner__id": 1,
        "data_owner__name": "Client"
    },
    {
        "campaign__id": 2,
        "campaign__name": "My second campaign",
        "campaign__start_date": "2018-02-14",
        "campaign__end_date": "2018-03-13",
        "campaign__archived_date": "",
        "campaign__is_active": true,
        "campaign__crm_type": "B2C",
        "data_owner__id": 1,
        "data_owner__name": "Client"
    }
]
  ```
