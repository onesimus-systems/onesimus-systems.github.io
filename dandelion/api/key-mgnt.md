---
layout: page-no-title
title: Dandelion - API - Key Management
permalink: /dandelion/api/key-mgnt/
---

Dandelion - API Documentation - Key Management
----------------------------------------------

Module name: keyanager

Index
-----

- [test](#test)
- [revoke](#revoke)
- [generate](#generate)

test
----

**Endpoint**: `/api/key/test`

**Parameters**: None

**Description**: Tests that the apikey is valid. This is a useful endpoint for extensions. An easy way to check the success is to check the `errorcode` field of the return object. A value of 0 means success, other values indicate failure means failure.

**Example Return Data**:

{% highlight json %}
{
	"data": true
}
{% endhighlight %}

**Permissions Needed**:

- None

[&#8657; Top](#index)

* * * * *

revoke
------

**Endpoint**: `/api/key/revoke`

**Parameters**: `[uid]`

| Parameter | Type   | Default | Required |
|-----------|--------|---------|----------|
| `uid`     | int    | User ID | false    |

**Description**: Revoke the API key for the user with `uid`. The default value for `uid` is the ID associated with the API key being used to make the request. Because of this, if `uid` is not defined, the key being used with no longer be valid.

**Example Return Data**:

{% highlight json %}
{
	"data": true
}
{% endhighlight %}

**Permissions Needed**:

- Edit user (not needed to revoke user's own key)

[&#8657; Top](#index)

* * * * *

generate
--------

**Endpoint**: `/api/key/generate`

**Parameters**: None

**Description**: Generate a new key for user who is associated with the apikey being used.

**Example Return Data**:

{% highlight json %}
{
	"data": "the new key"
}
{% endhighlight %}

**Returned Values**:

- data (string) - The regenerated API key (length: 40 char)

**Permissions Needed**:

- None

[&#8657; Top](#index)

* * * * *

[&#8656; API Documentation](/dandelion/api)
