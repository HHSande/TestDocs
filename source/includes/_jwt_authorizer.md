# JWT Authorizer

Every API request is handled by a Lambda which ensures that the given user is authorized to make the given request.
The user first has to add a token in the request header, this is done by calling (someUrl) where you pass your ClientId and ClientSecret to produce a token.  
This will then be validated by the lambda, verifying that the user has the correct permission to perform the given request against the given resource.

# Token

## Request

| Method | Resource |
| ------ | -------- |
| post   | /token   |

### Auth

Basic Auth
Username: < ClientId >
Password: < ClientSecret >

# Header (auth)

| Key           | Value                        |
| ------------- | ---------------------------- |
| Authorization | < token from token request > |
