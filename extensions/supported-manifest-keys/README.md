# Supported manifest keys

Every extension has a JSON-formatted manifest file, named manifest.json. This file provides important information for the extension ranging from its name to its permissions. Unless specified in a note below, the Microsoft Edge manifest properties follow the same implementation as Chrome.

See example of a [Microsoft Edge JSON manifest file](json-manifest-example/).

The following is the list of JSON manifest keys that are supported as of build 14316:

## Required keys

The following keys are required:

Key | Known issues | Chrome incompatibilities
:------------ | :------------- | :--------------
author  | | Specifies the author. Not supported in Chrome.
[name](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/name) | | |
[version](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/version) | | |

## Recommended keys

The following keys are recommended:

Key | Known issues | Chrome incompatibilities 
:------------ | :------------- | :--------------
[description](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/description) | | |
[manifest_version](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/manifest_version) | | Currently ignored in Microsoft Edge.
[icons](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/icons) | | |

## browser_action or page_action keys

One or none of the following keys must be specified:

Key | Known issues | Chrome incompatibilities
:------------ | :------------- | :--------------
[browser_action](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/browser_action)  | | Microsoft Edge does not support the following syntax:  `browser_action : {"default_icon" : "icon.png" }`   Size for icons must be specified. Preferred sizes: 20px, 25px, 30px, 40px. Other supported sizes: 19px, 35px, 38px.|
[page_action](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/page_action) | | Microsoft Edge does not support the following syntax:  `page_action : {"default_icon" : "icon.png" }`   Size for icons must be specified. Preffered sizes: 20px, 25px, 30px, 40px. Other supported sizes: 19px, 35px, 38px.|

## Optional keys

The following keys are optional:

Key | Known issues | Chrome incompatibilities
:------------ | :------------- | :--------------
[background](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/background) | | Persistent is a required field for Microsoft Edge.
[content_scripts](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/content_scripts)  | | |
options_page | | |
[permissions](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/permissions)  | | |
short_name  | | |
[web_accessible_resources](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/web_accessible_resources) | | |
