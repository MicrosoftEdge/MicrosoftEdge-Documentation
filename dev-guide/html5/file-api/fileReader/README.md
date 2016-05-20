# FileReader

The [`FileReader`](https://msdn.microsoft.com/library/hh772310) object enables asynchronous reads on individual [`File`](https://msdn.microsoft.com/library/hh772315) or [`Blob`](https://msdn.microsoft.com/library/hh772298) objects by firing progress events as the read occurs to event handler methods attached to the `FileReader` object. Because of the asynchronous reading, it is possible to catch errors, know when a load is complete, and monitor the read progress.

`FileReader` is able to read files four different ways:

Method | Description
:----- | :-------
[readAsBinaryString](https://msdn.microsoft.com/library/dn792847) | Reads the contents of a `Blob` or `File` as raw binary.
[readAsText](https://msdn.microsoft.com/library/hh772314) | Reads a `File`, `Blob`, or [`MSStream`](https://msdn.microsoft.com/library/hh772328) object into memory as a text string.
[readAsDataURL](https://msdn.microsoft.com/library/hh772313) | Reads a `File` or `Blob` object into memory as a data URL string.
[readAsArrayBuffer](https://msdn.microsoft.com/library/hh772312) | Reads a `File`, `Blob`, `MSStream` into memory as an [`ArrayBuffer`]() object.

## Example

A drag and drop(dnd) feature is an easy to use method for gathering local files from a user. 

See this example for how to select text files and display their contents using [`FileReader`](https://msdn.microsoft.com/library/hh772310). 
Using Windows Explorer (or similar), select one or more text files (directories are not allowed), and then drag them to the drop box below. The contents of the selected text files will be displayed in alerts:

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/KzzNaZ)(325)




The code is broken down into 6 steps:

1. If the specific file API feature is not present, replace all prior markup with HTML that alerts the user that the necessary [`File`](https://msdn.microsoft.com/library/hh772315) API feature is not available. Otherwise, add two DnD event listeners to the DnD box:
`<div id="fileDropBox">Drop files here.</div>`
2. When a user drags files from a Windows Explorer window (or similar) to the DnD box, the drop event fires and executes the `handleFileSelection` function. The event (`evt`) passed to `handleFileSelection` contains the file(s) the user selected.
3. `handleFileSelection` then loops through each file it was handed (via `evt.dataTransfer.files`), does some basic error checking, and fires off an asynchronous read request for the given file via `startFileRead(file)`. When the file has successfully been read into memory, an event handler is invoked to do something useful with the file data, as discussed next.
4. The `startFileRead(fileObject)` function creates a new [`FileReader`](https://msdn.microsoft.com/library/hh772310) object for each file passed to it. This per file `FileReader` object (i.e., reader in the code) exposes properties intended to contain function pointers (i.e., event handlers). reader also exposes a number of file reading methods, in particular `reader.readAsText`. When the `readAsText` method successfully (and asynchronously) loads the file’s content into memory, the function pointer contained in `reader.onloadend` is invoked. That is, the `displayFileText` event handler is executed.
5. The event object passed to `displayFileText` contains the results of the read (as instigated by `reader.reasAsText`). More precisely, `evt.target.result` contains the results of the requested read, in the form of a string, for the associated text file. We then display this string (that is, the file’s textual contents) as follows:
`alert(sanitizeHTML(fileString), {width: 40, tile: true});`
In case the user selects one or more HTML or HTML-like files, `santizeHTML` is called to replace "<" with "&lt;", ">" with "&gt;", etc.
6. Moving back to the `startFileRead` function, if a file read error should occur or if the user cancels a read operation, the `handleFileReadError` and `handleFileReadAbort` event handlers, respectively, are invoked.


## API reference
[FileReader](https://msdn.microsoft.com/library/hh772310)

## Specification
[File API](https://w3c.github.io/FileAPI/#dfn-filereader)

