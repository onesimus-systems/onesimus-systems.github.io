---
layout: page-no-title
title: Dandelion - Release Notes
permalink: /dandelion/release-notes/
---

Dandelion - Release Notes
-------------------------

**v6.0.0** - **Unstable (develop branch)**

- New: The category of a log can be edited
- New: Dandelion has undergone a major face lift
- Improved: The public API is completed. All tasks can now be done through the API.
    * [API Documentation](/dandelion/api)
- Improved: Unified, simplified, and more powerful search!!!
    * Search now uses a simple syntax to search any part of a log
    * [Search Documentation](/dandelion/search)
- Improved: Major source rewrite
    * Isolated public and application folders
    * Improved application structure for looser dependencies
    * Ability to easily implement different databases (Postgres and SQLite coming)
    * New routing functionality
    * Better templating
    * Cleaner bootstrap and application initialization
- Removed: The mail system has been removed because it didn't fit well into the idea of Dandelion

**v5.0.3** - **Current Stable (master branch)**

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
