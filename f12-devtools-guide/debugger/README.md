# Debugger

Use the **Debugger tool** to navigate your code as it runs, set watches and breakpoints, view call stacks, and improve the readability of compiled/minified JavaScript.

## When do you need the Debugger tool?
The **Debugger tool** helps you figure out why pieces of your code are:

  - not running as expected.
  - not running when expected.
  - running when they shouldn't.

The **Debugger tool** pauses code mid-execution, lets you back up and repeat blocks of code, and lets you inspect your code from different angles to see:

  - how the JavaScript engine got there.
  - what the values of certain variables are mid-execution.
  - how things are changing, step-by-step.

## Starting the Debugger tool
Load the problematic webpage in Microsoft Edge and open F12 developer tools by pressing the **F12** key or selecting the **F12 developer tools** option from the **More Actions** menu. Click the **Debugger** menu item or press CTRL + 3 to open the tool.

### The Debugger tool layout
The default layout of the **Debugger tool** shows three panes with adjustable widths and/or heights.

![Edge Debugger](../media/Edge_Debugger.png)

  - The *script* pane (left) shows the source of the webpage's HTML and JavaScript in a tabbed interface. The script pane's scroll bar area also highlights the location of breakpoints and matches for search terms.

  - The **Watches** pane (upper right) displays variable values. When you're in break mode, it shows the local variables for your current location in code, called locals, and specific variables you've asked it to track, called watches.

  - The **Callstack and Breakpoints** pane in the lower right includes:
    - **Callstack**: This mode shows the chain of function calls that led to the current point in execution. For example, if function *a()* called function *b()*, which called function *c()*, and execution paused in *c()*, it would show the path from *a()* to *b()* to *c()*.

    - **Breakpoints**: This mode shows a list of the breakpoints and tracepoints you've set and provides functions to delete, toggle, and edit breakpoints.

The **Console** icon (next to the **Help** icon at the top of the F12 tools) or CTRL + ` opens the [**Console tool**](../console/) in a fourth pane below the *script* pane. Open it when you want to view **Console** output, or use the **Console** command line.

### Starting a debugging session
There are three ways to begin a debugging session.

  - [Set a breakpoint](#setting-and-managing-breakpoints). When the execution of your code reaches it, you enter break mode and can start running code step-by-step.

  - Initiate a break in code. Click the **Break** icon (two vertical parallel lines) at the top of the tool or press CTRL + SHIFT + B. The **Debugger tool** breaks on the next statement executed.

  - Set the **Exception control** to break on unhandled exceptions and run your webpage's code until an exception is hit.

The **Debugger tool** debugs without requiring a page refresh, preserving state.

### Controlling session flow
After the **Debugger tool** reaches a breakpoint and you're ready to move on from it, you can use the execution control icons to decide what to do next.

![Edge Debugger Execution Control Icons](../media/gdr_f12_DebuggerIcons.png)

From left to right, the icons are:

  - **Continue** (F5 or F8): Leaves break mode and continues to the next breakpoint. Holding down F5 will repeatedly move past breaks until you release it.
  - **Break** (CTRL + SHIFT + B): Breaks on the next statement run.
  - **Step into** (F11): Steps into the function being called, or if not at a function, to the next statement.
  - **Step over** (F10): Steps over the function being called, or if not at a function, to the next statement.
  - **Step out** (SHIFT + F11): Steps out of the current function and into the calling function.
  - **Break on new worker** (CTRL + SHIFT + W): Breaks on the creation of a new web worker.
  - **Exception control** (CTRL+ SHIFT + E):

![Edge Debugger Execution Control Icons](../media/F12BlueDebuggerUnhandledException.png)

By default this ignores exceptions and they're just logged to the [**Console tool**](../console/). You can choose to break on all exceptions, or just those not being handled by try... catch exception handlers in your code.

**Note**  Be careful about breaking on unhandled exceptions when you have one or more large JavaScript libraries included in your webpage and you're not excluding them via Just my code. You might find yourself stepping through a lot of minified code that isn't yours.

Additionally, after you've broken on a statement, you can right-click in the script pane to expose three additional controls:

  - **Show next statement**: Puts the highlight on the next statement to be run by clicking Step into.
  - **Run to cursor** (CTRL + F10): Resumes execution and breaks at the point in code where your cursor is, so long as it's a valid place to break.
  - **Set next statement** (CTRL + SHIFT + F10): This lets you skip over statements in a function without having to step out of it, somewhat like commenting out the statements temporarily. You can also skip backwards to a statement that already ran. You won't rewind the webpage when you do this. You just repeat your code from that point.

### Formatting code for readability
The two icons to the right of **Exception control** make large blocks of code easier to read in the *script* pane.

  - **Pretty print** takes a compressed or minified block of JavaScript, HTML, or CSS and formats it for readability. This:

###### *JavaScript*
```javascript
function _ge(n){return _d.getElementById(n)}function sj_wf(n)
{var t=arguments;return function(){n.apply(null,[].slice.apply(t).slice(1))}}
function sj_ce(n,t,i){var r=_d.createElement(n);return t&&(r.id=t),i&&(r.className=i),r}
```

Becomes this:

```javascript
function _ge(n) {
  return _d.getElementById(n);
}
function sj_wf(n) {
  var t = arguments;
  return function () {
    n.apply(null, [].slice.apply(t).slice(1));
  };
}
function sj_ce(n, t, i) {
  var r = _d.createElement(n);
  return t && (r.id = t) , i && (r.className = i) , r;
}
```

  - **Word wrap** breakslong lines to fit them within the script pane so you don't have to scroll horizontally to see the full line.

### Source maps
When you've written code in a language that compiles to JavaScript or CSS and/or you've used a compressor, the code running in the browser is very different from the code you wrote. That can make debugging very difficult. Even compressed code that's been made more readable with **Pretty print** may have function, selector, and variable names that are much different than in your original source code. Debugging is much easier when errors point to where the issues are in your original source code, rather than a highly modified file running in the browser.

A number of compilers and compressors now provide source maps; intermediate files that map the compiled JavaScript or CSS back to the original source. When the compiled or compressed JavaScript or CSS contains a pointer to a source map, all files are present, and source map functionality is enabled, the Debugger tool shows the original source and maps breakpoints and errors to it.

**How do I enable source maps?** The compiler or compressor generating the JavaScript includes a comment with the name of the map file. For example, if `myfile.js` was compressed to `myfile.min.js` by a compressor that supported source maps, it would generate a map file called `myfile.min.js.map` and put a comment in `myfile.min.js` like this:

```javascript
//# sourceMappingURL=myfile.min.js.map
```

When you open a file with **Debugger tool** that has this kind of comment, the tool looks for the map file. If found, the last [toolbar](../debugger#controlling-session-flow) icon on the right ![Edge Debugger Execution Control Icons](../media/gdr_f12_SourceMapsIcon.png) is enabled as a toggle. When the icon is toggled on and the source file is where the map indicates, your source code is displayed instead of the compiled/compressed JavaScript or CSS. If the source file cannot be found, the **Debugger tool** displays an error message.

If the map isn't found automatically, you can choose a source map for a file. Right click the file's tab to find this option. This is useful for code where comments like the one with the source map's location have been stripped out.

![Edge Debugger Source Map](../media/sourcemapdesignate.png)

The **Debugger tool** won't display an error if the map is not found. In many cases people download compressed or compiled libraries, such as jQuery, and don't plan to or want to debug them. If the map file is not where the comment says it will be, the comment is ignored and the feature is not enabled

**Mapping is not 100% perfect.** Call stacks and inspector functions show the compiled/compressed variable's name as it is used in the running code, not in the original source. Also, the quality of source maps varies based on the software producing them. The quality of the mapping is affected by the quality of the map.

## Setting and managing breakpoints
Different types of points allow you to instruct the **Debugger tool** to do different things when it reaches them.

  - **Regular breakpoints** are the easiest to set if you have one statement per line. In the shaded leftmost margin of the script pane, click next to a line number. A dot appears and the breakpoint is set.

On lines with multiple statements, you can set breakpoints for individual statements. Right-click on a statement and set a breakpoint from the context menu or put the cursor inside the statement and click F9.

  - **Conditional breakpoints** only break if a condition you set evaluates to true. For example, let's assume there's a students variable in your code and you only want to break when the value of students is greater than 20.
Right-click the breakpoint or statement and click Condition from the context menu, or press ALT + F9. In the condition dialogue, enter `students > 20` and submit the condition. `A + symbol` appears on your breakpoint and your code only breaks on it when `students > 20` evaluates to true.

  - **Tracepoints** act like temporary `console.log()` commands.

To set one, right-click a statement and click **Insert tracepoint** from the context menu. In the dialog, enter a message in the same format you would use for an argument of the `console.log()` command. It has access to the same local and global variables the statement you clicked on does.

  - **Event Breakpoints and Tracepoints** work like the breakpoints and tracepoints above, but instead of being triggered when a specific block of code is executed, they are triggered by specific events. Each has an optional conditional filter to help you narrow down their scope to the specific instance of an event you want to inspect. They can be added using the **Add event breakpoint** and **Add event tracepoint** icons highlighted in the image below.

![Add event breakpoint](../media/eventpoints.png)

  - **XHR Breakpoints** set a breakpoint that breaks whenever an XHR request has been fulfilled and use the **Watches** pane to inspect the XHR object that received the response.

![Edge Debugger XHR Breakpoints](../media/Edge_Debugger_breakpoints.png)

### The Breakpoints pane
Besides appearing next to statements in the script pane, the full collection of breakpoints show in the **Breakpoints** pane.

![Breakpoints Pane](../media/F12BlueDebuggerBreakpoints.png)

You can manage multiple points in the **Breakpoints** pane. Right-click anywhere in it to get context menu options to delete all points or toggle them on or off. The options also appear as icons in the upper-right of the pane, and to the left and right of individual breakpoints. Right-clicking any individual point presents a **Condition** or **Trace message** option in the context menu to let you change the message or make the breakpoint conditional.

The panel can trace many breakpoints from many different scripts that may be feeding your pages. Clicking any breakpoint's associated file name makes that the active file in the *script* pane and scrolls to the appropriate line.

Breakpoints used to be session based in Windows Internet Explorer, but in Microsoft Edge the behavior was changed so they are kept and no longer disappear when you close the browser. This means you no longer have to set them every time you open the browser to debug, but it also means you might want to manually delete them when you're done debugging. The easiest way is to open a script file and click the **delete all** icon in the upper-right of the **Breakpoints** pane.

Multiple breakpoints can be selected using `CTRL + CLICK, SHIFT + CLICK, or CTRL + A` methods.

## Inspecting objects and variables
After you've set your breakpoints and stepped into your code, the Debugger tool gives you several ways to see what's going on.

![Edge Debugger Inspector](../media/Edge_Debugger_inspect.png)

  - In the *script* pane, when the debugger is paused on a statement, hover your mouse over any variable, function, or object to see more info in an overlay. Move your mouse down into the overlay to expand and inspect objects much like you can if you log them to the [**Console**](../console/) with the [**dirxml()**](https://msdn.microsoft.com/library/dn265067.aspx) method.
Click **Add watch** at the bottom of the overlay to add the variable or object to the **Watches** pane.

  - The **locals** node in the **Watches** gives you a catalog of all objects and variables, both in the local and global scope, available to the statement that is the focus of the current break. This can help identify variables that are in the wrong scope.

  - A variable or object added to the **Watches** pane with the **Add watch** command appears beneath the **locals** node and it is monitored at every step in break mode, even if the current breakpoint is in a different scope. Autocomplete functions give you suggestions of known variables when adding watches.

  - It's fairly common for a function to be called unexpectedly. This can cause data corruption and speed issues. The **Callstack** pane shows the route the JavaScript engine took to get to the function. The current function appears at the top, and the calling functions appear below it in reverse order.

  - To help you trace where a function was called when it's been called asynchronously, the **Callstack** pane displays a call's asynchronous roots.

![Edge Debugger Call Stack](../media/async.png)

The image above shows a very simple asynchronous call, created by running the following code in the console.

```javascript
function getReturn(){
  debugger;
}
function setup(){
  window.setTimeout(getReturn, 1000);
}
setup();
```

  - When breaking on a function with a **return value**, step into the function until you've stepped to the closing curly bracket. The return value will be displayed in the **Locals** portion of the **Watches** pane. Step again and the value will be returned to the code that called for it.

For a quick demonstration, try this code in the **Console**:

```
function showval() { var x = 0; x++; debugger; return x; } showval();
```

It will call the function, `break on debugger`, and you can step into it to see the return value.

## Managing multiple scripts
The *script* pane in the **Debugger tool** provides a tabbed interface where you can select open files by clicking their tabs and quickly navigate through open tabs using `CTRL + TAB`.

![Edge Debugger Script Pane](../media/gdr_f12_DebuggerFileOpen.png)

Open files by clicking the folder icon or pressing `CTRL + O` to open the file list. In the file list, documents are grouped into nodes under the primary document of the frame or window in which they're running. Hover over an individual file to show the file's full URI.

Web Workers are displayed as separate nodes from the documents(s) that created them. Iframes are displayed as child nodes of the main document.

The **Type to filter** box at the top of the file list will filter the available files by filename. To run a text search through all available files, use the **Find in files** `CTRL + F` box in the upper right of the F12 tools. If your text is found, it opens the first file where the search text is matched, and maps the matches in that file on the scrollbar of the *script* pane. Pressing `F3` takes you to the next match.

A list of which files you have open while debugging a webpage is recorded when you leave the page or close the browser. When you return to the webpage, the files you had open will re-open in the debugger.

## Just my code
Just my code lets you indicate that certain scripts are third-party libraries that should be ignored while debugging. This prevents the **Debugger tool** from stepping into code you didn't write and don't plan to change.

To indicate a file is library code you want excluded from debugging, the following methods are available:

  - place your mouse over its name in the script pane's file list. The Just my code icon appears next to the file name. Click the icon or type CTRL + L to toggle it on or off.

  - Right-click the script's tab at the top of the pane and select "Library code" from the context menu.

  - Right click an item in the **Call stack** and select "Library code" from the context menu to mark its parent script as library code.

> NOTE:   Because the icon displays when you mouse over the file's name, it continues to display after being toggled off if the mouse pointer is still over the file's line in the list. To check that it's been toggled off, move the mouse over another file.

The **Just my code** icon in the **Debugger tool**'s icon bar acts as a toggle to include or exclude all the files that have been marked as library code. When **Just my code** is enabled, if library code is part of the **Call stack** when execution pauses, the **Just my code** icon in the upper right corner of the **Call stack** pane toggles the details of that execution frame on and off. Double-clicking on a "[Library code]" line in the **Call stack** pane expands its details.

Keeping track of libraries between sessions is one of the features of **Just my code**. This is managed via JSON files located at `%APPDATA%\..\LocalLow\Microsoft\F12\header\MyCode.json` and `%APPDATA%\..\Local\Microsoft\F12\header\MyCode.json`.

You can edit the files to maintain a default list or add wildcards for a domain or file type. For example, the expression `*.min.js` is used to mark all files ending with `.min.js` as library code automatically.

## Debugging and In Private Browsing
In [Private Browsing](http://windows.microsoft.com/internet-explorer/products/ie-9/features/in-private) lets you browse without leaving a persisting trail in your browser history, but if you debug while using In Private Browsing, the Debugger might save some information that will persist.

The Debugger saves info about the pages and files you debug when you add a breakpoint in a file, mark a file as library code with the Just My Code feature, or open a file in the Debugger that isn't the root page (such as an external CSS or JavaScript file). These are saved to provide debugging functionality across sessions, are separate from the browser history, and are not cleared at the end of an In Private Browsing session.

If you have any privacy concerns, you can remove this info by clearing any breakpoints you set, closing all files you've opened in the debugger, and you can delete your **Just My Code** settings by deleting the files at `%APPDATA%\LocalLow\Microsoft\F12\header\MyCode.json` and `%APPDATA%\Local\Microsoft\F12\header\MyCode.json`.

## Don't debug and performance profile
Because of the additional overhead needed to run the Debugger and Performance tools at the same time, the values in your Performance report will not reflect the actual load and running time of your code. Trying to run both of these tools at once is not supported.

## Related topics

[Microsoft Edge Developer Tools on Twitter: Find helpful F12 hints and news updates](https://twitter.com/EdgeDevTools)

[Edit CSS in the Debugger](/edit-css-in-debugger)

[Webstorage in the Debugger](/webstorage-in-debugger)