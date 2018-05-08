# Hosting a WebView control

The EdgeHTML [WebView](https://docs.microsoft.com/en-us/microsoft-edge/webview) control enables you to embed web content directly into a *Universal Windows Platform* app, such as your PWA running on Windows 10. 

Like a standard HTML [iframe](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) element,  you can use WebView to load remote pages over HTTP and local pages (*ms-appx-web:///*) from your app package. However, the WebView can also:

 - Load pages and resources from your [ApplicationData](https://docs.microsoft.com/en-us/uwp/api/Windows.Storage.ApplicationData) (local, roaming, temp) folders (*ms-appdata:///*) and [in-memory streams](https://docs.microsoft.com/en-us/microsoft-edge/webview#buildlocalstreamuri) (*ms-local-stream:///*)

 - Provide browser-like controls: for going [back](https://docs.microsoft.com/en-us/microsoft-edge/webview#goback) and [forward](https://docs.microsoft.com/en-us/microsoft-edge/webview#goforward) in navigation history, and [stopping](https://docs.microsoft.com/en-us/microsoft-edge/webview#stop) or [refreshing](https://docs.microsoft.com/en-us/microsoft-edge/webview#refresh) the current page. 

 - [Capture screenshots of web content](https://docs.microsoft.com/en-us/microsoft-edge/webview#capturepreviewtoblobasync) making it easy to implement the Windows 10 app [Share](https://docs.microsoft.com/en-us/windows/uwp/app-to-app/share-data) contract.

 - Allow JavaScript code running within a webview to raise custom events ([MSWebViewScriptNotify](https://docs.microsoft.com/en-us/microsoft-edge/webview#mswebviewscriptnotify)) to your app, and allow your app to run JavaScript within the webview ([invokeScriptAsync](https://docs.microsoft.com/en-us/microsoft-edge/webview#invokescriptasync)).

 - Provide you with fine-tuned webview content events:
    
    WebView DOM event | Description
    --------- | ------
    [MSWebViewNavigationStarting](https://docs.microsoft.com/en-us/microsoft-edge/webview#mswebviewnavigationstarting) | Indicates the WebView is starting to navigate
    [MSWebViewContentLoading](https://docs.microsoft.com/en-us/microsoft-edge/webview#mswebviewcontentloading) | The HTML content is downloaded and is being loaded into the control
    [MSWebViewDOMContentLoaded](https://docs.microsoft.com/en-us/microsoft-edge/webview#mswebviewdomcontentloaded) | Indicates that the main DOM elements have finished loading
    [MSWebViewNavigationCompleted](https://docs.microsoft.com/en-us/microsoft-edge/webview#mswebviewnavigationcompleted) | Indicates the navigation is complete, and all media elements are rendered
    [MSWebViewUnviewableContentIdentified](https://docs.microsoft.com/en-us/microsoft-edge/webview#mswebviewunviewablecontentidentified) | The WebView found the content was not HTML
    [UnsafeContentWarningDisplaying](https://docs.microsoft.com/en-us/microsoft-edge/webview#mswebviewunsafecontentwarningdisplaying) | The WebView shows a warning page for content that was reported as unsafe by Windows *SmartScreen Filter*.

    ...including corresponding [events](https://docs.microsoft.com/en-us/microsoft-edge/webview#events) for iframe content loaded within a WebView (such as [MSWebView**Frame**NavigationStarting](https://docs.microsoft.com/en-us/microsoft-edge/webview#mswebviewframenavigationstarting) and so on.)

## Snippet

As with Windows Runtime APIs, the EdgeHTML WebView element is only available in the DOM of a web app [running as a standalone Windows 10 app](https://docs.microsoft.com/en-us/microsoft-edge/progressive-web-apps/windows-features) (in a *WWAHost.exe* process, rather than in the browser), so the best practice is to use feature detection before dynamically adding it to the document.

```JavaScript
// Feature detect for webview support
if (MSHTMLWebViewElement) {
    var wv = document.createElement('x-ms-webview'); // Use CSS to set width, height and other styles
    wv.navigate("https://www.bing.com");
    document.body.appendChild(wv);
}
```
You can also instantiate a WebView in in its own separate process:

```JavaScript
var wvprocess = new MSWebViewProcess();

// WebViews created with the same MSWebViewProcess object share the same process
wvprocess.CreateWebViewAsync().then(function (webview) {
    webview.navigate("https://www.bing.com");
    document.body.appendChild(webview);
});
```

## Related topics

[Blending apps and sites with the HTML x-ms-webview](https://blogs.windows.com/buildingapps/2013/10/01/blending-apps-and-sites-with-the-html-x-ms-webview/#eWZScr7KjxwpjHJo.97 )

### API Reference

[x-ms-webview](https://docs.microsoft.com/en-us/microsoft-edge/webview) (MSHTMLWebView)

[MSWebViewProcess](https://docs.microsoft.com/en-us/microsoft-edge/webview/mswebviewprocess)
