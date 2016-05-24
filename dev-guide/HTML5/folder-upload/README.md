# Folder upload

Microsoft Edge supports uploading files, folders, and combinations of files and folders using APIs that are interoperable with Chrome.

| API | Description |
---------------------
| DataTransferItem.[webkitGetAsEntry]() method | Returns the `WebKitEntry` object (a file or directory) corresponding to the `DataTransferItem`. |
| [WebKitEntry]() interface | Represents a file or directory. (Use the `isDirectory` and `isFile` properties to determine what it is.) |
| [WebKitDirectoryReader]() interface | Provides the `readEntries` method to traverse the files in the given directory. |
| [WebKitFileSystem]() interface | Provides an interface to the (sandboxed) file system for the upload. You can use the `filesystem` property of a `WebKitEntry` object to get the globally unique name and the root folder of the file system being used for the drag and drop (or file/folder picker) operation. |

## Example

This snippet demonstrates how to differentiate between the files and folders of an item
that's been selected for upload.


![spec](FileSystemAPI)

## API Reference

[FileSystem API]()

## Specification

[FileSystem API](https://wiki.whatwg.org/wiki/DragAndDropEntries)
