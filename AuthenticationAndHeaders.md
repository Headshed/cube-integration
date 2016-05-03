## HTTP Basic Authentication

HTTP Basic authentication is the simplest way of interacting with the Cube API. Requests require a username and password. HTTPS is required for accessing the API.

## Making A Request
Here’s an example of interacting with Cube via JSON. To make requests in JSON, specify application/json for your Content-Type and Accept headers. A simple example with curl:

`curl -H 'Content-Type: application/json' -H 'Accept: application/json' -u "user@example.com:password" https://YOURACCOUNT.cube4sales.com/account/who_am_i`

Successful requests return HTTP response code 200. Other response codes indicate a failed request or missing resource, in which case an error message may be returned.

### Headers
Request headers need to be set up with the following:
```
Accept: application/json
Content-Type: application/json
Authorization: Basic (insert your authentication string here)
```
Your authentication string is a base64 encoded version of your credentials. You can generate this in Python:
`base64.b64encode("myemail@example.com:password")`

Or in JavaScript:
`btoa("myemail@example.com:password")`

