# Navigation Commands
Microsoft Edge supports the following WebDriver commands for navigation: [Get](#get),
[Get Current URL](#get-current-url), [Back](#back), [Forward](#forward), [Refresh](#refresh),
[Title](#title).

## /session/{sessionId}/url

### Get

| **Name** | Get |
| :------- | :---------- |
| **Description** | Navigates to the specified URL. |
| **Spec** | [W3C WebDriver](https://w3c.github.io/webdriver/webdriver-spec.html#get), [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#/session/:sessionId/url) |
| **HTTP Request** | `POST /session/{sessionId}/url` |

**JSON Parameters**
```
{
    "url": "https://www.bing.com/"

}
```

**JSON Response Value**
```
{
    "sessionId": "{sessionId}",
    "status": 0,
    "value": null
}
```

### Get Current URL

| **Name** | Get Current URL |
| :------- | :---------- |
| **Description** | Retrieves the URL of the current page. |
| **Spec** | [W3C WebDriver](https://w3c.github.io/webdriver/webdriver-spec.html#get-current-url), [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#/session/:sessionId/url) |
| **HTTP Request** | `GET /session/{sessionId}/url` |

**JSON Parameters**
None.

**JSON Response Value**
```
{
    "sessionId": "{sessionId}",
    "status": 0,
    "value": "{url}"
}
```

## /session/{sessionId}/back

### Back

| **Name** | Back |
| :------- | :---------- |
| **Description** | Navigates backwards in the browser history, if possible. |
| **Spec** | [W3C WebDriver](https://w3c.github.io/webdriver/webdriver-spec.html#back), [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#POST_/session/:sessionId/back) |
| **HTTP Request** | `POST /session/{sessionId}/back` |

**JSON Parameters**
None.

**JSON Response Value**
```
{
    "sessionId": "{sessionId}",
    "status": 0,
    "value": null
}
```

## /session/{sessionId}/forward

### Forward

| **Name** | Forward |
| :------- | :---------- |
| **Description** | Navigates forward in the browser history, if possible. |
| **Spec** | [W3C WebDriver](https://w3c.github.io/webdriver/webdriver-spec.html#back), [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#POST_/session/:sessionId/back) |
| **HTTP Request** | `POST /session/{sessionId}/forward` |

**JSON Parameters**
None.

**JSON Response Value**
```
{
    "sessionId": "{sessionId}",
    "status": 0,
    "value": null
}
```

## /session/{sessionId}/refresh

### Refresh

| **Name** | Refresh |
| :------- | :---------- |
| **Description** | Reloads the current page. |
| **Spec** | [W3C WebDriver](https://w3c.github.io/webdriver/webdriver-spec.html#refresh), [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#/session/:sessionId/refresh) |
| **HTTP Request** | `POST /session/{sessionId}/refresh` |

**JSON Parameters**
None.

**JSON Response Value**
```
{
    "sessionId": "{sessionId}",
    "status": 0,
    "value": null
}
```

## /session/{sessionId}/title

### Get Title

| **Name** | Get Title |
| :------- | :---------- |
| **Description** | Gets the current page title. |
| **Spec** | [W3C WebDriver](https://w3c.github.io/webdriver/webdriver-spec.html#get-title), [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#/session/:sessionId/title) |
| **HTTP Request** | `GET /session/{sessionId}/title` |

**JSON Parameters**
None.

**JSON Response Value**
```
{
    "sessionId": "{sessionId}",
    "status": 0,
    "value": "{title}"
}
```
