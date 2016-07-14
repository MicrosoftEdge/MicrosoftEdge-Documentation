# Network

Use the Network tool to view communication between the browser and server(s), inspect request and reply headers, see response codes, and debug AJAX.

## Monitor your browser's communications
The **Network** tool in F12 developer tools helps you inspect page load times, responses to AJAX requests, and all network activity used to load and run modern webpages and applications.

**Start with the top row**

The top row of icons in the **Network** tool control the recording of network traffic and give you tools to provide better accuracy, manage your results, and search through the traffic you capture.

![Edge F12 Network Toolbar](../media/network-icons.png)

From left to right, the tools are:

  - **Enable/Disable network traffic capturing (Ctrl + E)** starts and stops the recording of network traffic.

  - **Export captured traffic as a HAR** (Ctrl + S) saves the data you've recorded to a .har file (HTTP Archive specification -- captures page loading information in a JSON format).

  - **Always refresh from server** is a toggle switch with on and off states. When on, Microsoft Edge downloads all page elements from the remote server, not from the browser cache.

  - **Clear cache** removes saved files from the browser's cache. Browsers commonly save page elements to disk and use them again for faster reloads. When you're trying to get the true measure of a page's load time, clearing the cache makes sure all elements are being downloaded from the network.

  - **Clear cookies** ensures that all cookies related to the current domain are removed, so that you get the experience of loading the page for the first time.

  - **Clear entries on navigate** is a toggle switch with on and off states. When in the off state, network traffic for a window or tab is recorded continuously as the browser moves from page to page. When in the on state, recorded traffic is cleared each time you navigate to a new page. This is turned on by default.

  - **Clear session** clears all recorded network traffic from the tool.

  - **Content type filter** lets you restrict the type of content displayed. Click for a drop down menu of content types, currently offering: Documents, Style sheets, Images, Scripts, Media, Fonts, XHR, and Other. The default is to show all, but you can limit it to any combination of those you choose.
 
  - **Find** (far right, not pictured) provides a text search in the item paths, so you can easily find specific files.

By default, a summary view is displayed, as seen here.

![Edge F12 Network Toolbar](../media/Edge_Network_files.png)

## Reading and interpreting the data
The **Network** tool includes two views of network traffic. The **Summary** view gives a quick look at all captured info for a tab or webpage, and the **Details** view gives you details of each connection, such as request and response headers and detailed timing info. You can view the details of any file/connection by clicking on it and the summary will expand out from the side.

![Edge F12 Network Summary Details](../media/Edge_Network_details.png)

### Summary view
The Summary view shows all network traffic for a page in a table. By default, the info is presented chronologically, but you can sort the table differently by clicking the header of any column. This table describes the type of info you can view.


Column header | Description 
:------------ | :------------- 
**Name/Path** | The filename and/or path of the item loaded.
**Protocol** |	The connection protocol. For example, connections to a standard web server use HTTP, while encrypted connections generally use HTTPS. Microsoft Edge supports a number of connection protocols.
**Method** |	The HTTP method verb (for example, `POST` or `GET`).
**Result/Description** |	The HTTP response code and a brief description of what it means.
**Content Type** |	The type of content that's received.
**Received** | The total amount of data that's received, in bytes.
**Taken** |	The total time elapsed to receive the content, in milliseconds.
**Initiator** |	The type of browser action or DOM node that prompted the network request. Where possible, this is linked to the place in the code where the download was called for or initiated, and clicking it will navigate to the Debugger tool with that file loaded and queued up to that place.
**Timings** |	A timeline of the network events.

### Details view
The **Details** view provides info about a specific request. To see the details, click an entry in the Summary view. You will find this info in each tab of the **Details** view.

Tab | Description 
:------------ | :------------- 
**Headers** | Displays the request headers that are sent to the server and the response headers received from the server.
**Body** | Indicates the response data received from the server. If the response is an image, the image is shown. If the response is binary, a link to save the content to disk is shown. Otherwise, the response text is shown in a scrollable text area.
**Parameters** | The query string parameters of GET requests. While POST requests put the parameters in the headers, GET requests include them in the URL. They're broken out here for easier reading.
**Cookies** | Indicates the cookies that are sent or received. There are eight columns in the Cookies tab. <table>
Column header |	Details
**Direction**  |	The cookie that is sent or received.	
**Key**  |	The identifier of the Key-Value pair.	
**Value**  |	The value of the Key-Value pair.	
**Expires**  |	The cookie expiry date.	
**Domain**  |	The cookie domain.	
**Path**  |	The cookie path.	
**Secure**  |	Indicates if the cookie is accessible only through Secure Hypertext Transfer Protocol (HTTPS) connections.	
**HTTP Only**  |	Indicates if the cookie is accessible only through HTTP (not JavaScript). </table> |
**Timings** | 	Lists events and their corresponding times that are relevant to the request. The timing info is displayed as table and a graphical timeline. The following events are captured: Wait, Start, Request, Response, Gap, DOMContentLoaded, and Load. Clicking an event in the table or the timeline highlights it and shows an explanation of the event type.

## Limitations
Microsoft Edge captures and reports network traffic efficiently, but there are some limitations. The network traffic measured and displayed in the **Network** tool has similar characteristics to unmeasured traffic, but the timings don't precisely match the unmonitored results.

HTTP traffic is captured only for the process associated with the Microsoft Edge window/tab that is open when you start capturing traffic in the Network tool. To debug two windows/tabs at the same time, you must open a **F12 developer tools** window for each. The network tools also cannot monitor network traffic for tabs that create multiple processes.

## Related Topics

[Microsoft Edge Developer Tools on Twitter: Find helpful F12 hints and news updates](https://twitter.com/EdgeDevTools)

[A look at new feedback-driven improvements to the network tool in our F12 Developer Tools](https://blogs.windows.com/msedgedev/2015/05/08/updates-for-the-f12-developer-tools-in-windows-insider-preview-10074/)