## Customer data API
The following request can be used to get Customer data from Cube:
GET
```
https://YOURACCOUNT.cube4sales.com/crm/customers?assignment_id={ID}
```
> HTTP Response: 200 OK

## Example
In this example, we have asked for all Customer records in assignment #9. What type of assignment this is can be seen in Cube. (TODO. Add REST API for listing Assignments)
Assignment #9 in this example have been configured as a B2B-assignment (Customer records are companies), and 6 assignment specific extra information fields have been configured:
(Add image to show configuration)
In the customer record shown below, only 3 if the assignment specific fields have data registered, and hence only these are displayed/included.
For other customer data, all fields are shown (with `null` values when no data is registered)

### Example response:

```json  
{
    "customer_id": 2488539,
    "name": "Lastname, Firstname",
    "gender": null,
    "birth_date": null,
    "assignment_id": 9,
    "care_of_name": null,
    "address_street": null,
    "address_street_no": null,
    "address_entrance": null,
    "zip_code": null,
    "city": "ELVERUM",
    "municipality": null,
    "county": "Hedmark",
    "country": null,
    "phone_1": "99999999",
    "phone_2": null,
    "phone_3": null,
    "email": null,
    "more_info_fields": {},
    "updated": "2016-04-07",
    "updated_by": "magnus@headshed.no",
    "update_method": "Import new",
    "org_number": "989898981",
    "org_number_main": "999911111",
    "org_name": "Company AS",
    "nace_code": null,
    "nace_text": "Utgivelse av blader og tidsskrifter",
    "number_of_employees": "6",
    "company_type": null,
    "established": null,
    "credit_rating": null,
    "need_to_know": null,
    "url": null,
    "company_email": "company@domain.no",
    "revenue": null,
    "po_box": null,
    "postal_address": null,
    "postal_zip": null,
    "postal_city": null,
    "Klassifisering": "C",
    "Landsforening": "XYZ",
    "Region": "Innlandet",
    "Hoved": "Ja"
  },
  ```
