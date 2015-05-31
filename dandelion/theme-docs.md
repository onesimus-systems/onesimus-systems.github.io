---
layout: page-no-title
title: Dandelion - Theme Documentation
permalink: /dandelion/theme-docs/
---

Dandelion - Theme Documentation
-------------------------------

Themes allow you to change the appearence of Dandelion. Right now only support for CSS sheets is possible. There are plans to implement a more thorough themeing system to change even the PHP templates themselves as well as JS and the like.

Creating a Theme
----------------

All themes are located under `public/assets/themes`. Each theme has a folder named with the themes unique slug. The folder name must match the slug declared in the theme's metadata file.

The first piece of a theme is the metadata.json file. If a theme doesn't have a metadata.json file, the theme is considered invalid and won't be available for use. The schema is as follows:

{% highlight json %}
{
	"slug": "",
	"name": "",
	"author": "",
	"email": "",
	"description": "",
	"version": "",
	"files": {},
	"extends": ""
}
{% endhighlight %}

**Fields**

- slug - Unique identifier for theme, should contain only alphanumeric characters, underscore, or hyphen
- name - Actual name of the theme, displayed to users
- author - Author/developer's name
- email - Author/developer's email contact
- description - Description of theme
- version - Version number
- files - Manual mapping of stylesheets to pages (see below)
- extends - Theme slug if this theme extends another (see below)

None of the fields are required necessarily. If a slug isn't defined, the folder name will be used. If a name isn't defined, it will show as "Unnamed". The rest are for informational use.


How The System Works
--------------------

The theme system is fairly simple. There are predefined names for styles that each page will call for when being generated. For a complete theme it will be necassary to create a stylesheet for each name. For a theme that simply extends another, any styles in the extending theme will be loaded after the extended theme; more on that later. Here's the list of page names and where they show up:

- admin - Used on the main administration page
- dashboard - Used on the main dashboard
- editgroup - Used on the page to edit a groups permissions
- edituser - Used on the page to edit a user
- installer - Used on the initial installer page
- login - Used on the login screen
- main - Base styles for the entire theme, loaded on every page
- usersettings - Used on the user settings page

The `installer` can typically be left out. When a new instance is being installed most likely the user will still be using the default Modern theme. But for completeness it can be added.

The CSS files should be located directly in the themes folder with an extension of either `.css` or `.min.css`. The files should be named `[pagename][.min].css`. So for the dashboard styles it would be `dashboard.min.css` or `dashboard.css`. If you wish to use different names, then you can use the `files` fields in the metadata.json as follows:

{% highlight json %}
{
	"files": {
		"dashboard": "dash.css"
	}
}
{% endhighlight %}

As you can see, `files` is an array of pagename -> filename pairs. The `files` field takes highest priority. Meaning, if there's a `dashboard.css` file, but there's also a `files` entry mapping `dashboard` to `dash.css`, then the system will use `dash.css` and disregard the `dashboard.css` file.

Extending Themes
----------------

If there's no need to create a completely new theme, for example to change the colors or make small modifications to the default Modern theme, then a theme can extend another theme and change only the styles that are needed. To extend a theme, use the `extends` field in the metadata.json:

{% highlight json %}
{
	"extends": "modern"
}
{% endhighlight %}

The value of `extends` is the slug of the theme being extended. In this case, the theme above is extending the theme with the slug `modern`. Themes can extend in a chain as well. In other words, theme3 can extend theme2 which itself extends theme1. This chain can be up to 5 themes long. Most likely, it will only be 2 long. But it's nice to have options.

When a theme is extending another, the last theme in the chain is loaded first and then the next and so on. So, using the example from above, theme1's styles would be loaded first, then theme2's, and finally theme3's. This way, each theme stacks on top of the others.

To see what classes and ids are used, please see the Modern and Legacy themes included in Dandelion. They are your ultimate guide for what can be styled on each page. The Modern theme is the most complete. Both were created using LESS, but that is not necassary for a theme to be created.
