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
* [POST /Startups/](./services/StartupService.md#post_startup) - Creates a startup
* [GET /Startups/](./services/StartupService.md#get_startup) - Gets a list of startups
* [GET /Startups/{startupId}/](./services/StartupService.md#get_startup_startupid) - Gets details on a startup

### SPV
* [POST /SPVs/](./services/SPVService.md#post_spv) - Creates a SPV
* [GET /SPVs/](./services/SPVService.md#get_spv) - Gets a list of SPVs
* [GET /SPVs/{SPVId}/](./services/SPVService.md#get_spv_spvid) - Gets details on a SPV
* [DELETE /SPVs/](./services/SPVService.md#delete_spv) - Cancels a SPV
* [POST /SPVs/{SPVId}/Documents/](./services/SPVService.md#post_spv_spvid_document) - Uploads KYC documents for the SPV
* [GET /SPVs/{SPVId}/Documents/](./services/SPVService.md#get_spv_spvid_document) - Gets the list of KYC documents for the SPV
* [GET /SPVs/{SPVId}/Documents/{documentId}/](./services/SPVService.md#get_spv_spvid_document_documentid) - Gets the list of KYC documents for the SPV
* [GET /SPVs/{SPVId}/Transfers/](./services/SPVService.md#get_spv_spvid_transfer) - Gets a list of Transfers linked to a SPV
* [PUT /SPVs/{SPVId}/Payout/](./services/SPVService.md#put_spv_spvid_payout) - Do the final payout on a SPV

### Investor
* [POST /Investors/](./services/InvestorService.md#post_investor) - Creates an investor
* [GET /Investors/](./services/InvestorService.md#get_investor) - Gets a list of investors
* [GET /Investors/{investorId}/](./services/InvestorService.md#get_investor_investorid) - Gets details on an investor
* [POST /Investors/{investorId}/Documents/](./services/InvestorService.md#post_investor_investorid_document) - Uploads KYC documents for the investor
* [GET /Investors/{investorId}/Documents/](./services/InvestorService.md#get_investor_investorid_document) - Gets the list of KYC documents for the investor
* [GET /Investors/{investorId}/Documents/{documentId}/](./InvestorService/investorService.md#get_investor_investorid_document_documentid) - Gets details of a KYC document for the investor
* [GET /Investors/{investorId}/Transfers/](./services/InvestorService.md#get_investor_investorid_transfer) - Gets a list of Transfers linked to an investor
* [POST /Investors/{investorId}/Accounts/](./services/InvestorService.md#post_investor_investorid_account) - Creates an account for an investor
* [GET /Investors/{investorId}/Accounts/](./services/InvestorService.md#get_investor_investorid_account) - Gets a list of accounts linked to an investor
* [GET /Investors/{investorId}/Accounts/{accountId}/](./services/InvestorService.md#get_investor_investorid_account_accountid) - Gets details of an account linked to an investor

### Transfer
* [POST /Transfers/](./services/TransferService.md#post_transfer) - Creates a transfer
* [GET /Transfers/](./services/TransferService.md#get_transfer) - Gets a list of transfers
* [GET /Transfers/{transferId}/](./services/TransferService.md#get_transfer_transferid) - Gets details on a transfer
* [DELETE /Transfers/{transferId}/](./services/TransferService.md#delete_transfer_transferid) - Cancels a transfer
* [PUT /Transfers/{transferId}/Validate/](./services/TransferService.md#put_transfer_transferid_validate) - Validates a transfer

