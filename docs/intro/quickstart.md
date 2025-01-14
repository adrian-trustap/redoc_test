# Quickstart

## Step 1: Create a guest seller
{% tabs %}
  {% tab label="Create a guest seller" %}
    ```
curl --location 'https://dev.stage.trustap.com/api/v1/guest_users' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic dHJ1c3RhcC1pbnRlZ3JhdGlvbi1jbGllbnQ6' \
--data-raw '{"email":"Brisa@gmail.com","first_name":"Brisa","last_name":"Parker","country_code":"bg","tos_acceptance":{"unix_timestamp":1736440650,"ip":"127.0.0.1"}}'
```
  {% /tab %}
  {% tab label="Response" %}
```
{
    "created_at": "2025-01-09T16:37:25.783476091Z",
    "email": "Marisa@gmail.com",
    "id": "1-cc5375e7-91ea-4ecc-906c-7bfe4b6f5a95"
}
```
  {% /tab %}
{% /tabs %}


## Step 2: Create a guest buyer
{% tabs %}
  {% tab label="Create a guest buyer" %}
        ```
curl --location 'https://dev.stage.trustap.com/api/v1/guest_users' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data-raw '{"email":"Joan@gmail.com","first_name":"Joan","last_name":"Klein","country_code":"ca","tos_acceptance":{"unix_timestamp":1736441841,"ip":"127.0.0.1"}}'
```
  {% /tab %}
  {% tab label="Response" %}
``` 
{
    "created_at": "2025-01-09T16:57:21.207947674Z",
    "email": "Joan@gmail.com",
    "id": "1-026095d2-b7ac-4032-b98e-c0c71de81b6b"
}
```
  {% /tab %}
{% /tabs %}



## Step 3: Calculate the charge
{% tabs %}
  {% tab label="Calculate the charge" %}
        ```
curl --location 'https://dev.stage.trustap.com/api/v1/p2p/charge?price=20000&currency=eur' \
--header 'Authorization: ••••••' \
--data ''
```

  {% /tab %}
  {% tab label="Response" %}
    ``` response
{
    "charge": 1080,
    "charge_calculator_version": 3,
    "charge_seller": 0,
    "currency": "eur",
    "price": 20000
}
```
  {% /tab %}
{% /tabs %}



## Step 4: Create a transaction
 

{% tabs %}
  {% tab label="Create a transaction" %}
           ```
    curl --location 'https://dev.stage.trustap.com/api/v1/p2p/me/transactions/create_with_guest_user' \
--header 'Trustap-User: 1-cc5375e7-91ea-4ecc-906c-7bfe4b6f5a95' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
"seller_id": "1-cc5375e7-91ea-4ecc-906c-7bfe4b6f5a95",
"buyer_id": "1-026095d2-b7ac-4032-b98e-c0c71de81b6b",
"creator_role": "seller",
"currency": "eur",
"description": "F2F no deposit",
"deposit_price": 20000,
"deposit_charge": 1080,
"charge_calculator_version": 3,
"skip_remainder": true
}'

```
  {% /tab %}
  {% tab label="Response" %}
    
  {% /tab %}
{% /tabs %}


## Step 5: Transfer funds
    ```
        https://actions.stage.trustap.com/f2f/transactions/20809/pay_deposit?redirect_uri=https://app.trustap.com&state=dG9rZW49Njc4ZmUyNGUwMWRiZTRhNzk4ZWViODVkZTZhMzE5NDA6dHhfdHlwZT1wMnA6b3JkZXJfaWQ9MjAyOTpuYW1lPXRlc3QgdGVzdDpsaW5lMT1BZGRyZXNzIDE6Y2l0eT1CTEFLRURPV046c3RhdGU9OnBvc3Rjb2RlPURZMTAgNUZTOmNvdW50cnk9R0I=
    ```

## Step 6: Confirm harndover
    




{% tabs %}
  {% tab label="Confirm harndover" %}
        ```
        curl --location --request POST 'https://dev.stage.trustap.com/api/v1/p2p/transactions/20837/confirm_handover_with_guest_user' \
--header 'Trustap-user: 1-cc5375e7-91ea-4ecc-906c-7bfe4b6f5a95' \
--header 'Authorization: Basic dHJ1c3RhcC1pbnRlZ3JhdGlvbi1jbGllbnQ6'
    ```

  {% /tab %}
  {% tab label="Response" %}
        ```
{
    "id": 20837,
    "status": "seller_handover_confirmed",
    "currency": "eur",
    "quantity": 1,
    "deposit_pricing": {
        "price": 20000,
        "charge": 1080,
        "charge_seller": 0,
        "deposit_fee_multiplier": {
            "fee_multiplier": 1
        },
        "charge_international_payment": 317
    },
    "description": "F2F no deposit",
    "created": "2025-01-09T16:37:50Z",
    "skip_remainder": true,
    "is_deposit_payment_in_progress": false,
    "is_remainder_payment_in_progress": false,
    "client_id": "118931fb-e3fc-44fc-8a86-06a79d26972c",
    "buyer_id": "1-4a6ae0aa-a815-4374-a057-89fdf29e1b4b",
    "seller_id": "1-cc5375e7-91ea-4ecc-906c-7bfe4b6f5a95",
    "joined": "2025-01-09T16:37:50Z",
    "deposit_payment_capture": null,
    "deposit_paid": "2025-01-09T16:40:43Z",
    "deposit_accepted": "2025-01-09T16:42:28Z",
    "remainder_skipped": "2025-01-09T16:42:28Z",
    "seller_handover_confirmed": "2025-01-09T16:42:55Z",
    "complaint_period_deadline": "2025-01-09T16:47:55Z",
    "buyer_is_guest": true,
    "seller_is_guest": true
}
```
  {% /tab %}
{% /tabs %}