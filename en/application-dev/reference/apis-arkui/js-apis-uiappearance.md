# @ohos.uiAppearance (UI Appearance)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

This module provides basic capabilities for obtaining system appearance configurations, including color mode (dark/light) settings, font size scale factors, and font weight scale factors.

> **NOTE**
>
> The initial APIs of this module are supported since API version 20. Updates will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```ts
import { uiAppearance } from '@kit.ArkUI';
```


## DarkMode

Enumerates the color modes.


**System capability**: SystemCapability.ArkUI.UiAppearance

| Name| Value| Description|
| -- | -- | -- |
| ALWAYS_DARK | 0 | The system is always in dark mode. |
| ALWAYS_LIGHT | 1 | The system is always in light mode.|

## uiAppearance.getDarkMode

getDarkMode(): DarkMode

Obtains the current system dark mode configuration.

<!--Del-->
> **NOTE**
>
> This API is a system API in API version 19 and earlier. Using this API requires the [ohos.permission.UPDATE_CONFIGURATION](../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration) permission.
<!--DelEnd-->

**System capability**: SystemCapability.ArkUI.UiAppearance

**Return value**

| Type| Description|
| -- | -- |
|[DarkMode](#darkmode) | Color mode obtained.|

**Error codes**

For details about the error codes, see [UI Appearance Error Codes](errorcode-uiappearance.md).

| ID| Error Message|
| -- | -- |
| 500001 | Internal error. |

**Example**

```ts
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let darkMode = uiAppearance.getDarkMode();
  console.info('Get dark-mode ' + darkMode);
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('Get dark-mode failed, ' + message);
}
```


## uiAppearance.getFontScale

getFontScale(): number

Obtains the current font size scale factor.

<!--Del-->
> **NOTE**
>
> This API is a system API in API version 19 and earlier. Using this API requires the [ohos.permission.UPDATE_CONFIGURATION](../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration) permission.
<!--DelEnd-->

**System capability**: SystemCapability.ArkUI.UiAppearance

**Return value**

| Type| Description|
| -- | -- |
| number | Current font size scale factor.|

**Error codes**

For details about the error codes, see [UI Appearance Error Codes](errorcode-uiappearance.md).

| ID| Error Message|
| -- | -- |
| 500001 | Internal error. |

**Example**

```ts
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let fontScale = uiAppearance.getFontScale();
  console.info('Get fontScale ' + fontScale);
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('Get fontScale failed, ' + message);
}
```


## uiAppearance.getFontWeightScale

getFontWeightScale(): number

Obtains the current font weight scale factor.

<!--Del-->
> **NOTE**
>
> This API is a system API in API version 19 and earlier. Using this API requires the [ohos.permission.UPDATE_CONFIGURATION](../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration) permission.
<!--DelEnd-->

**System capability**: SystemCapability.ArkUI.UiAppearance

**Return value**

| Type| Description|
| -- | -- |
| number | Current font weight scale factor.|

**Error codes**

For details about the error codes, see [UI Appearance Error Codes](errorcode-uiappearance.md).

| ID| Error Message|
| -- | -- |
| 500001 | Internal error. |

**Example**

```ts
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let fontWeightScale = uiAppearance.getFontWeightScale();
  console.info('Get fontScale ' + fontWeightScale);
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('Get fontWeightScale failed, ' + message);
}
```