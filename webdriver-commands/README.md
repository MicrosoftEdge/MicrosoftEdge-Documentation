The WebDriver API is a platform and language-neutral interface and wire protocol allowing programs or scripts to control
the behavior of a web browser. The Microsoft Edge implementation of WebDriver supports both the W3C WebDriver specification
and the JSON Wire Protocol. Here's how to [enable WebDriver for Microsoft Edge](https://msdn.microsoft.com/library/mt188085).

# WebDriver Commands
The following types of WebDriver commands are currently supported in Microsoft Edge.

| Command Category | Supported Commands |
| :--------------- | :------------------|
| [Dialogs](./dialogs/) | Accept Alert, Dismiss Alert, Get Text |
| [Element Inspection](./element-inspection/) | Find Element, Find Elements, Get CSS Value, Get Element Attribute, Get Element Tag Name, Get Element Text, Is Element Displayed, Is Element Enabled, Is Element Selected |
| [Input](./input/) | Clear, Click, Send Keys |
| [Navigation](./navigation/) | Back, Forward, Get, Get Title, Refresh |
| [Screenshots](./screenshots/) | Take Element Screenshot, Take Screenshot |
| [Script Execution](./script-execution/) | Add Cookie, Execute Script, Get Cookie, Get Cookies, Delete Cookie, Delete Cookies |
| [Server](./server/) | Shutdown, Status |
| [Sessions](./sessions/) | Delete, Get Capabilities, New Session, Sessions, Set Timeout |
| [Window](./window/) | Close Window, Get Window Handle, Get Window Handles, Switch To Window |

# WebDriver status

Command name | EndPoint | Status | Available build/priority
:---------------| :------------ | :----------- | :--------------
Shutdown |/Shutdown|Supported |10240|
[Status](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#status)|{GET} /Status|Supported|10240|
[Sessions](https://w3c.github.io/webdriver/webdriver-spec.html#sessions)|{GET} /sessions|Supported|10240|
[New session](https://w3c.github.io/webdriver/webdriver-spec.html#new-session)|{POST} /session|Supported|10240|
[Delete session](https://w3c.github.io/webdriver/webdriver-spec.html#delete-session)|{DELETE} /session/{sessionId}|Supported|10240|
[Set Timeout](https://w3c.github.io/webdriver/webdriver-spec.html#set-timeout)|{POST} /session/{sessionId}/timeouts|Supported|10240|
[Sessions](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessions)|/sessions|Supported|10240|
[Session ID](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionid)|/session/{sessionId}|Supported|10240|
[Page Source](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidsource)|{GET} /session/{sessionId}/Source|Preview|10547|
[Keys](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidkeys)|{POST} /session/{sessionId}/Keys|Preview|10532|
[Orientation](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidorientation)|{GET} /session/{sessionId}/orientation|Not Yet|Priority 2|
[moveTo](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidmoveto)|{GET} /session/{sessionId}/moveTo|Preview|10550|
[buttonDown](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidbuttondown)|{POST} /session/{sessionId}/buttonDown|Preview|10550|
[buttonUp](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidbuttonup)|{POST} /session/{sessionId}/buttonUp|Preview|10550|
[doubleClick](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessioniddoubleclick)|{POST} /session/{sessionId}/doubleClick|Preview|10550|
[GEO Location](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidlocation)|{GET} /session/{sessionId}/location|Preview|10547|
[local_storage](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidlocal_storage)|{GET} /session/{sessionId}/local_storage|Preview|10547|
[session_storage](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidsession_storage)|{GET} /session/{sessionId}/session_storage|Preview|10547|
[log](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidlog)|{GET} /session/{sessionId}/log|Not Yet|Priority 3|
[Log Types](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidlogtypes)|{GET} /session/{sessionId}/log/types|Not Yet|Priority 3|
[Get](https://w3c.github.io/webdriver/webdriver-spec.html#get)|{POST} /session/{sessionId}/url|Supported|10240|
[Get Current Url](https://w3c.github.io/webdriver/webdriver-spec.html#get-current-url)|{GET} /session/{sessionId}/url|Supported|10240|
[Back](https://w3c.github.io/webdriver/webdriver-spec.html#back)|{POST} /session/{sessionId}/back|Supported|10240|
[Forward](https://w3c.github.io/webdriver/webdriver-spec.html#forward)|{POST} /session/{sessionId}/forward|Supported|10240|
[Refresh](https://w3c.github.io/webdriver/webdriver-spec.html#refresh)|{POST} /session/{sessionId}/refresh|Supported|10240|
[Get Title](https://w3c.github.io/webdriver/webdriver-spec.html#get-title)|{GET} /session/{sessionId}/title|Supported|10240|
[Invalid SSL Certificates](https://w3c.github.io/webdriver/webdriver-spec.html#invalid-ssl-certificates)|N/A|Partial|10240 - ongoing work|
[Get Window Handle](https://w3c.github.io/webdriver/webdriver-spec.html#get-window-handle)|{GET} /session/{sessionId}/window/handle|Preview|10532|
[Get Window Handles](https://w3c.github.io/webdriver/webdriver-spec.html#get-window-handles)|{GET} /session/{sessionId}/window/handles|Preview|10532|
[Switch to Window](https://w3c.github.io/webdriver/webdriver-spec.html#switch-to-window)|{POST} /session/{sessionId}/window|Preview|10532|
[Close Window](https://w3c.github.io/webdriver/webdriver-spec.html#close-window)|{DELETE} /session/{sessionId}/window|Preview|10532|
[Switch to Frame](https://w3c.github.io/webdriver/webdriver-spec.html#switch-to-frame)|{POST} /session/{sessionId}/frame|Preview|10532|
[Switch to Parent Window](https://w3c.github.io/webdriver/webdriver-spec.html#get-window-handle)|{POST} /session/{sessionId}/frame/parent|Preview|10532|
[Resizing and Positioning Windows](https://w3c.github.io/webdriver/webdriver-spec.html#get-window-handle)|{GET} /session/{sessionId}/window/size|Preview|10532|
[Get Window Size](https://w3c.github.io/webdriver/webdriver-spec.html#get-window-size)|{GET} /session/{sessionId}/window/size|Preview|10532|
[Set Window Size](https://w3c.github.io/webdriver/webdriver-spec.html#set-window-size)|{POST} /session/{sessionId}/window/size|Preview|10532|
[Maximize Window](https://w3c.github.io/webdriver/webdriver-spec.html#maximize-window)|{GET} /session/{sessionId}/window/maximize|Preview|10532|
[Fullscreen Window](https://w3c.github.io/webdriver/webdriver-spec.html#fullscreen-window)|{GET} /session/{sessionId}/window/fullsize|Not Yet|Priority 4|
[Set Window Position](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidwindowwindowhandleposition)|{POST} /session/{sessionId}/window/{windowHandle}/position|Preview|10532|
[Find Elements](https://w3c.github.io/webdriver/webdriver-spec.html#findelements)|{POST} /session/{sessionId}/elements|Partial|10547|
[Find Elements](https://w3c.github.io/webdriver/webdriver-spec.html#findelements)|{POST} /session/{sessionId}/element/{elementId}/elements|Preview|10547|
[Find Element](https://w3c.github.io/webdriver/webdriver-spec.html#findelement)|{POST} /session/{sessionId}/element|Preview|10547|
[Find Element](https://w3c.github.io/webdriver/webdriver-spec.html#findelement)|{POST} /session/{sessionId}/element/{elementId}/element|Preview|10547|
[Get Active Element](https://w3c.github.io/webdriver/webdriver-spec.html#get-active-element)|{GET} /session/{sessionId}/element/active|Preview|10550|
[Describe Element](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidelementid)|{GET} /session/{sessionId}/element/{Id}|Under Consideration|Priority 3|
[Element Location Strategies](https://w3c.github.io/webdriver/webdriver-spec.html#element-location-strategies)|N/A|Supported/Preview | CSS Selectors - 10240, ECMA Script - 10240, Link Text - 10240, Partial Link Text - 10240, XPATH - 10547
[Is Element Displayed](https://w3c.github.io/webdriver/webdriver-spec.html#is-element-displayed)|{GET} /session/{sessionId}/element/{elementId}/displayed|Supported|10240|
[Is Element Selected](https://w3c.github.io/webdriver/webdriver-spec.html#is-element-selected)|{GET} /session/{sessionId}/element/{elementId}/selected|Supported|10240|
[Get Element Attribute](https://w3c.github.io/webdriver/webdriver-spec.html#getelementattribute)|{GET /session/{sessionId}/element/{elementId}/attribute/{name}|Supported|10240|
[Get Element Property](https://w3c.github.io/webdriver/webdriver-spec.html#get-element-property)|{GET} /session/{sessionId}/element/{elementId}/property/{name}|Under Consideration|Priority 2|
[Get Element CSS Value](https://w3c.github.io/webdriver/webdriver-spec.html#getcssvalue)|{GET} /session/{sessionId}/element/{id}/css/{propertyName}|Supported|10240|
[getElementText()](https://w3c.github.io/webdriver/webdriver-spec.html#gettext)|{GET} /session/{sessionId}/element/{elementId}/text|Supported|10240|
[Get Element Tag Name](https://w3c.github.io/webdriver/webdriver-spec.html#get-element-tag-name)|{GET} /session/{sessionId}/element/{id}/name|Supported|10240|
[Get Element Rect](https://w3c.github.io/webdriver/webdriver-spec.html#get-element-rect)|{GET} /session/{sessionId}/element/{elementId}/rect|Preview|10532|
[Is Element Enabled](https://w3c.github.io/webdriver/webdriver-spec.html#is-element-enabled)|{GET} /session/{sessionId}/element/{elementId}/enabled|Supported|10240|
[Element Location](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidelementidlocation)|{POST} /session/{sessionId}/element/{id}/location|Preview|10532|
[Element Location in View](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#get-sessionsessionidelementidlocation_in_view)|{POST}/session/{sessionId}/element/{id}/location_in_view|Preview|10532|
[Element Size](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidelementidsize)|{GET} /session/{sessionId}/element/{id}/size|Preview|10532|
[Execute Script](https://w3c.github.io/webdriver/webdriver-spec.html#execute-script)|{POST} /session/{sessionId}/execute|Supported|10240|
[Execute Async Script](https://w3c.github.io/webdriver/webdriver-spec.html#execute-aysnc-script)|{POST} /session/{sessionId}/execute_async|Preview|10532|
[Async Script Timeout](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidtimeoutsasync_script)|{POST} /session/{sessionId}/timeouts/async_script|Under Consideration|Priority 3|
[Get Cookie](https://w3c.github.io/webdriver/webdriver-spec.html#get-cookie)|{GET} /session/{sessionId}/cookie/{name}|Supported|10240|
[Add Cookie](https://w3c.github.io/webdriver/webdriver-spec.html#add-cookie)|{GET} /session/{sessionId}/cookie|Supported|10240|
[Delete Cookie](https://w3c.github.io/webdriver/webdriver-spec.html#delete-cookie)|{GET} /session/{sessionId}/cookie/{name}|Supported|10240|
[Click()](https://w3c.github.io/webdriver/webdriver-spec.html#click)|{POST} /session/{sessionId}/element/{elementId}/click|Supported|10240|
[Clear()](https://w3c.github.io/webdriver/webdriver-spec.html#clear)|{POST} /session/{sessionId}/element/{elementId}/clear|Supported|10240|
[sendKeys()](https://w3c.github.io/webdriver/webdriver-spec.html#sendkeys)|{POST} /session/{shessionId}/element/{elementId}/value|Supported|10240|
[dismiss() Alert](https://w3c.github.io/webdriver/webdriver-spec.html#dismiss)|{POST} /session/{sessionId}/dismiss_alert|Supported|10240|
[accept() Alert](https://w3c.github.io/webdriver/webdriver-spec.html#accept)|{POST} /session/{sessionId}/accept_alert|Supported|10240|
[getText() Alert](https://w3c.github.io/webdriver/webdriver-spec.html#gettext)|{GET} /session/{sessionId}/alert_text|Supported|10240|
[sendKeys() Alert](https://w3c.github.io/webdriver/webdriver-spec.html#sendkeys-1)|{POST} /session/{sessionId}/alert/text|Under Consideration|Priority 1|
[Modal Dialogs](https://w3c.github.io/webdriver/webdriver-spec.html#modal-dialogs)|N/A|Preview|10550|
[Take Screenshot](https://w3c.github.io/webdriver/webdriver-spec.html#take-screenshot)|{GET} /session/{sessionId}/screenshot|Supported|10240|
[Take Element Screenshot](https://w3c.github.io/webdriver/webdriver-spec.html#take-element-screenshot)|{GET} /session/{sessionId}/element/{elementId}/screenshot|Supported|10240|
[Implicit Wait](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#post-sessionsessionidtimeoutsimplicit_wait)|{POST} /session/{sessionId}/timeouts/implicit_wait|Preview|10532|
[IME Available Engines](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidimeavailable_engines)|{GET} /session/{sessionId}/ime/available_engines|Under Consideration|Priority 3|
[IME Active Engine](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidimeactive_engine)|{GET} /session/{sessionId}/ime/active_engines|Under Consideration|Priority 3|
[IME Activated](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidimeactivated)|{POST} /session/{sessionId}/ime/activated|Under Consideration|Priority 3|
[IME Decativate](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidimedeactivate)|{POST} /session/{sessionId}/ime/deactivate|Under Consideration|Priority 3|
[IME Activate](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidimeactivate)|{POST} /session/{sessionId}/ime/activate|Under Consideration|Priority 3|
[Application Cache Status](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidapplication_cachestatus)|{POST} /session/{sessionId}/application_cache/status|Preview|10550|
[Find Element From](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidelementidelement)|{POST} /session/{sessionId}/element/{id}/element|Preview|10550|
[Find Elements From](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidelementidelements)|{POST} /session/{sessionId}/element/{id}/elements|Preview|10550|
[Submit Form](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidelementidsubmit)|{POST} /session/{sessionId}/element/{id}/submit|Preview|10550|
[Local Storage Key](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidlocal_storagekeykey)|{GET} /session/{sessionId}/local_storage/key/{key}|Preview|10547|
[Local Storage Size](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidlocal_storagesize)|{GET} /session/{sessionId}/local_storage/size|Preview|10547|
[Session Storage Key](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidsession_storagekeykey)|{GET} /session/{sessionId}/session_storage/key/{key}|Preview|10547|
[Session Storage Size](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidsession_storagesize)|{GET} /session/{sessionId}/session_storage/size|Preview|10547|
[Equals](https://github.com/seleniumhq/selenium/wiki/jsonwireprotocol#sessionsessionidelementidequalsother)|{GET} /session/{sessionId}/element/{id}/equals/{other}|Preview|10550|
Testing Profiles|N/A|Under Consideration|Priority 2|

