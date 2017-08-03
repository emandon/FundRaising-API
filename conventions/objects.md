# Objects

## Error Object
This object represents an error. These objects are present int the body of the response when an error occurs on the API.

| parameter | type | description |
|-----------|------|-------------|
| ErrorCode	| Integer	| A unique identifier for the type of error. |
| ErrorType	| String	| A short description of the error. |
| link | String	| A string containing an URL from where you can find out more on the error. |

Example :

~~~~json
{
  "ErrorCode": 9,
  "ErrorType": "Entry already exists",
  "link": "https://api.ibanfirst.com/RestError/OTFlNGY5ZWVlOTNjODZkZDVhZjg3YTlkNzBmMzgxZmI=/9"
}
~~~~