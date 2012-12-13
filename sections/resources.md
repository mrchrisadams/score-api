Resources
=========

### Versioning

API endpoints are hosted under `/{version}/{rest-of-path}`, so requests for version 1.0 of the API would look like so:

```
curl -H "Accept: application/json" -u username:password \ https://hub.amee.com/1.0/companies/123456789/score
```

Further, detailed documentation of the [API versioning is available](versioning.md)

### Query Parameters

Some resources accept query paramters, as defined by the HTTP specification. Query parameters are used for traditional results filtering and querying, such as:

```
/score/123456789?type=CRO
```

Status Codes
------------

* Resource fetch: 200
* Resource not found: 404
* Request error (eg, validation): 400
* Server error: 500

Request Accept Types
--------------------

Only the JSON (application/json) content type is supported.

API requests should include this for the 'Accept' HTTP header.

```
curl -H "Accept: application/json" -u username:password \ https://hub.amee.com/1.0/companies/123456789/score
```


Usage Restrictions
------------------

The following restrictions are placed on API usage:

* Any request taking longer that 15 seconds will be timed-out.


Score Resource
==============

`GET /score/{companyId}` - Get scores for a single company.  

### Query Parameters

type - the type of the company ID specified, (DUNS|CRO|AMEE).  If no type is specified, defaults to AMEE


Sample Requests
---------------

Making the following request for a company's score:

```
curl -H "Accept: application/json" -u username:password \ 
http://hub-local.amee.com/1/score/UK123456?type=cro
```

Will return the following json:

```json
{
 "status" : "OK",
 "score" : {
   "amee_industry_score" : 0,
   "amee_profiles_url" : "https://beta.amee.com/companies/123456789",
   "amee_id" : "123456789",
   "amee_national_score" : 0
 },
 "version" : "1.0.0"
}
```


