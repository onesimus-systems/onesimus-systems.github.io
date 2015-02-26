---
layout: page-no-title
title: Dandelion - API - User Settings
permalink: /dandelion/api/user-settings/
---

Dandelion - API Documentation - User Settings
---------------------------------------------

Module name: usersettings

Index
-----

- [saveloglimit](#saveloglimit)
- [savetheme](#savetheme)
- [getthemelist](#getthemelist)

saveloglimit
------------

**Endpoint**: `/api/usersettings/saveloglimit`

**Parameters**: `[limit]`

| Parameter | Type   | Default | Required |
|-----------|--------|---------|----------|
| `limit`   | int    | 25      | false    |

**Description**: Log limit is the number of logs to show per page on the dashboard, and the number of logs to return by default from a logs read command without a limit. A request without `limit` is effectivly resetting the setting.

**Example Return Data**:

{% highlight json %}
{
	"data": "Success or error message"
}
{% endhighlight %}

**Returned Values**:

- data (string) - User displayable string if the save was successful or not

**Permissions Needed**:

- None

[&#8657; Top](#index)

* * * * *

savetheme
---------

**Endpoint**: `/api/usersettings/savetheme`

**Parameters**: `[theme]`

| Parameter | Type   | Default   | Required |
|-----------|--------|-----------|----------|
| `theme`   | string | 'default' | false    |

**Description**: Saves the user's preferred theme for the official Dandelion UI. A list of available themes can be received by calling the `getthemelist` task. A request without `theme` is effectivly resetting the setting.

**Example Return Data**:

{% highlight json %}
{
	"data": "Success or error message"
}
{% endhighlight %}

**Returned Values**:

- data (string) - User displayable string if the save was successful or not

**Permissions Needed**:

- None

[&#8657; Top](#index)

* * * * *

getthemelist
------------

**Endpoint**: `/api/usersettings/getthemelist`

**Parameters**: None

**Description**: Returns an array of theme names.

**Example Return Data**:

{% highlight json %}
{
	"data": {
		"theme1",
		"theme2"
	}
}
{% endhighlight %}

**Returned Values**:

- data (array) - Theme names, use these names to save a theme for a user

**Permissions Needed**:

- None

[&#8657; Top](#index)

* * * * *

[&#8656; API Documentation](/dandelion/api)
