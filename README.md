#iBanFirst Fundraising API
The iBanFirst fundraising API provides services around company fund raising and capital entries.

##API Reference

The FX4BIZ API is organized around [REST](http://en.wikipedia.org/wiki/Representational_state_transfer). Our API is designed to have predictable, resource-oriented URLs and use the HTTP response codes to indicate API errors. We use built-in HTTP features, like HTTP authentication and HTTP verbs, which can be understood by off-the-shelf HTTP clients, and we support [cross-origin resource sharing](http://en.wikipedia.org/wiki/Representational_state_transfer) to allow you to interact securely with our API from a client-side web application. [JSON](http://www.json.org/) will be returned in all responses from the API, including errors.

## Quick notes before starting

#### Authentication

As our API is designed to be secured, we highly recommend you to consult our [Authentication service](./services/authenticationService.md) in order to get your application working properly with our services.

#### Time

As a part of the authentication process is based on time, your systems should be synchronised through [Network Time Protocol](http://en.wikipedia.org/wiki/Network_Time_Protocol) to ensure the capability of reaching our services. Our API engine has a tolerance of 2 seconds gap to ensure that all systems are capable to reach the API, whatever the [Time Server](http://en.wikipedia.org/wiki/Time_server) you uses. Using our API with non-synchronized system will result in various errors in response to your query.

##Endpoints

The sandbox should be used during the testing period. All the information on the sandbox should be anonymized and/or faked.

The production environment must be only used for production calls and may not receive any test/uncertain call.

| Environment | URL |
|-------------|-----|
| Sandbox | https://sandbox.ibanfirst.com/fundraisingAPI |
| Production | https://api.ibanfirst.com/fundraisingAPI |

##Services


