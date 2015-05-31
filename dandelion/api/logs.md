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
- [create](#create)
- [edit](#edit)
- [search](#search)

read
----

**Endpoint**: `/api/logs/read`

**Parameters**: `[offset]`, `[limit]`

| Parameter | Type | Default | Required |
|-----------|------|---------|----------|
| `logid`   | int  | 		 | false    |
| `offset`  | int  | 0       | false    |
| `limit`	| int  |<span title="User defined">UD</span> | false |

**Description**: Returns `limit` number of logs newest first. `offset` is used for pagination. If `logid` is sent, then only the log with that id is returned. No metadata is returned for a request using `logid`.

**Example Return Data** (array of logs):

{% highlight json %}
{
	"data": {
		"0": {
			"id": "1",
			"date_created": "2015-02-12",
			"time_created": "12:24:53",
			"title": "Log title",
			"body": "Log content, contains HTML",
			"user_id": "1",
			"category": "Logs",
			"is_edited": "0",
			"fullname": "Admin",
			"canEdit": true
		},
		"metadata": {
			"limit": "25",
			"logSize": "1000",
			"offset": "0",
			"resultCount": "25"
		}
	}
}
{% endhighlight %}

**Returned Values**:

**Per Log**

- id (int) - ID number of log
- date_created (string) - Date log was created formatted in Y-m-d
- time_created (string) - Time log was created formated in H:i:s
- title (string) - Title of log
- body (string) - Body of log
- user_id (int) - ID of user who created the log
- category (string) - String representation of the log's category
- is_edited (bool) - Has the log been edited, 0 or 1
- fullname (string) - Name of user who created log
- canEdit (bool) - Does the user have permission to edit the log (for visual clues only, actual permissions are enforced server-side)

**Metadata** (not returned if `logid` is used)

- limit (int) - User defined number of logs to return
- logSize(int) - Number of total logs
- offset (int) - Database ID offset used to get results
- resultCount (int) - Number of logs returned

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

**Example Return Data**:

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

**Example Return Data**:

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

**Example Return Data** (array of logs):

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
		},
		"metadata": {
			"limit": "25",
			"logSize": "1000",
			"offset": "0",
			"resultCount": "25"
		}
	}
}
{% endhighlight %}

**Returned Values**:

**Per Log**

- id (int) - ID number of log
- date_created (string) - Date log was created formatted in Y-m-d
- time_created (string) - Time log was created formated in H:i:s
- title (string) - Title of log
- body (string) - Body of log
- user_id (int) - ID of user who created the log
- category (string) - String representation of the log's category
- is_edited (bool) - Has the log been edited, 0 or 1
- fullname (string) - Name of user who created log
- canEdit (bool) - Does the user have permission to edit the log (for visual clues only, actual permissions are enforced server-side)

**Metadata**

- limit (int) - User defined number of logs to return
- logSize(int) - Number of total logs
- offset (int) - Database ID offset used to get results
- resultCount (int) - Number of logs returned

**Permissions Needed**:

- Read log

**Additional Information**:

For the syntax of a search query, see the [search documentation](/dandelion/search).

[&#8657; Top](#index)

* * * * *

[&#8656; API Documentation](/dandelion/api)
