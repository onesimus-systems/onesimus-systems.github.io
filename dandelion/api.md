---
layout: page-no-title
title: Dandelion - General Use Help
permalink: /dandelion/api/
---

Dandelion - API Documentation
-----------------------------

The Dandelion API is a simplistic and standardized way of getting data from a Dandelion instance. To make an api request, you'll need the API key for a user and the hostname. The urls take the form of `http[s]://[path-to-dandelion]/api/{module}/{task}`. Every call requires some HTTP parameters to be passed either through GET or POST. The permissions used for the call comes from the user's key.

All request must pass the parameter `apikey` containing the user's key. If this parameter doesn't exist the call will fail.

The table below outlines the available endpoints, their paths, parameters, and what they do. A value in angle brackets after a parameter name indicates the default value if omitted, parameters without these are required. The value in parenthesis indicates its type.

API Enpoints
------------

Logs
----

|Module Path|Task|Parameters|Description|
|--|--|--|--|
|/api/logs/ | read | offset[0] (int), limit[?] (int) | Returns [limit] number of logs newest first. [offset] is used for pagination. The default value for [limit] is dictated by the user's setting.
|/api/logs/ | readone | logid (int) | Returns a single log whose ID is [logid].
|/api/logs/ | create | title (string), body (string), category (string) | Create a new log with [title] and content [body]. [category] should be a string of the category separated by colons for each level. E.g. "Logs:Networking"
|/api/logs/ | edit | logid (int), title (string), body (string), category (string) | Edit log with [logid] using [title] and content [body]. [category] should be a string of the category separated by colons for each level. E.g. "Logs:Networking"
|/api/logs/ | search | query (string), offset[0] (int), limit[?] (int) | Returns [limit] number of logs matching [query]. [offset] is used for pagination. If you want to get all the logs that match the query, pass a rather large number as the [limit]. The default value for [limit] is dictated by the user's setting.
