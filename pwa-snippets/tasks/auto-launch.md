# Automatic app launching

As a Windows 10 app, you can configure your PWA to launch automatically, with user consent, when your user logs in to Windows.

Please note the following constraints:

 - Currently this functionality only works for apps running in the Desktop.

 - If the user enables/disables the app startup state in Windows **Task Manager**, this value immediately overrides the value set by the app using the `StartupTask` class. Also,

    - If the user *enables* the app startup state in Task Manager, it can later later be programmatically disabled; however,
    - If the user *disables* the app startup state in Task Manager, it can no longer be programmaticaly enabled.

 - The app must be launched at least once before you can prompt the user to programmatically change the startup state.

## Snippet

Here's how to use the WinRT [StartupTask](
https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.StartupTask) class in your PWA to configure automatic launch.

1. Add the [*uap5*](https://docs.microsoft.com/en-us/uwp/schemas/appxpackage/uapmanifestschema/what-s-changed-in-windows-10#windows-10-fall-creators-update---build-1629915-version-1709) namespace and [*StartupTask*](https://docs.microsoft.com/en-us/uwp/schemas/appxpackage/uapmanifestschema/element-uap5-startuptask) extension to the [`.appxmanifest`](https://docs.microsoft.com/en-us/microsoft-edge/progressive-web-apps/windows-features#set-app-permissions) file of your PWA's *Universal Windows* app project. (Here's how to [generate a Universal Windows app project](https://docs.microsoft.com/microsoft-edge/progressive-web-apps/windows-features) for your PWA.)

    ```XML
    <Package ... xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5" IgnorableNamespaces="... uap5">
    ...
    <Application>
        ...
        <Extensions>
            <uap5:Extension Category="windows.startupTask" StartPage="">
                <uap5:StartupTask
                TaskId="Startup"
                DisplayName="The name of your app"/>
            </uap5:Extension>
        </Extensions>
    </Application>
    ```
    .. and change the following for your app:
    - **TaskId**: The ID for the startup task (you'll use this in your code to access the `StartupTask` API)
    - **DisplayName**: The name of your PWA as you'd like it to appear in Windows Task Manager

    Although you can also specify a value for the **StartPage**, this attribute is not currently used for anything (other than satisfing schema constraints).

2. Add the following client-side code to your project, for example, in a settings button *click* handler.

    ```javascript
    // Check if WinRT is supported on the device
    if (window.Windows) {
        var StartupTask = Windows.ApplicationModel.StartupTask;
        var StartupTaskState = Windows.ApplicationModel.StartupTaskState;

        // Obtain startup task and assign new value
        StartupTask.getAsync("Startup").then(function(task) {
            switch (task.state) {
            case StartupTaskState.disabled:
                // Task is disabled but can be enabled.
                task.requestEnableAsync().done(function(resultState) {
                    // Add your success and error handlers
                });
                break;
            case StartupTaskState.disabledByUser:
                // Inform user that task is disabled and they must enable it manually
                var help = "Looks like you chose to disable this app from launching automatically when you sign in to Windows. " +
                    "If you change your mind, you can enable it again in the 'Startup' tab of 'Task Manager'.";
                var md = new Windows.UI.Popups.MessageDialog(help);
                var cmd = new Windows.UI.Popups.UICommand("OK");
                md.commands.append(cmd);
                md.showAsync();
                break;
            case StartupTaskState.disabledByPolicy:
                // Startup disabled by group policy, or not supported on this device
                break;
            case StartupTaskState.enabled:
                // Task is enabled but can be disabled
                task.disable();
                break;
            case StartupTaskState.enabledByPolicy:
                // Startup is enabled by a policy set on this device
                break;
            }
        });
    }
    ```

## Related topics

[Configure your app to start at log-in](
https://blogs.windows.com/buildingapps/2017/08/01/configure-app-start-log/)

[Startup App Sample](https://github.com/Microsoft/AppModelSamples/tree/master/Samples/TestStartup) (Xaml)

### API Reference

[uap5:Extension](https://docs.microsoft.com/en-us/uwp/schemas/appxpackage/uapmanifestschema/element-uap5-extension) app manifest element

[StartupTask](
https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.StartupTask) class

[disable](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.startuptask.disable) method

[getAsync](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.startuptask.getasync#Windows_ApplicationModel_StartupTask_GetAsync_System_String_) method

[requestEnableAsync](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.startuptask.requestenableasync) method


