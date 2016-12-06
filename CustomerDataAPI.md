## Customer data API - Retrieving a single customer record.
The following request can be used to get Customer data from Cube:

**GET** ```https://YOURACCOUNT.cube4sales.com/crm/customer/?assignment_id={ASSIGNMENT_ID}&customer_id={CUSTOMER_ID}```

The assignment_id and customer_id must be integers

The API will return a > HTTP Response: 200 OK, and a JSON response with all available customer data, including any extra information fields configured for the assignment.
### Example response:

```json  
{
  "customer_id": 20101,
  "assignment_id": 246,
  "name": "Olas Reklameservice AS",
  "gender": "",
  "birth_date": null,
  "need_to_know": "500 mbps, 3990 kr",
  "care_of_name": null,
  "zone_name": "",
  "address_street": "My address",
  "address_street_no": 32,
  "address_entrance": "",
  "zip_code": "7000",
  "city": "Trondheim",
  "municipality": "",
  "county": "",
  "country": "",
  "phone_1": "90978457",
  "phone_2": "",
  "phone_3": "",
  "email": "ola@olasreklameservice.no",
  "Oppstartsdato": "2011-12-12",
  "Antall år": "6",
  "Pris på dagens avtale": "3990"
}
  ```

## Customer data API - Retrieving all customer records.
The following request can be used to get all customer data for an assignment in Cube:

**GET** ```https://YOURACCOUNT.cube4sales.com/crm/customers?assignment_id={ASSIGNMENT_ID}```

Cube will return > HTTP Response: 200 OK and a JSON containing a list of customer records similar to the example above.


## Example

**GET** ```https://YOURACCOUNT.cube4sales.com/crm/customers?assignment_id=9```

In this example, we have asked for all Customer records in assignment #9. What type of assignment this is can be seen in the Cube GUI. (We will add API support for listing assignment information).
Assignment #9 in this example have been configured as a B2B-assignment (Customer records are companies), and 6 assignment specific extra information fields have been configured:

For standard customer data fields, the fields are shown (with `null` values when no data is registered)



## Customer data API - Updating customer records.
The following request can be used to update Customer data records in Cube:

**POST** ```https://YOURACCOUNT.cube4sales.com/crm/update_customer/```

The POST body must contain the fields you want to update, and MUST include assignment_id and customer_id.

In the example below, we want to update ```gender```

```json 
{
    "customer_id": 2488539,
    "assignment_id": 9,
    "gender": "Male"
}
```  

Once updated, we will send a ```HTTP Response: 200 OK``` and return a copy of the updated customer record


## Customer data API - Creating customer records. (NOT YET IMPLEMENTED)
The following request can be used to create Customer data records in Cube:

**POST** ```https://YOURACCOUNT.cube4sales.com/crm/customers```

To create a new customer record, you need to POST the following parameters. Mandatory parameters have a * next to them.

| Parameter     | Description |
| ------------- |-------------|
| customer_id *  | A unique customer ID (typically the id from your CRM system |
| assignment_id * | The id of the assignment where the customer should be placed |
| name          | Name of the customer |
| etc..         | We have a lot of fields - will add them later |


