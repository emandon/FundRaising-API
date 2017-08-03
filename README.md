# iBanFirst Fundraising API
The iBanFirst fundraising API provides services around company fund raising and capital entries.

## API Reference

The FX4BIZ API is organized around [REST](http://en.wikipedia.org/wiki/Representational_state_transfer). Our API is designed to have predictable, resource-oriented URLs and use the HTTP response codes to indicate API errors. We use built-in HTTP features, like HTTP authentication and HTTP verbs, which can be understood by off-the-shelf HTTP clients, and we support [cross-origin resource sharing](http://en.wikipedia.org/wiki/Representational_state_transfer) to allow you to interact securely with our API from a client-side web application. [JSON](http://www.json.org/) will be returned in all responses from the API, including errors.

## Quick notes before starting

#### Authentication

As our API is designed to be secured, we highly recommend you to consult our [Authentication service](./services/authenticationService.md) in order to get your application working properly with our services.

#### Time

As a part of the authentication process is based on time, your systems should be synchronised through [Network Time Protocol](http://en.wikipedia.org/wiki/Network_Time_Protocol) to ensure the capability of reaching our services. Our API engine has a tolerance of 2 seconds gap to ensure that all systems are capable to reach the API, whatever the [Time Server](http://en.wikipedia.org/wiki/Time_server) you uses. Using our API with non-synchronized system will result in various errors in response to your query.

## Endpoints

The sandbox should be used during the testing period. All the information on the sandbox should be anonymized and/or faked.

The production environment must be only used for production calls and may not receive any test/uncertain call.

| Environment | URL |
|-------------|-----|
| Sandbox | https://sandbox.ibanfirst.com/fundraisingAPI |
| Production | https://api.ibanfirst.com/fundraisingAPI |

## Services

### Startup
* [POST /Startups/]() - Creates a startup
* [GET /Startups/]() - Gets a list of startups
* [GET /Startups/{startupId}/]() - Gets details on a startup
* [POST /Startups/{startupId}/Documents/]() - Uploads KYC documents for the startup
* [GET /Startups/{startupId}/Documents/]() - Gets the list of KYC documents for the startup
* [GET /Startups/{startupId}/Documents/{documentId}/]() - Gets details of a KYC document for the startup

### SPV
* [POST /SPVs/]() - Creates a SPV
* [GET /SPVs/]() - Gets a list of SPVs
* [GET /SPVs/{SPVId}/]() - Gets details on a SPV
* [DELETE /SPVs/]() - Cancels a SPV
* [GET /SPVs/{SPVId}/Transfers/]() - Gets a list of Transfers linked to a SPV
* [PUT /SPVs/{SPVId}/Payout/]() - Do the final payout on a SPV

### Investor
* [POST /Investors/]() - Creates an investor
* [GET /Investors/]() - Gets a list of investors
* [GET /Investors/{investorId}/]() - Gets details on an investor
* [POST /Investors/{investorId}/Documents/]() - Uploads KYC documents for the investor
* [GET /Investors/{investorId}/Documents/]() - Gets the list of KYC documents for the investor
* [GET /Investors/{investorId}/Documents/{documentId}/]() - Gets details of a KYC document for the investor
* [GET /Investors/{investorId}/Transfers/]() - Gets a list of Transfers linked to an investor
* [POST /Investors/{investorId}/Accounts/]() - Creates an account for an investor
* [GET /Investors/{investorId}/Accounts/]() - Gets a list of accounts linked to an investor
* [GET /Investors/{investorId}/Accounts/{accountId}/]() - Gets details of an account linked to an investor

### Transfer
* [POST /Transfers/]() - Creates a transfer
* [GET /Transfers/]() - Gets a list of transfers
* [GET /Transfers/{transferId}/]() - Gets details on a transfer
* [DELETE /Transfers/{transferId}/]() - Cancels a transfer
* [PUT /Transfers/{transferId}/Validate/]() - Validates a transfer

