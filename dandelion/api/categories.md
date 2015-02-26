---
layout: page-no-title
title: Dandelion - API - Categories
permalink: /dandelion/api/categories/
---

Dandelion - API Documentation - Categories
------------------------------------------

Module name: categories

Index
-----

- [create](#create)
- [edit](#edit)
- [delete](#delete)

create
------

**Endpoint**: `/api/categories/create`

**Parameters**: `pid`, `description`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `pid`         | int    |         | true     |
| `description` | string |         | true     |

**Description**: Create a new category whose parent is the category with id `pid` and whose description/text is `description`. A `pid` of 0 indicates a root category.

**Example Return Data**:

{% highlight json %}
{
	"data": "Success or error message"
}
{% endhighlight %}

**Returned Values**:

- data (string) - User displayable string if the save was successful or not

**Permissions Needed**:

- Create category

[&#8657; Top](#index)

* * * * *

edit
----

**Endpoint**: `/api/categories/edit`

**Parameters**: `cid`, `description`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `cid`         | int    |         | true     |
| `description` | string |         | true     |

**Description**: Update category `cid` with the description/text `description`.

**Example Return Data**:

{% highlight json %}
{
	"data": "Success or error message"
}
{% endhighlight %}

**Returned Values**:

- data (string) - User displayable string if the save was successful or not

**Permissions Needed**:

- Edit category

[&#8657; Top](#index)

* * * * *

delete
----

**Endpoint**: `/api/categories/delete`

**Parameters**: `cid`

| Parameter     | Type   | Default | Required |
|---------------|--------|---------|----------|
| `cid`         | int    |         | true     |

**Description**: Delete category `cid`. This operation will reassign all children categories to the parent of the deleted category. This will not affect the category associated with logs. Logs with the deleted category will remain in that category.

**Example Return Data**:

{% highlight json %}
{
	"data": "Success or error message"
}
{% endhighlight %}

**Returned Values**:

- data (string) - User displayable string if the save was successful or not

**Permissions Needed**:

- Delete category

[&#8657; Top](#index)

* * * * *

[&#8656; API Documentation](/dandelion/api)
