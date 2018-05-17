# InkCanvas

An exciting new feature in the Edge rendering engine (EdgeHTML 17) available in the Spring 2018 (1803) update of Windows 10 are the native inking extensions added to the ``<canvas>`` control. These extensions include support for the methods and properties of the InkCanvas class documented here: https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.inkcanvas.

With this control you can now support simple and complex inking scenarios in your web application. For example, drawing, signature capture, tilt and shading and multiple levels of pressure sensitivity. 

The canvas control is a good example of the 'progressive' nature of EdgeHTML. That is, the Inking extensions 'light up' when your page is run in a Windows PWA container.

With the following code we can detect if we're running as a Windows PWA and if the `InkingPresenter` is supported since this is supported in EdgeHTML 17.17134 introduced in the Windows 1803 release. If the test is successful we'll display UI that will let us change the inking properties of the canvas control.

```javascript
function runningWindows10withInkCanvasSupport() {
    if (typeof Windows !== 'undefined' &&
        typeof Windows.UI !== 'undefined' &&
        typeof Windows.UI.Input.Inking.InkPresenter !== 'undefined')
        return true;
    else
        return false;
}
```
Next we'll initialize the Inking properties of the canvas control:

```javascript
var inkCanvas;
var inkContext;
var inkPresenter;
...
// Set initial ink stroke attributes.
inkCanvas = document.getElementById("InkCanvas"); // get canvas control
inkCanvas.setAttribute("width", inkCanvas.offsetWidth);
inkCanvas.setAttribute("height", inkCanvas.offsetHeight);

// Get the ms-ink context
inkContext = inkCanvas.getContext("ms-ink");
inkPresenter = inkContext.msInkPresenter;

inkPresenter.inputDeviceTypes =
Windows.UI.Core.CoreInputDeviceTypes.mouse |
Windows.UI.Core.CoreInputDeviceTypes.pen |
Windows.UI.Core.CoreInputDeviceTypes.touch;

// Set the default drawing attributes.
inkColor = Windows.UI.Colors.black;
```
Code can be found here: https://github.com/Microsoft/Windows-AppConsult-samples-PWA/blob/master/Canvas/CanvasSimple/js/main.js


Resources:

[Windows 10: Inking and the InkCanvas](https://mva.microsoft.com/en-us/training-courses/windows-10-inking-and-the-inkcanvas-14586?l=LRhlWJFsB_5205632527)

[InkCanvas Namepace](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.inkcanvas.
)

[Progressive Web Apps on Windows](https://docs.microsoft.com/en-us/microsoft-edge/progressive-web-apps)