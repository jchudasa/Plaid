Plaid Challenge

Question 1:
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

Question 2:

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

