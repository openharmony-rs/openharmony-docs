# getFontScale

## Modules to Import

```TypeScript
import { uiAppearance } from '@kit.ArkUI';
```

## getFontScale

```TypeScript
function getFontScale(): number
```

Obtains the current font size scale factor.

<!--Del-->

> **NOTE:** 

> This API is a system API in API version 19 and earlier. Using this API requires the
> [ohos.permission.UPDATE_CONFIGURATION](../../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration)
> permission.

<!--DelEnd-->

**Since:** 20

**Required permissions:** 
- API version 20 and later: N/A
- API versions 12 to 19: ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.ArkUI.UiAppearance

**Return value:**

| Type | Description |
| --- | --- |
| number | current font-scale. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 12 - 19 |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 - 19 |
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
