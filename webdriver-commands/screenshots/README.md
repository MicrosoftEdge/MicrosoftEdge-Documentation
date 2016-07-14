# Screenshot Commands
Microsoft Edge supports the following WebDriver commands for taking screenshots:

| HTTP Request | Commands |
| ------------ | -------- |
| /session/{sessionId}/element/{id}/screenshot| [Take Element Screenshot](#take-element-screenshot)|
| /session/{sessionId}/screenshot| [Take Screenshot](#take-screenshot)|

## Take Element Screenshot
| **Name** | Take Element Screenshot |
| :------- | :------- |
| **Description** | Takes a screenshot of the currently selected element. |
| **Spec** | [W3C WebDriver](https://w3c.github.io/webdriver/webdriver-spec.html#take-element-screenshot) |
| **HTTP Request** | `GET /session/{sessionId}/element/{elementId}/screenshot` |

**JSON Parameters**
None

**JSON Response Value**
```
{
    "sessionId": "{sessionId}",
    "status": 0,
    "value": "{image}"
}
```

## Take Screenshot

| **Name** | Take Screenshot |
| :------- | :---------- |
| **Description** | Takes a screenshot of the current viewport. |
| **Spec** | [W3C WebDriver](https://w3c.github.io/webdriver/webdriver-spec.html#take-screenshot), [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#/session/:sessionId/screenshot) |
| **HTTP Request** | `GET /session/{sessionId}/screenshot` |

**JSON Parameters**
None.

**JSON Response Value**
```
{
    "sessionId": "{sessionId}",
    "status": 0,
    "value": "{base64EncodedString}"
}
```
