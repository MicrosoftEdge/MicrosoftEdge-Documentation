# App title bar

You can customize the appearance of the [title bar](https://docs.microsoft.com/en-us/uwp/api/windows.ui.viewmanagement.applicationviewtitlebar)  of your Windows 10 app window ([`ApplicationView`](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.ViewManagement.ApplicationView) class), which by default is *Windows system grey* and displays the title of your app on the left, and includes three buttons (*Minimize*, *Maximize*, and *Close*) on the right.

A common title bar customization is to update the [colors of various title bar elements](https://docs.microsoft.com/en-us/uwp/api/windows.ui.viewmanagement.applicationviewtitlebar) to blend with the color scheme of the app.

## Snippet

Here's an example of how to set custom colors for the title bar of your app (the [`titleBar`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.viewmanagement.applicationviewtitlebar) of your [`ApplicationView`](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.ViewManagement.ApplicationView)). The 
following code would be included in your client-side JavaScript.

```JavaScript
    if (window.Windows && Windows.UI.ViewManagement.ApplicationView) {
        var customColors = {
            backgroundColor: { a: 255, r: 54, g: 60, b: 116 },
            foregroundColor: { a: 255, r: 232, g: 211, b: 162 },
            buttonBackgroundColor: { a: 255, r: 54, g: 60, b: 116 },
            buttonForegroundColor: { a: 255, r: 232, g: 211, b: 162 },
            buttonHoverBackgroundColor: { a: 255, r: 19, g: 21, b: 40 },
            buttonHoverForegroundColor: { a: 255, r: 255, g: 255, b: 255 },
            buttonPressedBackgroundColor: { a: 255, r: 232, g: 211, b: 162 },
            buttonPressedForegroundColor: { a: 255, r: 54, g: 60, b: 116 },
            inactiveBackgroundColor: { a: 255, r: 135, g: 141, b: 199 },
            inactiveForegroundColor: { a: 255, r: 232, g: 211, b: 162 },
            buttonInactiveBackgroundColor: { a: 255, r: 135, g: 141, b: 199 },
            buttonInactiveForegroundColor: { a: 255, r: 232, g: 211, b: 162 },
        };

        var titleBar = Windows.UI.ViewManagement.ApplicationView.getForCurrentView().titleBar;
        titleBar.backgroundColor = customColors.backgroundColor;
        titleBar.foregroundColor = customColors.foregroundColor;
        titleBar.inactiveBackgroundColor = customColors.inactiveBackgroundColor;
        titleBar.inactiveForegroundColor = customColors.inactiveForegroundColor; 
    }
```

## Related topics

[Title bar customization](https://docs.microsoft.com/en-us/windows/uwp/design/shell/title-bar)

### API Reference

[ApplicationView](https://msdn.microsoft.com/library/windows/apps/windows.ui.viewmanagement.applicationview.aspx) class

[ApplicationViewTitleBar](https://docs.microsoft.com/en-us/uwp/api/windows.ui.viewmanagement.applicationviewtitlebar) class