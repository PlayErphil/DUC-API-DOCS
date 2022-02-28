# Resources

This describes API endpoints fetching via HTTPS calls.


## private/users/register

### Request

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

| NAME             | TYPE    | DESCRIPTION                                     |
| ---------------- | ------- | ----------------------------------------------- |
| `validatedUser`  | boolean | Indicates if the user has been validated or not |
| `activationCode` | string  | Code send to the user to validate the account   |
| `user`           | Object  | The user info                                   |
| `accessToken`    | string  | Token to access authenticated endpoints         |

## private/users/verify

### Request

| NAME             | TYPE   | DESCRIPTION                          |
| ---------------- | ------ | ------------------------------------ |
| `userID`         | string | Id of the user to be activated       |
| `activationCode` | string | Code send to the user phone or email |

### Response

| NAME            | TYPE    | DESCRIPTION                                     |
| --------------- | ------- | ----------------------------------------------- |
| `validatedUser` | boolean | Indicates if the user has been validated or not |
| `user`          | Object  | The user info                                   |

## auth/login

### Request

| NAME       | TYPE   | DESCRIPTION                  |
| ---------- | ------ | ---------------------------- |
| `phone`    | string | Registered User phone number |
| `password` | string | Registered User password     |

### Response

| NAME          | TYPE    | DESCRIPTION                             |
| ------------- | ------- | --------------------------------------- |
| `accessToken` | boolean | Token to access authenticated endpoints |

## private/transactions/cash-out/countries

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

## private/transactions/cash-out/services

### Request

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




## private/transactions/cash-out/services

### Request

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



## private/transactions/cash-out/request-send

### Request

| NAME              | TYPE     | DESCRIPTION                                                        |
| ----------------- | -------- | ------------------------------------------------------------------ |
| `payer_id`        | string   | The Id of the payer of the selected service                        |
| `destination`     | `object` | Destination Info                                                   |
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


## private/transactions/cash-out/confirm-send

### Request

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

## private/transactions/{id}

### Response

| NAME                | TYPE   | DESCRIPTION                   |
| ------------------- | ------ | ----------------------------- |
| `transactionStatus` | string | The status of the transaction |
| `transactionID`     | string | The id of the transaction     |


## private/transactions

### Path

| NAME    | TYPE   | DESCRIPTION            |
| ------- | ------ | ---------------------- |
| `skip`  | number | The pagination offset  |
| `limit` | number | The the amount of rows |

### Response

| NAME                | TYPE   | DESCRIPTION                   |
| ------------------- | ------ | ----------------------------- |
| `transactionStatus` | string | The status of the transaction |
| `transactionID`     | string | The id of the transaction     |


## private/transactions/token/p2p

### Request

| NAME                   | TYPE     | DESCRIPTION                                                                  |
| ---------------------- | -------- | ---------------------------------------------------------------------------- |
| `toAddress`            | string   | The receiver wallet address                                                  |
| `amount`               | number   | The the amount to send                                                       |
| `currency`             | string   | The the currency of the user                                                 |
| `concept`              | string   | A brief description                                                          |
| `location`             | `object` | Information on the users GPS location at the time of the transaction         |
| `creditCardNumber`     | string   | Information for payment, credit card number                                  |
| `creditCardHolderName` | string   | Information for payment, name that appears on the credit card                |
| `expiryDate`           | string   | Information for payment, expiration date                                     |
| `cvc`                  | string   | Information for payment, cvc                                                 |
| `avs_street_name`      | string   | Information for payment, street name                                         |
| `avs_street_number`    | string   | Information for payment, residence number                                    |
| `avs_zipcode`          | string   | Information for payment, zip code                                            |
| `iso_code`             | string   | Information for payment, card currency                                       |
| `cardCurrency`         | string   | Currency of the sending user                                                 |
| `currencyCountry`      | string   | Information for payment, country code of the cards currency                  |
| `currencyCountryName`  | string   | Information for the payment, name of the country of the currency of the card |

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

## private/transactions/cash-out/email

### Request

| NAME                   | TYPE     | DESCRIPTION                                                                  |
| ---------------------- | -------- | ---------------------------------------------------------------------------- |
| `email`                | string   | The destination email                                                        |
| `amount`               | number   | The the amount to send                                                       |
| `currency`             | string   | The the currency of the user                                                 |
| `concept`              | string   | A brief description                                                          |
| `location`             | `object` | Information on the users GPS location at the time of the transaction         |
| `creditCardNumber`     | string   | Information for payment, credit card number                                  |
| `creditCardHolderName` | string   | Information for payment, name that appears on the credit card                |
| `expiryDate`           | string   | Information for payment, expiration date                                     |
| `cvc`                  | string   | Information for payment, cvc                                                 |
| `avs_street_name`      | string   | Information for payment, street name                                         |
| `avs_street_number`    | string   | Information for payment, residence number                                    |
| `avs_zipcode`          | string   | Information for payment, zip code                                            |
| `iso_code`             | string   | Information for payment, card currency                                       |
| `cardCurrency`         | string   | Currency of the sending user                                                 |
| `currencyCountry`      | string   | Information for payment, country code of the cards currency                  |
| `currencyCountryName`  | string   | Information for the payment, name of the country of the currency of the card |

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




## private/transactions/cash-out/creditcard

### Request

| NAME                   | TYPE     | DESCRIPTION                                                                  |
| ---------------------- | -------- | ---------------------------------------------------------------------------- |
| `service`              | string   | The service identifier (cardUSD, cardCUP)                                    |
| `amount`               | number   | The the amount to send                                                       |
| `currency`             | string   | The the currency of the user                                                 |
| `concept`              | string   | A brief description                                                          |
| `cardNumber`           | string   | The beneficiarys card number                                                 |
| `cardHolderName`       | string   | The beneficiarys card name                                                   |
| `bankName`             | string   | The beneficiarys bank name                                                   |
| `contactPhone`         | string   | The beneficiarys phone number                                                |
| `deliveryCurrency`     | string   | The beneficiarys card currency                                               |
| `deliveryCountry`      | string   | The beneficiarys country                                                     |
| `deliveryAmount`       | string   | The amount to receive by the beneficiary                                     |
| `deliveryCountryCode`  | string   | The beneficiarys alpha2 country iso code                                     |
| `location`             | `object` | Information on the users GPS location at the time of the transaction         |
| `creditCardNumber`     | string   | Information for payment, credit card number                                  |
| `creditCardHolderName` | string   | Information for payment, name that appears on the credit card                |
| `expiryDate`           | string   | Information for payment, expiration date                                     |
| `cvc`                  | string   | Information for payment, cvc                                                 |
| `avs_street_name`      | string   | Information for payment, street name                                         |
| `avs_street_number`    | string   | Information for payment, residence number                                    |
| `avs_zipcode`          | string   | Information for payment, zip code                                            |
| `iso_code`             | string   | Information for payment, card currency                                       |
| `cardCurrency`         | string   | Currency of the sending user                                                 |
| `currencyCountry`      | string   | Information for payment, country code of the cards currency                  |
| `currencyCountryName`  | string   | Information for the payment, name of the country of the currency of the card |


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


## private/transactions/cash-out/delivery

### Request

| NAME                     | TYPE     | DESCRIPTION                                                                  |
| ------------------------ | -------- | ---------------------------------------------------------------------------- |
| `service`                | string   | The service identifier (deliveryUSD, deliveryCUP)                            |
| `amount`                 | number   | The the amount to send                                                       |
| `currency`               | string   | The the currency of the user                                                 |
| `concept`                | string   | A brief description                                                          |
| `deliveryAddress`        | string   | The beneficiarys address                                                     |
| `deliveryFirstName`      | string   | The beneficiarys first name                                                  |
| `deliveryID`             | string   | The beneficiarys identification number                                       |
| `deliveryPhone`          | string   | The beneficiarys phone number                                                |
| `deliveryCurrency`       | string   | The beneficiarys currency                                                    |
| `deliveryCountry`        | string   | The beneficiarys country                                                     |
| `deliveryAmount`         | string   | The amount to receive by the beneficiary                                     |
| `deliveryArea`           | string   | The beneficiarys province                                                    |
| `deliveryLastName`       | string   | The beneficiarys lastname                                                    |
| `deliverySecondLastName` | string   | The beneficiarys second lastname                                             |
| `deliveryCountryCode`    | string   | The beneficiarys alpha2 country iso code                                     |
| `location`               | `object` | Information on the users GPS location at the time of the transaction         |
| `creditCardNumber`       | string   | Information for payment, credit card number                                  |
| `creditCardHolderName`   | string   | Information for payment, name that appears on the credit card                |
| `expiryDate`             | string   | Information for payment, expiration date                                     |
| `cvc`                    | string   | Information for payment, cvc                                                 |
| `avs_street_name`        | string   | Information for payment, street name                                         |
| `avs_street_number`      | string   | Information for payment, residence number                                    |
| `avs_zipcode`            | string   | Information for payment, zip code                                            |
| `iso_code`               | string   | Information for payment, card currency                                       |
| `cardCurrency`           | string   | Currency of the sending user                                                 |
| `currencyCountry`        | string   | Information for payment, country code of the cards currency                  |
| `currencyCountryName`    | string   | Information for the payment, name of the country of the currency of the card |


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