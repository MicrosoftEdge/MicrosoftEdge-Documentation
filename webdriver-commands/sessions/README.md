# Session Commands
Microsoft Edge supports the following session-related WebDriver commands: [New Session](#new-session), [Sessions](#sessions),
[Get Capabilities](#get-capabilities), [Delete](#delete), [Set Timeout](#set-timeout).

## /session

### New Session

| **Name** | New Session |
| :------- | :---------- |
| **Description** | Creates a new session. |
| **Spec** | [W3C WebDriver](https://w3c.github.io/webdriver/webdriver-spec.html#new-session) |
| **HTTP Request** | `POST /session` |

**JSON Parameters**
```
{
    "desiredCapabilities": {
        "browserName": "&lt;browserName&gt;",
        "browserVersion": "&lt;browserVersion&gt;",
        "platformName": "Windows NT",
        "platformVersion": "10"
    },
    "requiredCapabilities": {}
}
```

**JSON Response Value**
```
{
    "sessionId": "{sessionId}",
    "status": 0,
    "value": {
        "browserName": "MicrosoftEdge",
        "browserVersion": "20.10192.0.0",
        "platformName": "windows",
        "platformVersion": "10",
        "takesElementScreenshot": true,
        "takesScreenshot": true,
        "acceptSslCerts": true,
        "pageLoadStrategy": "normal"
    }
}
```

## /sessions

### Sessions
| **Name** | Sessions |
| :------- | :------- |
| **Description** | Returns a list of the currently active sessions. |
| **Spec** | [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#/sessions) |
| **HTTP Request** | `GET /sessions` |

**JSON Parameters**
None.

**JSON Response Value**
```
{
    "status": "success",
    "value": [
        {
            "id": "{sessionId}",
            "capabilities": {
                "browserName": "MicrosoftEdge",
                "browserVersion": "20.10192.0.0",
                "platformName": "windows",
                "platformVersion": "10",
                "takesElementScreenshot": true,
                "takesScreenshot": true,
                "acceptSslCerts": true,
                "pageLoadStrategy": "normal"
            }
        }
    ]
}
```

## /session/{sessionId}

### Get Capabilities
| **Name** | Get Capabilities |
| :------- | :------- |
| **Description** | Retrieves the capabilities of the specified session. |
| **Spec** | [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#/session/:sessionId) |
| **HTTP Request** | `GET /session/{sessionId}` |

**JSON Parameters**
None.

**JSON Response Value**
```
{
    "sessionId": "{sessionId}",
    "status": 0,
    "value": {
        "browserName": "MicrosoftEdge",
        "browserVersion": "20.10192.0.0",
        "platformName": "windows",
        "platformVersion": "10",
        "takesElementScreenshot": true,
        "takesScreenshot": true,
        "acceptSslCerts": true,
        "pageLoadStrategy": "normal"
    }

}
```

### Delete Session
| **Name** | Delete Session |
| :------- | :------- |
| **Description** | Deletes the specified session. |
| **Spec** | [W3C WebDriver](https://w3c.github.io/webdriver/webdriver-spec.html#dfn-delete-session), [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#/session/:sessionId) |
| **HTTP Request** | `DELETE /session/{sessionId}` |

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

## /session/{sessionId}/timeouts

### Set Timeout
| **Name** | Set Timeout |
| :------- | :------- |
| **Description** | Configures the amount of time a particular type of operation can execute before it's aborted. |
| **Spec** | [JSON Wire Protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol#/session/:sessionId) |
| **HTTP Request** | `POST /session/{sessionId}/timeouts` |

**JSON Parameters**
```
{
    "type": "{type}",
    "ms": {time}
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
