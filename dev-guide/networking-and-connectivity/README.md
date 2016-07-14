# Networking and Connectivity 

## Application Cache
The Application Cache API (or [AppCache](./application-cache)) enables you to cache resources locally, including images, script libraries, style sheets, and so on. 

## HTTP/2

[HTTP/2](./HTTP2) introduces header compression and server push, utilizes multiplexing, enables prioritizing while making multiple HTTP requests to a domain, and uses binary protocol (whereas HTTP/1.1 uses text protocol).

## Top-Level Domains

Microsoft Edge updates its parsing of TLDs (top-level domains) and eTLDs (effective top level domains) to support the [publicsuffix.org](http://go.microsoft.com/fwlink/p/?LinkId=524481) list. This provides improved support for the rapidly growing number of domains entering the market and provides both a more standardized and centralized method for handling exceptions.

## WebSocket API
The [WebSocket API](./webSocket) provides a protocol for two-way communication between browser and server. 

## XHR Caching

Microsoft Edge improves performance by caching resources downloaded via [CORS-enabled XMLHttpRequest](https://msdn.microsoft.com/library/hh673569(v=vs.85).aspx) operations in the same manner as it would if they had been downloaded directly. Previously, under many circumstances, caching would be disabled for such items. This new behavior allows more resources to be loaded from the local disk on subsequent requests, reducing network use and improving load times.

