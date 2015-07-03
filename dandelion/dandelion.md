---
layout: page
title: Dandelion Web Journal
permalink: /dandelion/
menutitle: Dandelion
---

Dandelion is a web-based logbook designed to make it simple to keep track of just about anything. Dandelion helps you remember what you did those many moons ago. Dandelion was developed out of the mindset of IT. However, it is versatile enough to be used in just about any situation.

License: [GPLv3](http://www.gnu.org/licenses/gpl-3.0.html)

Source: [Github Repo](https://github.com/dragonrider23/dandelion)

Current Stable: [v6.0.2](https://github.com/dragonrider23/dandelion/tree/master) [Download](https://github.com/onesimus-systems/dandelion/releases/tag/v6.0.2)

Current Unstable: [v6.1.0](https://github.com/dragonrider23/dandelion/tree/develop)

Documentation:

* [Installation](/dandelion/install)
* [Release Notes](/dandelion/release-notes)
* [Search Docs](/dandelion/search)
* [API Docs](/dandelion/api)
* [Theme Docs](/dandelion/theme-docs)

Contributing
------------

Thank you for considering contributing to Dandelion, please make sure to follow these guidelines:

* Use [PSR-2](http://www.php-fig.org/psr/psr-2/) code style
* For items that are not specified in PSR-2, please conform to the surrounding code
* Dandelion adheres to the [PSR-4](http://www.php-fig.org/psr/psr-4/) autoloader guidelines. Please see the Composer file for details.
* If you are wanting to contribute a significantly sized feature, please let me know before you start

Dandelion uses [this style of git branching](http://nvie.com/posts/a-successful-git-branching-model/). So for development, you should clone the Dandelion repository, and checkout a new feature branch off of the develop branch (not the master) and name it appropriately such as "issue-48-feature". Commit your changes to that branch and then send a pull-request back into the develop branch.

The exception to this rule is urgent hotfixes to master. To perform a hotfix, make a new branch off of master. When you're ready to submit the changes, make a pull request to both the master and develop branches.

Versioning
----------

For transparency into the release cycle and in striving to maintain backward compatibility, Dandelion is maintained under the Semantic Versioning guidelines. Sometimes we screw up, but we'll adhere to these rules whenever possible.

Releases will be numbered with the following format:

`<major>.<minor>.<patch>`

And constructed with the following guidelines:

- Breaking backward compatibility **bumps the major** while resetting minor and patch
- New additions without breaking backward compatibility **bumps the minor** while resetting the patch
- Bug fixes and misc changes **bumps only the patch**

For more information on SemVer, please visit <http://semver.org/>.
