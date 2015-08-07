# Window Commands
Microsoft Edge supports the following window-related WebDriver commands:
[Close Window](#close-window), [Switch To Window](#switch-to-window),
[Get Window Handle](#get-window-handle), [Get Window Handles](#get-window-handles).

## /session/{sessionId}/window

### Close Window

| **Name** | Close Window |
| :------- | :---------- |
| **Description** | Closes the current window. |
| **Spec** | [W3C WebDriver](https://w3c.github.io/webdriver/webdriver-spec.html#dfn-close-window), [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#DELETE_/session/:sessionId/window) |
| **HTTP Request** | `DELETE /session/{sessionId}/window` |

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

### Switch To Window

| **Name** | Switch To Window |
| :------- | :---------- |
| **Description** | Changes focus to another window. |
| **Spec** | [W3C WebDriver](https://w3c.github.io/webdriver/webdriver-spec.html#switch-to-window), [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#POST_/session/:sessionId/window) |
| **HTTP Request** | `POST /session/{sessionId}/window` |

**JSON Parameters**
None.

**JSON Response Value**
```
{
    "name": "{windowHandle}"
}
```

## /session/{sessionId}/window_handle

### Get Window Handle

| **Name** | Click |
| :------- | :---------- |
| **Description** | Retrieves the current window handle. |
| **Spec** | [W3C WebDriver](https://w3c.github.io/webdriver/webdriver-spec.html#get-window-handle), [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#GET_/session/:sessionId/window_handle) |
| **HTTP Request** | `GET /session/{sessionId}/window_handle` |

**JSON Parameters**
None.

**JSON Response Value**
```
{
    "sessionId": "{sessionId}",
    "status": 0,
    "value": "{windowHandle}"
}
```

## /session/{sessionId}/window_handles

### Get Window Handles

| **Name** | Get Window Handles |
| :------- | :---------- |
| **Description** | Retrieves the list of all window handles available to the session. |
| **Spec** | [W3C WebDriver](https://w3c.github.io/webdriver/webdriver-spec.html#get-window-handles), [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#GET_/session/:sessionId/window_handles) |
| **HTTP Request** | `POST /session/{sessionId}/element/{elementId}/value` |

**JSON Parameters**
None.

**JSON Response Value**
```
{
    "sessionId": "{sessionId}",
    "status": 0,
    "value": [
        "{windowHandleOne}",
        "{windowHandleTwo}"
    ]

}
```
