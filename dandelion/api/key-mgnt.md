---
layout: page-no-title
title: Dandelion - API - Key Management
permalink: /dandelion/api/key-mgnt/
---

Dandelion - API Documentation - Key Management
----------------------------------------------

Module name: keyManager

Index
-----

- [testkey](#testkey)
- [revokekey](#revokekey)
- [newkey](#newkey)

testkey
-------

**Endpoint**: `/api/testkey` **note irregular path**

**Parameters**: None

**Description**: Tests that the apikey is valid. This is a useful endpoint for extensions. **Note**: This request doesn't return anything in the `data` field. To check the success, check the `errorcode` field of the return object. A value of 0 means success, a value of 1 means failure. Pay careful attention to this, if comparing as a truth value it will be the opposite of what might be expected.

**Returned Data**:

{% highlight json %}
{
	"data": ""
}
{% endhighlight %}

**Returned Values**:

- No data returned

**Permissions Needed**:

- None

[&#8657; Top](#index)

* * * * *

revokekey
---------

**Endpoint**: `/api/keymanager/revokekey`

**Parameters**: `[uid]`

| Parameter | Type   | Default | Required |
|-----------|--------|---------|----------|
| `uid`     | int    | User ID | false    |

**Description**: Revoke the API key for the user with `uid`. The default value for `uid` is the ID associated with the API key being used to make the request. Because of this, if `uid` is not defined, the key being used with no longer be valid.

**Returned Data**:

{% highlight json %}
{
	"data": true
}
{% endhighlight %}

**Returned Values**:

- data (bool) - Was the request fulfilled successfully
	* Note: The returned object's `errorcode` and this field may not match. Meaning the request itself may have completed successfully, but saving the data did not.

**Permissions Needed**:

- Edit user (not needed to revoke user's own key)

[&#8657; Top](#index)

* * * * *

newkey
------

**Endpoint**: `/api/keymanager/newkey`

**Parameters**: None

**Description**: Get a new key for user who is associated with the apikey being used.

**Returned Data**:

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
