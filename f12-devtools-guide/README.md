# Meet the Microsoft Edge Developer Tools

[Some information relates to pre-released product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.]

Microsoft Edge implements the improved F12 developer tools found so useful in Internet Explorer 11. Debug, test, and speed up your webpages using a familiar tool that will continue to grow and improve with Microsoft Edge.

## The F12 tools at work

There are seven distinct tools, each with their own tab in the F12 tools interface. Here you'll find an image of each tool and a quick summary of what it does, followed by lists of its main features and typical tasks.

## The DOM Explorer tool (CTRL+1)

[The DOM Explorer tool](./dom-explorer/) shows the structure of your webpage as it's being rendered in the browser and makes it possible to edit your HTML and styles in a live page. You can do this without having to edit and reload your sources, so you can quickly solve display issues or experiment with new ideas.
![Edge DOM Explorer](./media/Edge_DOMExplorer.png)

**Features** in the DOM Explorer tool include:
 - IntelliSense autocompletion suggestions when editing HTML attributes and CSS properties.		+|IntelliSense autocompletion suggestions when editing HTML attributes and CSS properties.|
 - Drag DOM nodes to rearrange them.		+|Drag DOM nodes to rearrange them.|
 - Support for compiled CSS sourcemaps		+|Support for compiled CSS sourcemaps|

**Development and debugging tasks it makes easier:**		
  - Determining why an element is not displaying at the right place or right size.
 - Figuring out which CSS styles and media queries are being applied to an element.
 - Testing a series of different colors for an element to see which looks best.

[Learn more about the DOM Explorer tool.](./dom-explorer/)

## The Console tool (CTRL+2)
![Edge Console Tool](./media/Edge_Console.png)

The [Console tool](./console/) provides a way to interact with your running code:

  - change variable values or inject code into a live site with the Console's command line.
  - use the [Console Debugging API](./console/using-the-console-api/) to send out debug information.
  - see browser error messages and status codes.

**Features** in the [Console tool](./console/) include:

  - Open the Console at the bottom of any other tool with the Console button or CTRL + `.
  - [Console Debugging API](./console/using-the-console-api/) methods for timing, counting, grouping, and more.
  - IntelliSense autocompletion suggestions on the command line speed up input, reduce typos, and help you discover aspects of JavaScript APIs.

**Development and debugging tasks it makes easier:**

  - targeting specific iFrames.
  - timing code execution down to the statement with new timing methods.
  - changing the value of a variable in running code without reloading.

[Learn more about the Console tool.](./console/)

## The Debugger tool (CTRL+3)
![Edge Debugger Tool](./media/Edge_Debugger.png)

You use the [Debugger tool](./debugger/) to examine what your code is doing, when it's doing it, and how it's doing it. Pause code in mid-execution, step through it line-by-line, and watch the state of variables and objects at each step.

**Features** in the [Debugger tool](./debugger/) include:

  - No-refresh debugging. Set your breakpoints and go without reloading and losing state.
  - Tabbed document interface for easier management of multiple scripts.
  - Breakpoints on standard code, XHR responses, and events.

**Development and debugging tasks it makes easier:**

  - Seeing what led to a function call using the Call stack.
  - Making compressed or minified code more readable using source maps.
  - Monitoring web worker creation and execution.
  - 
[Learn more about the Debugger tool.](./debugger/)

## The Network tool (CTRL+4)
![Edge Network Tool](./media/Edge_Network_details.png)

The [Network tool](./network/) gives you the fine details of any network requests involved in the loading and operation of your webpages.

**Development and debugging tasks it makes easier:**
  - Viewing the amount of bandwidth your page consumes across resources.
  - Debugging AJAX requests by viewing request and response headers and bodies.
  - Identifying network requests that slow the loading of your webpages.

[Learn more about the Network tool.](./network/)

## The Performance Tool (CTRL+5)
![Edge Performance Tool](./media/Edge_Performance.png)

The [Performance tool](./performance/) helps you dig into what is happening when your page slows down. Using it to profile specific points of slowness shows the operations that are causing them. In Microsoft Edge, the Performance tool combines the previous **UI Responsiveness** and **Profiler** tools to create an end-to-end view of your scripting and painting performance.

Some interesting features are:

  - Identifying the different sources of CPU activity causing UI slowness.
  - Insight into your webpage's frame rate and how much repaints and reflows cost.
  - Setting labels on the timeline to isolate user scenarios.

**Development and debugging tasks it makes easier:**

  - Testing code optimizations.
  - Speeding up your webpages.

[Learn more about the Performance tool.](./performance/) 

## The Memory tool (CTRL+6)
![Edge Memory Tool](./media/Edge_Memory.png)

When a webpage starts out fast and slows down after you use it for a while, the culprit is usually a memory leak. The [Memory tool](./memory/) tracks the memory use of your webpage, helping you identify where memory use is growing, why it's growing, and how to fix it.

Some interesting features are:

  - A timeline to see progressive changes in memory use.
  - Snapshots to examine the details of memory use at specific points.
  - Snapshot comparisons to identify specific points of growth.

**Development and debugging tasks it makes easier:**

  - Identifying detached DOM nodes.
  - Identifying points of memory growth.
  - Measuring the memory use of objects.

[Learn more about the Memory tool.](./memory/)

## The Emulation tool (CTRL+7)
![Edge Emulation Tool](./media/Edge_Emulation.png)

The [Emulation](./emulation/) helps you test how your webpages run on different screen sizes and hardware features, and how they respond to different user agent strings.

Some interesting features are:

  - You can emulate different screen sizes and resolutions.
  - GPS simulation.

**Development and debugging tasks it makes easier:**

  - Testing responsive designs on multiple screen types.
  - Testing location-aware features for a mobile site.

[Learn more about the Emulation tool.](./emulation/)
