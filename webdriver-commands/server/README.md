# Server Commands
Microsoft Edge supports the following server-related WebDriver commands.

## /shutdown

| Command Name | (Shutdown) |
| :------------|----------- |
| **Description** | Shuts down the server. |
| **HTTP Request** | GET /shutdown |
| **JSON Parameters** | None |
| **JSON Response Value** | None |
| **Spec** | N/A |
| **Spec Link** | N/A |

## /Status

| Command Name | Status |
| :------------|----------- |
| **Description** | Queries the current status of the server. |
| **HTTP Request** | GET /status |
| **JSON Parameters** | None |
| **JSON Response Value** |
```
{
    "sessionId": "{sessionId}",
    "status": 0,
    "value": {
        "build": {
            "version": "beta"
        },
        "os": {
            "arch": "x86",
            "name": "Windows 10",
            "version": "10.0"
        }
    }
}
```
| **Spec** | JSON Wire Protocol |
| **Spec Link** | https://code.google.com/p/selenium/wiki/JsonWireProtocol#/status |
