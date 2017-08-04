# Startup

* [POST /Startups/](#post_startup) - Creates a startup
* [GET /Startups/](#get_startup) - Gets a list of startups
* [GET /Startups/{startupId}/](#get_startup_startupid) - Gets details on a startup

## <a id="post_startup"></a> Creates a startup
This request allows you to create a startup for a future fundraising on it.

~~~text
POST /Startups/
~~~

| field | required | type | description |
|-------|----------|------|-------------|
| legalName | true  | string(100) | The legal name of the startup. |
| legalForm | true  | string(255) | The legal form of the startup. |
| address   | true  | [NewAddress](../conventions/objects.md#newaddress) | The address of the startup |
| owners    | true  | Array of [NewPersonalStartupOwner](../conventions/objects.md#newpersonalstartupowner) or [NewLegalStartupOwner](../conventions/objects.md#newlegalstartupowner) | An array containing all the personal and legal owners of the startup. |

~~~json
{
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

This request will respond with a [Startup](../conventions/objects.md#startup) as a response, or an [Error](../conventions/objects.md#startup) if something goes wrong.

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

## <a id="get_startup"></a> Gets a list of startups
This request allows you to get a list of startups.

This request applies for the [pagination and list sorting](../conventions/pagination.md) parameters.

~~~text
GET /Startups/
~~~

This request will respond with a [Startup](../conventions/objects.md#startup) Array as a response, or an [Error object](../conventions/objects.md#startup) if something goes wrong.

| field | type | description |
|-------|------|-------------|
| startups | Array of [Startup](../conventions/objects.md#startup) | An array containing a startup list |

~~~json
{
  "startups": [
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
  },
  { 
   //...
  }
  ]
}
~~~

## <a id="get_startup_startupid"></a> Gets details on a startup
This request allows you to get details on a particular startup.

~~~text
GET /Startups/{startupId}/
~~~

| field | required | type | description |
|-------|----------|------|-------------|
| startupId | true | string | The unique identifier of the startup you want details on. |

This request will respond with a [Startup](../conventions/objects.md#startup) as a response, or an [Error](../conventions/objects.md#startup) if something goes wrong.

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
