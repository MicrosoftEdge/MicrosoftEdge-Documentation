# Security features

## Content Security Policy (CSP)

With [Content Security Policy](./content-Security-Policy), you create an allow list of sources of trusted content in the HTTP headers, pre-approving certain servers for content loaded into a webpage and instructing the browser to only execute or render resources from those sources. This can be used to prevent malicious content from being injected into sites.

## HTTP Strict Transport Security (HSTS)

[HSTS policy](./HSTS) protects against variants of man-in-the-middle attacks that can strip TLS out of communications with a server, leaving the user vulnerable. HSTS does this by allowing sites to specify that the browser should always use a secure connection to the server.

## Meta referrer

The [meta name="referrer"](./meta-referrer) tag lets you specify what information about a webpage should be passed in the HTTP header to any request sent from the page.

## Web Cryptography API
[Web Crytography API](./web-Cryptography-API) provides basic cryptographic operations in web applications, such as hashing, signature generation and verification, and encryption and decryption.

## Transport Layer Security (TLS)

TLS, the successor to [SSL](http://blogs.msdn.com/b/kaushal/archive/2011/10/02/support-for-ssl-tls-protocols-on-windows.aspx), is a protocol that provides communications privacy and security between two applications communicating over a network. For more info about the TLS protocol, check out the [Windows Dev Center](https://msdn.microsoft.com/library/windows/desktop/aa380516).
