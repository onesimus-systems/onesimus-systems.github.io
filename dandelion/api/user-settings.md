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
| `theme`   | string | 'modern'  | false    |

**Description**: Saves the user's preferred theme for the official Dandelion UI. A list of available themes can be received by calling the `getthemelist` task. `theme` should be the slug of the desired theme. A request without `theme` will reset to the instance default (Modern is the default theme for a new instance).

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
		"0": {
			"author": "Author",
			"description": "Awesome theme",
			"email": "author@example.org",
			"extends": "",
			"files": [],
			"name": "The Best Theme",
			"selected": "false",
			"slug": "best-theme",
			"version": "1.2.3"
		}
	}
}
{% endhighlight %}

**Returned Values**:

**Per Theme**

- author (string) - Theme author
- description (string) - Theme description
- email (string) - Author/developer email
- extends (string) - Theme this theme extends
- files (array) - Manual mapping of page names to files
- name (string) - Theme name
- selected (bool) - Whether or not the user is using this theme
- slug (string) - Shorthand identifier for theme (used to set theme)
- version (string) - Theme version

**Permissions Needed**:

- None

[&#8657; Top](#index)

* * * * *

[&#8656; API Documentation](/dandelion/api)
