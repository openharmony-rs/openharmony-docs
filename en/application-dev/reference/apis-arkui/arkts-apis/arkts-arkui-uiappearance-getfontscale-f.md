# getFontScale

## Modules to Import

```TypeScript
import { uiAppearance } from '@kit.ArkUI';
```

## getFontScale

```TypeScript
function getFontScale(): number
```

Obtains the current font size scale factor. This scale is the ratio of the font size configured by the user in system settings to the default font size. For the value range, refer to the system font size settings. You can adjust the font size within the application based on this scale factor to accommodate the user's font size preferences.

<!--Del-->

> **NOTE:** 
> 
> This API is a system API in API version 19 and earlier. Using this API requires the
> [ohos.permission.UPDATE_CONFIGURATION](../../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration)
> permission.

<!--DelEnd-->

**Since:** 20

<!--Device-uiAppearance-function getFontScale(): number--><!--Device-uiAppearance-function getFontScale(): number-End-->

**System capability:** SystemCapability.ArkUI.UiAppearance

**Return value:**

| Type | Description |
| --- | --- |
| number | current font-scale. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [500001](../errorcode-uiappearance.md#500001-internal-error) | Internal error. |

**Examples**

```TypeScript
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let fontScale = uiAppearance.getFontScale();
  console.info('Get fontScale ' + fontScale);
} catch (error) {
  let err = error as BusinessError;
  console.error(`Get fontScale failed. Code: ${err.code}, message: ${err.message}`);
}
```
