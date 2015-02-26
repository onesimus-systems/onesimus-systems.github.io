---
layout: page-no-title
title: Dandelion - API - Ĉeesto
permalink: /dandelion/api/cheesto/
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

**Parameters**: `[uid]`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `uid`         | int    |         | false    |

**Description**: Get the statuses for Ĉeesto enabled users. If `uid` is given, only that user's status will be returned.

**Example Return Data**:

{% highlight json %}
{
	"data": {
		"0": {
			"id": "1",
			"uid": "1",
			"realname": "Admin",
			"status": "0",
			"message": "",
			"returntime": "00:00:00",
			"dmodified": "2015-01-06 16:16:58",
			"statusInfo": {
				"symbol":"&#x2713;",
				"color":"green"
			}
		},
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

- "0": Row of data for each Ĉeesto user
	* id (int) - Ĉeesto ID of user
	* uid (int) - ID of associated user
	* realname (string) - Name of user
	* status (int) - ID of status (associated with index of statusOptions)
	* message (string) - Away message
	* returntime (string, time) - Time set by user of their return to "Available"
	* dmodified (string, datetime) - When the status was last modified
	* statusInfo (array) - Symbol and color associated with the set status (used in official UI)
		* symbol (string) - HTML encoded symbol either &#x2713;, &#8709;, or &#x2717;
		* color (string) - Color associated with status either green, blue, or red
- statusOptions (array) - List of available statuses. Their index constitues the "status" field for a user

**Permissions Needed**:

- Read Ĉeesto

[&#8657; Top](#index)

* * * * *

update
------

**Endpoint**: `/api/cheesto/update`

**Parameters**: `[uid]`, `[message]`, `[status]`, `[returntime]`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `uid`         | int    |         | false    |
| `message`     | string | Empty   | false    |
| `status`      | int    | 0       | false    |
| `returntime`  | string | 'Today' | false	  |

**Description**: Update the status of user `uid` (defaults to ID of API key user). If this request is sent with no parameters, it will assign the user to the status of 'Available' (0) with an empty message and return time of 'Today'.

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

**Parameters**: None

**Description**: Get the available status texts.

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

[&#8656; API Documentation](/dandelion/api)
