---
layout: page-no-title
title: Dandelion - API - Rights
permalink: /dandelion/api/rights/
---

Dandelion - API Documentation - Rights
--------------------------------------

Module name: rights

Index
-----

- [getlist](#getlist)
- [getgroup](#getgroup)
- [create](#create)
- [edit](#edit)
- [delete](#delete)
- [getuserrights](#getuserrights)

getlist
-------

**Endpoint**: `/api/rights/getlist`

**Parameters**: None

**Description**: Get list of role names and their IDs.

**Example Return Data**:

{% highlight json %}
{
	"data": [
		{
			"id": "1",
			"role": "user"
		},
		{
			"id": "2",
			"role": "admin"
		},
		{
			"id": "3",
			"role": "guest"
		}
	]
}
{% endhighlight %}

**Returned Values**:

- id (int) - ID of role, used to get the permissions with [getgroup](#getgroup)
- role (string) - Name of role/group

**Permissions Needed**:

- None

[&#8657; Top](#index)

* * * * *

getgroup
--------

**Endpoint**: `/api/rights/getgroup`

**Parameters**: `groupid`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `groupid`     | int    |         | true     |

**Description**: Get array of permissions for group

**Example Return Data**:

{% highlight json %}
{
	"data": {
		"id": "3",
		"role": "guest",
		"permissions": {
			"createlog": false,
			"editlog": false,
			... (see full list below)
		}
		"permissionNames": {
			"createlog": "Create a log entry",
			"editlog": "Edit any log entry",
			...
		}
	}
}
{% endhighlight %}

**Returned Values**:

- id (int) - ID of role, used to get the permissions with [getgroup](#getgroup)
- role (string) - Name of role/group
- permissions (array) - Keyed array of permission names and their values
- permissionNames (array) - Keyed array of human readable permission names keyed to their respecive permission

**Permissions Needed**:

- None

[&#8657; Top](#index)

* * * * *

create
------

**Endpoint**: `/api/rights/create`

**Parameters**: `name`, `rights`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `name`        | string |         | true     |
| `rights`      | string |         | false    |

**Description**: Create a new group named `name` and assign it the permissions `rights`. `rights` is a stringified JSON object with the format as returned by the [getuserrights](#getuserrights) endpoint. If `rights` is omitted, the group is blank meaning it has no permission set to true by default.

**Example Return Data**:

{% highlight json %}
{
	"data": "Success or error message"
}
{% endhighlight %}

**Returned Values**:

- data (string) - User displayable string if the creation was successful or not

**Permissions Needed**:

- Add group

[&#8657; Top](#index)

* * * * *

edit
----

**Endpoint**: `/api/rights/edit`

**Parameters**: `groupid`, `rights`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `groupid`     | int    |         | true     |
| `rights`      | string |         | true     |

**Description**: Edit `groupid` and assign it the permissions `rights`. `rights` is a stringified JSON object with the format as returned by the [getuserrights](#getuserrights) endpoint.

**Example Return Data**:

{% highlight json %}
{
	"data": "Success or error message"
}
{% endhighlight %}

**Returned Values**:

- data (string) - User displayable string if the save was successful or not

**Permissions Needed**:

- Edit group

[&#8657; Top](#index)

* * * * *

delete
------

**Endpoint**: `/api/rights/delete`

**Parameters**: `groupid`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `groupid`     | int    |         | true     |

**Description**: Delete group `groupid`

**Example Return Data**:

{% highlight json %}
{
	"data": "Success or error message"
}
{% endhighlight %}

**Returned Values**:

- data (string) - User displayable string if the delete was successful or not

**Permissions Needed**:

- Delete group

[&#8657; Top](#index)

* * * * *

getuserrights
-------------

**Endpoint**: `/api/rights/getuserrights`

**Parameters**: None

**Description**: Get permissions for current user (user of key).

**Example Return Data**:

{% highlight json %}
{
	"data": {
		"createlog": false,
		"editlog": false,
		... (see full list below)
	}
}
{% endhighlight %}

**Returned Values**:

- permissions (array) - Keyed array of permission names and their values

**Permissions Needed**:

- None

[&#8657; Top](#index)

* * * * *

Full permission list:

- "createlog": false
- "editlog": false
- "viewlog": true
- "createcat": false
- "editcat": false
- "deletecat": false
- "createuser": false
- "edituser": false
- "deleteuser": false
- "creategroup": false
- "editgroup": false
- "deletegroup": false
- "viewcheesto": true
- "updatecheesto": false
- "admin": false

* * * * *

[&#8656; API Documentation](/dandelion/api)

