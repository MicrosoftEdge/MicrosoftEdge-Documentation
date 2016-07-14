# Selection API

The  [`selection`](https://msdn.microsoft.com/library/ff974359) object represents the active selection, which is typically a highlighted block of text or other elements in the document. The active selection can be used to complete an action issued by a user or a script.
This object contains info about the range of a text selection, regardless of which direction (left to right, or right to left) the selection has been made. Info is also stored about the caret position.

Both users and scripts can create selections. Users create selections by dragging a finger or mouse over a portion of the document. Scripts create selections by calls to `selection` methods. To get the active selection, apply the [`getSelection`](https://msdn.microsoft.com/library/ff975169) method to the document object. 

## Selection range

Range is a continuous selection of nodes. With a text node, it can be seen as the highlighted text. The following methods are used for a selection's range:

Method | Description
:------ | :-------
[addRange](https://msdn.microsoft.com/library/ff975172) | Adds a range to the current selection.
[removeAllRanges](https://msdn.microsoft.com/library/ff975178)/[empty](https://msdn.microsoft.com/library/dn903932) | Removes all ranges of the selection.
[getRangeAt](https://msdn.microsoft.com/library/ff975177) | Returns a specified [`range`](https://msdn.microsoft.com/library/hh772133) from a selection. The [`range`](https://msdn.microsoft.com/library/hh772133) is specified by an index and cannot be greater than the number that is returned by [`rangeCount`](https://msdn.microsoft.com/library/ff974693). 
[removeRange](https://msdn.microsoft.com/library/ff975179) | Removes a range from a selection.
[setBaseAndExtent](https://msdn.microsoft.com/library/dn903953) | Sets the *anchor* (base) and *focus* (extent) boundary points for the selection.

For `setBaseAndExtent`, an *anchor* is the start of a selection, a the *focus* is where the selection ends. Both ignore direction, meaning an anchor/focus could be at either the beginning or end of a seleciton.

In this code sample, `removeAllRanges` is used to clear the selection range on a page:

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/WwZQmV)

> Currently, Microsoft Edge doesn't support multiple or disjointed selections. A selection always has one [range](https://msdn.microsoft.com/library/hh772133). 

## Collapsing selections

Collapsing is used to replace the current selection with an empty selection. Different methods provide different locations for the caret upon collapsing:

Method | Description
:----- | :----------
[collapse](https://msdn.microsoft.com/library/ff975173) | Replaces the current selection with an empty selection (or a caret) at the given offset.
[collapseToEnd](https://msdn.microsoft.com/library/ff975174) | Collapses or sets the insertion point or caret at the end of a selection object.
[collapseToStart](https://msdn.microsoft.com/library/ff975175) | Collapses, or sets the insertion point or caret at the beginning of a selection object.


The following code snippet shows [`collapseToEnd`](https://msdn.microsoft.com/library/ff975174) being used to put the caret at the end of a selection made by the user upon pressing a button:

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/NNaGmQ)

## Node manipulation

The `selection` API includes methods that enable replacing, deleting, extending, and searching selections for nodes. 

Method | Description
:------ | :-------
[containsNode](https://msdn.microsoft.com/library/dn903930) | Determines if the given node is included in the selection.
[deleteFromDocument](https://msdn.microsoft.com/library/ff975176) | Deletes the selected nodes from a document.
[extend](https://msdn.microsoft.com/library/dn903952) | Moves the focus of the selection to a specified offset within the given node.
[selectAllChildren](https://msdn.microsoft.com/library/ff975180) | Replaces the current selection with all the contents of the given node.

In the case of using the `extend` method, the *focus* of the selection can be shifted forwards or backwards. The *focus* is the where the selection ends, regardless of direction.

![spec](Selection)

## Specification
[Selection API](http://rniwa.github.io/selection-api)
