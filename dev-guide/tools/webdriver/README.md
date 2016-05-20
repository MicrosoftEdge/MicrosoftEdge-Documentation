# WebDriver

The W3C [WebDriver](http://go.microsoft.com/fwlink/p/?LinkID=619305) API is a platform and language-neutral interface and wire protocol allowing programs or scripts to control the behavior of a web browser. 

WebDriver enables developers to create automated tests that simulate user interaction. This is different from JavaScript unit tests because WebDriver has access to functionality and information that JavaScript running in the browser doesn't, and it can more accurately simulate user events or OS-level events. WebDriver can also manage testing across multiple windows, tabs and webpages in a single test session.

Here's how to get started with WebDriver for Microsoft Edge.

The Microsoft Edge implementation of WebDriver supports both the W3C [WebDriver](http://go.microsoft.com/fwlink/p/?LinkID=619305) specification and the [JSON Wire Protocol](https://github.com/SeleniumHQ/selenium/wiki/JsonWireProtocol) for backwards compatibility with existing tests. Check out the [WebDriver Status](http://dev.modern.ie/platform/status/webdriver/details/) page for more details on supported commands.

## Enabling WebDriver with Microsoft Edge


For security reasons, WebDriver is disabled by default in Microsoft Edge. To enable it, you need to install the MicrosoftWebDriver server (see below) in the location of your test respository. With that, WebDriver in Microsoft Edge should work just like it does with other supporting browsers.

To use WebDriver with Microsoft Edge, you'll need to do the following:

* Install Windows 10.
* Download the Microsoft WebDriver server: 
  * For Windows 10 Build 10240, install this version of Microsoft [WebDriver](http://go.microsoft.com/fwlink/p/?LinkID=716880).
  * For Windows 10 Fall 2015 Update, install [Microsoft WebDriver Fall 2015 Update](http://go.microsoft.com/fwlink/p/?LinkID=716879).
  * For the latest preview build from the Windows Insider Program, install this version of [Microsoft WebDriver](http://go.microsoft.com/fwlink/p/?LinkId=716882).
* Download a WebDriver language binding of your choice. Currently [C# and Java Selenium language bindings](http://docs.seleniumhq.org/download/) are supported.
* Download a testing framework of your choice.


## Using WebDriver


To get started using WebDriver with Microsoft Edge, check out these samples:

* [C\# code sample](https://gist.github.com/InstyleVII/baf25274c55e891076d5#file-webdriver-cs) for opening a browser window, navigating to bing.com and searching for 'webdriver' (GitHub Gist)


## Related topics
[Microsoft WebDriver Fall 2015 Update (download)](http://go.microsoft.com/fwlink/p/?LinkID=716879)

[Microsoft WebDriver (download)](http://go.microsoft.com/fwlink/p/?LinkID=716880)

[WebDriver commands (reference)](https://developer.microsoft.com/en-us/microsoft-edge/platform/status/webdriver/details/)

[Bringing automated testing to Microsoft Edge through WebDriver](https://blogs.windows.com/msedgedev/2015/07/23/bringing-automated-testing-to-microsoft-edge-through-webdriver/)

## Specification
[WebDriver](http://www.w3.org/TR/webdriver/)
