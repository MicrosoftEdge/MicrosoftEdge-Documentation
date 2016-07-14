# Page Visibility API

The [Page Visibility API](https://msdn.microsoft.com/library/hh772738.aspx) provides a means for developers to determine the current visibility of a document (or whether the page is in focus) and be notified when the visibility changes. Changes in visibility could include any given webpage being in the background, on an inactive browser tab, or minimized and not visible to the user. Without knowing the visibility state of a page, a web developer must design the webpage with the assumption that it is always visible. This results in higher machine resource utilization and it prevents web developers from making runtime decisions based on whether the webpage is visible to the user. Using Page Visibility, the API can send a [`visibilitychange`](https://msdn.microsoft.com/library/hh772093.aspx) event to report when a page is minimized or moved to an inactive tab and perform or behave differently.

## Page Visibility API Properties and Events

Knowing the page visibility when designing webpages will allow for improved user experiences and power efficient sites. The Page Visibility API makes this possible. It consists of the following two properties.

| Property | Description
|:------------ | :-------------
| [document.hidden](https://msdn.microsoft.com/library/hh773167.aspx) | A Boolean value that describes whether the page is visible or not. Returns true if the page is hidden.
| [document.visibilityState](https://msdn.microsoft.com/library/hh773170.aspx) | Returns the page visibility state. Values include: `hidden`, `visible`, and `prerender`.


The Page Visibility API also exposes the following event.

| Event | Description
|:------------ | :-------------
| [visibilitychange](https://msdn.microsoft.com/library/hh772093.aspx) | An event that gets fired anytime the visibility state of the page changes.

By using this API, web applications can choose to alter behavior based on whether they are visible to the user or not. This API can be used to scale back work when the page is no longer visible. For example, if a web-based email client is visible, it might check the server for new mail every few seconds. When hidden, it might scale back so it checks email every few minutes instead of every few seconds. This API can also be used to provide a more effective user experience in situations not related to power management. For example, a puzzle game or a video could be paused when the user no longer has the game visible. Similarly, advertisers could use it to not charge for ads when they are not visible to viewers. The Page Visibility API can be used to guard against scripts firing before they're rendered on the user's screen

## Live examples

The example below logs the visibility of the current window. Go ahead and try to minimize and reopen the window to see the log in action!

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/eZGGbX)

Like the example above, this example uses the Page Visibility API to determine the visibility of the screen to perform an action. For this situation, if the video is playing and then the window is minimized, the video will pause.

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/eZGGxX)


## API Reference

[hidden](https://msdn.microsoft.com/library/hh773167)
 
[visibilitychange](https://developer.microsoft.com/microsoft-edge/platform/documentation/apireference/events/visibilitychanged/)

## Specification

[Page Visibility](http://go.microsoft.com/fwlink/p/?LinkID=247521)
