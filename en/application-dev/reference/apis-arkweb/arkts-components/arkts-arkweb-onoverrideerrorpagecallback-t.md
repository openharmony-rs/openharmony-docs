# OnOverrideErrorPageCallback

```TypeScript
type OnOverrideErrorPageCallback = (errorPageEvent: OnErrorReceiveEvent) => string
```

Defines a callback of **onOverrideErrorPage**. This callback is triggered when a web page fails to be loaded.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| errorPageEvent | [OnErrorReceiveEvent](arkts-arkweb-onerrorreceiveevent-i.md) | Yes | Information returned when an error occurs during web page loading. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Base64-encoded HTML text content. |
