### Internal resources

These are internal methods usd by amee's own systems. 

They currently aren't exposed over the public API, they're listed here, for developers interested in further integration down the line.

User Resource
==============

At present, all user operations except GETing their own user are restricted for internal use.

* [POST](https://github.com/AMEE/score-api/blob/internal-api/sections/user.md#post-user)
* [PUT](https://github.com/AMEE/score-api/blob/internal-api/sections/user.md#put-user)
* [DELETE](https://github.com/AMEE/score-api/blob/internal-api/sections/user.md#delete-user)

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
http://score.amee.com/1/users
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


Put User
---------

* `PUT /users/{username}` - Update a user's details

### Form parameters

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
-X PUT \
-d "password=NEW_PASSWORD" \
http://score.amee.com/1/users/sample-user
```

Sample Response
---------------

```json
{
  "status": "OK",
  "version": "1.0.0"
}
```


Delete User
-----------

* `DELETE /users/username` - Delete a given user. (admin only)

Sample Request
--------------

```shell
curl -H "Accept: application/json" \
-u username:password \
-X DELETE \
http://score.amee.com/1/users/sample-user1
```

Sample Response
---------------

```json
{
  "status": "OK",
  "version": "1.0.0"
}
```
