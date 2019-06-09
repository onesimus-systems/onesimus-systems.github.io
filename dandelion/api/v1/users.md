---
layout: page-no-title
title: Dandelion - API - User Management
permalink: /dandelion/api/v1/users/
---

Dandelion - API Documentation - User Management
-----------------------------------------------

Module name: users

Index
-----

- [resetpassword](#resetpassword)
- [create](#create)
- [edit](#edit)
- [delete](#delete)
- [enable](#enable)
- [disable](#disable)
- [getusers](#getusers)
- [getuser](#getuser)

resetpassword
-------------

**Endpoint**: `/api/users/resetpassword`

**Method**: `POST`

**Parameters**: `[uid]`, `pw`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `uid`         | int    |         | false    |
| `pw`			| string |		   | true	  |

**Description**: Reset password for `uid` (defaults to API key user) to password `pw`.

**Example Return Data**:

{% highlight json %}
{
	"data": "Success or error message"
}
{% endhighlight %}

**Returned Values**:

- data (string) - User displayable string if the save was successful or not

**Permissions Needed**:

- Edit user (if `uid` is given)

[&#8657; Top](#index)

* * * * *

create
------

**Endpoint**: `/api/users/create`

**Method**: `POST`

**Parameters**: `username`, `password`, `fullname`, `role`, `[cheesto]`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `username`    | string |         | true     |
| `password`    | string |         | true     |
| `fullname`    | string |         | true     |
| `role`        | int    |         | true     |
| `cheesto`     | string | true    | false    |

**Description**: Create new user. The `cheesto` parameter determines if a Ĉeesto account will be created for this user. `role` is the ID of the group to which the user should belong. (See [Rights getlist function](/dandelion/api/v1/rights/#getlist))

**Example Return Data**:

{% highlight json %}
{
	"data": "Success or error message"
}
{% endhighlight %}

**Returned Values**:

- data (string) - User displayable string if the save was successful or not

**Permissions Needed**:

- Create user

[&#8657; Top](#index)

* * * * *

edit
----

**Endpoint**: `/api/users/edit`

**Method**: `POST`

**Parameters**: `uid`, `[fullname]`, `[role]`, `[prompt]`, `[theme]`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `uid`         | int    |         | true     |
| `fullname`    | string |         | false    |
| `role`        | int    |         | false    |
| `prompt`      | int    |         | false    |
| `theme`       | string |         | false    |

**Description**: Edit properties of a user. The defaults for optional parameters are the values currently present on the user.

**Example Return Data**:

{% highlight json %}
{
	"data": "Success or error message"
}
{% endhighlight %}

**Returned Values**:

- data (string) - User displayable string if the save was successful or not

**Permissions Needed**:

- Edit user

[&#8657; Top](#index)

* * * * *

delete
------

**Endpoint**: `/api/users/delete`

**Method**: `POST`

**Parameters**: `uid`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `uid`         | int    |         | true     |

**Description**: Delete user `uid`.

**Example Return Data**:

{% highlight json %}
{
	"data": "Success or error message"
}
{% endhighlight %}

**Returned Values**:

- data (string) - User displayable string if the save was successful or not

**Permissions Needed**:

- Delete user

[&#8657; Top](#index)

* * * * *

enable
------

**Endpoint**: `/api/users/enable`

**Method**: `POST`

**Parameters**: `uid`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `uid`         | int    |         | true     |

**Description**: Enable user `uid`.

**Example Return Data**:

{% highlight json %}
{
	"data": "Success or error message"
}
{% endhighlight %}

**Returned Values**:

- data (string) - User displayable string if the save was successful or not

**Permissions Needed**:

- Edit user

**Dandelion Version**

- 6.1.0

[&#8657; Top](#index)

* * * * *

disable
------

**Endpoint**: `/api/users/disable`

**Method**: `POST`

**Parameters**: `uid`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `uid`         | int    |         | true     |

**Description**: Disable user `uid`.

**Example Return Data**:

{% highlight json %}
{
	"data": "Success or error message"
}
{% endhighlight %}

**Returned Values**:

- data (string) - User displayable string if the save was successful or not

**Permissions Needed**:

- Edit user

**Dandelion Version**

- 6.1.0

[&#8657; Top](#index)

* * * * *

getusers
--------

**Endpoint**: `/api/users/getusers`

**Method**: `GET`

**Parameters**: None

**Description**: Get list of user's and their information

**Example Return Data**:

{% highlight json %}
{
	"data": {
		"0": {
			"id": "1",
			"fullname": "Admin",
			"username": "admin",
			"group_id": "1",
			"created": "2014-01-1",
			"theme": "Halloween",
			"initial_login": "0",
			"disabled": false
		}
	}
}
{% endhighlight %}

**Returned Values**:

**Per User**

- id (int) - ID of user
- fullname (string) - Full name of user
- username (string) - ...username
- group_id (int) - ID for user's group
- created (string, date) - When the user was created
- theme (string) - Preferred theme of user
- initial_login (int) - Value to determine if user needs to reset password, also reserved for future use
- disabled (bool) - Whether or not the user is disabled

**Permissions Needed**:

- Edit user

**Notes**:

- The `disabled` field was added in version 6.1.

[&#8657; Top](#index)

* * * * *

getuser
-------

**Endpoint**: `/api/users/getuser`

**Method**: `GET`

**Parameters**: `uid`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `uid`         | int    |         | false (see note 2) |

**Description**: Get information for user `uid`. If `uid` is not given, the user of the API key will be assumed.

**Example Return Data**:

{% highlight json %}
{
	"data": {
		"0": {
			"id": "1",
			"fullname": "Admin",
			"username": "admin",
			"group_id": "1",
			"created": "2014-01-1",
			"theme": "Halloween",
			"initial_login": "0",
			"disabled": false
		}
	}
}
{% endhighlight %}

**Returned Values**:

**Per User**

- id (int) - ID of user
- fullname (string) - Full name of user
- username (string) - ...username
- group_id (int) - ID for user's group
- created (string, date) - When the user was created
- theme (string) - Preferred theme of user
- initial_login (int) - Value to determine if user needs to reset password, also reserved for future use
- disabled (bool) - Whether or not the user is disabled

**Permissions Needed**:

- Edit user

**Notes**:

1. The `disabled` field was added in version 6.1.
2. The `uid` parameter was required up to version 6.1.

[&#8657; Top](#index)

* * * * *

[&#8656; API Documentation](/dandelion/api/v1)
