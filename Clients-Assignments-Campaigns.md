##Services related to Clients, Assignments and Campaigns(NOT YET IMPLEMENTED)

### Campaigns API

The following request can be used to get information about Campaigns in Cube:

GET
```
https://YOURACCOUNT.headshed.com/campaigns?include_inactive_campaigns=True
```
> HTTP Response: 200 OK

The `include_inactive_campaigns `parameter is optional and will be set to False of not included. (i.e. retrieving only active campaigns)

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

### Assignments API
The following request can be used to get information about Assignments in Cube:

GET
```
https://YOURACCOUNT.headshed.com/assignments
```
> HTTP Response: 200 OK

#### Example response:
```json  
{
    {   "assignment_id": 32,
        "assignment_name": "My Assignment number one",
        "client_id": 42,
        "client_name": "My best Client",
    }
    {   "assignment_id": 33,
        "assignment_name": "My Assignment number two",
        "client_id": 42,
        "client_name": "My best Client",
    }
    {   "assignment_id": 72,
        "assignment_name": "My Special Assignment",
        "client_id": 44,
        "client_name": "My second best Client",
    }    
}
```
