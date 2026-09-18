# installFont (System API)

## Modules to Import

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## installFont

```TypeScript
function installFont(path: string): Promise<number>
```

Installs a font file from a specified path into the system font library. This API uses a promise to return the result. After successful installation, applications can use the font by its font name.

**Since:** 19

**Required permissions:** ohos.permission.UPDATE_FONT

**System capability:** SystemCapability.Global.FontManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path to the font file to be installed. Only .ttf and .ttc font files are supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the installation result.<br>- The value **0** indicates that the installation is successful and the font has been added to the system font library. <br>- Any other value indicates that the installation failed. Troubleshoot based on the error code. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [31100101](../errorcode-font-manager.md#31100101-font-file-not-exist) | The font does not exist. |
| [31100102](../errorcode-font-manager.md#31100102-failed-to-install-font-file) | The font is not supported. |
| [31100103](../errorcode-font-manager.md#31100103-failed-to-copy-font-file) | Failed to copy the font file. |
| [31100104](../errorcode-font-manager.md#31100104-font-file-already-installed) | The font file is installed. |
| [31100105](../errorcode-font-manager.md#31100105-number-of-installed-font-files-reaching-the-maximum) | Exceeded the maximum number of installed files. |
| [31100106](../errorcode-font-manager.md#31100106-font-file-installation-failed-due-to-other-errors) | The system ability works abnormally. |
