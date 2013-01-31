Company Resource
================

The company resource relates to the amee environmental data for a given company, using a particular identifier, like a company registration number (`CRO`) or amee id (`AMEE`)

Get company
-----------

* `GET /company/{companyId}` - Get data for a single company.  

### Query Parameters

`type` - the type of the company ID specified, (CRO|AMEE).  If no type is specified, defaults to AMEE.

* `CRO`  - company registration number
* `AMEE` - amee id


Sample Request
--------------

Making the following request for a company's score:

```shell
curl -H "Accept: application/json" -u username:password \ 
https://score.amee.com/1/companies/UK123456?type=cro
```

Sample Response
---------------


Will return the following json:

```json
{
 "status" : "OK",
 "score" : {
   "amee_id" : "123456789",
   "cro" : "UK123456"
   "amee_industry_score" : 50,
   "amee_profiles_url" : "https://beta.amee.com/companies/123456789-example-company-ltd"
 },
 "version" : "1.0.0"
}
```




