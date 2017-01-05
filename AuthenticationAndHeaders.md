## HTTPS
HTTPS is required for accessing the API.

## HTTP Basic Authentication
HTTP Basic authentication is the simplest way of interacting with the Cube API. Requests require a username and password.
```
Authorization: Basic (insert your authentication string here)
```

## Token based authentication
Headshed Cube also support Token-based authentication. Contact Headshed support to aquire a Token
The token must be placed in the Header: ```Authorization: Token (insert your token here)```

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
