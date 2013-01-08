This section describes various aspects of API interaction that apply to all or most of the resources exposed over the API.

# Versioning

All URIs are versioned.

API endpoints are hosted under `/{version}/{rest-of-path}`

The version path segment is structured like this: '{major}.{minor}.{fix}'.

For example, '1.0.0'.

The first part of the version is the major version which won't change often and any change would be significant and likely breaking.
The second part is the minor version and will change when incremental enhancements are added within the major version. Minor version changes will be non-breaking (backwards compatible) but clients may need to make changes to use newer versions.

The last part is for small fixes and may change often but will be non-breaking.

Each version number part is incremented separately and can increment to 10 and beyond. So, '3.3.12' is valid for example.
We can allow 'x' in the version string to allow the latest version of that part. So, '1.0.x' would always route to the most recent fix version but stick to the same major and minor version.
We will allow the latter parts of the version string to be omitted, for example: '1.0' & '1'.
To be clear, the first path segment of all API URIs is reserved for this version string.

All URIs described in this document are assumed to conform to the above versioning rules and to have '1.0' as the version value. Most example URIs in this document will omit the version segment.

The versioning scheme described above is similar to and perhaps a subset of SemVer.

# Security

All requests to the API must be over SSL (https).


# Authentication

All API requests need to be authenticated using an AMEEhub username & password via HTTP basic access authentication.

For example, the following curl command makes an authenticated request to the Users resource.

```shell
curl -H "Accept: application/json" -u username:password \ https://hub.amee.com/1.0/users
```

In the example the username is `username` and the password is `password` . This particular request should result in a JSON representation showing a list of Users.

# Authorisation

Authorisation is managed through assigning users to particular roles. To begin with there are only two roles: 'ROLE_USER' and 'ROLE_ADMIN'. Note: these are not hierarchical.

Some API operations are restricted to users with ROLE_ADMIN, eg, listing all users, creating a user.

# Query & Matrix Parameters

Some resources accept query and/or matrix parameters, as defined by the HTTP specification. Query parameters are used for traditional results filtering and querying, such as:

```shell
/score/123456789?type=CRO 
```

Matrix parameters are used to modify the representation itself, to lower or increase the level of detail or to add aspects missing from the default representation, for example `/users;roles`.

# Pagination

There is no 'pagination' as such, in the sense of distinct pages of results. Instead the API will allow you to specify the start offset and limit of result items. This is done with the following two parameters:

`resultStart` - Index of the first item in a list, zero-based. Defaults to 0.
`resultLimit` - Max number of results to return, with contextual server defined defaults & upper limits.

Some representations may return information to help clients with pagination, such as:

`truncated` - Indicates if the result set was truncated (more items are available). This can be 'true' or 'false'.

# Status Codes

* Resource creation: 201
* Resource fetch: 200
* Resource update: 200
* Resource delete: 200
* Resource not found: 404
* Request error (eg, validation): 400
* Server error: 500

# Validation

All API requests are validated consistently. This covers:

All request query parameters.
All request form parameters (`application/x-www-form-urlencoded` content type).
Individual and multiple entities within JSON representations.

There are two forms of validation representation response:

### For 'flat' or single entity requests:

* There is a single validation context.
* Requests with query or form parameters.
* Requests with a single entity in the JSON.

### For multiple entity requests:

* There are multiple validation contexts.
* Requests with multiple entities in the JSON.

Here is an example single entity JSON representation for a 'flat' request with form parameters. This request has two validation errors; the required name parameter was empty and the path parameter was too long.

```json
{
  "status":"INVALID",
  "validationResult":{
     "errors":[
        {
           "field":"name",
           "code":"empty",
         "message":"A human readable message.",
         "value":"The original value submitted."
        },
        {
           "field":"path",
           "code":"long",
         "message":"A human readable message.",
           "value":"The original value submitted."
        }
     ]
  }
}
```

# Request Accept Types

Only the JSON (`application/json`) content type is supported.

API requests should include this for the `Accept` HTTP header.

# Response Content Types

API requests POSTing data should include a `Content-Type` HTTP header declaring the content type, as `application/x-www-form-urlencoded`:

```shell
curl -H "Accept: application/json" \
-H "Content-Type: application/x-www-form-urlencoded" \
-u username:password \
-X POST \
-d "data-payload=goeshere" \
https://hub-dev.amee.com/1/users
```

# Usage Restrictions

The following restrictions are placed on API usage.

Any request taking longer that 15 seconds will be timed-out.
Max incoming number of 'items', depending on API resource.
