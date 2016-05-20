# File API


The [`File` API](https://msdn.microsoft.com/library/Hh772315), currently being standardized by the [World Wide Web Consortium (W3C)](https://w3c.github.io/FileAPI/), represents file objects in web applications and allows access to file information via JavaScript and an `input[type=file]` element. By using `File` API, web developers can access local files on the client machine in a secure way without the need for extensions or plugins.

The `File` API allows a browser or app to read and manipulate files but only if the user provides permission to do so. Additionally, the File API allows for smoother file upload experiences without plugins.

Multiple file uploads (4 GB per file) with file type filtering is also supported. In the following example, multiple GIF or JPEG files can be selected by the user:

```html
<input type="file" name="pic" multiple accept="image/gif, image/jpeg" />
```

For more information, see the [File Upload state (type=file)](http://www.w3.org/TR/html5/forms.html#file-upload-state-(type=file))  section within the HTML5 spec.


## File API Example

The following code example acquires basic file-related information such as name, type, and size.

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/ZWXQpe?editors=1010)

## Blob constructor

The [`Blob`](https://msdn.microsoft.com/library/Hh772298) constructor enables a web developer to create or manipulate a `Blob` (often equivalent to a file) directly on the client. The constructor is defined in the W3C's [File API](http://go.microsoft.com/fwlink/p/?LinkId=210224) spec.

Check out the [Blob](./blob/) Dev Guide entry for more details.

## FileReader object

The  [`FileReader`](https://msdn.microsoft.com/library/hh772310) object lets you asynchronously read individual  `File`  or  `Blob`  objects by firing progress events as the read occurs to event handler methods attached to the  `FileReader`  object. Because of the asynchronous reading, it is possible to catch errors, know when a load is complete, and monitor the read progress.

For more details check out the [FileReader](./fileReader/) Dev Guide entry!

## Streams

The Steams API is based off of the [W3C Streams API specification](https://www.w3.org/TR/streams-api/), and is supported in the ms-prefixed form, [`MSStream`](https://msdn.microsoft.com/library/hh772328).

The `MSStream` object is a Document Object Model (DOM) type that represents a stream of unsized, sequential binary data. You use the `MSStream` object for data that is streaming over the network which hasn't completed downloaded yet, or as an analogous type to `IInputStream` WinRT objects. `MSStream` is backed by `IInputStream`.

When you get `MSStream` from HTML5 API (like an [`XmlHttpRequest`](https://msdn.microsoft.com/library/ms535874) with a [`responseType`](https://msdn.microsoft.com/library/hh872882) of “`ms-stream`”, as you’d use when downloading a file or video), you can pass those results to various WinRT APIs that accept [`IInputStream`](https://msdn.microsoft.com/library/windows/apps/windows.storage.streams.iinputstream.aspx) or [`IRandomAccessStream`](https://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream) as input.

![spec](FileAPI)

## API Reference

[File API](https://msdn.microsoft.com/library/Hh772315)

## Specification

[File API](http://go.microsoft.com/fwlink/p/?LinkID=210224)


