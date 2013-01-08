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

Post User
---------

* `POST /users/` - Create a new user

### Form parameters

* `username` - the username
* `password` - the password
* `email` - the email address
* `enabled` - is the user enabled (true/false)
* `roles` - CSV list of roles assigned to the user, e.g. roles=ROLE_USER,ROLE_ADMIN

Sample Request
--------------

```shell
curl -H "Accept: application/json" \
-H "Content-Type: application/x-www-form-urlencoded" \
-u username:password \
-X POST \
-d "username=sample-user1&password=topSekrit&email=sample-user@domain.com&enabled=true&roles=ROLE_USER" \
http://hub.amee.com/1/users
```

Sample Response
---------------

```json
{
  "status": "OK",
  "entity": {
    "username": "sample-user"
  },
  "path": "/1.0.0/users/sample-user",
  "version": "1.0.0"
}
```