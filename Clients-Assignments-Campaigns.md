##Services related to Clients, Assignments and Campaigns

### Campaigns API
#### Internal users
The following request can be used by internal users to get information about all Campaigns in Cube:

GET
```
https://YOURACCOUNT.headshed.com/api/v1/campaigns
```
> HTTP Response: 200 OK

#### External users
Users with granted access to specific client information (we call them External users) can use the following API request to get information about available Campaigns in Cube:

GET
```
https://AGENTACCOUNT.headshed.com/api/v1/client_access/campaigns
```
> HTTP Response: 200 OK

#### Example response:
```json  
[
    {
        "campaign__id": 1,
        "campaign__name": "My first campaign",
        "campaign__description": "",
        "campaign__start_date": "2018-10-31",
        "campaign__end_date": "2019-11-14",
        "campaign__archived_date": "",
        "campaign__is_active": true,
        "assignment__id": 1,
        "assignment__name": "My Assignment number one",
        "assignment__description": "Main assignment to use",
        "client__id": 1,
        "client__short_name": "My best Client",
        "client__full_name": "A very good client"
    },
    {
        "campaign__id": 2,
        "campaign__name": "My second campaign",
        "campaign__description": "",
        "campaign__start_date": "2016-10-31",
        "campaign__end_date": "2016-11-14",
        "campaign__archived_date": "",
        "campaign__is_active": false,
        "assignment__id": 1,
        "assignment__name": "My Assignment number one",
        "assignment__description": "Main assignment to use",
        "client__id": 1,
        "client__short_name": "My best Client",
        "client__full_name": "A very good client"
    }
]
  ```
