# Element Inspection Commands
Microsoft Edge supports the following WebDriver commands for inspecting elements: [Find Element](#find-element),
[Find Elements](#find-elements).

## /session/{sessionId}/element

### Find Element

| **Name** | Find Element |
| :------- | :---------- |
| **Description** | Searches for a given element on the page, starting from the document root. |
| **Spec** | [W3C WebDriver](https://w3c.github.io/webdriver/webdriver-spec.html#findelement), [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#/session/:sessionId/element) |
| **HTTP Request** | `POST /session/{sessionId}/element` |

**JSON Parameters**
```
{
    "using": "id",
    "value": "clickAnchorElement"
}
```

**JSON Response Value**
```
{
    "sessionId": "{sessionId}",
    "status": 0,
    "value": {
        "ELEMENT": "{elementId}",
        "element-6066-11e4-a52e-4f735466cecf": "{elementId}"
    }
}
```

### Find Elements

| **Name** | Find Element |
| :------- | :---------- |
| **Description** | Searches for all elements on the page with a given attribute value, starting from the document root. |
| **Spec** | [W3C WebDriver](https://w3c.github.io/webdriver/webdriver-spec.html#findelements), [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#/session/:sessionId/elements) |
| **HTTP Request** | `POST /session/{sessionId}/elements` |

**JSON Parameters**
```
{
    "using": "id",
    "value": "clickAnchorElement"
}
```

**JSON Response Value**
```
{
    "sessionId": "{sessionId}",
    "status": 0,
    "value": {
        "ELEMENT": "{elementId}",
        "element-6066-11e4-a52e-4f735466cecf": "{elementId}"
    }
}
```
