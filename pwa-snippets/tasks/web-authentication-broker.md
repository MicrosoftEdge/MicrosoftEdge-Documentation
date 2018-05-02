# Web authentication broker

You can use the web authentication broker to handle the login flow for your users if you have an online identity provider that uses internet authentication and authorization protocols like OpenID or OAuth. You specify the start and end URIs in a `<meta>` tag on an html page in your app. Windows detects these URIs and passes them to the web authentication broker to complete the login flow. The start URI consists of the address where you send the authentication request to your online provider appended with other required information, such as an app ID, a redirect URI where the user is sent after completing authentication, and the expected response type. You can find out from your provider what parameters are required.

## Snippet

Here is an example use of the `<meta>` tag:

```HTML
<meta name="ms-webauth-uris" content="https://<providerstartpoint>?client_id=<clientid>&response_type=token, https://<appendpoint>"/>
```
## Related topics

[Web authentication broker](https://docs.microsoft.com/en-us/windows/uwp/security/web-authentication-broker)
