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

The `base-url` for all requests is `https://trickle-shop.herokuapp.com`

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
# User Management

## Find User By ID

> Example URL:

```http
https://trickle-shop.herokuapp.com/user/id/57d3c27ee4b097a655347347
```

> if successful, server returns JSON structured like this:

```json
{
  "status": true,
  "result":   "result": {
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

```http
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

```http
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


