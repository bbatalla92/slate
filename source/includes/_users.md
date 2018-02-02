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
    "message": "Success",
    "status": "Success",
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
        "stripe_id": "cus_2F3G4SI5f1AoG7",
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

Parameter | Required | Type     | Description
--------- | -------  | ------- | ------- 
id  | TRUE | String | Unique Id that firebase generates for each new user.
first_name | TRUE | String | First name of user
last_name| TRUE | String | Last Name of User
email| TRUE | String | Email of user 
phone_number| FALSE | String | Phone number of user
birth_date | FALSE | Number (EPOCH) | Date of birth of user, Min age: 18
street | FALSE | String | street address of user
email_verified | FALSE | Boolean | Has user confirmed their email by recieving the email lendet send them.
phone_verified | FALSE | String | Has the user input the verification code that lendet sent them
lender | FALSE | Boolean | Is the user renting out items
bio | FALSE | String | Description the user wants every to know about them
lat | FALSE | Number | Latitude of the users home address
lng | FALSE | Number | Longitude of the users home address
stripe_id | FALSE | String | Stripe Id of user, **AUTO GENERATED**
city | FALSE | String | Home city of user 
country | FALSE | String| Home country of user
state | FALSE | String | Home state of user (US ONLY)
zipcode | FALSE | String | Postal code of user
rating| FALSE | Number | Rating of the user made by other people. Calculated on new reviews 
last_initial | FALSE | String | Initial of last name. **AUTO GENERATED**
created | FALSE | String | Date when user signed up.  **AUTO GENERATED**
total_reviews | FALSE | Number | Total number of reviews the user has gotten
image | FALSE | String/Blob/Base 64 Encoding | Users Image
disabled | FALSE | Boolean | Is the users account disabled
gender | FALSE | Boolean | Gender of user

## Get User
```javascript
"GET api/v1/users/jLApbXN2ItRFa72jSXZJ21uFt"
```

> The above request with the token containing same id,
 returns JSON structured like this:

```json
{
    "message": "Success",
    "status": "Success",
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
        "stripe_id": "cus_2F3G4SI5f1AoG7",
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
        "disabled": false
    }
}
```


> If no user is found, the follow json will be returned:

```json
{
    "message": "No User Found",
    "status": "Failed"
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
stripe_id | city | country 
state | zipcode | rating
last_initial | created | total_reviews 

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

