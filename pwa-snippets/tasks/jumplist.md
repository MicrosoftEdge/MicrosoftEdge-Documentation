# Customizing jump list commands

A *jump list* is a system-provided menu that appears when the user right-clicks a program in the taskbar or on the **Start** menu. It is used to provide quick access to recently or frequently-used documents and offer direct links to app functionality.

Here's how to use the WinRT **JumpList** class to add custom taskbar commands and command groupings for your PWA.

## Add a custom command to the jump list

Only the desktop device family supports jump lists. Changes made to a jump list with a different device family will not persist, so you'll first want to confirm jump list support ([`JumpList.isSupported`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.startscreen.jumplist.issupported#Windows_UI_StartScreen_JumpList_IsSupported)).

From there, you can add a custom jump list item by:

1. Loading your app's jump list ([`JumpList.loadCurrentAsync`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.startscreen.jumplist.loadcurrentasync#Windows_UI_StartScreen_JumpList_LoadCurrentAsync)).
2. Creating a custom jump list item ([`JumpListItem.createWithArguments`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.startscreen.jumplistitem.createwitharguments#Windows_UI_StartScreen_JumpListItem_CreateWithArguments_System_String_System_String_)) by specifying its display name and arguments. Also, you can:
    - Categorize the item in a new or existing group ([`JumpListItem.groupName`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.startscreen.jumplistitem.groupname)). If no group name is specified, the item will appear under the default *Tasks* group in the jump list.
    - Specify a logo URI from your [appx package](https://docs.microsoft.com/microsoft-edge/progressive-web-apps/get-started#enhance-your-web-app-into-a-pwa) for the item ([`JumpListItem.logo`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.startscreen.jumplistitem.logo)). If no logo is specified, a *file* image is used by default.
3. Appending the new item to your jump list items ([`JumpList.items.append`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.startscreen.jumplist.items)), and then
4. Saving the changes to your jump list ([`JumpList.saveAsync`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.startscreen.jumplist.saveasync)).

For example:

```JavaScript
// Check if WinRT is available AND if JumpList is supported on the device
if (window.Windows && Windows.UI.StartScreen.JumpList.isSupported()) {
    var JumpList = Windows.UI.StartScreen.JumpList;
    var JumpListItem = Windows.UI.StartScreen.JumpListItem;

    JumpList.loadCurrentAsync().done(function (jumpList) {

        var arguments = "jump list command args"; //These will get passed to your app upon activation
        var displayName = "Custom jump list command name";
        var item = JumpListItem.createWithArguments(arguments, displayName);
        item.description = "Tooltip description of the custom jump list item";

        item.groupName = "Custom group name";
        item.logo = new Windows.Foundation.Uri("ms-appx:///images/custom-jumplist-command.png");
        jumpList.items.append(item);
        jumpList.saveAsync();
    });
}
```

## Respond to jump list commands

When a user invokes a jump list command, Windows will [activate](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/activate-an-app
) your app, passing the selected jump list item's arguments with the [`WebUIApplication.activated`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.webui.webuiapplication.activated) event. Here's an example that handles the custom jump list item created from the code above:

```JavaScript
Windows.UI.WebUI.WebUIApplication.addEventListener("activated", function (activatedEventArgs) {
    if (activatedEventArgs.kind == Windows.ApplicationModel.Activation.ActivationKind.launch &&
        activatedEventArgs.arguments == "jump list command args") {
        // Respond to jumplist command specified by argument(s)
    }
});
```

Note that jump list commands trigger an app activation event of type *Launch*, as does the regular launching of an app from the Windows **Start** menu. (There are also a [number of other ways ](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.activation.activationkind
) Windows 10 apps can be activated.) The way to differentiate that your app was launched from a custom jump list command is through the  *arguments* you specify when creating the custom jump list item ([`JumpListItem.createWithArguments`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.startscreen.jumplistitem.createwitharguments#Windows_UI_StartScreen_JumpListItem_CreateWithArguments_System_String_System_String_)).

## Entries for frequent items

If your app is used to open different files, you can [maintain a list](https://docs.microsoft.com/en-us/windows/uwp/files/how-to-track-recently-used-files-and-folders) of the *most recently used* (MRU) files and use them to populate jump list entries under the system-managed *Recent* jump list group.

Here's how to add a file to your app's MRU list ([`StorageItemMostRecentlyUsedList`](https://docs.microsoft.com/en-us/uwp/api/windows.storage.accesscache.storageitemmostrecentlyusedlist)):

```JavaScript
function addFile(fileName)
{
    var localFolder = Windows.Storage.ApplicationData.current.localFolder;
    var AccessCache = Windows.Storage.AccessCache;

    localFolder.tryGetItemAsync(fileName).done(function (file) {
        if (file == null) {
            localFolder.createFileAsync(fileName).done(function (newFile) {
                AccessCache.StorageApplicationPermissions.mostRecentlyUsedList.add(newFile, "", AccessCache.RecentStorageItemVisibility.appAndSystem);
            });
        }
    });
}
```

And here's how to add files from the MRU list as jump list entries under the *Frequent* group ([`JumpListSystemGroupKind`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.startscreen.jumplistsystemgroupkind)):

```JavaScript
var StartScreen = Windows.UI.StartScreen;

StartScreen.JumpList.loadCurrentAsync().done(function (jumpList) {
    jumpList.systemGroupKind = StartScreen.JumpListSystemGroupKind.frequent;
    jumpList.saveAsync();
});
```

You would respond to these commands in the same way you would [respond to custom jump list commands](#respond-to-jump-list-commands), by handling the [`WebUIApplication.activated`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.webui.webuiapplication.activated) event. However in this case, the [`ActivationKind`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.activation.activationkind) is *file* and [`WebUIFileActivatedEventArgs`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.webui.webuifileactivatedeventargs) will be passed to your handler. With that, you can obtain further details for opening the selected file:

```JavaScript
Windows.UI.WebUI.WebUIApplication.addEventListener("activated", function (activatedEventArgs) {
    if (activatedEventArgs.kind == Windows.ApplicationModel.Activation.ActivationKind.file &&
        activatedEventArgs.length > 0 &&
        activatedEventArgs[0].files.length > 0) {
        // Open the selected file: activatedEventArgs[0].files[0].name
    }
});
```

## Clearing the jump list

Once you load your app's jump list ([`JumpList.loadCurrentAsync`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.startscreen.jumplist.loadcurrentasync#Windows_UI_StartScreen_JumpList_LoadCurrentAsync))
 you can enumerate, modify and delete individual items ([`JumpList.items`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.startscreen.jumplist.items)) using standard [Windows collection methods](https://docs.microsoft.com/en-us/uwp/api/windows.foundation.collections.ivector_t_#methods-), such as `append`, `insertAt`, and `removeAt`. You can also `clear` the entire jump list.

 Make sure you save any modifications back to the jump list.

 Here's an example of how to clear the jump list:

 ```JavaScript
JumpList.loadCurrentAsync().done(function (jumpList) {
    // Clear the system-managed (recent, frequent) jump list items 
    jumpList.systemGroupKind = JumpListSystemGroupKind.none;

    // Clear the jump list items that were added programmatically
    jumpList.items.clear();

    jumpList.saveAsync();
});
 ```

## Related topics

[Jump list customization sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/JumpList)

[Windows 10 universal Windows platform (UWP) app lifecycle](
https://docs.microsoft.com/en-us/windows/uwp/launch-resume/app-lifecycle)

[Handle app activation](
https://docs.microsoft.com/en-us/windows/uwp/launch-resume/activate-an-app)

[Track recently used files and folders](https://docs.microsoft.com/en-us/windows/uwp/files/how-to-track-recently-used-files-and-folders)


### API Reference

[ActivationKind](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.activation.activationkind) enum

[JumpList](
https://docs.microsoft.com/en-us/uwp/api/windows.ui.startscreen.jumplist) class

[JumpListItem](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.StartScreen.JumpListItem) class

[StorageItemMostRecentlyUsedList](https://docs.microsoft.com/en-us/uwp/api/windows.storage.accesscache.storageitemmostrecentlyusedlist) class

[WebUI.Activated](
https://docs.microsoft.com/en-us/uwp/api/windows.ui.webui.webuiapplication.activated) event