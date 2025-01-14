# Authentication

Trustap authenticates your API requests using API keys and a unique URI associated only with your account. 



## Step 1: Contact Trustap
Use our [contact form](https://www.trustap.com/contact-us/) get in touch.

To help us understand your use case tell us the following, 
```
* What does your company do
* What problem can Trustap solve for you
```
     
## Step 2: Obtain Authentication credentials
    Our support team will contact you with credentials. These include the following.
    1. `URI` that is unique to you. This is normalling in the form `<YOUR-COMPANY-NAME>.stage.trustap.com`.
    2. A security `TOKEN`.
    
## Step 3: Use Authentication credentials
To make a call to the Trustap API, replace `<YOUR_URI>` and `<TOKEN>` with the URI and token provided to you by 
```
curl --location 'https://<YOUR_URI>/api/v1/guest_users' \
--header 'Content-Type: application/json' \
--header 'Authorization: <TOKEN>' \
--data-raw '{"email":"Joan@gmail.com","first_name":"Joan","last_name":"Klein","country_code":"ca","tos_acceptance":{"unix_timestamp":1736441841,"ip":"127.0.0.1"}}'
```