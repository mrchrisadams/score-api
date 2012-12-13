Using the amee Score API
========================

Looking to use amee's score API? 

Everything you need to start is listed right here, including sample code and detailed documentation

Where to start
--------------

1. Drop an email titled "API credentials request" to chris.adams@amee.com
2. Once you have credentials, see how to make a sample request using your credentials, and see a sample response.
3. Look over the detailed [API docs](https://github.com/AMEE/score-api/sections/resources.md) to see how to make the requests specific to you app.
5. Join the [API mailing list](http://groups.google.com/group/amee-developer) to talk to others using the APIs and give us feedback.

API Documentation
-----------------

[Score](https://github.com/AMEE/score-api/sections/resources.md)


Authentication and Security
---------------------------

All requests to the API must be over SSL (https), and need to be authenticated using an AMEEhub username & password via HTTP basic access authentication.

For example, the following curl command makes an authenticated request to the Score resource:


```shell
curl -H "Accept: application/json" -u username:password \ https://hub.amee.com/1.0/companies/123456789/score
```


Help us make it better
----------------------

Please tell us how we can make the APIs better. If you have a specific feature request or if you found a bug, or the docs aren't clear, please file an issue](https://github.com/AMEE/score-api/issues). Also, feel free to fork these docs and send a pull request with improvements!

To talk with us and other developers about the API, subscribe to the [amee developer mailing list](http://groups.google.com/group/amee-developer).

