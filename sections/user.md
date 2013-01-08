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

Sample Request
--------------

Making the following request for a user:

```shell
curl -H "Accept: application/json" -u username:password \ 
http://hub-local.amee.com/1/users/sample-user
```

Sample Response
---------------

Will return the following json:

```json
{
 "status" : "OK",
 "users" : {
   "tbc": "Some content here"
 },
 "version" : "1.0.0"
}
```
