# onFontObserver

## Modules to Import

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## onFontObserver

```TypeScript
function onFontObserver(observer: FontClientObserver): void
```

Registers a font service death observer. When the font service dies unexpectedly, the [onServiceDied](arkts-localization-fontmanager-fontclientobserver-i.md#onservicedied) callback is invoked.

**Since:** 26.1.0

**Required permissions:** ohos.permission.UPDATE_SCOPE_FONT

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Global.FontManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| observer | [FontClientObserver](arkts-localization-fontmanager-fontclientobserver-i.md) | Yes | Font service death observer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [31100110](../errorcode-font-manager.md#31100110-failed-to-call-the-api-due-to-system-errors) | Call failed due to system error. |
| 31100113 | The font observer is already registered. |
| 31100114 | The maximum number of font observers has been reached. |
