# Window Commands
Microsoft Edge supports the following window-related WebDriver commands:

| HTTP Request | Commands |
| ------------ | -------- |
| /session/{sessionId}/window| [Close Window](#close-window), [Switch To Window](#switch-to-window)|
| /session/{sessionId}/window_handle| [Get Window Handle](#get-window-handle)|
| /session/{sessionId}/window_handles| [Get Window Handles](#get-window-handles)|

## Close Window

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

## Switch To Window

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

## Get Window Handle

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

## Get Window Handles

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
