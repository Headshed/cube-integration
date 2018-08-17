##Services related to Clients, Assignments and Campaigns

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
[
    {
        "campaign__id": 1,
        "campaign__type": "Booking",
        "campaign__name": "My first campaign",
        "campaign__description": "This is how I describe this campaign",
        "campaign__start_date": "2016-10-31",
        "campaign__end_date": "2016-11-14",
        "campaign__archived_date": "",
        "assignment__id": 1,
        "assignment__name": "Test assignment",
        "assignment__description": "This assignment is used for testing",
        "client__id": 1,
        "client__short_name": "Test client",
        "client__full_name": "This client is used for testing"
    },
    {
        "campaign__id": 2,
        "campaign__type": "Sales",
        "campaign__name": "My sales campaign",
        "campaign__description": "A campaign for selling things",
        "campaign__start_date": "2016-02-20",
        "campaign__end_date": "2017-03-23",
        "campaign__archived_date": "",
        "assignment__id": 1,
        "assignment__name": "Test assignment",
        "assignment__description": "This assignment is used for testing",
        "client__id": 1,
        "client__short_name": "Test client",
        "client__full_name": "This client is used for testing"
    }
    ]
  ```

### Assignments API (NOT YET IMPLEMENTED)
The following request can be used to get information about Assignments in Cube:

GET
```
https://YOURACCOUNT.headshed.com/assignments
```
> HTTP Response: 200 OK

#### Example response:
```json  
{
    {   "assignment__id": 32,
        "assignment__name": "My Assignment number one",
        "client__id": 42,
        "client__short_name": "My best Client",
    }
    {   "assignment__id": 33,
        "assignment__name": "My Assignment number two",
        "client__id": 42,
        "client__short_name": "My best Client",
    }
    {   "assignment__id": 72,
        "assignment__name": "My Special Assignment",
        "client__id": 44,
        "client__short_name": "My second best Client",
    }    
}
```
