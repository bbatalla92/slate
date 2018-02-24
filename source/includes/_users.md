# Users

## Create User
```javascript
"POST api/v1/users/"
```
```json
{
        "id": "jLApbXN2ItRFa72jSXZJ21uFt",
        "last_name": "Bat",
        "gender": "male",
        "email": "bren@gmail.com",
        "email_verified": true,
        "phone_number": "( 609 ) 567 - 4650",
        "phone_verified": true,
        "birth_date": "720594000000",
        "bio": "I am the real user",
        "lat": 39.941209,
        "lng": -75.1664449,
        "first_name": "Bren",
        "city": "Philadelphia",
        "country": "US",
        "state": "PA",
        "street": "1622 South St",
        "zipcode": "19146",
        "image": "https://res.cloudinary.com/hko0mswnc/image/upload/q_auto/f_auto/v1514494289/jLApbXN2ItRFa72jSXZJ21uFtwm1.png"
}
```

> The above request with the specified body will return json as below:

```json
{
    
    "status": {
    "message": "Success",
    "success": true
    },
    "content": {
        "id": "jLApbXN2ItRFa72jSXZJ21uFt",
        "last_name": "Bat",
        "gender": "male",
        "email": "bren@gmail.com",
        "email_verified": true,
        "phone_number": "( 609 ) 567 - 4650",
        "phone_verified": true,
        "lender": false,
        "birth_date": "720594000000",
        "bio": "I am the real user",
        "lat": 39.941209,
        "lng": -75.1664449,
        "stripe_customer_id": "cus_2F3G4SI5f1AoG7",
        "stripe_account_id": "cus_2F3G4SI5f1AoG7",
        "first_name": "Bren",
        "city": "Philadelphia",
        "country": "US",
        "state": "PA",
        "street": "1622 South St",
        "zipcode": "19146",
        "rating": null,
        "last_initial": "B",
        "created": "2017-12-29T01:05:20.304Z",
        "total_reviews": null,
        "image": "https://res.cloudinary.com/hko0mswnc/image/upload/q_auto/f_auto/v1514494289/jLApbXN2ItRFa72jSXZJ21uFtwm1.png",
        "disabled": false
    }
}
```

This endpoint will create a new user in the database
### HTTP Request

`POST /api/v1/users`

### User Public or Private Parameters

Parameter | Required | Type     | Description | Public
--------- | -------  | ------- | ------- | ------- 
id  | TRUE | String | Unique Id that firebase generates for each new user. | TRUE
first_name | TRUE | String | First name of user | TRUE
last_name| TRUE | String | Last Name of User | FALSE
email| TRUE | String | Email of user  | FALSE
phone_number| FALSE | String | Phone number of user | FALSE
birth_date | FALSE | Number (EPOCH) | Date of birth of user, Min age: 18 | FALSE
street | FALSE | String | street address of user | FALSE
email_verified | FALSE | Boolean | Has user confirmed their email by recieving the email lendet send them. | TRUE
phone_verified | FALSE | String | Has the user input the verification code that lendet sent them | TRUE
lender | FALSE | Boolean | Is the user renting out items | TRUE
bio | FALSE | String | Description the user wants every to know about them | TRUE
lat | FALSE | Number | Latitude of the users home address | FALSE
lng | FALSE | Number | Longitude of the users home address | FALSE
stripe_customer_id | FALSE | String | Stripe customer Id of user, **AUTO GENERATED**, Allows cards to be charged (for renters) | FALSE
stripe_account_id | FALSE | String | Stripe Id of user, **AUTO GENERATED**, Allows money to be deposited into bank account (for lenders) | FALSE
city | FALSE | String | Home city of user  | TRUE
country | FALSE | String| Home country of user | TRUE
state | FALSE | String | Home state of user (US ONLY) | FALSE
zipcode | FALSE | String | Postal code of user | FALSE
rating| FALSE | Number | Rating of the user made by other people. Calculated on new reviews | TRUE 
last_initial | FALSE | String | Initial of last name. **AUTO GENERATED** | TRUE
created | FALSE | String | Date when user signed up.  **AUTO GENERATED** | TRUE
total_reviews | FALSE | Number | Total number of reviews the user has gotten | TRUE
image | FALSE | String/Blob/Base 64 Encoding | Users Image | TRUE
disabled | FALSE | Boolean | Is the users account disabled | FALSE
gender | FALSE | Boolean | Gender of user | FALSE
connected_bank | FALSE | String | Stripe Account Id of lenders account | FALSE

## Get User
```javascript
"GET api/v1/users/jLApbXN2ItRFa72jSXZJ21uFt"
```

> The above request with the token containing same id,
 returns JSON structured like this:

```json
{
    "status": {
        "message": "Success",
        "success": true
        },
    "content": {
        "id": "jLApbXN2ItRFa72jSXZJ21uFt",
        "last_name": "Bat",
        "gender": "male",
        "email": "bren@gmail.com",
        "email_verified": true,
        "phone_number": "( 609 ) 567 - 4650",
        "phone_verified": true,
        "lender": true,
        "birth_date": "720594000000",
        "bio": "I am the real user",
        "lat": 39.941209,
        "lng": -75.1664449,
        "stripe_customer_id": "cus_2F3G4SI5f1AoG7",
        "stripe_account_id": "cus_2F3G4SI5f1AoG7",
        "first_name": "Bren",
        "city": "Philadelphia",
        "country": "US",
        "state": "PA",
        "street": "1622 South St",
        "zipcode": "19146",
        "rating": 3,
        "last_initial": "B",
        "created": "2017-12-29T01:05:20.304Z",
        "total_reviews": 0,
        "image": "https://res.cloudinary.com/hko0mswnc/image/upload/q_auto/f_auto/v1514494289/jLApbXN2ItRFa72jSXZJ21uFtwm1.png",
        "disabled": false,
        "connected_bank":"b_34jkhj343khb3j"
    }
}
```


> If no user is found, the follow json will be returned:

```json
{
    "message": "No User Found",
    "success": false
}
```

This endpoint retrieves a single user.  If the id in the path is the same id in the JWT token, the api will get you all
 information related to a user, if they do not match, only the publicly available data will be retrieved. 
 

### HTTP Request

`GET /api/v1/users/:id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | TRUE | The id of the user being retrieved.

### User Public ONLY Parameters

Parameters | . | . 
--------- | ------- | -------
id  | first_name | image
email_verified | phone_verified | lender
bio | lat | lng
city | country | total_reviews 
state | zipcode | rating
last_initial | created 

## Update User

This endpoint updates a specific user.  Because it is a **PUT**, the properties that 
are passed in will override the current values.  If the property is not put in, it will be
replaced by *null*.  

### HTTP Request

`PUT api/v1/users/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the User to be updated

## Delete a USER

```javascript
"DELETE api/v1/users/:id"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific user.  Only the owner of the account or an 
Administrator has the ability to delete a user.  This is determined by the id in the token.
Upon initial **DELETE** the account will not be deleted, but instead disabled.
*Not yet Implemented*
### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to be deleted

## Convert user to Lender

```javascript
"POST api/v1/users/stripe/account"
```

> The above command returns JSON structured like this:

```json
{
  "ssn_last_four" : "1234"
}
```

This endpoint turns a normal renting user into a lender.  Requires last four digits of users social security.  Endpoint will 
generates a stripe account id.
### HTTP Request

`POST api/v1/users/stripe/account`

### URL Parameters

Parameter | Description
--------- | -----------
ssn_last_four | Users last four digits of their social security number

## Add bank account to lenders account

```javascript
"POST api/v1/users/stripe/bankAccount"

```

```json

{
  "account_number" : "000123456789",
  "routing_number": "110000000"
}

```

> The above command returns JSON structured like this:

```json
{
    "content": "<USER Object>",
    "status": {
        "success": true,
        "message": "Success"
    }
}
```

This endpoint attaches a **checking bank account** to a lenders account.  
### HTTP Request

`POST api/v1/users/stripe/bankAccount`

### Request Parameters

Parameter | Description
--------- | -----------
account_number | Checking account number
routing_number | Checking account routing number

## Get bank account attached to lenders account

```javascript
"GET api/v1/users/stripe/bankAccount"
```

> The above command returns JSON structured like this:

```json
{
    "content": {
        "bank_name": "STRIPE TEST BANK",
        "account_number_last_4": "6789",
        "routing_number": "110000000"
    },
    "status": {
        "success": true,
        "message": "Success"
    }
}
```

This endpoint retrieves an attached **checking bank account** of a lenders account.  
### HTTP Request

`GET api/v1/users/stripe/bankAccount`
