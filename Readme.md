# Payop REST-like API Reference

The Payop API is organized around [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer).

Payop API has predictable resource-oriented URLs, accepts [JSON](http://www.json.org/) request bodies,
 returns [JSON](http://www.json.org/) responses, and uses standard HTTP response codes.

Each request to Payop API should have **Content-Type HTTP header** with `application/json` value.

### API Response examples

**Successful response**

Headers
```
HTTP/1.1 200 OK
Content-Type: application/json
token: eyJ0eXAiO...
```
Body
```json
{
    "data": {
        "id": "423131",
        "status": 1,
        "dateTime": {
            "createdAt": 1566543694,
            "updatedAt": null
        }
    },
    "status": 1
}
```
Each successful response this is JSON object with keys:   

Key       | Type                              | Description                                                        |
----------|-----------------------------------|--------------------------------------------------------------------| 
data      | **JSON object** OR **string**     | Email address                                                      |
status    | **Number**                        | Don't care about it. It's required for internal technical purposes |

**Failed responses**

* Invalid requests.
    
    Headers
    ```
    HTTP/1.1 415 Unsupported Media Type
    Content-Type: application/json
    ```
    Body
    ```json
    {
        "message": "Unsupported media type. Only json allowed"
    }
    ```

* Validation fails

    Headers
    ```
    HTTP/1.1 422 Unprocessable Entity
    Content-Type: application/json
    ```
    Body
    ```json
    {
        "message": {
            "email": [
                "This value should not be blank."
            ],
            "password": [
                "This value should not be blank."
            ]
        }
    }
    ```

1. [Authentication](authentication.md)
1. [Transaction Info](transaction.md)
1. [Checkout](checkout.md)
1. [Signature](signature.md)
1. [Withdrawal](withdrawal.md)


