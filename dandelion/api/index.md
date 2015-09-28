---
layout: page-no-title
title: Dandelion - API Documentation
permalink: /dandelion/api/
---

Dandelion - API Documentation
-----------------------------

The Dandelion API is a simple and standardized way of getting data from a Dandelion instance. To make an api request, you'll need the API key for a user and the hostname. The urls take the form of `http[s]://[path-to-dandelion]/api/{module}/{task}`. Every call requires some HTTP parameters to be passed either through GET or POST. The permissions used for the call comes from the user's key.

All requests must pass the parameter `apikey` containing the user's key. If this parameter doesn't exist the call will fail.

Below are links to docs for the available endpoints, their paths, parameters, and what they do.

If a documented endpoint has a Dandelion Version section, that is the minimum version necessary for the endpoint to work. If no version exists, then the endpoint has existed since v6.0.0 when the API was introduced.

Each request will return a standard JSON object in the format:

{% highlight json %}
{
	"status": "Status message",
	"errorcode": 0,
	"module": "Requested module",
	"requestTime": "12.01ms",
	"data": {}
}
{% endhighlight %}

The `errorcode` field is an integer in the range [0,6] with the following meanings:

- 0 - Successful API call
- 1 - Invalid API key
- 2 - External API disabled
- 3 - Action requires active login
- 4 - Insufficient permissions
- 5 - General error
- 6 - Server error

The `status` field is a textual representation of the errorcode. For example, `API key is not valid`.

The `module` field is simply the module that was requested. Example, `logs`, `cheesto`.

The `data` field is where the good stuff is. This can range from a string, to a JS object. You will have to refer to the documentation for each endpoint to know what kind of data to expect.

The `requestTime` field is how long the API call took to complete. This time does not include the time for setup and teardown the request. Added in v6.1.0.

API Enpoints
------------

[Logs](/dandelion/api/logs)

[Categories](/dandelion/api/categories)

[Ĉeesto](/dandelion/api/cheesto)

[User Settings](/dandelion/api/user-settings)

[Rights Management](/dandelion/api/rights)

[User Management](/dandelion/api/users)

[Key Management](/dandelion/api/key-mgnt)
