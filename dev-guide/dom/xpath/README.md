# XPath API


The XPath API provides a way to locate and process elements in XML documents. As of Microsoft Edge, the [Document Object Model (DOM) Level 3 XPath Specification](http://go.microsoft.com/fwlink/p/?LinkId=524495) is supported which offers native support in the DOM for XPath navigation and searching in XML documents.

In older versions of Windows Internet Explorer, developers had to use 3rd party libraries or a MSXML hack to provide XPath functionality. With Microsoft Edge, XPath API code that has worked in other browsers should work seamlessly in Microsoft Edge too.


For more information about XPath, check out [Improving interoperability with DOM L3 XPath](http://blogs.windows.com/msedgedev/2015/03/19/improving-interoperability-with-dom-l3-xpath/) on the Microsoft Edge dev blog.

## Example
The code below demonstrates a use of the new XPath functionality. It delivers the same results across all major browsers: logging the appropriate numbers within the `span` elements to the developer [console](../../f12-devtools-guide/console/).

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/eZEjBN)

![spec](Document Object Model (DOM) Level 3 Xpath Specification)

## Related topics
[Improving interoperability with DOM L3 XPath](http://blogs.windows.com/msedgedev/2015/03/19/improving-interoperability-with-dom-l3-xpath/)

## Specification
[Document Object Model (DOM) Level 3 XPath Specification](http://go.microsoft.com/fwlink/p/?LinkId=524495)


