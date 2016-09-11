---
title: trickle API Reference

language_tabs:
  - json

toc_footers:


includes:
  - errors

search: true
---

# Introduction

The `base-url` for all requests is : 

`https://trickle-shop.herokuapp.com`

All responses are of the format JSON. they contain the following keys :

* status - shows the status of the request `true` or `false`

* result - contains the actual data you requested for

* message - shows information of the response

* count - contaisn the number of objects returned

> Example of Response

```json
{
   "status" : true,
   "result" : "HELLO WORLD",
   "message" : "SUCCESS",
   "count" : 2
}
``` 

# User Auth

## Register User

> Example request to create a new trickle user. Make sure to provide `username`, `password` and `email` because they are the required fields. Request might fail without them.

```json
{
   "username" : "sample",
   "password" : "sample",
   "email" : "sample@gmail.com",
   "firstName" : "Sir",
   "lastName" : "Addico"
}
```

> if successful, the above request returns JSON structured like this:

```json
{
  "status": true,
  "result": {
    "id": "57d3c27ee4b097a655347347",
    "username": "sample",
    "password": "$2a$10$sVs/zU5tj8qxJTjX5AbNfuFCouRKPcfP1b8XXff7t1UHw7.zEeuIy",
    "firstName": "Sir",
    "lastName": "Addico",
    "profilePicture": null,
    "email": "sample@gmail.com",
    "membership": "STANDARD",
    "activated": true,
    "followed": null,
    "followers": null,
    "wishList": null,
    "dateCreated": {},
    "lastModified": {}
  },
  "message": "ACCOUNT_CREATED",
  "count": 1
}
```

This endpoint registers new users.

### HTTP Request

`POST [base-url]/registration/register`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
username | true | the display name of the new user
password | true | the password for the user `should not be less than 6 characters`
email | true | the correct email of the user `used for verification and notifications`
firstName | false | user's first name
lastName | false | user's last name

<aside class="success">
Remember — email validation will save us a lot of time :)
</aside>

## Login User

> Example request to login a user. Make sure to provide `username` and `password` because they are the required fields. Request might fail without them.

```json
{
   "username" : "sample",
   "password" : "sample"
}
```

> if successful, the above request returns JSON structured like this:

```json
{
  "status": true,
  "result": "sample",
  "message": "WELCOME",
  "count": 1
}
```

This endpoint logs in authenticated users.

### HTTP Request

`POST [base-url]/registration/login`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
username | true | the display name of the new user
password | true | the password for the user `should not be less than 6 characters`

<aside class="success">
Remember — password validation will save us a lot of time :)
</aside>
# User API

## Find User By ID

> Example URL:

```curl
https://trickle-shop.herokuapp.com/user/id/57d3c27ee4b097a655347347
```

> if successful, server returns JSON structured like this:

```json
{
  "status": true,
  "result": {
    "id": "57d3c27ee4b097a655347347",
    "username": "sample",
    "password": "$2a$10$sVs/zU5tj8qxJTjX5AbNfuFCouRKPcfP1b8XXff7t1UHw7.zEeuIy",
    "firstName": "Sir",
    "lastName": "Addico",
    "profilePicture": null,
    "email": "sample@gmail.com",
    "membership": "STANDARD",
    "activated": false,
    "followed": null,
    "followers": null,
    "wishList": null,
    "dateCreated": {},
    "lastModified": {}
  },
  "message": "WELCOME",
  "count": 1
}
```

This endpoint is to find a user by a given ID

### HTTP Request

`GET [base-url]/user/id/{{userID}}`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userID | true | the ID of the user to retrieve

<aside class="success">
Remember — password validation will save us a lot of time :)
</aside>

## Find User By Username

> Example URL:

```curl
https://trickle-shop.herokuapp.com/user/username/sample
```

> if successful, server returns JSON structured like this:

```json
{
  "status": true,
  "result": {
    "id": "57d3c27ee4b097a655347347",
    "username": "sample",
    "password": "$2a$10$sVs/zU5tj8qxJTjX5AbNfuFCouRKPcfP1b8XXff7t1UHw7.zEeuIy",
    "firstName": "Sir",
    "lastName": "Addico",
    "profilePicture": null,
    "email": "sample@gmail.com",
    "membership": "STANDARD",
    "activated": false,
    "followed": null,
    "followers": null,
    "wishList": null,
    "dateCreated": {},
    "lastModified": {}
  },
  "message": "WELCOME",
  "count": 2
}
```

This endpoint is to find a user with given username

### HTTP Request

`GET [base-url]/user/username/{{username}}`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
username | true | the username of user to retrieve

<aside class="success">
Remember — cookies for authorization coming soon :)
</aside>


## Find Users By Username

> Example URL:

```curl
https://trickle-shop.herokuapp.com/user/search/username/sample
```

> if successful, server returns JSON structured like this:

```json
{
  "status": true,
  "result":   [{
    "id": "57d3c27ee4b097a655347347",
    "username": "sample",
    "password": "$2a$10$sVs/zU5tj8qxJTjX5AbNfuFCouRKPcfP1b8XXff7t1UHw7.zEeuIy",
    "firstName": "Sir",
    "lastName": "Addico",
    "profilePicture": null,
    "email": "sample@gmail.com",
    "membership": "STANDARD",
    "activated": false,
    "followed": null,
    "followers": null,
    "wishList": null,
    "dateCreated": {},
    "lastModified": {}
  },{
    "id": "57d33r47ee4b097a090347347",
    "username": "sample1",
    "password": "$2a$10$sVs/zUsjkcjsdvsdvsRKPcfP143443b8XXff7t1UHw7.zEeuIy",
    "firstName": "Sir",
    "lastName": "Addico1",
    "profilePicture": null,
    "email": "sample1@gmail.com",
    "membership": "GOLD",
    "activated": false,
    "followed": null,
    "followers": null,
    "wishList": null,
    "dateCreated": {},
    "lastModified": {}
  }],
  "message": "WELCOME",
  "count": 2
}
```

This endpoint is to find users by a given username

### HTTP Request

`GET [base-url]/user/search/username/{{username}}`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
username | true | the username of the user to retrieve

<aside class="success">
Remember — cookies for authorization coming soon :)
</aside>


## Find All Users

> Example URL:

```curl
https://trickle-shop.herokuapp.com/user/all
```

> if successful, server returns JSON structured like this:

```json
{
  "status": true,
  "result":   [{
    "id": "57d3c27ee4b097a655347347",
    "username": "sample",
    "password": "$2a$10$sVs/zU5tj8qxJTjX5AbNfuFCouRKPcfP1b8XXff7t1UHw7.zEeuIy",
    "firstName": "Sir",
    "lastName": "Addico",
    "profilePicture": null,
    "email": "sample@gmail.com",
    "membership": "STANDARD",
    "activated": false,
    "followed": null,
    "followers": null,
    "wishList": null,
    "dateCreated": {},
    "lastModified": {}
  },{
    "id": "57d33r47ee4b097a090347347",
    "username": "sample1",
    "password": "$2a$10$sVs/zUsjkcjsdvsdvsRKPcfP143443b8XXff7t1UHw7.zEeuIy",
    "firstName": "Sir",
    "lastName": "Addico1",
    "profilePicture": null,
    "email": "sample1@gmail.com",
    "membership": "GOLD",
    "activated": false,
    "followed": null,
    "followers": null,
    "wishList": null,
    "dateCreated": {},
    "lastModified": {}
  },{
    "id": "57d33r47ee4b097a090347347",
    "username": "sample2",
    "password": "$2a$10$sVs/zUsjkcjsdvsdvsRKPcfP143443b8XXff7t1UHw7.zEeuIy",
    "firstName": "Sir",
    "lastName": "Addico2",
    "profilePicture": null,
    "email": "sample2@gmail.com",
    "membership": "PLATINUM",
    "activated": false,
    "followed": null,
    "followers": null,
    "wishList": null,
    "dateCreated": {},
    "lastModified": {}
  }],
  "message": "WELCOME",
  "count": 3
}
```

This endpoint is to find all users

### HTTP Request

`GET [base-url]/user/all`

### Query Parameters
none

<aside class="success">
Remember — cookies for authorization coming soon :)
</aside>

# Shop API

## Find Shop By ID

> Example URL:

```curl
https://trickle-shop.herokuapp.com/usershop/57d47ab0e4b0eca0903e167b
```

> if successful, server returns JSON structured like this:

```json
{
  "status": true,
  "result": {
    "id": "57d47ab0e4b0eca0903e167b",
    "user_id": "57d3c27ee4b097a655347347",
    "store_name": "Beats Store",
    "store_description": "The most affordable Beats By Dre headphones on the market",
    "image": "https://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Beats_Electronics_logo.svg/1024px-Beats_Electronics_logo.svg.png",
    "tag": "headphone",
    "views": 0,
    "status": true,
    "dateCreated": {},
    "lastModified": {}
    },
  "message": "WELCOME",
  "count": 1
}
```

This endpoint is to find a shop with given ID

### HTTP Request

`GET [base-url]/usershop/{{shop_id}}`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
shop_id | true | the ID of the shop to retrieve

<aside class="success">
Remember — cookies for authorization coming soon :)
</aside>


## Find AllProducts for Shop

> Example URL:

```curl
https://trickle-shop.herokuapp.com/shop/all/products/57d47a09e4b0eca0903e167a
```

> if successful, server returns JSON structured like this:

```json
{
  "status": true,
  "result": [
    {
      "id": "57d4a38ee4b0a424e0a8eb56",
      "shop_id": "57d47a09e4b0eca0903e167a",
      "user_id": "57d3c27ee4b097a655347347",
      "product_name": "Esense Casual",
      "product_description": "Esense if the most innovative footwear on the market today",
      "product_price": 30,
      "in_stock": true,
      "on_sale": false,
      "stock": 8,
      "views": 0,
      "images": [
        "http://ecx.images-amazon.com/images/I/41EWkstrQsL.jpg",
        "http://ecx.images-amazon.com/images/I/41%2Br%2BRJ7pML.jpg",
        "http://ecx.images-amazon.com/images/I/61ELxKSG34L._UL1500_.jpg"
      ],
      "tag": "shoe",
      "comments": null,
      "dateCreated": {},
      "lastModified": {}
    }
  ],
  "message": "PRODUCTS_FOUND",
  "count": 1
}
```

This endpoint is to find all the products of a shop with given ID

### HTTP Request

`GET [base-url]/shop/all/products/{{shop_id}}`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
shop_id | true | the ID of the shop whose products to retrieve

<aside class="info">
Remember — finding the shop by ID is a better alternative to finding by shop_name :)
</aside>



## Add Shop

> Example Request:

```json
{
  "user_id" : "57d3c27ee4b097a655347347",
  "store_name" : "Beats Store",
  "store_description" : "The most affordable Beats By Dre headphones on the market",
  "image" : "https://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Beats_Electronics_logo.svg/1024px-Beats_Electronics_logo.svg.png",
  "tag" : "headphone"
}
```

> if successful, server returns JSON structured like this:

```json
{
  "status": true,
  "result": {
    "id": "57d47ab0e4b0eca0903e167b",
    "user_id": "57d3c27ee4b097a655347347",
    "store_name": "Beats Store",
    "store_description": "The most affordable Beats By Dre headphones on the market",
    "image": "https://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Beats_Electronics_logo.svg/1024px-Beats_Electronics_logo.svg.png",
    "tag": "headphone",
    "views": 0,
    "status": true,
    "dateCreated": {},
    "lastModified": {}
  },
  "message": "STORE_CREATED",
  "count": 1
}
```

This endpoint is to create a shop for a particular user

### HTTP Request

`POST [base-url]/usershop/create/shop`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
user_id | true | the id of the owner of the shop
store_name | true | the name of the shop
store_description | true | description of the shop
image | false | image of the shop
tag | false | a tag to associate the shop with example : `headphone`

<aside class="success">
Remember — the user_id is required to assign the shop to its rightful owner
</aside>


# Product API

## Find Product By ID

> Example URL:

```curl
https://trickle-shop.herokuapp.com/userproduct/57d47ab0e4b0eca0903e167b
```

> if successful, server returns JSON structured like this:

```json
{
  "status": true,
  "result": {
    "id": "57d47ab0e4b0eca0903e167b",
    "user_id": "57d3c27ee4b097a655347347",
    "store_name": "Beats Store",
    "store_description": "The most affordable Beats By Dre headphones on the market",
    "image": "https://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Beats_Electronics_logo.svg/1024px-Beats_Electronics_logo.svg.png",
    "tag": "headphone",
    "views": 0,
    "status": true,
    "dateCreated": {},
    "lastModified": {}
    },
  "message": "WELCOME",
  "count": 1
}
```

This endpoint is to find a product with given ID

### HTTP Request

`GET [base-url]/userproduct/{{product_id}}`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
product_id | true | the ID of the product to retrieve

<aside class="success">
Remember — cookies for authorization coming soon :)
</aside>


## Add Shop

> Example Request:

```json
{
  "user_id" : "57d3c27ee4b097a655347347",
  "store_name" : "Beats Store",
  "store_description" : "The most affordable Beats By Dre headphones on the market",
  "image" : "https://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Beats_Electronics_logo.svg/1024px-Beats_Electronics_logo.svg.png",
  "tag" : "headphone"
}
```

> if successful, server returns JSON structured like this:

```json
{
  "status": true,
  "result": {
    "id": "57d47ab0e4b0eca0903e167b",
    "user_id": "57d3c27ee4b097a655347347",
    "store_name": "Beats Store",
    "store_description": "The most affordable Beats By Dre headphones on the market",
    "image": "https://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Beats_Electronics_logo.svg/1024px-Beats_Electronics_logo.svg.png",
    "tag": "headphone",
    "views": 0,
    "status": true,
    "dateCreated": {},
    "lastModified": {}
  },
  "message": "STORE_CREATED",
  "count": 1
}
```

This endpoint is to add a product to a particular user

### HTTP Request

`POST [base-url]/userproduct/create/product`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
shop_id | true | the id of the shop to add to
product_name | true | the name of the product
product_description | true | description of the product
images | false | images of the product
tag | false | a tag to associate the product with ,example : `nike`

<aside class="success">
Remember — the shop_id is required to assign the shop to its rightful owner
</aside>


