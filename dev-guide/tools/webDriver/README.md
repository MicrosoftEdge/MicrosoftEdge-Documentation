# WebDriver
The W3C [WebDriver](http://www.w3.org/TR/webdriver/) API is a platform and language-neutral interface and wire protocol allowing programs or scripts to control the behavior of a web browser. 

WebDriver enables developers to create automated tests that simulate user interaction. This is different from JavaScript unit tests because WebDriver has access to functionality and information that JavaScript running in the browser doesn't, and it can more accurately simulate user events or OS-level events. WebDriver can also manage testing across multiple windows, tabs and webpages in a single test session.

Here's how to get started with WebDriver for Microsoft Edge.

The Microsoft Edge implementation of WebDriver supports both the W3C [WebDriver](http://www.w3.org/TR/webdriver/) specification and the [JSON Wire Protocol](https://github.com/SeleniumHQ/selenium/wiki/JsonWireProtocol) for backwards compatibility with existing tests. Check out the [WebDriver Status and Commands](https://developer.microsoft.com/en-us/microsoft-edge/platform/documentation/webdriver-commands/) page for more details on supported commands.

## Getting started with WebDriver for Microsoft Edge
* Install Windows 10.
* Download the appropriate [Microsoft WebDriver](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/) server for your build of Windows.
* Download the WebDriver language binding of your choice. Currently the [Selenium C#, Java and JavaScript language bindings](http://docs.seleniumhq.org/download/) are supported.


## Using WebDriver
To get started using WebDriver with Microsoft Edge, check out these samples:

* [C\# code sample](https://gist.github.com/InstyleVII/baf25274c55e891076d5#file-webdriver-cs) for opening a browser window, navigating to bing.com and searching for 'webdriver' (GitHub Gist).


## Related topics
[Microsoft WebDriver (download)](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/)

[WebDriver Status and Commands (reference)](https://developer.microsoft.com/en-us/microsoft-edge/platform/documentation/webdriver-commands/)

[Bringing automated testing to Microsoft Edge through WebDriver](https://blogs.windows.com/msedgedev/2015/07/23/bringing-automated-testing-to-microsoft-edge-through-webdriver/)

## Specification
[WebDriver](http://www.w3.org/TR/webdriver/)
