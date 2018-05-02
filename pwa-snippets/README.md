# PWA task snippets

This repo collects snippets of ready-to-use code that accomplish common tasks of *Progressive Web Apps* (PWAs) running on Windows, such as calling *Windows Runtime* (WinRT) APIs in order to implement native app features and further integrate web application UX with the Windows 10 operating system.

If you're just getting started, you might want to first check out these resources:

 - [**Get started with Progressive Web Apps**](https://docs.microsoft.com/en-us/microsoft-edge/progressive-web-apps/get-started) to learn how turn your website into a PWA with service workers to support an offline experience and push notifications.
 - [**Tailor your PWA for Windows**](https://docs.microsoft.com/en-us/microsoft-edge/progressive-web-apps/windows-features) to learn how to run/debug your PWA as a *Universal Windows Platform* app and understand how to use Windows Runtime (WinRT) APIs.
 - [**PWAS in the Microsoft Store**](https://docs.microsoft.com/en-us/microsoft-edge/progressive-web-apps/microsoft-store) to learn how (and why!) to submit your PWA for distribution through the Microsoft Store.

## Snippets

### Tiles and notifications

[Pinning app tiles](./tasks/tiles.md)

Tile notifications and badge updates

Toast notifications using the Push API

### OS integration

File handler registration

[App launch at startup](./tasks/auto-launch.md)

Handling activation

Native messaging

### Windows UX customizations

[App title bar color](./tasks/title-bar.md)

[App context menu](./tasks/context-menu.md)

[Desktop jumplist commands](./tasks/jumplist.md)

### Other tasks

Background tasks

Caching and data storage

[Cortana voice commands](./tasks/cortana-voice-commands.md)

Hosting HTMLWebView

Using a custom WinRT component

[Web authentication broker](./tasks/web-authentication-broker.md)
