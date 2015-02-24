---
layout: page-no-title
title: Dandelion - API - Logs Module
permalink: /dandelion/api/logs/
---

Dandelion - API Documentation - Logs Module
-------------------------------------------

Module Name: logs

Index
-----

- [read](#read)
- [readone](#readone)
- [create](#create)
- [edit](#edit)
- [search](#search)

read
----

**Endpoint**: `/api/logs/read`

**Parameters**: `[offset]`, `[limit]`

| Parameter | Type | Default | Required |
|-----------|------|---------|----------|
| `offset`  | int  | 0       | false    |
| `limit`	| int  |<span title="User defined">UD</span> | false |

**Description**: Returns `limit` number of logs newest first. `offset` is used for pagination.

**Returned Data** (array of logs):

{% highlight json %}
{
	"data": {
		"0": {
			"logid": "1",
			"datec": "2015-02-12",
			"timec": "12:24:53",
			"title": "Log title",
			"entry": "Log content, contains HTML",
			"usercreated": "1",
			"cat": "Logs",
			"edited": "0",
			"realname": "Admin",
			"canEdit": true
		}
	}
}
{% endhighlight %}

**Returned Values**:

- logid (int) - ID number of log
- datec (string) - Date log was created formatted in Y-m-d
- timec (string) - Time log was created formated in H:i:s
- title (string) - Title of log
- entry (string) - Body of log
- usercreated (int) - ID of user who created the log
- cat (string) - String representation of the log's category
- edited (bool) - Has the log been edited, 0 or 1
- realname (string) - Name of user who created log
- canEdit (bool) - Does the user have permission to edit the log (for visual clues only, actual permissions are enforced server-side)

**Permissions Needed**:

- Read log

[&#8657; Top](#index)

* * * * *

readone
-------

**Endpoint**: `/api/logs/readone`

**Parameters**: `logid`

| Parameter | Type | Default | Required |
|-----------|------|---------|----------|
| `logid`   | int  | 		 | true     |

**Description**: Returns log with id of `logid`.

**Returned Data** (single log, always index 0 (data[0])):

{% highlight json %}
{
	"data": {
		"0": {
			"logid": "1",
			"datec": "2015-02-12",
			"timec": "12:24:53",
			"title": "Log title",
			"entry": "Log content, contains HTML",
			"usercreated": "1",
			"cat": "Logs",
			"edited": "0",
			"realname": "Admin",
			"canEdit": true
		}
	}
}
{% endhighlight %}

**Returned Values**:

- logid (int) - ID number of log
- datec (string) - Date log was created formatted in Y-m-d
- timec (string) - Time log was created formated in H:i:s
- title (string) - Title of log
- entry (string) - Body of log
- usercreated (int) - ID of user who created the log
- cat (string) - String representation of the log's category
- edited (bool) - Has the log been edited, 0 or 1
- realname (string) - Name of user who created log
- canEdit (bool) - Does the user have permission to edit the log (for visual clues only, actual permissions are enforced server-side)

**Permissions Needed**:

- Read log

[&#8657; Top](#index)

* * * * *

create
------

**Endpoint**: `/api/logs/create`

**Parameters**: `title`, `body`, `cat`

| Parameter | Type   | Default | Required |
|-----------|--------|---------|----------|
| `title`   | string | 		   | true     |
| `body`    | string | 		   | true     |
| `cat`     | string | 		   | true     |

**Description**: Create a new log with `title` and content `body`. `cat` should be a string of the category separated by colons for each level. E.g. "Logs:Networking"

**Returned Data**:

{% highlight json %}
{
	"data": "Message indicating success of failure"
}
{% endhighlight %}

**Returned Values**:

- data (string) - Message that can be displayed to a user indicating either success or report an error if failed.

**Permissions Needed**:

- Create log

[&#8657; Top](#index)

* * * * *

edit
----

**Endpoint**: `/api/logs/edit`

**Parameters**: `logid`, `title`, `body`, `cat`

| Parameter | Type   | Default | Required |
|-----------|--------|---------|----------|
| `logid`   | int    | 		   | true     |
| `title`   | string | 		   | true     |
| `body`    | string | 		   | true     |
| `cat`     | string | 		   | true     |

**Description**: Edit log with `logid` using `title` and content `body`. `cat` should be a string of the category separated by colons for each level. E.g. "Logs:Networking"

**Returned Data**:

{% highlight json %}
{
	"data": "Message indicating success of failure"
}
{% endhighlight %}

**Returned Values**:

- data (string) - Message that can be displayed to a user indicating either success or report an error if failed.

**Permissions Needed**:

- Edit log

[&#8657; Top](#index)

* * * * *

search
------

**Endpoint**: `/api/logs/search`

**Parameters**: `query`, `[offset]`, `[limit]`

| Parameter | Type   | Default | Required |
|-----------|--------|---------|----------|
| `query`   | string | 		   | true	  |
| `offset`  | int    | 0       | false    |
| `limit`	| int    |<span title="User defined">UD</span> | false |

**Description**: Returns `limit` number of logs matching `query`. `offset` is used for pagination. If you want to get all the logs that match the query, pass a rather large number as the `limit`.

**Returned Data** (array of logs):

{% highlight json %}
{
	"data": {
		"0": {
			"logid": "1",
			"datec": "2015-02-12",
			"timec": "12:24:53",
			"title": "Log title",
			"entry": "Log content, contains HTML",
			"usercreated": "1",
			"cat": "Logs",
			"edited": "0",
			"realname": "Admin"
		}
	}
}
{% endhighlight %}

**Returned Values**:

- logid (int) - ID number of log
- datec (string) - Date log was created formatted in Y-m-d
- timec (string) - Time log was created formated in H:i:s
- title (string) - Title of log
- entry (string) - Body of log
- usercreated (int) - ID of user who created the log
- cat (string) - String representation of the log's category
- edited (bool) - Has the log been edited, 0 or 1
- realname (string) - Name of user who created log

**Permissions Needed**:

- Read log

**Additional Information**:

For the syntax of a search query, see the [search documentation](/dandelion/search).

[&#8657; Top](#index)

* * * * *

[&#8656; API Documentation](/dandelion/api)
