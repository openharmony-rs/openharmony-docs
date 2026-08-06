# @ohos.uiAppearance (UI Appearance)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fangzhiyuan1-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=77dbe37290f6691d2779cf62e1218d62529d67d2 translatedAt=2026-07-29T09:28:58.176Z pushedAt=2026-08-04T04:08:53.384Z -->

This module provides basic capabilities for obtaining system appearance configurations, including color mode (dark/light) settings, font size scale factors, and font weight scale factors. It is applicable to scenarios where the application UI style needs to be dynamically adjusted based on the system appearance configuration (such as dark/light mode switching), as well as adapting to the system font size and font weight scale settings. This helps applications maintain consistency with the system appearance and improves user experience.

> **NOTE**
>
> The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { uiAppearance } from '@kit.ArkUI';
```

## DarkMode

Enumerates the color modes, used to configure the dark or light mode of the system.

**System capability**: SystemCapability.ArkUI.UiAppearance

| Name| Value| Description|
| -- | -- | -- |
| ALWAYS_DARK | 0 | The system is always in dark mode.|
| ALWAYS_LIGHT | 1 | The system is always in light mode.|

## uiAppearance.getDarkMode

getDarkMode(): DarkMode

Obtains the current system color mode configuration. This API is applicable to scenarios where the application UI theme needs to be dynamically adapted based on the system appearance mode, such as implementing automatic switching between dark and light theme styles within the application.

<!--Del-->

> **NOTE**
>
> This API is a system API in API version 19 and earlier. Using this API requires the [ohos.permission.UPDATE_CONFIGURATION](../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration) permission.

<!--DelEnd-->

**System capability**: SystemCapability.ArkUI.UiAppearance

**Return value**

| Type| Description|
| -- | -- |
|[DarkMode](#darkmode) | Current system color mode. |

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
  let err = error as BusinessError;
  console.error(`Get dark-mode failed. Code: ${err.code}, message: ${err.message}`);
}
```

## uiAppearance.getFontScale

getFontScale(): number

Obtains the current font size scale factor. This scale is the ratio of the font size configured by the user in system settings to the default font size. For the value range, refer to the system font size settings. You can adjust the font size within the application based on this scale factor to accommodate the user's font size preferences.

<!--Del-->

> **NOTE**
>
> This API is a system API in API version 19 and earlier. Using this API requires the [ohos.permission.UPDATE_CONFIGURATION](../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration) permission.

<!--DelEnd-->

**System capability**: SystemCapability.ArkUI.UiAppearance

**Return value**

| Type| Description|
| -- | -- |
| number | Current font size scale factor. The value **1.0** indicates the default font size, a value greater than **1.0** enlarges the font size, and a value less than **1.0** shrinks the font size. |

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
  let err = error as BusinessError;
  console.error(`Get fontScale failed. Code: ${err.code}, message: ${err.message}`);
}
```

## uiAppearance.getFontWeightScale

getFontWeightScale(): number

Obtains the current font weight scale factor. This scale is the ratio of the font weight configured by the user in system settings to the default font weight. For the value range, refer to the system font weight settings. You can adjust the font weight within the application based on this scale factor to accommodate the user's font weight preferences.

<!--Del-->

> **NOTE**
>
> This API is a system API in API version 19 and earlier. Using this API requires the [ohos.permission.UPDATE_CONFIGURATION](../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration) permission.

<!--DelEnd-->

**System capability**: SystemCapability.ArkUI.UiAppearance

**Return value**

| Type| Description|
| -- | -- |
| number | Current font weight scale factor. The value **1.0** indicates the default font weight, a value greater than **1.0** makes the font bolder, and a value less than **1.0** makes the font  thinner. |

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
  console.info('Get fontWeightScale ' + fontWeightScale);
} catch (error) {
  let err = error as BusinessError;
  console.error(`Get fontWeightScale failed. Code: ${err.code}, message: ${err.message}`);
}
```