# Hello Trustap

## Make your first API call
Use this guide to make your first Trustap API call. 


## Step 1: Authentication
    Follow our [Authentication](./auth.md) guide to get your API token. 

## Step 2: Make your first call>

{% tabs %}
  {% tab label="Request" %}
    ```shell title="Create a guest buyer"
curl --location 'https://dev.stage.trustap.com/api/v1/guest_users' \
--header 'Content-Type: application/json' \
--header 'Authorization: <API_TOKEN>' \
--data-raw '{"email":"Niko@gmail.com","first_name":"Niko","last_name":"Beahan","country_code":"at","tos_acceptance":{"unix_timestamp":1736354931,"ip":"127.0.0.1"}}'
    ```
  {% /tab %}
  {% tab label="Response" %}
          ```json
        {
    "created_at": "2025-01-08T16:48:50.973364941Z",
    "email": "Niko@gmail.com",
    "id": "1-4a6ae0aa-a815-4374-a057-89fdf29e1b4b"
}
        ```
  {% /tab %}
{% /tabs %}

## Step 3: Congratulations
You have successfully made your first call to the Trustap API. 