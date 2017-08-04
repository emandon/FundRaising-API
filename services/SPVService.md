# SPV

* [POST /SPVs/](#post_spv) - Creates a SPV
* [GET /SPVs/](#get_spv) - Gets a list of SPVs
* [GET /SPVs/{SPVId}/](#get_spv_spvid) - Gets details on a SPV
* [DELETE /SPVs/](#delete_spv) - Cancels a SPV
* [POST /SPVs/{SPVId}/Documents/](#post_spv_document) - Uploads KYC documents for the SPV
* [GET /SPVs/{SPVId}/Documents/](#get_spv_document) - Gets the list of KYC documents for the SPV
* [GET /SPVs/{SPVId}/Documents/{documentId}/](#get_spv_document_documentid) - Gets the list of KYC documents for the SPV
* [GET /SPVs/{SPVId}/Transfers/](#get_spv_spvid_transfer) - Gets a list of Transfers linked to a SPV
* [PUT /SPVs/{SPVId}/Payout/](#put_spv_spvid_payout) - Do the final payout on a SPV

## <a id="post_spv"></a> Creates a SPV
This request allows you to create a SPV for a fundraising.

~~~text
POST /SPVs/
~~~

| field | required | type | description |
|-------|----------|------|-------------|
| startupId | true | string | The unique identifier of the startup linked to the SPV for the fundraising. |
| targetAccount | true | [NewTargetAccount](#newtargetaccount) | A NewTargetAccount object that contains all information about the final recipient account of the SPV. |
| amount        | true | [NewAmount](#newamount) | An NewAmount object that contains information about fundraising final value and currency. |

~~~json
{    
    "StartupId":"Ntx5c3",
    "targetAccount": {
        "accountNumber":"FR7630006000011234567890189",
        "bic":"AGRIFRPP",
        "clearingType": null,
        "clearingCode": null,
        "name": null,
        "address": {
            "street": "91 93, BD PASTEUR",
            "city": "Paris",
            "zipcode": "75001",
            "province": null,
            "country": "FR"
        }
    },
    "amount": {
        "value": 500000.00,
        "currency": "EUR"
    }
}
~~~

This request will respond with a [SPV](../conventions/objects.md#spv) as a response, or an [Error](../conventions/objects.md#startup) if something goes wrong.

~~~json
{    
    "spvId":"Vtx78d",
    "StartupId":"Ntx5c3",
    "status":"initialized",
    "createdDate":"2017-08-01 11:42:50",
    "targetAccount": {
        "accountNumber":"FR7630006000011234567890189",
        "bic":"AGRIFRPP",
        "clearingType": null,
        "clearingCode": null,
        "name": null,
        "address": {
            "street": "91 93, BD PASTEUR",
            "city": "Paris",
            "zipcode": "75001",
            "province": null,
            "country": "FR"
        }
    },
    "amount": {
        "value": 500000.00,
        "currency": "EUR"
    },
    "documents": []
}
~~~

## <a id="get_spv"></a> Gets a list of SPVs
This request allows you to get a list of SPVs.

This request applies for the [pagination and list sorting](../conventions/pagination.md) parameters.

~~~text
GET /SPVs/
~~~

This request will respond with a [SPVs](../conventions/objects.md#spv) Array as a response, or an [Error object](../conventions/objects.md#startup) if something goes wrong.

| field | type | description |
|-------|------|-------------|
| spvs | Array of [SPV](../conventions/objects.md#spv) | An array containing a SPV list |

~~~json
{
    "spvs": [
        {    
            "spvId":"Vtx78d",
            "StartupId":"Ntx5c3",
            "status":"initialized",
            "createdDate":"2017-08-01 11:42:50",
            "targetAccount": {
                "accountNumber":"FR7630006000011234567890189",
                "bic":"AGRIFRPP",
                "clearingType": null,
                "clearingCode": null,
                "name": null,
                "address": {
                    "street": "91 93, BD PASTEUR",
                    "city": "Paris",
                    "zipcode": "75001",
                    "province": null,
                    "country": "FR"
                }
            },
            "amount": {
                "value": 500000.00,
                "currency": "EUR"
            },
            "documents": []
        },
        {
        //...
        }
    ]
}
~~~

## <a id="get_spv_spvid"></a> Gets details on a SPV
This request allows you to get details on a particular SPV.

~~~text
GET /SPVs/{spvId}/
~~~

| field | required | type | description |
|-------|----------|------|-------------|
| spvId | true | string | The unique identifier of the SPV you want details on. |

This request will respond with a [SPV](../conventions/objects.md#spv) as a response, or an [Error](../conventions/objects.md#startup) if something goes wrong.

~~~json
{    
    "spvId":"Vtx78d",
    "StartupId":"Ntx5c3",
    "status":"initialized",
    "createdDate":"2017-08-01 11:42:50",
    "targetAccount": {
        "accountNumber":"FR7630006000011234567890189",
        "bic":"AGRIFRPP",
        "clearingType": null,
        "clearingCode": null,
        "name": null,
        "address": {
            "street": "91 93, BD PASTEUR",
            "city": "Paris",
            "zipcode": "75001",
            "province": null,
            "country": "FR"
        }
    },
    "amount": {
        "value": 500000.00,
        "currency": "EUR"
    },
    "documents": []
}
~~~

## <a id="delete_spv"></a> Cancels a SPV
This request allows you to cancel a SPV and the fundraising linked to it.

~~~text
DELETE /SPVs/{spvId}/
~~~

| field | required | type | description |
|-------|----------|------|-------------|
| spvId | true | string | The unique identifier of the SPV you want to cancel. |

This request will respond with a canceled [SPV](../conventions/objects.md#spv) as a response, or an [Error](../conventions/objects.md#startup) if something goes wrong.

~~~json
{    
    "spvId":"Vtx78d",
    "StartupId":"Ntx5c3",
    "status":"canceled",
    "createdDate":"2017-08-01 11:42:50",
    "targetAccount": {
        "accountNumber":"FR7630006000011234567890189",
        "bic":"AGRIFRPP",
        "clearingType": null,
        "clearingCode": null,
        "name": null,
        "address": {
            "street": "91 93, BD PASTEUR",
            "city": "Paris",
            "zipcode": "75001",
            "province": null,
            "country": "FR"
        }
    },
    "amount": {
        "value": 500000.00,
        "currency": "EUR"
    },
    "documents": []
}
~~~


## <a id="post_spv_document"></a> Uploads KYC documents for the SPV
## <a id="get_spv_document"></a> Gets the list of KYC documents for the SPV
## <a id="get_spv_document_documentid"></a> Gets the list of KYC documents for the SPV
## <a id="get_spv_spvid_transfer"></a> Gets a list of Transfers linked to a SPV
## <a id="put_spv_spvid_payout"></a> Do the final payout on a SPV