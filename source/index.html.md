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

`https://finderr-esb.herokuapp.com/esb`

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

> Example request to create a new trickle user. Make sure to provide `username`, `password` and `email` because they are the required fields. Request will fail without them.

```json
{
	"username" : "user",
	"password" : "password",
	"email" : "user@mail.com",
	"mobile" : ""
}
```

> if successful, the above request returns JSON structured like this:

```json
{
	"status": true,
	"result": {
		"id": "5b01d841449bc6000492f47d",
		"username": "user",
		"password": "$2a$10$Wcx1B5OoIV9tcBsyVz6hEut2D.A0TOkNTPuIzTnVcU.Nj6zpLlXlW",
		"firstName": null,
		"lastName": null,
		"profilePicture": null,
		"email": "user@mail.com",
		"mobile": "",
		"membership": "STANDARD",
		"activated": true,
		"followed": null,
		"followers": null,
		"likes": null,
		"reposts": null,
		"number_of_followers": 0,
		"number_of_followed": 0,
		"number_of_likes": 0,
		"number_of_reposts": 0,
		"wishList": null,
		"dateCreated": {
			"yearOfEra": 2018,
			"yearOfCentury": 18,
			"weekyear": 2018,
			"monthOfYear": 5,
			"weekOfWeekyear": 20,
			"hourOfDay": 20,
			"minuteOfHour": 19,
			"secondOfMinute": 13,
			"millisOfSecond": 614,
			"centuryOfEra": 20,
			"year": 2018,
			"dayOfMonth": 20,
			"dayOfYear": 140,
			"dayOfWeek": 7,
			"era": 1,
			"secondOfDay": 73153,
			"minuteOfDay": 1219,
			"millisOfDay": 73153614,
			"millis": 1526847553614,
			"zone": {
				"fixed": true,
				"id": "Etc/UTC"
			},
			"chronology": {
				"zone": {
					"fixed": true,
					"id": "Etc/UTC"
				}
			},
			"beforeNow": true,
			"afterNow": false,
			"equalNow": false
		},
		"lastModified": {
			"yearOfEra": 2018,
			"yearOfCentury": 18,
			"weekyear": 2018,
			"monthOfYear": 5,
			"weekOfWeekyear": 20,
			"hourOfDay": 20,
			"minuteOfHour": 19,
			"secondOfMinute": 13,
			"millisOfSecond": 614,
			"centuryOfEra": 20,
			"year": 2018,
			"dayOfMonth": 20,
			"dayOfYear": 140,
			"dayOfWeek": 7,
			"era": 1,
			"secondOfDay": 73153,
			"minuteOfDay": 1219,
			"millisOfDay": 73153614,
			"millis": 1526847553614,
			"zone": {
				"fixed": true,
				"id": "Etc/UTC"
			},
			"chronology": {
				"zone": {
					"fixed": true,
					"id": "Etc/UTC"
				}
			},
			"beforeNow": true,
			"afterNow": false,
			"equalNow": false
		}
	},
	"message": "USER_REGISTERED",
	"count": 1
}
```

This endpoint registers new users.

### HTTP Request

`POST [base-url]/register/user`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
username | true | the display name of the new user
password | true | the password for the user `should not be less than 6 characters`
email | true | the correct email of the user `used for verification and notifications`
mobile | false | the mobile number of the user `used for verification and notifications`

<aside class="success">
Remember — email validation will save us a lot of time :)
</aside>

## Login User

> Example request to login a user. Make sure to provide `username` and `password` because they are the required fields. Request might fail without them.

```json
{
   "username" : "user",
   "password" : "password"
}
```

> if successful, the above request returns JSON structured like this:

```json
{
	"status": true,
	"result": {
		"id": "5b01d841449bc6000492f47d",
		"username": "user",
		"password": "$2a$10$Wcx1B5OoIV9tcBsyVz6hEut2D.A0TOkNTPuIzTnVcU.Nj6zpLlXlW",
		"firstName": null,
		"lastName": null,
		"profilePicture": null,
		"email": "user@mail.com",
		"mobile": "",
		"membership": "STANDARD",
		"activated": true,
		"followed": null,
		"followers": null,
		"likes": null,
		"reposts": null,
		"number_of_followers": 0,
		"number_of_followed": 0,
		"number_of_likes": 0,
		"number_of_reposts": 0,
		"wishList": null,
		"dateCreated": {
			"yearOfEra": 2018,
			"yearOfCentury": 18,
			"weekyear": 2018,
			"monthOfYear": 5,
			"weekOfWeekyear": 20,
			"hourOfDay": 20,
			"minuteOfHour": 19,
			"secondOfMinute": 13,
			"millisOfSecond": 614,
			"centuryOfEra": 20,
			"year": 2018,
			"dayOfMonth": 20,
			"dayOfYear": 140,
			"dayOfWeek": 7,
			"era": 1,
			"secondOfDay": 73153,
			"minuteOfDay": 1219,
			"millisOfDay": 73153614,
			"millis": 1526847553614,
			"zone": {
				"fixed": true,
				"id": "Etc/UTC"
			},
			"chronology": {
				"zone": {
					"fixed": true,
					"id": "Etc/UTC"
				}
			},
			"beforeNow": true,
			"afterNow": false,
			"equalNow": false
		},
		"lastModified": {
			"yearOfEra": 2018,
			"yearOfCentury": 18,
			"weekyear": 2018,
			"monthOfYear": 5,
			"weekOfWeekyear": 20,
			"hourOfDay": 20,
			"minuteOfHour": 19,
			"secondOfMinute": 13,
			"millisOfSecond": 614,
			"centuryOfEra": 20,
			"year": 2018,
			"dayOfMonth": 20,
			"dayOfYear": 140,
			"dayOfWeek": 7,
			"era": 1,
			"secondOfDay": 73153,
			"minuteOfDay": 1219,
			"millisOfDay": 73153614,
			"millis": 1526847553614,
			"zone": {
				"fixed": true,
				"id": "Etc/UTC"
			},
			"chronology": {
				"zone": {
					"fixed": true,
					"id": "Etc/UTC"
				}
			},
			"beforeNow": true,
			"afterNow": false,
			"equalNow": false
		}
	},
	"message": "SUCCESS",
	"count": 0
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


## Add Product to Shop`

> Example Request:

```json
{
  "shop_id" : "57d47a09e4b0eca0903e167a",
  "user_id" : "57d3c27ee4b097a655347347",
  "product_name" : "Esense Casual",
  "product_description" : "Esense if the most innovative footwear on the market today",
  "product_price" : 30,
  "in_stock" : true,
  "on_sale" : false,
  "stock" : 8,
  "tag" : "shoe",
  "images" : ["http://ecx.images-amazon.com/images/I/41EWkstrQsL.jpg","http://ecx.images-amazon.com/images/I/41%2Br%2BRJ7pML.jpg","http://ecx.images-amazon.com/images/I/61ELxKSG34L._UL1500_.jpg"]
}
```

> if successful, server returns JSON structured like this:

```json
{
  "status": true,
  "result": {
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
  },
  "message": "PRODUCT_CREATED",
  "count": 1
}
```

This endpoint is to add a product to a particular shop

### HTTP Request

`POST [base-url]/userproduct/create/product`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
shop_id | true | the id of the shop to add to
user_id | true | the id of the shop owner
product_name | true | the name of the product
product_description | true | description of the product
images | false | images of the product
tag | false | a tag to associate the product with ,example : `nike`

<aside class="success">
Remember — the shop_id is required to assign the shop to its rightful owner
</aside>


