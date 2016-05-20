# Meta referrer

Microsoft Edge offers a meta [referrer](https://msdn.microsoft.com/library/ms534365(v=vs.85).aspx), `<meta name="referrer">`, to specify what information about a webpage should be passed in the HTTP header to any request sent from the page.  Traffic remains encrypted and all the benefits of HTTPS remain, but the passing of referral data can be controlled between HTTPS and HTTP sites.

```HTML
<head>
	<meta name="referrer" content="origin">
</head>
```

Developers can specify meta referrer behavior using one of the following content values:

Value | Description
:------------ | :-------------
default | Full URI if HTTP, blank if HTTPS.
never | Pass nothing.
origin | Pass the origin only.
always | Pass the full URI always.

## Meta Referrer Demo

Test the meta referrer tags by changing the values in the "Stuff for `<head>`" section of the "Settings" in this Codepen.

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/ONLMBa)

## API Reference
[Referrer property](https://msdn.microsoft.com/library/ms534365(v=vs.85).aspx)

## Specification
[Referrer Policy](https://w3c.github.io/webappsec-referrer-policy/)
