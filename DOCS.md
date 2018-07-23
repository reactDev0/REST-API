# rest-api v0.0.0



- [Article](#article)
	- [Create article](#create-article)
	- [Delete article](#delete-article)
	- [Get article](#get-article)
	- [Get articles](#get-articles)
	- [Update article](#update-article)
	
- [Auth](#auth)
	- [Authenticate](#authenticate)
	
- [User](#user)
	- [Create user](#create-user)
	- [Delete user](#delete-user)
	- [Get current user](#get-current-user)
	- [Get user](#get-user)
	- [Get users](#get-users)
	- [Update password](#update-password)
	- [Update user](#update-user)
	


# Article

## Create article



	POST /articles


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| title			| 			|  <p>Article's title.</p>							|
| author			| 			|  <p>Article's author.</p>							|
| content			| 			|  <p>Article's content.</p>							|

## Delete article



	DELETE /articles/:id


## Get article



	GET /articles/:id


## Get articles



	GET /articles


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| q			| String			| **optional** <p>Query to search.</p>							|
| page			| Number			| **optional** <p>Page number.</p>							|
| limit			| Number			| **optional** <p>Amount of returned items.</p>							|
| sort			| String[]			| **optional** <p>Order of returned items.</p>							|
| fields			| String[]			| **optional** <p>Fields to be returned.</p>							|

## Update article



	PUT /articles/:id


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| title			| 			|  <p>Article's title.</p>							|
| author			| 			|  <p>Article's author.</p>							|
| content			| 			|  <p>Article's content.</p>							|

# Auth

## Authenticate



	POST /auth

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization			| String			|  <p>Basic authorization with email and password.</p>							|

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>Master access_token.</p>							|

# User

## Create user



	POST /users


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>Master access_token.</p>							|
| email			| String			|  <p>User's email.</p>							|
| password			| String			|  <p>User's password.</p>							|
| name			| String			| **optional** <p>User's name.</p>							|
| picture			| String			| **optional** <p>User's picture.</p>							|
| role			| String			| **optional** <p>User's role.</p>							|

## Delete user



	DELETE /users/:id


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>User access_token.</p>							|

## Get current user



	GET /users/me


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>User access_token.</p>							|

## Get user



	GET /users/:id


## Get users



	GET /users


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>User access_token.</p>							|
| q			| String			| **optional** <p>Query to search.</p>							|
| page			| Number			| **optional** <p>Page number.</p>							|
| limit			| Number			| **optional** <p>Amount of returned items.</p>							|
| sort			| String[]			| **optional** <p>Order of returned items.</p>							|
| fields			| String[]			| **optional** <p>Fields to be returned.</p>							|

## Update password



	PUT /users/:id/password

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization			| String			|  <p>Basic authorization with email and password.</p>							|

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| password			| String			|  <p>User's new password.</p>							|

## Update user



	PUT /users/:id


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>User access_token.</p>							|
| name			| String			| **optional** <p>User's name.</p>							|
| picture			| String			| **optional** <p>User's picture.</p>							|


