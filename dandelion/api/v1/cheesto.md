---
layout: page-no-title
title: Dandelion - API - Ĉeesto
permalink: /dandelion/api/v1/cheesto/
---

Dandelion - API Documentation - Ĉeesto
--------------------------------------

Module name: cheesto

Index
-----

- [read](#read)
- [update](#update)
- [statustexts](#statustexts)

read
----

**Endpoint**: `/api/cheesto/read`

**Method**: `GET`

**Parameters**: `[uid]`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `uid`         | int    |         | false    |

**Description**: Get the statuses for Ĉeesto enabled users. If `uid` is given, only that user's status will be returned.

**Example Return Data**:

{% highlight json %}
{
	"data": {
		"statuses": [{
			"id": "1",
			"user_id": "1",
			"fullname": "Admin",
			"status": "0",
			"message": "",
			"returntime": "00:00:00",
			"modified": "2015-01-06 16:16:58",
			"disabled": "0"
		}],
		"statusOptions": [
			"Available",
			"Away From Desk",
			"At Lunch",
			"Out for Day",
			"Out",
			"Appointment",
			"Do Not Disturb",
			"Meeting",
			"Out Sick",
			"Vacation"
		]
	}
}
{% endhighlight %}

**Returned Values**:

**Per User**

- id (int) - Ĉeesto ID of user
- user_id (int) - ID of associated user
- fullname (string) - Name of user
- status (int) - ID of status (associated with index of statusOptions)
- message (string) - Away message
- returntime (string, time) - Time set by user of their return to "Available"
- modified (string, datetime) - When the status was last modified
- disabled (bool) - Whether the cheesto account is disabled

**statusOptions**

- statusOptions (array) - List of available statuses. Their index constitues the "status" field for a user

**Permissions Needed**:

- Read Ĉeesto

[&#8657; Top](#index)

* * * * *

update
------

**Endpoint**: `/api/cheesto/update`

**Method**: `POST`

**Parameters**: `[uid]`, `[message]`, `[status]`, `[returntime]`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `uid`         | int    |         | false    |
| `message`     | string | Empty   | false    |
| `status`      | string | 'Available' | false    |
| `returntime`  | string | '00:00:00' | false	  |

**Description**: Update the status of user `uid` (defaults to ID of API key user). If this request is sent with no parameters, it will assign the user to the status of 'Available' with an empty message and return time of '00:00:00'.

**Example Return Data**:

{% highlight json %}
{
	"data": "Success or error message"
}
{% endhighlight %}

**Returned Values**:

- data (string) - User displayable string if the save was successful or not

**Permissions Needed**:

- Update Ĉeesto
- Edit user (if `uid` is given)

[&#8657; Top](#index)

* * * * *

statustexts
-----------

**Endpoint**: `/api/cheesto/statustexts`

**Method**: `GET`

**Parameters**: None

**Description**: Get the available status texts as defined in the app configuration.

**Example Return Data**:

{% highlight json %}
{
	"data": [
		"Available",
		"Away From Desk",
		"At Lunch",
		"Out for Day",
		"Out",
		"Appointment",
		"Do Not Disturb",
		"Meeting",
		"Out Sick",
		"Vacation"
	]
}
{% endhighlight %}

**Returned Values**:

- data (array) - List of available statuses. Their index constitues the "status" field for a user

**Permissions Needed**:

- None

[&#8657; Top](#index)

* * * * *

[&#8656; API Documentation](/dandelion/api/v1)
