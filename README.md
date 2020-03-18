## Spring Security OAuth
This is an example of microservices security using zuul proxy server.
</br></br></br>


## Run the Modules
You can run any sub-module using command line: 
```
mvn spring-boot:run
```

You can login using these credentials, username:john and password:123 

##### To get the access token build following POST request:
````
http://localhost:8080/oauth/token?username=john&password=123&grant_type=password
````
with headers 
````
authorization: Basic Zm9vQ2xpZW50SWRQYXNzd29yZDpzZWNyZXQ=
content-type:  application/json
````

Expected result: 
````
{
"access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX25hbWUiOiJqb2huIiwic2NvcGUiOlsiZm9vIiwicmVhZCIsIndyaXRlIl0sIm9yZ2FuaXphdGlvbiI6ImpvaG5WVXdXIiwiZXhwIjoxNTg0NTEyNjg4LCJhdXRob3JpdGllcyI6WyJST0xFX1VTRVIiXSwianRpIjoiYjJiNTJmNzAtODNhYy00OWYxLWIxMzktY2E4YTRiNDE4NmRjIiwiY2xpZW50X2lkIjoiZm9vQ2xpZW50SWRQYXNzd29yZCJ9.TQtVie_geQejKAvY0wS5lbxPH1NzSvEg75uupFAtCyw",
"token_type": "bearer",
"refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX25hbWUiOiJqb2huIiwic2NvcGUiOlsiZm9vIiwicmVhZCIsIndyaXRlIl0sIm9yZ2FuaXphdGlvbiI6ImpvaG5WVXdXIiwiYXRpIjoiYjJiNTJmNzAtODNhYy00OWYxLWIxMzktY2E4YTRiNDE4NmRjIiwiZXhwIjoxNTg3MTAxMDg4LCJhdXRob3JpdGllcyI6WyJST0xFX1VTRVIiXSwianRpIjoiNjU4NmZiNDEtYjIwZC00YjM3LWEwYTUtMWM2OTcxOGIxNDMxIiwiY2xpZW50X2lkIjoiZm9vQ2xpZW50SWRQYXNzd29yZCJ9.Tq4RlrTRmg7u3dt_wnGpEZKH5EHUNwciATkY0X0vUW8",
"expires_in": 3599,
"scope": "foo read write",
"organization": "johnVUwW",
"jti": "b2b52f70-83ac-49f1-b139-ca8a4b4186dc"
}
````

##### To access the resource(s) build similar GET request:
````
http:/localhost:8080/oauth-rs/users/extra
```` 
with headers
````
authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX25hbWUiOiJqb2huIiwic2NvcGUiOlsiZm9vIiwicmVhZCIsIndyaXRlIl0sIm9yZ2FuaXphdGlvbiI6ImpvaG5WVXdXIiwiZXhwIjoxNTg0NTEyNjg4LCJhdXRob3JpdGllcyI6WyJST0xFX1VTRVIiXSwianRpIjoiYjJiNTJmNzAtODNhYy00OWYxLWIxMzktY2E4YTRiNDE4NmRjIiwiY2xpZW50X2lkIjoiZm9vQ2xpZW50SWRQYXNzd29yZCJ9.TQtVie_geQejKAvY0wS5lbxPH1NzSvEg75uupFAtCyw
```` 
Expected result:
````
{
"user_name": "john",
"scope": [
  "foo",
  "read",
  "write"
],
"organization": "johnVUwW",
"exp": 1584512688,
"authorities": [
  "ROLE_USER"
],
"jti": "b2b52f70-83ac-49f1-b139-ca8a4b4186dc",
"client_id": "fooClientIdPassword"
}
````
