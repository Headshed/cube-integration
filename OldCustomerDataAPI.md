## Customer data API - Retrieving updated customer data.
The following request can be used to get Customer data from Cube:
GET
```
https://YOURACCOUNT.headshed.com/api/v1/assignments/{assignment_id}/customers/
```
> HTTP Response: 200 OK

## Example
In this example, we have asked for all Customer records in assignment #1. What type of assignment this is can be seen in the Cube GUI. (We will add API support for listing assignment information).

Example: ```https://YOURACCOUNT.headshed.com/api/v1/assignments/1/customers/```


### Pagination
As the result may contain many customers, we use Pagination to limit the number of results fetched in one go.
Read more about how our Pagination works [in the Readme](README.md).

### Example response:

```json  
{
    "count": 2676,
    "next": "https://demotest.headshed.com/api/v1/assignments/1/customers/?page=2",
    "previous": null,
    "results": [
        {
            "crm__customer_id": "481846",
            "crm__standard_info__name": "NAVN NAVNESEN",
            "crm__standard_info__phone_1": "55667788",
            "crm__standard_info__phone_2": "1122344",
            "crm__standard_info__phone_3": "99887766",
            "crm__standard_info__email": "ingen@epost.com",
            "crm__custom_info__1": "storfamilie",
            "crm__custom_info__2": "5",
            "crm__custom_info__3": "Hund"
        },
        {
            "crm__customer_id": "481847",
            "crm__standard_info__name": "Ola Nordmann",
            "crm__standard_info__phone_1": "55667788",
            "crm__standard_info__phone_2": "1122344",
            "crm__standard_info__phone_3": "99887766",
            "crm__standard_info__email": "ola@epost.com",
            "crm__custom_info__1": "enslig",
            "crm__custom_info__2": "1",
            "crm__custom_info__3": ""
        }  
   }
  ```
## Lookup for crm__custom_info__xx fields
The crm__custom_info__1 and crm__custom_info__87 fields in this example are custom fields defined on the crm model for the assignment.
If you need to know the label/name of this field, you can look it up in the [CustomerCustomFields](https://github.com/Headshed/cube-integration/blob/master/CustomerCustomFields.md "Customer Custom Fields")
