# onFontObserver

## Modules to Import

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## onFontObserver

```TypeScript
function onFontObserver(observer: FontClientObserver): void
```

Registers a listener for monitoring the font service status.

> **NOTE:** 
> - Each application can register only one font service status change listener. Repeated registration will result in an error.
> - A maximum of five applications per user can be registered simultaneously; otherwise, an error will occur.

**Since:** 26.0.1

**Required permissions:** ohos.permission.UPDATE_SCOPE_FONT

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Global.FontManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| observer | [FontClientObserver](arkts-localization-fontmanager-fontclientobserver-i.md) | Yes | Listener for the font service status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [31100110](../errorcode-font-manager.md#31100110-failed-to-call-the-api-due-to-system-errors) | Call failed due to system error. |
| 31100113 | The font observer is already registered. |
| 31100114 | The maximum number of font observers has been reached. |
