## Customer data API - Creating customer records.
The following request can be used to create Customer data records in Cube:

**POST** ```https://YOURACCOUNT.cube4sales.com/crm/customers```

To create a new customer record, you need to POST the following parameters. Mandatory parameters have a * next to them.

| Parameter     | Description |
| ------------- |-------------|
| customer_id   | A unique customer ID (typically the id from your CRM system |
| assignment_id | The id of the assignment where the customer should be placed |
| name          | Name of the customer |
| etc..         | We have a lot of fields - will add them later |


## Customer data API - Updating customer records.
The following request can be used to update Customer data records in Cube:

**PUT** ```https://YOURACCOUNT.cube4sales.com/crm/customers/{customer_id}```

You can send any parameter (except the customer_id and the assignment_id) to be updated.
Once updated, we will send a ```HTTP Response: 200 OK```
