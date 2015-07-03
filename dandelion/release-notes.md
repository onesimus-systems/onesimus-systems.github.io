---
layout: page-no-title
title: Dandelion - Release Notes
permalink: /dandelion/release-notes/
---

Dandelion - Release Notes
-------------------------

**v6.1.0** - **Unstable (develop branch)**

**v6.0.2** - **Current Stable (master branch)**

- Fixed: Category rendering in IE
- Fixed (in 6.0.1): Theme rendering in IE
- Fixed: Session expiration
- Fixed: Updating application version causes infinite redirect

**v6.0.0**

- New: Interface update
    * Dandelion has been updated with a fresh, new look. But don't worry, if you don't like the new look, just switch to the Legacy theme.
- New: The category of a log can be edited
- New: Unified, simplified, and more powerful search!!!
    * Search now uses a simple syntax to search any part of a log
    * Sample syntax: ```title:"router 1" categories:"Configuration:Routes"```
    * [Documentation](/dandelion/search)
- Improved: Completed and cleaned public API
    * All tasks can now be done through the API.
    * [Documentation](/dandelion/api)
- Improved: Major source rewrite
    * This help development in several ways:
        * Isolated public and application folders
        * Improved application structure for looser dependencies
        * Ability to easily implement different databases (Postgres and SQLite coming)
        * New routing functionality
        * Better templating
        * Cleaner bootstrap and application initialization
- Improved: Theme management system
    * Themes are handled a bit more elegantly and the structure have been simplified. Making creating themes much easier.
- Improved: Replaced TinyMCE with jHtmlArea
- Removed: The mail system has been removed because it didn't fit well with the purpose of Dandelion

**v5.0.3**

- Bug fix: No spellcheck in TinyMCE editor

**v5.0.1**

- Bug fix: User's name not showing on filtered logs

**v5.0.0**

- Rights management
- Internal email system
- Better look and feel when adding/editing logs
- Migration to fill jQuery utilization
- Cheesto status is set without extra button click
- Internal and Public API (the public API is disabled by default)
    * Can be disabled/enabled at will
    * Per user API keys
    * Available APIs:
        - Read/Update Cheesto Status
        - Read log entries
        - Key management
        - Test API key
- Code refactoring
    * Consolidation of methods
    * Working on consistant formatting
    * Namespacing
    * Modularization

**v4.6.0**

- Better theme handling
    * Easier to create themes
    * Admins can set a default theme
- Cheesto can be disabled site-wide
- Internal APIs for stylesheet and JS loading
- PHP session cookies are identified with a unique prefix
- Tutorial no longer show for new users, it's still available in the menu
- Bug fixes
- Code refactoring

**v4.5.1**

- Added compatibility libraries for older PHP versions
    * password_combat for PHP 5.5 password_* functions

- Major bug fixes
    * JSON syntax error for category display
    * Incorrect boolean value for add logs
    * Old column name for presence table when adding user
    * Incorrect file names

**v4.5.0**

- Filter by category from each log entry
- Admin ability to backup database
- Database prefix so Dandelion doesn't conflict for other apps
- Bug fixes

**v4.4.0**

- Lots of under the hood changes
- Mainly bug fix and optimization

**v4.3.1**

- Fixed issue where Cheesto couldn't get a time and message from user

**v4.3.0**

- Fixed compatibility bug with IE on Windows 7 (Dandelion is compatible with IE9+)
- Added category management
- Other bugs

**v4.2.1**

- Fixed bug where category filter wasn't using updated AJAX API

**< v4.2.1**

- Uhhh.... Stuffz
