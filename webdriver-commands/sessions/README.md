# Session Commands
Microsoft Edge supports the following session-related WebDriver commands.

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
}```

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
