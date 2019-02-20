Plaid Challenge

Challenge 1:

Hi there,
I’m trying to get up and running with Plaid, and I need some help. When I try to create an item, Plaid returns an INVALID_CREDENTIALS error. What am I doing wrong? Also, can you explain the difference between a public_token and access_token?
Thanks for the help.
Amy

Response

-----

Hi Amy,

I hope this email finds you well.

A public_token is a short-lived (~30 minutes) token returned by Plaid when creating an item. The public_token is then exchanged for an access_token. The access_token can then be used to make requests against an item. Additional online support material can be found under our [FAQ](https://support.plaid.com/hc/en-us/articles/360008413793-Access-token-and-Item-FAQ#What%20are%20the%20differences%20among%20a%20public_token,%20access_token,%20and%20an%20item)

The INVALID_CREDENTIALS error is a rejection message from the financial institution indicating your credentials provided were incorrect. I would suggest checking your credentials for typos, and if you still face issues try the credentials against the financial institution website.

I have also included some additional online support material related to common [Errors](https://github.com/plaid/support/blob/master/errors.md) and [Error Handling](https://support.plaid.com/hc/en-us/articles/360012859833-Handling-Plaid-Errors).

If you need any further assistance, please don’t hesitate to reach out.

Thank you,

Jay C
TSE – Plaid

-------------

Challenge 2:

Hi there,
The docs seem to be wrong. I'm trying to learn more about BB&T using the example provided in the documentation:

```
curl -G https://sandbox.plaid.com/institutions/search
 -H 'content-type: application/json'
 -d '{
   "query": "BB&T",
   "products": ["auth"]
 }'
```

but I get this error:

```
{
 "display_message": null,
 "error_code": "MISSING_FIELDS",
 "error_message": "the following required fields are missing: public_key",
 "error_type": "INVALID_REQUEST",
 "request_id": "Ehvcc"
}
```

Is there a problem with the API, or are the docs just wrong?

Thanks, 

George

Response:

-----

Hi George,

I hope this email finds you well.

The /institution-search requires three mandatory fields: query, products, and public_key. Based on the error_message, the public_key field was missing from your request. To fix this error, please add the public_key field to your request, as follows:

```
curl -G https://sandbox.plaid.com/institutions/search
 -H 'content-type: application/json'
 -d '{
   "query": "BB&T",
   "products": ["auth"],
   "public_key": String	
   }’
```

Your public_key can be found in your account dashboard under [Keys](https://dashboard.plaid.com/account/keys)

Thank you pointing out where our documentation can be improved. I will review internally with the team and revise accordingly.
Thanks,

Jay
TSE – Plaid

-----

Challenge 3

Follow the Plaid Quickstart, setting up a local application, to create a new transactions item, using Sandbox credentials. Once you've authenticated for the application, please provide the following information:

Names of the accounts, and their respective balances
Item details

Response

-----

Bank - Chase

ITEM_ID
klj6QZ816ns46m1KPpgws36Jba5xQMcWBnG85

ACCESS_TOKEN
access-sandbox-b8a845b3-423f-4148-82f6-df0aaa71b5ed


Name	Balance	Account #	Routing #
Plaid Checking	$100	1111222233330000	011401533
Plaid Saving	$200	1111222233331111	011401533

Balances:

Name	Balance	Subtype	Mask
Plaid Checking	$100	checking	0000
Plaid Saving	$200	savings	1111
Plaid CD	$1000	cd	2222
Plaid Credit Card	$410	credit card	3333
Plaid Money Market	$43200	money market	4444
Plaid IRA	$320.75	ira	5555
Plaid 401k	$22258.294	401k	6666

```
{
  "auth": {
    "accounts": [
      {
        "account_id": "lk5GQMyLGbunGqlva7BQiNGxjjNXJruZ14vB4", 
        "balances": {
          "available": 100, 
          "current": 110, 
          "iso_currency_code": "USD", 
          "limit": null, 
          "unofficial_currency_code": null
        }, 
        "mask": "0000", 
        "name": "Plaid Checking", 
        "official_name": "Plaid Gold Standard 0% Interest Checking", 
        "subtype": "checking", 
        "type": "depository"
      }, 
      {
        "account_id": "q3pG1g8EGKSGWbnd56Z8c5WJZZ547qCd8Eqlj", 
        "balances": {
          "available": 200, 
          "current": 210, 
          "iso_currency_code": "USD", 
          "limit": null, 
          "unofficial_currency_code": null
        }, 
        "mask": "1111", 
        "name": "Plaid Saving", 
        "official_name": "Plaid Silver Standard 0.1% Interest Saving", 
        "subtype": "savings", 
        "type": "depository"
      }, 
      {
        "account_id": "Ko9KN8ljKbUdpk5MgWEeiEdP33EKnWiVgyvoZ", 
        "balances": {
          "available": null, 
          "current": 1000, 
          "iso_currency_code": "USD", 
          "limit": null, 
          "unofficial_currency_code": null
        }, 
        "mask": "2222", 
        "name": "Plaid CD", 
        "official_name": "Plaid Bronze Standard 0.2% Interest CD", 
        "subtype": "cd", 
        "type": "depository"
      }, 
      {
        "account_id": "rxyGW8mlGrS5G93aRme4FXG7nnXmDqFlLQvbw", 
        "balances": {
          "available": null, 
          "current": 410, 
          "iso_currency_code": "USD", 
          "limit": 2000, 
          "unofficial_currency_code": null
        }, 
        "mask": "3333", 
        "name": "Plaid Credit Card", 
        "official_name": "Plaid Diamond 12.5% APR Interest Credit Card", 
        "subtype": "credit card", 
        "type": "credit"
      }, 
      {
        "account_id": "zexGwyDdGNIAMDkZeLqvFKpgxxKByocoDVGdr", 
        "balances": {
          "available": 43200, 
          "current": 43200, 
          "iso_currency_code": "USD", 
          "limit": null, 
          "unofficial_currency_code": null
        }, 
        "mask": "4444", 
        "name": "Plaid Money Market", 
        "official_name": "Plaid Platinum Standard 1.85% Interest Money Market", 
        "subtype": "money market", 
        "type": "depository"
      }, 
      {
        "account_id": "BjdMKe3zMpIRLZEanwBJUgRG33gqWwhwqBGvl", 
        "balances": {
          "available": null, 
          "current": 320.75, 
          "iso_currency_code": "USD", 
          "limit": null, 
          "unofficial_currency_code": null
        }, 
        "mask": "5555", 
        "name": "Plaid IRA", 
        "official_name": null, 
        "subtype": "ira", 
        "type": "brokerage"
      }, 
      {
        "account_id": "3RwrXl9er3H9NERxAjBPukLPxxk7ydtqGAagL", 
        "balances": {
          "available": null, 
          "current": 22258.294, 
          "iso_currency_code": "USD", 
          "limit": null, 
          "unofficial_currency_code": null
        }, 
        "mask": "6666", 
        "name": "Plaid 401k", 
        "official_name": null, 
        "subtype": "401k", 
        "type": "brokerage"
      }
    ], 
    "item": {
      "available_products": [
        "assets", 
        "balance", 
        "credit_details", 
        "identity", 
        "income"
      ], 
      "billed_products": [
        "auth", 
        "transactions"
      ], 
      "error": null, 
      "institution_id": "ins_3", 
      "item_id": "klj6QZ816ns46m1KPpgws36Jba5xQMcWBnG85", 
      "webhook": ""
    }, 
    "numbers": {
      "ach": [
        {
          "account": "1111222233330000", 
          "account_id": "lk5GQMyLGbunGqlva7BQiNGxjjNXJruZ14vB4", 
          "routing": "011401533", 
          "wire_routing": "021000021"
        }, 
        {
          "account": "1111222233331111", 
          "account_id": "q3pG1g8EGKSGWbnd56Z8c5WJZZ547qCd8Eqlj", 
          "routing": "011401533", 
          "wire_routing": "021000021"
        }
      ], 
      "eft": []
    }, 
    "request_id": "LkVo7glphFIBPfF"
  }, 
  "error": null
}
```

Item

```
{
  "error": null, 
  "institution": {
    "credentials": [
      {
        "label": "User ID", 
        "name": "username", 
        "type": "text"
      }, 
      {
        "label": "Password", 
        "name": "password", 
        "type": "password"
      }
    ], 
    "has_mfa": true, 
    "institution_id": "ins_3", 
    "mfa": [
      "code", 
      "list"
    ], 
    "mfa_code_type": "numeric", 
    "name": "Chase", 
    "products": [
      "assets", 
      "auth", 
      "balance", 
      "transactions", 
      "credit_details", 
      "income", 
      "identity"
    ]
  }, 
  "item": {
    "available_products": [
      "assets", 
      "balance", 
      "credit_details", 
      "identity", 
      "income"
    ], 
    "billed_products": [
      "auth", 
      "transactions"
    ], 
    "error": null, 
    "institution_id": "ins_3", 
    "item_id": "klj6QZ816ns46m1KPpgws36Jba5xQMcWBnG85", 
    "webhook": ""
  }
}
```
