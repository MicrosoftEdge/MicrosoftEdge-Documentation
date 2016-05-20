# Search provider discovery


Rich search integration is built into the Microsoft Edge address bar, including search suggestions, results from the web, your browsing history, and favorites. Microsoft Edge follows the [OpenSearch 1.1](http://go.microsoft.com/fwlink/p/?LinkID=208582) specification to discover and use web search providers. If you are a search provider, here's how to ensure that Microsoft Edge supports your service.



 

1.  Provide an OpenSearch description file, which contains the name of the search provider, and the template to use to construct the search. Here is an example document:
	```html
	<?xml version="1.0" encoding="UTF-8"?> 
    <OpenSearchDescription xmlns="http://a9.com/-/spec/opensearch/1.1/">
        <ShortName>Contoso Search</ShortName>
        <Url type="text/html" template="https://www.contoso.com/?query={searchTerms}"/> 
    </OpenSearchDescription>
	```

2.  Include a reference to your OpenSearch description file in the header section of your pages (typically this would include your site home page and search result pages), for example:
	```html
	<html>
        <head>
            <link rel="search" 
                type="application/opensearchdescription+xml"  
                href="https://contoso.com/content-search.xml" 
                title="Contoso search" /> 
        </head> 
        <body> 
        ...
	```

When a user browses to your search service, your OpenSearch description will be automatically picked up and saved for later use. The user will then be able to go to Microsoft Edge settings and choose to add your search service to his or her list of search providers for the Microsoft Edge address bar.

For user security and privacy, Microsoft Edge requires that all searches be conducted over SSL. Therefore, the following pages and URLs must be https URLs:
* The site that contains the reference to the description document
* The URL to the description document itself
* The search query template

 

 

 


