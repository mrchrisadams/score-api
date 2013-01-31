User Resource
==============

At present, all user operations except GETing their own user are restricted for internal use.

Get users
---------

* `GET /users/{username}` - Get information about a given user.  

### Matrix parameters

Adding the following matrix parameters will change how a given user is represented in the response:

* `full` - show all
* `audit` - show the created and modified dates
* `roles` - show the roles assigned to the user

[Further information about using matrix parameters is available](https://github.com/AMEE/score-api/blob/master/sections/resources.md#query--matrix-parameters)

Sample Request
--------------

Making the following request for a user:

```shell
curl -H "Accept: application/json" -u username:password \ 
https://score.amee.com/1/users/sample-user
```

Sample Response
---------------

Will return the following json:

```json
{
 "status" : "OK",
 "user" : {
   "username": "sample-user",
   "email": "sample-user@amee.com"
 },
 "version" : "1.0.0"
}
```
