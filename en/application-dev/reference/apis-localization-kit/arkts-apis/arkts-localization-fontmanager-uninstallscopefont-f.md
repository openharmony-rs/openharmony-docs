# uninstallScopeFont

## Modules to Import

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## uninstallScopeFont

```TypeScript
function uninstallScopeFont(url: string): Promise<void>
```

Uninstalls a scope font file from the system font library by URL. This API uses a promise to return the result.

**Since:** 26.1.0

**Required permissions:** ohos.permission.UPDATE_SCOPE_FONT

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Global.FontManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL of the font to be uninstalled. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [31100108](../errorcode-font-manager.md#31100108-failed-to-delete-font-file) | Failed to delete the font file. |
| [31100110](../errorcode-font-manager.md#31100110-failed-to-call-the-api-due-to-system-errors) | Call failed due to system error. |
| 31100112 | The scope font is not found. |
