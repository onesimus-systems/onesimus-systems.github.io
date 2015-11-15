---
layout: post
title:  "Dandelion 6.1.0 Feature Freeze"
author: "Lee Keitel"
date:   2015-11-15
categories: dandelion
---

As the smell of turkey and your weird aunt Margaret grow ever stronger, Dandelion has been shaping up for its 6.1.0 release. The scheduled release date is December 19. Beginning today, 6.1.0 will be in feature freeze. This means no new features will be added or developed for 6.1. I'll be focusing on getting the installation and upgrade procedures working correctly, update any lingering documentation, and fix any bugs in existing features.

As of now the new feature list of 6.1 includes:

- Disable users (to keep name information)
- Single-threaded log comments
- Permalink for logs
- Validation of API parameters
- Better internal handling of permissions
- Misc. bug fixes and internal improvements

There will be an upgrade path from 6.0.x to 6.1. There are a few database changes that need to be ran before using. All of this will be taken care of in a PHP script. Installation of a fresh instance won't change much. You can always see the current development version on the develop branch [on GitHub](https://github.com/onesimus-systems/dandelion/tree/develop). Report any bugs to the [Issue Tracker](https://github.com/onesimus-systems/dandelion/issues).
