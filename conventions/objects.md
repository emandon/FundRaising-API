# Objects

## <a id="error"></a> Error Object
This object represents an error. These objects are present int the body of the response when an error occurs on the API.

| field | type | description |
|-------|------|-------------|
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

## <a id="startup"></a> Startup object
This object represents a startup.

| field | type | description |
|-------|------|-------------|
| startupId     | string      | The unique identifier of the startup. |
| createdDate   | string      | The creation datetime of the object. As this field represents a date and time, it will implement the `Y-m-d H:i:s` format (ex: 1970-01-01 14:30:00)
| legalName     | string(100) | The legal name of the startup. |
| legalForm     | string(255) | The legal form of the startup. |
| address       | [NewAddress](#newaddress) | The address of the startup |
| owners        | Array of [NewPersonalStartupOwner](#newpersonalstartupowner) or [NewLegalStartupOwner](#newlegalstartupowner) | An array containing all the personal and legal owners of the startup. |

~~~json
{
    "startupId":"Mtx9D1",
    "createdDate":"2017-08-01 22:03:40",
    "legalName":"My company INC",
    "legalForm":"SA",
    "address" : {
        "street": "350 Avenue Louise",
        "city": "Bruxelles",
        "zipcode": "10001",
        "state":null,
        "country":"BE"
    },
    "owners": [
        {
            "type":"person",
            "civility":"Mr.",
            "firstName":"John",
            "lastName":"Doe",
            "birthDate":"1970-01-01",
            "nationality":"FR",
            "address" : {
                "street": "2b Avenue Marbotte",
                "city": "Dijon",
                "zipcode": "21000",
                "state":null,
                "country":"FR"
            },
            "isDirector":true,
            "position":"CEO",
            "email":"jd@mymail.com",
            "phone":"+33123456789",
            "is10percentOwner":true,
            "isPoliticalyExposed":false
        },
        {
            "type": "legal",
            "legalName": "My legal entity INC",
            "legalForm": "SA",
            "address" : {
                "street": "33 1st Street",
                "city": "New-York",
                "zipcode": "10001",
                "state":"NY",
                "country":"US"
            },
            "email": "my@legalentity.com",
            "phone": "+33123456789",
            "is10percentOwner": true
        }
    ]
}
~~~

## <a id="newaddress"></a> NewAddress Object
This object represents an address contained in a creation request.

| field | required | type | description |
|-------|----------|------|-------------|
| street	| true     | string(100)	| The concatenated street number, street type and street name of the represented address. |
| city	    | true     | string(100)	| The city of the represented address |
| zipCode	| true     | string(20)	    | The ZIP or postal code of the city for the represented address. |
| state	    | false    | string(100)	| The state of the represented address. This field could be required if the country use a [state system](http://www.mapability.com/ei8ic/contest/states.php) like United States or Canada. |
| country	| true     | string(2)	    | The country of the represented address. The format of the country must implement the [ISO 3166](https://en.wikipedia.org/wiki/ISO_3166) country code format. |

~~~~json
{
    "street": "2b Avenue Marbotte",
    "city": "Dijon",
    "zipcode": "21000",
    "state":null,
    "country":"FR"
}
~~~~

## <a id="newpersonalstartupowner"></a> NewPersonalStartupOwner Object
This object represents a physical person, owner of a startup contained in a creation request.

| field | required | type | description |
|-------|----------|------|-------------|
| type                  | true | string(6)      | The type of the owner. It must be `person`.
| civility	            | true | string(4)	    | The civility of the owner. The civility can be `Mr.` or `Mrs.`. |
| firstName	            | true | string(100)	| The first name of the owner. |
| lastName	            | true | string(100)	| The last name of the owner. |
| birthDate	            | true | string(10)	    | The date of birth of the owner. As this field represents a date, it will implement the `Y-m-d` format (ex: 1970-01-01) |
| nationality	        | true | string(2)	    | The nationality of the owner. The format of the nationality will implement the [ISO 3166](https://en.wikipedia.org/wiki/ISO_3166) country code format. |
| address               | true | [NewAddress](#newaddress)     | The address of the owner. |
| is10PercentOwner	    | true | boolean	    | Either the owner owns 10% or more of the company or not. |
| isPoliticallyExposed	| true | boolean	    | Either the owner is politically exposed or not. |
| isDirector	        | true | boolean	    | Either is the owner a director of the company or not. |
| position	            | false | string(100)	| The position of the owner. Only needed if `isDirector = true`. |
| email	                | false | string	    | The email address of the owner. Only needed if `isDirector = true`. |
| phone	                | false | string	    | The phone number of the owner. The format of the phone number will implement the [E.164 international phone number format](https://en.wikipedia.org/wiki/E.164). Only needed if `isDirector = true`. |

~~~~json
{
    "type":"person",
    "civility":"Mr.",
    "firstName":"John",
    "lastName":"Doe",
    "birthDate":"1970-01-01",
    "nationality":"FR",
    "address" : {
        "street": "2b Avenue Marbotte",
        "city": "Dijon",
        "zipcode": "21000",
        "state":null,
        "country":"FR"
    },
    "isDirector":true,
    "position":"CEO",
    "email":"jd@mymail.com",
    "phone":"+33123456789",
    "is10percentOwner":true,
    "isPoliticalyExposed":false
}
~~~~

## <a id="newlegalstartupowner"></a> NewLegalStartupOwner Object
This object represents a legal entity, owner of a startup contained in a creation request.

| field | required | type | description |
|-------|----------|------|-------------|
| type              | true | string(5)  | The type of the owner. It must be `legal`. |
| legalName         | true | string(100)| The legal name of the legal entity. |
| legalForm         | true | string(255)| The legal form of the legal entity. |
| address           | true | [NewAddress](#newaddress) | The address of the legal entity. |
| email             | true | string     | A contact email for the legal entity. |
| phone             | true | string     | A contact phone for the legal entity. The format of the phone number will implement the [E.164 international phone number format](https://en.wikipedia.org/wiki/E.164). |
| is10percentOwner  | true | string     | Either the legal entity owns 10% or more of the company or not.|

~~~~json
{
    "type": "legal",
    "legalName": "My legal entity INC",
    "legalForm": "SA",
    "address" : {
        "street": "33 1st Street",
        "city": "New-York",
        "zipcode": "10001",
        "state":"NY",
        "country":"US"
    },
    "email": "my@legalentity.com",
    "phone": "+33123456789",
    "is10percentOwner": true
}
~~~~
