Score Resource
==============

The company resource relates to the data for a given company, using a particular identifier, like a company registration number (`CRO`), or amee id (`AMEE`)

Get scores
----------

* `GET /companies/{companyId}` - Get data for a single company.  

### Query Parameters

`type` - the type of the company ID specified, (CRO|AMEE).  If no type is specified, defaults to AMEE.

* `CRO`  - company registration number
* `AMEE` - amee id


Sample Request
--------------

Making the following request for a company's score:

```shell
curl -H "Accept: application/json" -u username:password \ 
http://score.amee.com/1/companies/UK123456?type=cro
```

Sample Response
---------------


Will return the following json:

```json
{
 "status" : "OK",
 "score" : {
   "amee_industry_score" : 50,
   "amee_profiles_url" : "https://www.amee.com/companies/123456789",
   "amee_id" : "123456789"
 },
 "version" : "1.0.0"
}
```




