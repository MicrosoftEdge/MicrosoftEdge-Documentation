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
[content_security_policy](https://developer.mozilla.org/en-US/Add-ons/WebExtensions/manifest.json/content_security_policy)  | The content security policy of a page blocks websockets in content scripts, generating an undefined exception. | Microsoft Edge extensions currently only support [Default Policy Restrictions](https://developer.mozilla.org/en-US/Add-ons/WebExtensions/Content_Security_Policy#Default_content_security_policy): `script-src 'self'; object-src 'self'` |

### Supported permissions
The following permissions are supported as of build 14316:

Permission | Description
:---------- | :------------
\<any url\> | Allows content scripts to run.
contextMenus | Gives access to `contextMenus` API. This enables adding items to Microsoft Edge's context menu.
cookies | Gives access to the `cookies` API. This enable querying and modifying cookies as well as being notified when they change.
geolocation | Allow the extension to use the HTML5 `geolocation` API without prompting the user for permission.
idle | Gives access to the `idle` API. This enables detection of when the machine's idle state changes.
storage | Gives access to the `storage` API. This enables storing, retrieving, and tracking changes to user data. 
tabs | Gives access to the `tabs` API to interact with the browser's tab system. This enables creating, modifying, and rearranging tabs in the browser, including the URLs associated with each tab. 
webNavigation | Gives access to the `webNavigation` API. This enables receiving notifications about the status of navigation requests.
webRequest | Gives access to the `webRequest` API. This enables observing and analyzing traffic, as well as intercepting, blocking or modifying request in-flight.
webRequestBlocking | Required if an extension uses the `webRequest` API in a blocking fashion.

