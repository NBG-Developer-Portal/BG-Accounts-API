## **Berlin Group Account Information v1.3.6 Sandbox API** 
****
### **Introduction to the API**
This API helps you obtain a list of your accounts and cards and their respective information such as balances and transactions.
The api follows the Berlin Group Specification v1.3.6.

### **Real Life Use Case Scenario**
Imagine you want to create an application which handles all of your banks' accounts. What can you do about it? Just use this api to create a custom made Account Management Application, in any platform you prefer, in order to retrieve your accounts' information.

### **Create Sandbox**
Your first job is to create a sandbox and save your **sandbox-id** in order to be able to **"play"** with the api.

We will create our sandbox by making an **HTTP POST** request to the following URL:
> https://apis.nbg.gr/sandbox/bg.openbanking.accounts/oauth2/v1/sandbox

Request Body:
```json
 {
   "sandbox-id": "my-accounts-sandbox"
 }
``` 

**Note: Remember to store *sandbox-id* somewhere in your application, because you will need to provide it as a header
in each api call. Also remember to use the *Client-Id* provided when you create your application in the portal.**

When you create the sandbox application it has some default data.
## **Request Headers**
The following headers are required for every call. In postman they are in the appropriate environment variables.

**Request Headers**:
```
   'accept: application/json'
   'Client-Id: {{client-id}}'
   'sandbox-id: {{sandbox-id}}'
   'x-fapi-interaction-id: {{$guid}}'
   'x-fapi-customer-ip-address: {{$randomIP}}' 
``` 
## **Scenario Request**
You send **GET /accounts** request to get a list of the available accounts among with their balances. 
> https://apis.nbg.gr/sandbox/bg.openbanking.accounts/oauth2/v1/sandbox/accounts?withBalance=true


**Response** (Contains information about the available accounts (e.g. currency, type, description)):
```json
{
    "accounts": [
        {
            "resourceId": "9d49d3c0-6c92-4a61-4457-f0cea5a654a8",
            "iban": "GR3201106970000069774934603",
            "currency": "EUR",
            "ownerName": "FIRST BENEFICIARY",
            "displayName": "Account Alias",
            "product": "This is a personal savings account",
            "cashAccountType": "SVGS",
            "status": "enabled",
            "bic": "ETHNGRAA",
            "usage": "PRIV",
            "balances": [
                {
                    "balanceAmount": {
                        "currency": "EUR",
                        "amount": "1120.67"
                    },
                    "balanceType": "interimAvailable"
                },
                {
                    "balanceAmount": {
                        "currency": "EUR",
                        "amount": "1150.67"
                    },
                    "balanceType": "interimBooked"
                }
            ],
            "_links": {
                "balances": {
                    "href": "https://apis.nbg.gr/sandbox/bg.openbanking.accounts/oauth2/v1/sandbox/accounts/9d49d3c0-6c92-4a61-4457-f0cea5a654a8/balances"
                },
                "transactions": {
                    "href": "https://apis.nbg.gr/sandbox/bg.openbanking.accounts/oauth2/v1/sandbox/accounts/9d49d3c0-6c92-4a61-4457-f0cea5a654a8/transactions"
                }
            }
        }
    ]
}

``` 


Created by **NBG**.\
See more at https://developer.nbg.gr/