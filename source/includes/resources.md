# Endpoints

## Login

```shell
curl --location --request POST 'https://backend.ducapp.net/api/auth/login' \
--header 'x-api-key: <YOUR_API_KEY>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "phone": "+13057032683",
    "password": "StrongPassword1@"
}
'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("x-api-key", "<YOUR_API_KEY>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "phone": "+13057032683",
  "password": "StrongPassword1@"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://backend.ducapp.net/api/auth/login", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```



```python
import requests
import json

url = "https://backend.ducapp.net/api/auth/login"

payload = json.dumps({
  "phone": "+13057032683",
  "password": "StrongPassword1@"
})
headers = {
  'x-api-key': '<YOUR_API_KEY>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

> Example Response:

```json 
{
    "firstLoginRequired": false,
    "twoFactorCheckRequired": false,
    "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2MTlkNGQ0MjA1MGUyOTIxNTYwMmQzNGMiLCJmaXJzdE5hbWUiOiJIYWJsYXgiLCJsYXN0TmFtZSI6IkhhYmxheCIsImVtYWlsIjoiaW5mb0BoYWJsYXMuY29tIiwicGhvbmUiOiIrMTMwNTkwMzI2ODIiLCJ3YWxsZXRBZGRyZXNzIjoiMHhkOTUzOTkzRDA5OTBiZGVkZDJCQzJlNWRFNUQ1N2MyM0EyRTMyNmQwIiwiZGVmYXVsdEN1cnJlbmN5IjoiVVNEIiwicm9sZXMiOlsiNWRlMDMwMmE1OGU1MzAwMDBkZTBkZDJjIl0sImxhbmd1YWdlIjoiRU4iLCJsYXN0TG9naW5BdCI6IjIwMjEtMTItMjhUMTU6NTg6MzYuNjA1WiIsInN0YXR1cyI6IkFjdGl2YXRlZCIsInZlcmlmaWVkIjpmYWxzZSwidHJ1c3RMZXZlbCI6NywiaXNCbG9ja2VkIjpmYWxzZSwibG9naW5GYWlsQ291bnQiOjAsImJsb2NrZWRVbnRpbCI6bnVsbCwiaWF0IjoxNjQzOTI2MDcwLCJleHAiOjE2NDM5NDQwNzB9.fNp9TwXvn5964ZaKeDaI221lwHQJx4CFVMp8iO--e_o",
    "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJyZWZyZXNoVG9rZW4iOiJvU3d6NVppRGdXVmlSMjF2QUc2MmlYeDY3eSIsImlhdCI6MTY0MzkyNjA3MCwiZXhwIjoxNjQzOTgwMDcwfQ.nxcSprbfrGiIeOCypj0V0xtOSNW7tcmtpRwq2A-CXCk"
}
```

### Request
POST `/api/auth/login`

Host: `backend.ducapp.net`

x-api-key: `<YOUR_API_KEY>`

Content-Type: `application/json`


### Request Body

| NAME       | TYPE   | DESCRIPTION                  |
| ---------- | ------ | ---------------------------- |
| `phone`    | string | Registered User phone number |
| `password` | string | Registered User password     |

### Response

| NAME                     | TYPE    | DESCRIPTION                             |
| ------------------------ | ------- | --------------------------------------- |
| `firstLoginRequired`     | boolean |                                         |
| `twoFactorCheckRequired` | boolean |                                         |
| `accessToken`            | string  | Token to access authenticated endpoints |
| `refreshToken`           | string  |                                         |

## Register User

```shell
curl --location --request POST 'https://backend.ducapp.net/api/private/users/register' \
--header 'x-api-key: <YOUR_API_KEY>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "appVersion": "1.67.0",
    "language": "EN",
    "defaultCurrency": "USD",
    "providerValue": "username@domail.com",
    "password": "changeme*123",
    "firstName": "UserName",
    "lastName": "UserLastName",
    "phone": "+11234567890",
    "birthDate": "1995-07-05",
    "identityNumber": "96060188121",
    "houseNumber": "1",
    "street": "1ra",
    "city": "DE",
    "zipcode": "19804",
    "country": "United State of America",
    "country_iso_code": "US",
    "status": "Activated",
    "areConditionsAccepted": "true",
    "province": "Delaware",
    "source1": {
        "url": "someUrl",
        "name": "passportPicture",
        "type": "mime/jpg",
        "size": "50"
    },
    "source2": {
        "url": "someUrl",
        "name": "passportPicture",
        "type": "mime/jpg",
        "size": "50"
    },
    "image": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAfQAAAH0CAYAAA...Jggg=="
}
'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("x-api-key", "<YOUR_API_KEY>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "appVersion": "1.67.0",
  "language": "EN",
  "defaultCurrency": "USD",
  "providerValue": "username@domail.com",
  "password": "changeme*123",
  "firstName": "UserName",
  "lastName": "UserLastName",
  "phone": "+11234567890",
  "birthDate": "1995-07-05",
  "identityNumber": "96060188121",
  "houseNumber": "1",
  "street": "1ra",
  "city": "DE",
  "zipcode": "19804",
  "country": "United State of America",
  "country_iso_code": "US",
  "status": "Activated",
  "areConditionsAccepted": "true",
  "province": "Delaware",
  "source1": {
    "url": "someUrl",
    "name": "passportPicture",
    "type": "mime/jpg",
    "size": "50"
  },
  "source2": {
    "url": "someUrl",
    "name": "passportPicture",
    "type": "mime/jpg",
    "size": "50"
  },
  "image": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAfQAAAH0CAYAAA...Jggg=="
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://backend.ducapp.net/api/private/users/register", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

```python
import requests
import json

url = "https://backend.ducapp.net/api/private/users/register"

payload = json.dumps({
  "appVersion": "1.67.0",
  "language": "EN",
  "defaultCurrency": "USD",
  "providerValue": "username@domail.com",
  "password": "changeme*123",
  "firstName": "UserName",
  "lastName": "UserLastName",
  "phone": "+11234567890",
  "birthDate": "1995-07-05",
  "identityNumber": "96060188121",
  "houseNumber": "1",
  "street": "1ra",
  "city": "DE",
  "zipcode": "19804",
  "country": "United State of America",
  "country_iso_code": "US",
  "status": "Activated",
  "areConditionsAccepted": "true",
  "province": "Delaware",
  "source1": {
    "url": "someUrl",
    "name": "passportPicture",
    "type": "mime/jpg",
    "size": "50"
  },
  "source2": {
    "url": "someUrl",
    "name": "passportPicture",
    "type": "mime/jpg",
    "size": "50"
  },
  "image": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAfQAAAH0CAYAAA...Jggg=="
})
headers = {
  'x-api-key': '<YOUR_API_KEY>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```
> Example Response:

```json
{
    "validatedUser": false,
    "message": "We send a welcome message to you, please check it",
    "activationCode": "336519",
    "user": {
        "connected": false,
        "deleted": false,
        "loginFailCount": 0,
        "blockedUntil": null,
        "disabled": false,
        "isBlocked": false,
        "publicFields": [],
        "validatedUser": false,
        "onBoardingComplete": false,
        "isBusinessType": false,
        "firstLoginRequired": true,
        "changePasswordRequired": false,
        "twofAuthEnabled": false,
        "registeredUser": false,
        "walletPrivateKey": "0x25590b0f8817d93d956fa9672591922c1640e75fdb1a82e187a2b9bc5a9baace",
        "defaultCurrency": "USD",
        "language": "EN",
        "allowFaceRecognition": true,
        "roles": [
            "5de0302a58e530000de0dd2c"
        ],
        "needKYCVerification": false,
        "verified": false,
        "userWasUpdate": false,
        "trustLevel": 0,
        "isVirgin": true,
        "transactionCount": 0,
        "beneficiaries": [],
        "requestOTPCount": 0,
        "firstRequestOTPAt": null,
        "_id": "61bc2d893c83e9346b64d456",
        "password": "pk/dEnrRpQUjss/VRWU/CosO7qdwCJO4mMAlnrX0C5VBScTogQZyiDxxZc6I2I68RkUanxPU0KTgjvSrCx/otg==",
        "firstName": "Test",
        "lastName": "Test",
        "phone": "+5352552613",
        "birthDate": "2021-11-23T00:00:00.000Z",
        "identityNumber": "833688881",
        "houseNumber": "508",
        "street": "Main Street",
        "city": "DE",
        "zipcode": "19804",
        "country": "United States of America",
        "status": "To Verify",
        "email": "koroyel38@swsguide.com",
        "linkedProviders": [
            {
                "provider": "localEmail",
                "_id": "61bc2d893c83e9125864d457",
                "associatedValue": "koroyel38@swsguide.com"
            },
            {
                "provider": "localPhone",
                "_id": "61bc2d893c83e965df64d45b",
                "associatedValue": "+5352552613"
            }
        ],
        "twofAuthSecret": "G5JF2OTTJ5KFIL26GBZFUS2JMYXSY33N",
        "activationCode": "336519",
        "walletAddress": "0x8D9FD032852815a789c212C1EacD0A3644E4E798",
        "walletQRCode": "data:image/png;base64,iVBORw0KGgoAAAANSU…QmCC",
        "refreshTokenProviders": [],
        "devices": [],
        "metadata": [],
        "settings": {
            "frequency": "instant",
            "_id": "61bc2d893c83e978c964d458",
            "providers": [
                {
                    "_id": "61bc2d893c83e9e75f64d459",
                    "provider": "email",
                    "value": "koroyel38@swsguide.com",
                    "active": true
                },
                {
                    "_id": "61bc2d893c83e94a8d64d45a",
                    "provider": "sms",
                    "value": "+5352552613",
                    "active": true
                }
            ]
        },
        "privacyConfigurations": [
            {
                "key": "localization",
                "value": true
            }
        ],
        "verifications": [],
        "verificationComments": [],
        "linkedAttemptsValues": [],
        "reviews": [],
        "personalMargin": {
            "ADD_FUND": 0,
            "BANK_ACCOUNT_TRANSACTION": 0,
            "CREDIT_CARD_TRANSACTION": 0,
            "MLC_CREDIT_CARD_TRANSACTION": 0,
            "DELIVERY_TRANSACTION": 0,
            "DELIVERY_TRANSACTION_USD": 0,
            "THUNES_TRANSACTION": 0,
            "EMAIL_MONEY_TRANSACTION": 0,
            "EMAIL_PAYMENT_REQUEST": 0,
            "PAYMENT_REQUEST": 0,
            "P2P_TRANSFER": 0,
            "TOKENS_BUY": 0,
            "TOKENS_BUY_INLINE": 0,
            "TOKENS_BUY_MCP": 0,
            "TOKENS_BUY_CRYPTO": 0,
            "TOKENS_BUY_CRYPTO_INLINE": 0,
            "TOKENS_BUY_GPAY": 0,
            "TOKENS_BUY_GPAY_INLINE": 0,
            "TOKENS_BUY_APPLE_PAY": 0,
            "TOKENS_BUY_APPLE_PAY_INLINE": 0,
            "TOKEN_EXCHANGE": 0,
            "TOPUP_RECHARGE": 0
        },
        "payProvidersMeta": [],
        "availableServices": {
            "ADD_FUND": true,
            "BANK_ACCOUNT_TRANSACTION": true,
            "CREDIT_CARD_TRANSACTION": true,
            "MLC_CREDIT_CARD_TRANSACTION": true,
            "DELIVERY_TRANSACTION": true,
            "DELIVERY_TRANSACTION_USD": true,
            "THUNES_TRANSACTION": true,
            "EMAIL_MONEY_TRANSACTION": true,
            "EMAIL_PAYMENT_REQUEST": true,
            "PAYMENT_REQUEST": true,
            "P2P_TRANSFER": true,
            "TOKENS_BUY": true,
            "TOKENS_BUY_INLINE": true,
            "TOKENS_BUY_MCP": true,
            "TOKENS_BUY_CRYPTO": true,
            "TOKENS_BUY_CRYPTO_INLINE": true,
            "TOKENS_BUY_GPAY": true,
            "TOKENS_BUY_GPAY_INLINE": true,
            "TOKENS_BUY_APPLE_PAY": true,
            "TOKENS_BUY_APPLE_PAY_INLINE": true,
            "TOKEN_EXCHANGE": true,
            "TOPUP_RECHARGE": true
        },
        "createdAt": "2021-12-17T06:26:17.430Z",
        "updatedAt": "2021-12-17T06:26:17.430Z",
        "nameFull": "Test Test",
        "salt": "JAYcHx1kq//Dcn2QekgZzQ==",
        "__v": 0,
        "fullName": "Test Test",
        "fullNameShort": "Test T.",
        "fullNameLong": "Test Test",
        "score": 3,
        "id": "61bc2d893c83e9346b64d456"
    },
    "hasPassword": true,
    "hasActivationCode": true,
    "firstLoginRequired": true,
    "twoFactorCheckRequired": false,
    "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ…",
    "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9…"
}
```

### Request

POST `/api/private/users/register`

Host: `backend.ducapp.net`

x-api-key: `<YOUR_API_KEY>`

Content-Type: `application/json`

### Request Body

| NAME                    | TYPE                | DESCRIPTION                                                 |
| ----------------------- | ------------------- | ----------------------------------------------------------- |
| `appVersion`            | string              | Allowed version to interact with the platform               |
| `language`              | string              | The preferred user language                                 |
| `defaultCurrency`       | string              | The preferred user currency                                 |
| `providerValue`         | string              | The value of the used provider (phone/email)                |
| `password`              | string              | The user password                                           |
| `firstName`             | string              | The user firstName                                          |
| `lastName`              | string              | The user lastName                                           |
| `phone`                 | string              | The user phone number                                       |
| `birthDate`             | string              | The user birthDate                                          |
| `identityNumber`        | string              | The user identity number                                    |
| `houseNumber`           | string              | The user identity house number                              |
| `street`                | string              | The user street name                                        |
| `city`                  | string              | The user city name                                          |
| `zipcode`               | string              | The user zipcode number                                     |
| `province`              | string              | The user province name                                      |
| `country`               | string              | The user country name                                       |
| `country_iso_code`      | string              | The user alpha2 country iso code                            |
| `status`                | string              | The user initial status                                     |
| `areConditionsAccepted` | string              | The user agreement to use his data for verification purpose |
| `source1`               | `image object`      | The user pasport picture                                    |
| `source2`               | `image object`      | The user driving license pciture                            |
| `image`                 | base64 string image | The user pattern picture                                    |

### Image Object

| NAME   | TYPE   | DESCRIPTION                        |
| ------ | ------ | ---------------------------------- |
| `url`  | string | Url to access the image asset      |
| `name` | string | Name of the image asset            |
| `type` | string | Type of the image asset (mime/jpg) |
| `size` | string | Size of the image asset            |



### Response

## Verify User

```python
import requests
import json

url = "https://backend.ducapp.net/api/private/users/verify"

payload = json.dumps({
  "userID": "61c0da6a7623905113d7683e",
  "activationCode": "162660"
})
headers = {
  'x-api-key': 'test.8f495a50-cc9f-5877-addf-1da6f7e13353',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request POST 'https://backend.ducapp.net/api/private/users/verify' \
--header 'x-api-key: test.8f495a50-cc9f-5877-addf-1da6f7e13353' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userID": "61c0da6a7623905113d7683e",
    "activationCode": "162660"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("x-api-key", "test.8f495a50-cc9f-5877-addf-1da6f7e13353");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "userID": "61c0da6a7623905113d7683e",
  "activationCode": "162660"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://backend.ducapp.net/api/private/users/verify", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Example Response:

```json
{
    "validatedUser": true,
    "message": "Your account has been validated. Welcome to DUC App!!!",
    "user": {
        "connected": false,
        "deleted": false,
        "loginFailCount": 0,
        "blockedUntil": null,
        "disabled": false,
        "isBlocked": false,
        "publicFields": [],
        "validatedUser": false,
        "onBoardingComplete": false,
        "isBusinessType": false,
        "firstLoginRequired": true,
        "changePasswordRequired": false,
        "twofAuthEnabled": false,
        "registeredUser": false,
        "walletPrivateKey": "0x73ee170dc309c6f94d1c607d05a717a6c6504dd58295ff21ff68a0e5ae8eb841",
        "defaultCurrency": "USD",
        "language": "EN",
        "allowFaceRecognition": true,
        "roles": [
            "5de0302a58e530000de0dd2b"
        ],
        "needKYCVerification": false,
        "verified": false,
        "userWasUpdate": true,
        "trustLevel": 0,
        "isVirgin": true,
        "transactionCount": 0,
        "beneficiaries": [],
        "requestOTPCount": 0,
        "firstRequestOTPAt": null,
        "_id": "61c0da6a7623905113d7683e",
        "password": "xnV0XPrYWDkBSMgCBvpQAP5jqr11I2RpSgkeMc7L5m6R93GlLTuIIUwLIl7DyqC8ycGRHw9gzv403YkbJPPiMw==",
        "firstName": "Test",
        "lastName": "Test",
        "phone": "+5352552614",
        "birthDate": "2021-11-23T00:00:00.000Z",
        "identityNumber": "833688881",
        "houseNumber": "508",
        "street": "Main Street",
        "city": "DE",
        "zipcode": "19804",
        "country": "United States of America",
        "status": "To Verify",
        "email": "koroyel39@swsguide.com",
        "linkedProviders": [
            {
                "provider": "localEmail",
                "_id": "61c0da6a76239084bad7683f",
                "associatedValue": "koroyel39@swsguide.com"
            },
            {
                "provider": "localPhone",
                "_id": "61c0da6a7623905439d76843",
                "associatedValue": "+5352552614"
            }
        ],
        "twofAuthSecret": "GV6UI63EMEZG46ZYJIYCMQ3RJRRHM7JY",
        "activationCode": "162660",
        "walletAddress": "0xfC24A1C439a81BE9828e2e44899Df52386121D0D",
        "walletQRCode": "data:image/png;base64,iVBORw0KGgoA…kJggg==",
        "refreshTokenProviders": [
            {
                "_id": "61c0da7576239098c4d76848",
                "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6Ikp…FNY",
                "clientID": "c5b7eb67-3828-4029-ab03-0578bb5019ac"
            }
        ],
        "devices": [
            {
                "isBlocked": false,
                "lastLogin": "2021-12-20T15:58:34.343Z",
                "_id": "61c0da75762390aa31d76846",
                "createdAt": "2021-12-20T19:33:09.799Z",
                "updatedAt": "2021-12-20T19:33:09.799Z",
                "id": "61c0da75762390aa31d76846"
            }
        ],
        "metadata": [
            {
                "_id": "61c0da7576239043dbd76845",
                "id": "appVersion",
                "value": "1.65.0"
            }
        ],
        "settings": {
            "frequency": "instant",
            "_id": "61c0da6a76239079bad76840",
            "providers": [
                {
                    "_id": "61c0da6a76239000ccd76841",
                    "provider": "email",
                    "value": "koroyel39@swsguide.com",
                    "active": true
                },
                {
                    "_id": "61c0da6a7623908790d76842",
                    "provider": "sms",
                    "value": "+5352552614",
                    "active": true
                }
            ]
        },
        "privacyConfigurations": [
            {
                "key": "localization",
                "value": true
            }
        ],
        "verifications": [
            {
                "isActive": false,
                "wasChanged": true,
                "verificationId": "5ecb3db88e4629000d0963dc",
                "attachment": {
                    "name": "passportPicture",
                    "url": "someUrl",
                    "type": "mime/jpg",
                    "size": 50
                }
            },
            {
                "isActive": false,
                "wasChanged": true,
                "verificationId": "5ecb3db88e4629000d0963db",
                "attachment": {
                    "name": "passportPicture",
                    "url": "someUrl",
                    "type": "mime/jpg",
                    "size": 50
                }
            }
        ],
        "verificationComments": [],
        "linkedAttemptsValues": [],
        "reviews": [],
        "personalMargin": {
            "ADD_FUND": 0,
            "BANK_ACCOUNT_TRANSACTION": 0,
            "CREDIT_CARD_TRANSACTION": 0,
            "MLC_CREDIT_CARD_TRANSACTION": 0,
            "DELIVERY_TRANSACTION": 0,
            "DELIVERY_TRANSACTION_USD": 0,
            "THUNES_TRANSACTION": 0,
            "EMAIL_MONEY_TRANSACTION": 0,
            "EMAIL_PAYMENT_REQUEST": 0,
            "PAYMENT_REQUEST": 0,
            "P2P_TRANSFER": 0,
            "TOKENS_BUY": 0,
            "TOKENS_BUY_INLINE": 0,
            "TOKENS_BUY_MCP": 0,
            "TOKENS_BUY_CRYPTO": 0,
            "TOKENS_BUY_CRYPTO_INLINE": 0,
            "TOKENS_BUY_GPAY": 0,
            "TOKENS_BUY_GPAY_INLINE": 0,
            "TOKENS_BUY_APPLE_PAY": 0,
            "TOKENS_BUY_APPLE_PAY_INLINE": 0,
            "TOKEN_EXCHANGE": 0,
            "TOPUP_RECHARGE": 0
        },
        "payProvidersMeta": [],
        "availableServices": {
            "ADD_FUND": true,
            "BANK_ACCOUNT_TRANSACTION": true,
            "CREDIT_CARD_TRANSACTION": true,
            "MLC_CREDIT_CARD_TRANSACTION": true,
            "DELIVERY_TRANSACTION": true,
            "DELIVERY_TRANSACTION_USD": true,
            "THUNES_TRANSACTION": true,
            "EMAIL_MONEY_TRANSACTION": true,
            "EMAIL_PAYMENT_REQUEST": true,
            "PAYMENT_REQUEST": true,
            "P2P_TRANSFER": true,
            "TOKENS_BUY": true,
            "TOKENS_BUY_INLINE": true,
            "TOKENS_BUY_MCP": true,
            "TOKENS_BUY_CRYPTO": true,
            "TOKENS_BUY_CRYPTO_INLINE": true,
            "TOKENS_BUY_GPAY": true,
            "TOKENS_BUY_GPAY_INLINE": true,
            "TOKENS_BUY_APPLE_PAY": true,
            "TOKENS_BUY_APPLE_PAY_INLINE": true,
            "TOKEN_EXCHANGE": true,
            "TOPUP_RECHARGE": true
        },
        "createdAt": "2021-12-20T19:32:58.720Z",
        "updatedAt": "2021-12-20T19:33:12.360Z",
        "nameFull": "Test Test",
        "salt": "DkGwD0oNx+AJArM66D1BOw==",
        "__v": 1,
        "kyc": {
            "RecordStatus": "nomatch",
            "consultedAt": "2021-12-20T19:33:11.000Z",
            "transactionID": "331f64d3-75a9-46d8-933d-02d08db74621",
            "gatheredInfo": "{\"PersonInfo\":{\"FirstGivenName\":\"Test\",\"FirstSurName\":\"Test\",\"DayOfBirth\":24,\"MonthOfBirth\":11,\"YearOfBirth\":2021},\"Location\":{\"BuildingNumber\":\"508\",\"StreetName\":\"Main Street\",\"City\":\"DE\",\"StateProvinceCode\":\"Delaware\",\"PostalCode\":\"19804\"}}"
        },
        "fullNameShort": "Test T.",
        "fullNameLong": "Test Test",
        "score": 3,
        "id": "61c0da6a7623905113d7683e"
    }
}
```

### Request

POST `/api/private/users/verify`

Host: `backend.ducapp.net`

x-api-key: `<YOUR_API_KEY>`

Content-Type: `application/json`


### Request Body

| NAME             | TYPE   | DESCRIPTION                          |
| ---------------- | ------ | ------------------------------------ |
| `userID`         | string | Id of the user to be activated       |
| `activationCode` | string | Code send to the user phone or email |

### Response

| NAME            | TYPE    | DESCRIPTION                                     |
| --------------- | ------- | ----------------------------------------------- |
| `validatedUser` | boolean | Indicates if the user has been validated or not |
| `user`          | Object  | The user info                                   |

## Get countries

List all available countries.

```python
import requests

url = "https://backend.ducapp.net/api/private/transactions/cash-out/countries"

payload={}
headers = {
  'x-api-key': '<YOUR_API_KEY>',
  'authorization': 'Bearer <YOUR_ACCESS_TOKEN> '
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```


```shell
curl --location --request GET 'https://backend.ducapp.net/api/private/transactions/cash-out/countries' \
--header 'x-api-key: <YOUR_API_KEY>' \
--header 'authorization: Bearer <YOUR_ACCESS_TOKEN> '
```

```javascript
var myHeaders = new Headers();
myHeaders.append("x-api-key", "<YOUR_API_KEY>");
myHeaders.append("authorization", "Bearer <YOUR_ACCESS_TOKEN> ");

var urlencoded = new URLSearchParams();

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  body: urlencoded,
  redirect: 'follow'
};

fetch("https://backend.ducapp.net/api/private/transactions/cash-out/countries", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Example Response:

```json 
{
    "statusText": "OK",
    "status": 200,
    "data": [
        {
            "iso_code": "AND",
            "name": "Andorra"
        },
        {
            "iso_code": "AUT",
            "name": "Austria"
        }
    ],
    "pagination": {
        "totalPages": "1",
        "total": "44",
        "perPage": "50",
        "page": "1"
    }
}
```

### Request
GET `/api/private/transactions/cash-out/countries` 

Host: `backend.ducapp.net`

authorization: `Bearer <YOUR_ACCESS_TOKEN>`

x-api-key: `<YOUR_API_KEY>`

### Request Body

Empty

### Response

| NAME         | TYPE             | DESCRIPTION                                   |
| ------------ | ---------------- | --------------------------------------------- |
| `statusText` | string           | Text that indicates the status of the request |
| `status`     | number           | The request status code                       |
| `data`       | `array[Country]` | An array of counties object                   |

### Country

| NAME       | TYPE   | DESCRIPTION          |
| ---------- | ------ | -------------------- |
| `iso_code` | string | The country iso code |
| `name`     | string | The country name     |

## Get Services

List of available services by country

```javascript
var myHeaders = new Headers();
myHeaders.append("authorization", "Bearer <YOUR_ACCESS_TOKEN> ");
myHeaders.append("x-api-key", "<YOUR_API_KEY>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "country_iso_code": "MEX"
});

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://backend.ducapp.net/api/private/transactions/cash-out/services", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

```shell
curl --location --request GET 'https://backend.ducapp.net/api/private/transactions/cash-out/services' \
--header 'authorization: Bearer <YOUR_ACCESS_TOKEN> ' \
--header 'x-api-key: <YOUR_API_KEY>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "country_iso_code":"MEX"
}'
```

```python
import requests
import json

url = "https://backend.ducapp.net/api/private/transactions/cash-out/services"

payload = json.dumps({
  "country_iso_code": "MEX"
})
headers = {
  'authorization': 'Bearer <YOUR_ACCESS_TOKEN> ',
  'x-api-key': '<YOUR_API_KEY>',
  'Content-Type': 'application/json'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

> Example Response:

```json
{
    "statusText": "OK",
    "status": 200,
    "data": [
        {
            "id": 1,
            "name": "MobileWallet"
        },
        {
            "id": 2,
            "name": "BankAccount"
        },
        {
            "id": 3,
            "name": "CashPickup"
        }
    ],
    "pagination": {
        "totalPages": "1",
        "total": "3",
        "perPage": "50",
        "page": "1"
    }
}
```



### Request

GET `/api/private/transactions/cash-out/services`

Host: `backend.ducapp.net`

authorization: `Bearer <YOUR_ACCESS_TOKEN>`

x-api-key: `<YOUR_API_KEY>`

Content-Type: `application/json`

### Request Body

| NAME               | TYPE   | DESCRIPTION                                 |
| ------------------ | ------ | ------------------------------------------- |
| `country_iso_code` | string | The ISO code of the coutry to send money to |

### Response

| NAME         | TYPE             | DESCRIPTION                                   |
| ------------ | ---------------- | --------------------------------------------- |
| `statusText` | string           | Text that indicates the status of the request |
| `status`     | number           | The request status code                       |
| `data`       | `array[Service]` | An array of services object                   |

### Service

| NAME   | TYPE   | DESCRIPTION      |
| ------ | ------ | ---------------- |
| `id`   | string | The country id   |
| `name` | string | The service name |

## Get payers

List of available payers by country service.

```python
import requests
import json

url = "https://backend.ducapp.net/api/private/transactions/cash-out/payers"

payload = json.dumps({
  "service_id": 2,
  "country_iso_code": "AND"
})
headers = {
  'authorization': 'Bearer <YOUR_ACCESS_TOKEN>',
  'x-api-key': '<YOUR_API_KEY>',
  'Content-Type': 'application/json'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

```javascript
var myHeaders = new Headers();
myHeaders.append("authorization", "Bearer <YOUR_ACCESS_TOKEN>");
myHeaders.append("x-api-key", "<YOUR_API_KEY>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "service_id": 2,
  "country_iso_code": "AND"
});

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://backend.ducapp.net/api/private/transactions/cash-out/payers", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

```shell
curl --location --request GET 'https://backend.ducapp.net/api/private/transactions/cash-out/payers' \
--header 'authorization: Bearer <YOUR_ACCESS_TOKEN>' \
--header 'x-api-key: <YOUR_API_KEY>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "service_id": 2,
    "country_iso_code": "AND"
}
'
```

> Example Response:

```json
{
    "statusText": "OK",
    "status": 200,
    "data": [
        {
            "country_iso_code": "AND",
            "currency": "EUR",
            "id": 2838,
            "increment": 0.01,
            "name": "All Banks Andorra / EUR / Payment System: SEPA",
            "precision": 2,
            "service": {
                "id": 2,
                "name": "BankAccount"
            },
            "transaction_types": {
                "B2B": {
                    "maximum_transaction_amount": null,
                    "minimum_transaction_amount": "0.00000000",
                    "credit_party_identifiers_accepted": [
                        "iban"
                    ],
                    "required_documents": [],
                    "required_receiving_entity_fields": [
                        "registered_name",
                        "country_iso_code"
                    ],
                    "required_sending_entity_fields": [
                        "registered_name",
                        "country_iso_code"
                    ]
                }
            }
        }
    ],
    "pagination": {
        "totalPages": "1",
        "total": "1",
        "perPage": "50",
        "page": "1"
    }
}
```


### Request

GET `/api/private/transactions/cash-out/payers`

Host: `backend.ducapp.net`

authorization: `Bearer <YOUR_ACCESS_TOKEN>`

x-api-key: `<YOUR_API_KEY>`

Content-Type: `application/json`

### Request Body

| NAME               | TYPE   | DESCRIPTION                                   |
| ------------------ | ------ | --------------------------------------------- |
| `service_id`       | string | The Id of the service of the selected country |
| `country_iso_code` | string | The ISO code of the coutry to send money to   |

### Response

| NAME         | TYPE           | DESCRIPTION                                   |
| ------------ | -------------- | --------------------------------------------- |
| `statusText` | string         | Text that indicates the status of the request |
| `status`     | number         | The request status code                       |
| `data`       | `array[Payer]` | An array of payers object                     |

### Payer

| NAME                | TYPE                      | DESCRIPTION                                     |
| ------------------- | ------------------------- | ----------------------------------------------- |
| `id`                | string                    | The payer id                                    |
| `transaction_types` | `transaction type object` | The payes asociated transactions type (C2C\B2B) |
| `currency`          | string                    | The payer currency                              |

### transaction type object

| NAME                                | TYPE            | DESCRIPTION                               |
| ----------------------------------- | --------------- | ----------------------------------------- |
| `credit_party_identifiers_accepted` | `array[string]` | Dynamic field to be completed by the user |
| `required_receiving_entity_fields`  | `array[string]` | Dynamic field to be completed by the user |
| `required_sending_entity_fields`    | `array[string]` | Dynamic field to be completed by the user |


## Request Quotation

```python
import requests
import json

url = "https://backend.ducapp.net/api/private/transactions/cash-out/request-send"

payload = json.dumps({
  "payer_id": "2838",
  "destination": {
    "currency": "EUR",
    "amount": "111"
  },
  "quotationMode": "DESTINATION_AMOUNT",
  "transactionType": "B2B",
  "currency": "USD"
})
headers = {
  'authorization': 'Bearer <YOUR_ACCESS_TOKEN>',
  'x-api-key': '<YOUR_API_KEY>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request POST 'https://backend.ducapp.net/api/private/transactions/cash-out/request-send' \
--header 'authorization: Bearer <YOUR_ACCESS_TOKEN>' \
--header 'x-api-key: <YOUR_API_KEY>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "payer_id": "2838",
    "destination": {
        "currency": "EUR",
        "amount": "111"
    },
    "quotationMode": "DESTINATION_AMOUNT",
    "transactionType": "B2B",
    "currency": "USD"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("authorization", "Bearer <YOUR_ACCESS_TOKEN>");
myHeaders.append("x-api-key", "<YOUR_API_KEY>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "payer_id": "2838",
  "destination": {
    "currency": "EUR",
    "amount": "111"
  },
  "quotationMode": "DESTINATION_AMOUNT",
  "transactionType": "B2B",
  "currency": "USD"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://backend.ducapp.net/api/private/transactions/cash-out/request-send", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Example Response:

```json
{
    "data": {
        "creation_date": "2021-12-17T17:01:03Z",
        "destination": {
            "amount": 111,
            "currency": "EUR"
        },
        "expiration_date": "2021-12-17T18:01:03Z",
        "external_id": "AA00174887",
        "id": 15063344,
        "mode": "DESTINATION_AMOUNT",
        "payer": {
            "country_iso_code": "AND",
            "currency": "EUR",
            "id": 2838,
            "increment": 0.01,
            "name": "All Banks Andorra / EUR / Payment System: SEPA",
            "precision": 2,
            "service": {
                "id": 2,
                "name": "BankAccount"
            },
            "transaction_types": {
                "B2B": {
                    "maximum_transaction_amount": null,
                    "minimum_transaction_amount": 0,
                    "credit_party_identifiers_accepted": [
                        "iban",
                        "swift_bic_code"
                    ],
                    "required_documents": [],
                    "required_receiving_entity_fields": [
                        "registered_name",
                        "country_iso_code"
                    ],
                    "required_sending_entity_fields": [
                        "registered_name",
                        "country_iso_code"
                    ]
                }
            }
        },
        "sent_amount": {
            "amount": 111,
            "currency": "EUR"
        },
        "source": {
            "amount": 111,
            "country_iso_code": "USA",
            "currency": "EUR"
        },
        "transaction_type": "B2B",
        "fee": {
            "currency": "USD",
            "amount": 0
        },
        "wholesale_fx_rate": 0.8482,
        "feeTotal": {
            "currency": "USD",
            "amount": 0
        }
    }
}
```


### Request

POST `/api/private/transactions/cash-out/request-send`

Host: `backend.ducapp.net`

authorization: `Bearer <YOUR_ACCESS_TOKEN>`

x-api-key: `<YOUR_API_KEY>`

Content-Type: `application/json`

### Request Body

| NAME              | TYPE     | DESCRIPTION                                                        |
| ----------------- | -------- | ------------------------------------------------------------------ |
| `payer_id`        | string   | The Id of the payer of the selected service                        |
| `destination`     | `object` | Destination Info                                                   |
| `quotationMode`   | string   |                                                                    |
| `transactionType` | string   | The type of transaction selected from those available by the payet |
| `currency`        | string   | Currency of the sending user                                       |

### Response

| NAME              | TYPE                      | DESCRIPTION                                     |
| ----------------- | ------------------------- | ----------------------------------------------- |
| `id`              | string                    | The id of the quotation                         |
| `external_id`     | number                    | The external id                                 |
| `payer`           | `object`                  | The external id                                 |
| `fee`             | `object`                  | An object with the fee info                     |
| `transactionType` | `transaction type object` | The payes asociated transactions type (C2C\B2B) |

### payer

| NAME              | TYPE                      | DESCRIPTION                                     |
| ----------------- | ------------------------- | ----------------------------------------------- |
| `transactionType` | `transaction type object` | The payes asociated transactions type (C2C\B2B) |

### transaction type object

| NAME                                | TYPE          | DESCRIPTION                               |
| ----------------------------------- | ------------- | ----------------------------------------- |
| `credit_party_identifiers_accepted` | array[string] | Dynamic field to be completed by the user |
| `required_receiving_entity_fields`  | array[string] | Dynamic field to be completed by the user |
| `required_sending_entity_fields`    | array[string] | Dynamic field to be completed by the user |

### fee

| NAME       | TYPE   | DESCRIPTION      |
| ---------- | ------ | ---------------- |
| `amount`   | string | The fee amount   |
| `currency` | string | The fee currency |



## Confirm Quotation


```javascript
var myHeaders = new Headers();
myHeaders.append("x-api-key", "<YOUR_API_KEY>");
myHeaders.append("authorization", "Bearer <YOUR_ACCESS_TOKEN>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "quotation_id": "15171738",
  "external_id": "AA00174904",
  "credit_party_identifier": {
    "iban": "AL47 2121 1009 0000 0002 3569 8741",
    "swift_bic_code": "BINAADADXXX"
  },
  "sender": {},
  "beneficiary": {},
  "sending_business": {
    "registered_name": "Test",
    "country_iso_code": "AND"
  },
  "receiving_business": {
    "registered_name": "Test",
    "country_iso_code": "AND"
  },
  "totalAmount": "135",
  "currency": "USD",
  "country_iso_code": "AND",
  "service_id": "2",
  "payer_id": "",
  "external_fee": 0,
  "amount": 135,
  "location": {
    "latitude": "-76.25804853625596",
    "longitude": "20.888864980079234",
    "timestamp": "1635185398"
  },
  "creditCardNumber": "4242424242424242",
  "creditCardHolderName": "Hablax Test",
  "expiryDate": "05/22",
  "cvc": "123",
  "avs_street_name": "Main Street",
  "avs_street_number": "508",
  "avs_zipcode": "19804",
  "iso_code": "840",
  "cardCurrency": "USD",
  "currencyCountry": "US",
  "currencyCountryName": "United States"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://backend.ducapp.net/api/private/transactions/cash-out/confirm-send", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

```python 
import requests
import json

url = "https://backend.ducapp.net/api/private/transactions/cash-out/confirm-send"

payload = json.dumps({
  "quotation_id": "15171738",
  "external_id": "AA00174904",
  "credit_party_identifier": {
    "iban": "AL47 2121 1009 0000 0002 3569 8741",
    "swift_bic_code": "BINAADADXXX"
  },
  "sender": {},
  "beneficiary": {},
  "sending_business": {
    "registered_name": "Test",
    "country_iso_code": "AND"
  },
  "receiving_business": {
    "registered_name": "Test",
    "country_iso_code": "AND"
  },
  "totalAmount": "135",
  "currency": "USD",
  "country_iso_code": "AND",
  "service_id": "2",
  "payer_id": "",
  "external_fee": 0,
  "amount": 135,
  "location": {
    "latitude": "-76.25804853625596",
    "longitude": "20.888864980079234",
    "timestamp": "1635185398"
  },
  "creditCardNumber": "4242424242424242",
  "creditCardHolderName": "Hablax Test",
  "expiryDate": "05/22",
  "cvc": "123",
  "avs_street_name": "Main Street",
  "avs_street_number": "508",
  "avs_zipcode": "19804",
  "iso_code": "840",
  "cardCurrency": "USD",
  "currencyCountry": "US",
  "currencyCountryName": "United States"
})
headers = {
  'x-api-key': '<YOUR_API_KEY>',
  'authorization': 'Bearer <YOUR_ACCESS_TOKEN>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request POST 'https://backend.ducapp.net/api/private/transactions/cash-out/confirm-send' \
--header 'x-api-key: <YOUR_API_KEY>' \
--header 'authorization: Bearer <YOUR_ACCESS_TOKEN>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "quotation_id": "15171738",
    "external_id": "AA00174904",
    "credit_party_identifier": {
        "iban": "AL47 2121 1009 0000 0002 3569 8741",
        "swift_bic_code": "BINAADADXXX"
    },
    "sender": {},
    "beneficiary": {},
    "sending_business": {
        "registered_name": "Test",
        "country_iso_code": "AND"
    },
    "receiving_business": {
        "registered_name": "Test",
        "country_iso_code": "AND"
    },
    "totalAmount": "135",
    "currency": "USD",
    "country_iso_code": "AND",
    "service_id": "2",
    "payer_id": "",
    "external_fee": 0,
    "amount": 135,
    "location": {
        "latitude": "-76.25804853625596",
        "longitude": "20.888864980079234",
        "timestamp": "1635185398"
    },
    "creditCardNumber": "4242424242424242",
    "creditCardHolderName": "Hablax Test",
    "expiryDate": "05/22",
    "cvc": "123",
    "avs_street_name": "Main Street",
    "avs_street_number": "508",
    "avs_zipcode": "19804",
    "iso_code": "840",
    "cardCurrency": "USD",
    "currencyCountry": "US",
    "currencyCountryName": "United States"
}'
```

> Example Response:

```json
{
    "data": {
        "transactionAmount": 135,
        "transactionStatus": "queued",
        "currency": "USD",
        "type": "CASH_OUT_TRANSACTION",
        "images": [],
        "balanceSender": 0,
        "balanceReceiver": 0,
        "_id": "61c0e32d7623907918d768bf",
        "sender": "0xd953993D0990bdedd2BC2e5dE5D57c23A2E326d0",
        "receiver": "0x946ec5B0fC2B78adaC1fC39DC2eE682ddFc3913E",
        "owner": "619d4d42050e29215602d34c",
        "transactionID": "AA00174904",
        "createdAt": "2021-12-20T20:10:21.282Z",
        "updatedAt": "2021-12-20T20:10:21.282Z",
        "__v": 0,
        "id": "61c0e32d7623907918d768bf"
    }
}
```

### Request

POST `/api/private/transactions/cash-out/confirm-send`

Host: `backend.ducapp.net`

authorization: `Bearer <YOUR_ACCESS_TOKEN>`

x-api-key: `<YOUR_API_KEY>`

Content-Type: `application/json`

### Request Body

| NAME                      | TYPE     | DESCRIPTION                                                                  |
| ------------------------- | -------- | ---------------------------------------------------------------------------- |
| `quotation_id`            | string   | The id of the requested quotation                                            |
| `external_id`             | object   | The external id of the requested quotation                                   |
| `credit_party_identifier` | string   | Dynamic fields to be completed by the user                                   |
| `sender`                  | string   | Dynamic fields to be completed by the user (Only for C2C transactions type)  |
| `beneficiary`             | string   | Dynamic fields to be completed by the user (Only for C2C transactions type)  |
| `sending_business`        | string   | Dynamic fields to be completed by the user (Only for B2B transactions type)  |
| `receiving_business`      | string   | Dynamic fields to be completed by the user (Only for B2B transactions type)  |
| `totalAmount`             | string   | The total amount to be paid by the user with the fee included                |
| `currency`                | string   | The user's currency                                                          |
| `country_iso_code`        | string   | The ISO code of the coutry to send money to                                  |
| `service_id`              | string   | The Id of the service of the selected country                                |
| `payer_id`                | string   | The Id of the payer of the selected service                                  |
| `external_fee`            | string   | The fee.amount field of the response from the previous request               |
| `amount`                  | string   | The amount entered by the user                                               |
| `location`                | `object` | Information on the users GPS location at the time of the transaction         |
| `creditCardNumber`        | string   | Information for payment, credit card number                                  |
| `creditCardHolderName`    | string   | Information for payment, name that appears on the credit card                |
| `expiryDate`              | string   | Information for payment, expiration date                                     |
| `cvc`                     | string   | Information for payment, cvc                                                 |
| `avs_street_name`         | string   | Information for payment, street name                                         |
| `avs_street_number`       | string   | Information for payment, residence number                                    |
| `avs_zipcode`             | string   | Information for payment, zip code                                            |
| `iso_code`                | string   | Information for payment, card currency                                       |
| `cardCurrency`            | string   | Currency of the sending user                                                 |
| `currencyCountry`         | string   | Information for payment, country code of the cards currency                  |
| `currencyCountryName`     | string   | Information for the payment, name of the country of the currency of the card |

### location

| NAME        | TYPE   | DESCRIPTION |
| ----------- | ------ | ----------- |
| `latitude`  | string | Latitude    |
| `longitude` | string | Longitude   |
| `timestamp` | string | Timestamp   |

### Response

| NAME                | TYPE   | DESCRIPTION                   |
| ------------------- | ------ | ----------------------------- |
| `transactionStatus` | string | The status of the transaction |
| `transactionID`     | string | The id of the transaction     |



## Dynamic Payment

```python
import requests
import json

url = "https://backend.ducapp.net/api/private/payments/order"

payload = json.dumps({
  "merchantId": "Merchant-c22681FE77",
  "externalID": "Ext-1643392247983",
  "toWalletAddress": "0x0F673BAF2C67eb6165CC526df5386032d653fbB5",
  "amount": 50,
  "currency": "EUR",
  "expiryTime": {
    "amount": 24,
    "unit": "hours"
  },
  "description": "Some Description"
})
headers = {
  'authorization': 'Bearer <YOUR_ACCESS_TOKEN>',
  'x-api-key': '<YOUR_API_KEY>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request POST 'https://backend.ducapp.net/api/private/payments/order' \
--header 'authorization: Bearer <YOUR_ACCESS_TOKEN>' \
--header 'x-api-key: <YOUR_API_KEY>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "merchantId": "Merchant-c22681FE77",
    "externalID": "Ext-1643392247983",
    "toWalletAddress": "0x0F673BAF2C67eb6165CC526df5386032d653fbB5",
    "amount": 50,
    "currency": "EUR",
    "expiryTime": {
        "amount": 24,
        "unit": "hours"
    },
    "description": "Some Description"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("authorization", "Bearer <YOUR_ACCESS_TOKEN>");
myHeaders.append("x-api-key", "<YOUR_API_KEY>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "merchantId": "Merchant-c22681FE77",
  "externalID": "Ext-1643392247983",
  "toWalletAddress": "0x0F673BAF2C67eb6165CC526df5386032d653fbB5",
  "amount": 50,
  "currency": "EUR",
  "expiryTime": {
    "amount": 24,
    "unit": "hours"
  },
  "description": "Some Description"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://backend.ducapp.net/api/private/payments/order", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Example Response:

```json
{
    "expiryTime": {
        "amount": 24,
        "unit": "hours"
    },
    "status": "pending",
    "_id": "61fbe1309cd18d1d35320d77",
    "merchantId": "Merchant-c22681FE67",
    "externalID": "Ext-1643392247925",
    "toWalletAddress": "0xb36812b78b520A73086A5Fe275Fb704C7eC53066",
    "amount": 50,
    "currency": "EUR",
    "description": "Some Description",
    "callbackUrl": "https://somecallbackurl.com",
    "createdAt": "2022-02-03T14:05:36.728Z",
    "updatedAt": "2022-02-03T14:05:36.918Z",
    "orderId": "OI0000000021",
    "__v": 0,
    "qrCode": "data:image/png;base64,iVBORw0KGgoAAAANSU…svUQb9AIAAAAASUVORK5CYII=",
    "dynamicLink": "https://ducwallet.page.link/payment/50/EUR/Generic_payment_order/Ext-1643392247925/OI0000000021/0xb36812b78b520A73086A5Fe275Fb704C7eC53066/DYNAMIC_PAYMENT",
    "expiresAt": "2022-02-04T14:05:36.728Z",
    "id": "61fbe1309cd18d1d35320d77"
}
```

### Request

POST `/api/private/payments/order`

Host: `backend.ducapp.net`

authorization: `Bearer <YOUR_ACCESS_TOKEN>`

x-api-key: `<YOUR_API_KEY>`

Content-Type: `application/json`

### Request Body



### Response

## Transaction Status

## Get Order Details

```javascript
var myHeaders = new Headers();
myHeaders.append("x-api-key", "<YOUR_API_KEY>");
myHeaders.append("authorization", "Bearer <YOUR_ACCESS_TOKEN>");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://backend.ducapp.net/api/private/payments/order/{order_id}", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

```python
import requests

url = "https://backend.ducapp.net/api/private/payments/order/{order_id}"

payload={}
headers = {
  'x-api-key': '<YOUR_API_KEY>',
  'authorization': 'Bearer <YOUR_ACCESS_TOKEN>'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location -g --request GET 'https://backend.ducapp.net/api/private/payments/order/{order_id}' \
--header 'x-api-key: <YOUR_API_KEY>' \
--header 'authorization: Bearer <YOUR_ACCESS_TOKEN>'
```


> Example Response;

```json
{
    "expiryTime": {
        "amount": 24,
        "unit": "hours"
    },
    "status": "pending",
    "_id": "61fbe1309cd18d1d35320d77",
    "merchantId": "Merchant-c22681FE67",
    "externalID": "Ext-1643392247925",
    "toWalletAddress": "0xb36812b78b520A73086A5Fe275Fb704C7eC53066",
    "amount": 50,
    "currency": "EUR",
    "description": "",
   "callbackUrl": "https://somecallbackurl.com",
    "createdAt": "2022-02-03T14:05:36.728Z",
    "updatedAt": "2022-02-03T14:05:36.918Z",
    "orderId": "OI0000000021",
    "__v": 0,
    "dynamicLink": "https://ducwallet.page.link/payment/50/EUR/Generic_payment_order/Ext-1643392247925/OI0000000021/0xb36812b78b520A73086A5Fe275Fb704C7eC53066/DYNAMIC_PAYMENT",
    "qrCode": "data:image/png;base64,iVBORw0KGgoAAAAN…AAAAASUVORK5CYII=",
    "expiresAt": "2022-02-04T14:05:36.728Z",
    "id": "61fbe1309cd18d1d35320d77"
}
```

### Request

GET `/api/private/payments/order/{order_id}`

Host: `backend.ducapp.net`

authorization: `Bearer <YOUR_ACCESS_TOKEN>`

x-api-key: `<YOUR_API_KEY>`

### Request Body

Empty, but the order_id is required. Eg. `/api/private/payments/order/OI0000000021`

### Response



## Get Exchange Rates

GET `/api/public/rates?base={currency}`

Host: `backend.ducapp.net`

authorization: `Bearer <YOUR_ACCESS_TOKEN>`

x-api-key: `<YOUR_API_KEY>`

