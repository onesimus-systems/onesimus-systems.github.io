---
layout: page-no-title
title: Dandelion - Search
permalink: /dandelion/search/
---

Searching Logs in Dandelion
---------------------------

**Search syntax**: `field:"query"`

**Available fields**: `title`, `body`, `log` (both title and body), `date`, `category`

**Escaped characters**

* backslash `\`
* double quote `"`
* exclamation mark `!` (if used at beginning of query and not for negation, e.g. `title:"\!query"`)

**Operators**

| Operator | Field | Description                     |
|:--------:|-------|---------------------------------|
| !        | all   | Negates query                   |
| <        | date  | Date created before query       |
| <=       | date  | Date created before or on query |
| >        | date  | Date created after query        |
| >=       | date  | Date created after or on query  |

**Special Syntax**

* **Note**: Searches are case insensative
* Date range: `date:"2015-01-01 to 2015-01-30"` returns logs with date in the range. This also takes the negation operator returning then the logs whose date is not in the range.
* Date keywords: The date fields takes the words `today`, `yesterday`, and `last week` as queries. They will be translated into the appropriate date relative to when the query was performed.

Examples
--------

- Log contains "server room": `log:"server room"` or `server room`
    * When using just the `log` field, the field name and quotes may be omitted

- Title contains "windows": `title:"windows"`
- Title does not contain "windows": `title:"!windows"`
- Title with escaped exclamation mark: `title:"\!windows"` (searches for the text "!windows")
- Title with exclamation mark: `title:"Windows!"` (searches for the text "windows!", notice no escaping is necassary since it's not the first character)
- Title with double quote: `title:"Turtles \"are\" awesome"`
- Body contains "text": `body:"text"`
- Category begins with "Logs:Server 1": `category:"Logs:Server 1"`
- Title contains "windows" in category "Server Room 1": `title:"windows" category:"Server Room 1"`

Dates:

- Log created on 02/18/2015: `date:"2015-02-18"`
- Logs created after 02/18/2015: `date:">2015-02-18"`
- Logs created between 01/01/2015 and 01/30/2015: `date:"2015-01-01 to 2015-01-30"`
- Logs not created between 01/01/2015 and 01/30/2015: `date:"!2015-01-01 to 2015-01-30"`
- Logs created yesterday: `date:"yesterday"`

And of course they can be used together:

- `title:"windows" date:"2015-02-18"`
