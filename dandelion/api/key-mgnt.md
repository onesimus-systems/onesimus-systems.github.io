---
layout: page-no-title
title: Dandelion - API - Key Management
permalink: /dandelion/api/key-mgnt/
---

Dandelion - API Documentation - Key Management
----------------------------------------------

Index
-----

- [revokekey](#revokekey)
- [newkey](#newkey)

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

* * * * *

[&#8656; API Documentation](/dandelion/api)
