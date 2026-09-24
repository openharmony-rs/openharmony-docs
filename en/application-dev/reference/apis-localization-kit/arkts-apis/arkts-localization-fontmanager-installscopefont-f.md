# installScopeFont

## Modules to Import

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## installScopeFont

```TypeScript
function installScopeFont(url: string, scope: FontScope): Promise<void>
```

Install the font file in the specified path as an application-level or session-level font. This API uses a promise to return the result.

> **NOTE:** 
> - When installing an application-level font, you need to call the [onFontObserver](arkts-localization-fontmanager-onfontobserver-f.md) API to register a listener for font service status changes.
> - After the font is installed, the application can use the font by name. The same font path cannot be installed repeatedly.
> - The maximum number of font files that can be installed on the PC/2in1 is 800, while other devices support a maximum of 200 font files.

**Since:** 26.0.1

**Required permissions:** ohos.permission.UPDATE_SCOPE_FONT

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Global.FontManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | Path to the font file to be installed. Only .ttf,ttc or .otf font files are supported. |
| scope | [FontScope](arkts-localization-fontmanager-fontscope-e.md) | Yes | Font scope. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [31100101](../errorcode-font-manager.md#31100101-font-file-not-exist) | The font does not exist. |
| [31100102](../errorcode-font-manager.md#31100102-failed-to-install-font-file) | The font is not supported. |
| [31100103](../errorcode-font-manager.md#31100103-failed-to-copy-font-file) | Failed to copy the font file. |
| [31100104](../errorcode-font-manager.md#31100104-font-file-already-installed) | The font file is installed. |
| [31100105](../errorcode-font-manager.md#31100105-number-of-installed-font-files-reaching-the-maximum) | Exceeded the maximum number of installed files. |
| [31100110](../errorcode-font-manager.md#31100110-failed-to-call-the-api-due-to-system-errors) | Call failed due to system error. |
| 31100115 | The font observer is not registered. |
