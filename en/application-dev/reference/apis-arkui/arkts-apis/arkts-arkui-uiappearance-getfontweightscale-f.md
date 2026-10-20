# getFontWeightScale

## Modules to Import

```TypeScript
import { uiAppearance } from '@kit.ArkUI';
```

## getFontWeightScale

```TypeScript
function getFontWeightScale(): number
```

Obtains the current font weight scale factor. This scale is the ratio of the font weight configured by the user in system settings to the default font weight. For the value range, refer to the system font weight settings. You can adjust the font weight within the application based on this scale factor to accommodate the user's font weight preferences.

<!--Del-->

> **NOTE:** 
> 
> This API is a system API in API version 19 and earlier. Using this API requires the
> [ohos.permission.UPDATE_CONFIGURATION](../../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration)
> permission.

<!--DelEnd-->

**Since:** 20

<!--Device-uiAppearance-function getFontWeightScale(): number--><!--Device-uiAppearance-function getFontWeightScale(): number-End-->

**System capability:** SystemCapability.ArkUI.UiAppearance

**Return value:**

| Type | Description |
| --- | --- |
| number | current font-weight-scale. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [500001](../errorcode-uiappearance.md#500001-internal-error) | Internal error. |

**Examples**

```TypeScript
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let fontWeightScale = uiAppearance.getFontWeightScale();
  console.info('Get fontWeightScale ' + fontWeightScale);
} catch (error) {
  let err = error as BusinessError;
  console.error(`Get fontWeightScale failed. Code: ${err.code}, message: ${err.message}`);
}
```
