##Services related to Clients, Assignments and Campaigns

### Campaigns API
#### Internal users
The following request can be used by internal users to get information about all Campaigns in Cube:

GET
```
https://YOURACCOUNT.headshed.com/campaigns
```
> HTTP Response: 200 OK

#### External users
Users with granted access to specific client information (we call them External users) can use the following API request to get information about available Campaigns in Cube:

GET
```
https://AGENTACCOUNT.headshed.com/client_access/campaigns
```
> HTTP Response: 200 OK

#### Example response:
```json  
{
    {   "campaign_id": 1,
        "campaign_name": "My First Campaign",
        "start_date": "2016-04-07",
        "end_date": "",
        "assignment_id": 32,
        "assignment_name": "My Assignment number one",
        "client_id": 42,
        "client_name": "My best Client",
    }
    {   "campaign_id": 2,
        "campaign_name": "My Second Campaign",
        "start_date": "2016-05-07",
        "end_date": "2016-12-24",
        "assignment_id": 32,
        "assignment_name": "My Assignment number one",
        "client_id": 42,
        "client_name": "My best Client",
    }
}
  ```
