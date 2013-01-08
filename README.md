Using the amee Score API
========================

Looking to use amee's score API? 

Everything you need to start is listed right here, including sample code and detailed documentation

Where to start
--------------

1. The first thing you'll need are some API credentials (a user name and password) to sign requests with. If you drop an an email titled "API credentials request" to [chris.adams@amee.com](mailto:mail@chrisadams.me.uk). You should usually receive them the same day.
2. Once you have credentials, see how to make a sample request using your credentials, and see a sample response.
3. Look over the detailed [API docs](https://github.com/AMEE/score-api/blob/master/sections/resources.md) to see how to make the requests specific to you app.
5. Join the [API mailing list](http://groups.google.com/group/amee-developer) to talk to others using the APIs and give us feedback.

Making a sample response
------------------------

Once you have credentials, you can make a sample request to the amee Score resource like so:

```shell
curl -H "Accept: application/json" -u username:password \ 
  https://hub.amee.com/1.0/companies/123456789/score
```

You should receive a json response looking something like this:

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


Authentication
--------------

All requests are sent over SSL, and use HTTP Basic Authentication with your user credentials. [More detailed documentation is also available ](https://github.com/AMEE/score-api/blob/master/sections/score.md#Authentication)

Just JSON, no XML
-----------------

The API only supports JSON, so be sure to use a header requesting the response as JSON, like so: `Accept: application/json`


API Documentation
-----------------

There are currently two resources available on the public Score API:

* [Score](https://github.com/AMEE/score-api/blob/master/sections/score.md) - for returning the environmental score for a given company
* [Users](https://github.com/AMEE/score-api/blob/master/sections/user.md) - for managing your own user account

##### Shared docs for all resources

There is more detailed documentation that applies to making all requests to resources exposed by amee. Find it here in the shared [resources](https://github.com/AMEE/score-api/blob/master/sections/user.md) documentation.

#### APIs under development

Over the coming weeks and months, we'll be exposing further resources to use:

* Companies - fetching full information about companies, and sending updates to the data
* Search - exposing the search visible on http://beta.amee.com in machine readable form


Help us make it better
----------------------

Please tell us how we can make the APIs better. If you have a specific feature request or if you found a bug, or the docs aren't clear, please [file an issue](https://github.com/AMEE/score-api/issues). Also, feel free to fork these docs and send a pull request with improvements!

To talk with us and other developers about the API, subscribe to the [amee developer mailing list](http://groups.google.com/group/amee-developer).