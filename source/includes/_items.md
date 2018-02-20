# Items

## Create Item
```javascript
"POST api/v1/items/"
```
```json
{
        
}
```

> The above request with the specified body will return json as below:

```json
{
    
}
```

This endpoint will create a new item in the database and relate it to the user id that is in the token.
### HTTP Request

`POST /api/v1/users`

### User Public or Private Parameters

Parameter | Required | Type     | Description
--------- | -------  | ------- | ------- 


## Get Item
```javascript
"GET api/v1/items/8217e4cc19ba53e5c20d60d46aca53f398136d5c6d863c74e950be48bf28ff16"
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
                  "name": "Snowboard",
                  "owner_uid": "5S8e2s0gs6ZIy4v0vS5fB47WJJ43",
                  "description": "Sons snowboard.  It is a 165 and the bindings are for medium to large boots. good condition.",
                  "status": "active",
                  "pickup_instructions": "For pick up and drop off only.",
                  "currency": "usd",
                  "daily": 10,
                  "weekly": null,
                  "monthly": null,
                  "id": "8217e4cc19ba53e5c20d60d46aca53f398136d5c6d863c74e950be48bf28ff16",
                  "address_id": 18,
                  "created": "2017-12-29T23:20:56.969Z",
                  "rating": null,
                  "total_reviews": null,
                  "tsv": "'165':7 'bind':10 'boot':16 'condit':18 'good':17 'larg':15 'medium':13 'snowboard':1,3 'son':2",
                  "instant_booking": false,
                  "will_deliver": false,
                  "images": [
                      {
                          "image_url": "https://res.cloudinary.com/hko0mswnc/image/upload/q_auto/f_auto/v1514589657/ubakznavehqliqizxj7v.png",
                          "entity_id": "8217e4cc19ba53e5c20d60d46aca53f398136d5c6d863c74e950be48bf28ff16",
                          "ord": 0,
                          "image_id": "ubakznavehqliqizxj7v",
                          "created": "2017-12-29T23:20:58.543Z"
                      },
                      {
                          "image_url": "https://res.cloudinary.com/hko0mswnc/image/upload/q_auto/f_auto/v1514589657/ijmskgmbudhpjjon8tev.png",
                          "entity_id": "8217e4cc19ba53e5c20d60d46aca53f398136d5c6d863c74e950be48bf28ff16",
                          "ord": 1,
                          "image_id": "ijmskgmbudhpjjon8tev",
                          "created": "2017-12-29T23:20:58.543Z"
                      }
                  ]
              }
          }
            
```


> If no user is found, the follow json will be returned:

```json
{
    "message": "No Item Found",
    "status": "Failed"
}
```

This endpoint retrieves a single item.  If the owner of the item is the same id in the JWT token, the api will get you all
 information related to the items exact address, if they do not match, only the publicly available address info will be retrieved. 
 

### HTTP Request

`GET /api/v1/items/:id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | TRUE | The id of the item being retrieved.


## Update Item

This endpoint updates a specific item.  Because it is a **PUT**, the properties that 
are passed in will override the stored values.  If the property is not put in, it will be
replaced by *null*.  *Only the owner of an item can update an item*.

### HTTP Request

`PUT api/v1/items/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the User to be updated




## Search Items
```javascript
"GET api/v1/items/search"
```

> The above request with the token containing same id,
 returns JSON structured like this:

```json
{
    
}
```


> If no user is found, the follow json will be returned:

```json
{
    "message": "No Item Found",
    "status": "Failed"
}
```

This endpoint retrieves a single item.  If the owner of the item is the same id in the JWT token, the api will get you all
 information related to the items exact address, if they do not match, only the publicly available address info will be retrieved. 
 

### HTTP Request

`GET /api/v1/items/search`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | TRUE | The id of the item being retrieved.






## Get Logged In User Items
```javascript
"GET api/v1/items/8217e4cc19ba53e5c20d60d46aca53f398136d5c6d863c74e950be48bf28ff16"
```

> The above request with the token containing same id,
 returns JSON structured like this:

```json
{
    
}
```


> If no user is found, the follow json will be returned:

```json
{
    "message": "No Item Found",
    "status": "Failed"
}
```

This endpoint retrieves a single item.  If the owner of the item is the same id in the JWT token, the api will get you all
 information related to the items exact address, if they do not match, only the publicly available address info will be retrieved. 
 

### HTTP Request

`GET /api/v1/items/userItems`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | TRUE | The id of the item being retrieved.








## Get User Items
```javascript
"GET api/v1/items/8217e4cc19ba53e5c20d60d46aca53f398136d5c6d863c74e950be48bf28ff16"
```

> The above request with the token containing same id,
 returns JSON structured like this:

```json
{
    
}
```


> If no user is found, the follow json will be returned:

```json
{
    "message": "No Item Found",
    "status": "Failed"
}
```

This endpoint retrieves a single item.  If the owner of the item is the same id in the JWT token, the api will get you all
 information related to the items exact address, if they do not match, only the publicly available address info will be retrieved. 
 

### HTTP Request

`GET /api/v1/items/userItems/:UID`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | TRUE | The id of the item being retrieved.









## Add Item Image
```javascript
"GET api/v1/items/8217e4cc19ba53e5c20d60d46aca53f398136d5c6d863c74e950be48bf28ff16"
```

> The above request with the token containing same id,
 returns JSON structured like this:

```json
{
    
}
```


> If no user is found, the follow json will be returned:

```json
{
    "message": "No Item Found",
    "status": "Failed"
}
```

This endpoint retrieves a single item.  If the owner of the item is the same id in the JWT token, the api will get you all
 information related to the items exact address, if they do not match, only the publicly available address info will be retrieved. 
 

### HTTP Request

`PATCH /api/v1/items/:id/image`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | TRUE | The id of the item being retrieved.










## Remove Item Image
```javascript
"GET api/v1/items/8217e4cc19ba53e5c20d60d46aca53f398136d5c6d863c74e950be48bf28ff16"
```

> The above request with the token containing same id,
 returns JSON structured like this:

```json
{
    
}
```


> If no user is found, the follow json will be returned:

```json
{
    "message": "No Item Found",
    "status": "Failed"
}
```

This endpoint retrieves a single item.  If the owner of the item is the same id in the JWT token, the api will get you all
 information related to the items exact address, if they do not match, only the publicly available address info will be retrieved. 
 

### HTTP Request

`DELETE /api/v1/items/:id/image/:imageId`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | TRUE | The id of the item being retrieved.










## Delete an Item

```javascript
"DELETE api/v1/items/:id"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific item.  Only the owner of the account or an 
Administrator has the ability to delete a user.  This is determined by the id in the token.

*Not yet Implemented*
### HTTP Request

`DELETE api/v1/items/:id`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to be deleted

