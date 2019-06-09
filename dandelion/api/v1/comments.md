---
layout: page-no-title
title: Dandelion - API - Comments
permalink: /dandelion/api/v1/comments/
---

Dandelion - API Documentation - Comments
----------------------------------------

Module name: comments

Index
-----

- [add](#add)
- [get](#get)

add
---

**Endpoint**: `/api/comments/add`

**Method**: `POST`

**Parameters**: `[logid]`, `[comment]`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `logid`       | int    |         | true     |
| `comment`     | string |         | true     |

**Description**: Create a new comment on the given log.

**Example Return Data**:

{% highlight json %}
{
	"data": "Comment created successfully"
}
{% endhighlight %}

**Permissions Needed**:

- Add Comment

[&#8657; Top](#index)

* * * * *

get
------

**Endpoint**: `/api/comments/get`

**Method**: `GET`

**Parameters**: `[logid]`, `[order]`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `logid`       | int    |         | true     |
| `order`       | string | 'new'   | false    |

**Description**: Retrieve comments for a log entry. `order` can be either 'new'
or 'old' to sort the comments.

**Example Return Data**:

{% highlight json %}
{
	"data": [
		{
			"id": 1,
			"user_id": 1,
			"comment": "Hello",
			"created": "2019-06-09 15:15:20",
			"log_id": 2,
			"fullname": "Administrator"
		}
	]
}
{% endhighlight %}

**Returned Values**:

- id (int) - ID number of comment
- user_id (int) - ID of user who created the comment
- comment (string) - Comment text
- created (string) - Date and time the comment was created 'Y-m-d H:i:s'
- log_id (int) - ID number of the log entry
- fullname (string) - Name of user who created comment

**Permissions Needed**:

- View logs

[&#8657; Top](#index)

* * * * *

[&#8656; API Documentation](/dandelion/api/v1)
