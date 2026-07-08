# @ohos.uiAppearance (UI Appearance) (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fangzhiyuan1-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->

This module provides basic capabilities for managing system appearance configurations, including color mode (dark/light) settings, font size scale factors, and font weight scale factors.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.uiAppearance (UI Appearance)](js-apis-uiappearance.md).


## Modules to Import

```ts
import { uiAppearance } from '@kit.ArkUI';
```


## uiAppearance.setDarkMode

setDarkMode(mode: DarkMode, callback: AsyncCallback\<void>): void

Sets the system color mode. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.UPDATE_CONFIGURATION

**System capability**: SystemCapability.ArkUI.UiAppearance

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -- | -- | -- | -- |
| mode | [DarkMode](js-apis-uiappearance.md#darkmode) | Yes| Color mode to set.|
| callback | AsyncCallback\<void>| Yes| Callback used to return the system color mode result. If the operation is successful, **error** is **undefined**. If the operation fails, **error** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [UI Appearance Error Codes](errorcode-uiappearance.md).

| ID| Error Message|
| -- | -- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| 500001 | Internal error. |

**Example**

```ts
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  uiAppearance.setDarkMode(uiAppearance.DarkMode.ALWAYS_DARK, (error) => {
    if (error) {
      console.error(`Set dark-mode failed. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Set dark-mode successfully.');
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`Set dark-mode failed. Code: ${err.code}, message: ${err.message}`);
}
```


## uiAppearance.setDarkMode

setDarkMode(mode: DarkMode): Promise\<void>;

Sets the system color mode. This API uses a promise to return the result.

**Permission required**: ohos.permission.UPDATE_CONFIGURATION

**System capability**: SystemCapability.ArkUI.UiAppearance

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -- | -- | -- | -- |
| mode | [DarkMode](js-apis-uiappearance.md#darkmode) | Yes| Color mode to set.|

**Return value**

| Type  | Description                          |
| ------ | ------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [UI Appearance Error Codes](errorcode-uiappearance.md).

| ID| Error Message|
| -- | -- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| 500001 | Internal error. |

**Example**

```ts
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  uiAppearance.setDarkMode(uiAppearance.DarkMode.ALWAYS_DARK).then(() => {
    console.info('Set dark-mode successfully.');
  }).catch((error: BusinessError) => {
    console.error(`Set dark-mode failed. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`Set dark-mode failed. Code: ${err.code}, message: ${err.message}`);
}
```


## uiAppearance.setFontScale<sup>12+</sup>

setFontScale(fontScale: number): Promise\<void>

Sets a font size scale factor.

**Permission required**: ohos.permission.UPDATE_CONFIGURATION

**System capability**: SystemCapability.ArkUI.UiAppearance

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -- | -- | -- | -- |
| fontScale | number | Yes| Font size scale factor.<br> Value range: (0, 5.0]. If the value is outside this range, error code 401 is thrown.|

**Return value**

| Type| Description|
| -- | -- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [UI Appearance Error Codes](errorcode-uiappearance.md).

> **NOTE**
>
> If the ohos.permission.UPDATE_CONFIGURATION permission is not requested, the application installation will fail, and error code 202 will not be returned.

| ID| Error Message|
| -- | -- |
| 201 | Permission denied. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| 500001 | Internal error. |

**Example**

```ts
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let fontScale = 1.5;

try {
  uiAppearance.setFontScale(fontScale).then(() => {
    console.info('Set fontScale successfully.');
  }).catch((error: BusinessError) => {
    console.error(`Set fontScale failed. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`Set fontScale failed. Code: ${err.code}, message: ${err.message}`);
}
```


## uiAppearance.setFontWeightScale<sup>12+</sup>

setFontWeightScale(fontWeightScale: number): Promise\<void>

Sets a font weight scale factor.

**Permission required**: ohos.permission.UPDATE_CONFIGURATION

**System capability**: SystemCapability.ArkUI.UiAppearance

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -- | -- | -- | -- |
| fontWeightScale | number | Yes| Font weight scale factor.<br> Value range: (0, 5.0]. If the value is outside this range, error code 401 is thrown.|

**Return value**

| Type| Description|
| -- | -- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [UI Appearance Error Codes](errorcode-uiappearance.md).

> **NOTE**
>
> If the ohos.permission.UPDATE_CONFIGURATION permission is not requested, the application installation will fail, and error code 202 will not be returned.

| ID| Error Message|
| -- | -- |
| 201 | Permission denied. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed.  |
| 500001 | Internal error. |

**Example**

```ts
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let fontWeightScale = 1;

try {
  uiAppearance.setFontWeightScale(fontWeightScale).then(() => {
    console.info('Set fontWeightScale successfully.');
  }).catch((error: BusinessError) => {
    console.error(`Set fontWeightScale failed. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`Set fontWeightScale failed. Code: ${err.code}, message: ${err.message}`);
}
```
