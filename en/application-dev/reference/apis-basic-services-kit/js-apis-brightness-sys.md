# @ohos.brightness (Screen Brightness) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @w_Machine_cc-->

The **brightness** module provides an API for setting the screen brightness.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs provided by this module are system APIs.

## Modules to Import

```js
import {brightness} from '@kit.BasicServicesKit';
```

## brightness.setValue

setValue(value: number): void

Sets the screen brightness.

**System API**: This is a system API.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| value  | number | Yes  | Brightness value. Value range: 0 to 255. The value of this parameter must be a number.|

**Error codes**

For details about the error codes, see [Brightness Error Codes](errorcode-brightness.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4700101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**Example:**

```js
try {
    brightness.setValue(128);
} catch(err) {
    console.error('set brightness failed, err: ' + err);
}
```

## brightness.setValue<sup>11+</sup>

setValue(value: number, continuous: boolean): void

Sets the screen brightness. This API is used for continuous brightness adjustment. To achieve a better performance, set **continuous** to **true** when you start, and set it to **false** after you finish.

**System API**: This is a system API.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| value  | number | Yes  | Brightness value. Value range: [0, 255]|
| continuous  | boolean | Yes  | Whether the brightness adjustment is continuous. The value **true** indicates that the brightness adjustment is continuous; **false** indicates the opposite. Default value: **false**|

**Error codes**

For details about the error codes, see [Brightness Error Codes](errorcode-brightness.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 4700101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**Example:**

```js
try {
    brightness.setValue(128, true);
} catch(err) {
    console.error('set brightness failed, err: ' + err);
}
```

## brightness.setValue

setValue(value: number, continuous: boolean, displayId: number): void

Sets the screen brightness of a specified screen. This API is used for continuous brightness adjustment. To achieve a better performance, set **continuous** to **true** when you start, and set it to **false** after you finish.

**Start version:** 26.0.1

**Model constraint**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.PowerManager.DisplayPowerManager

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| value  | number | Yes  | Brightness value. Value range: [0, 255]|
| continuous  | boolean | Yes  | Whether the brightness adjustment is continuous. The value **true** indicates that the brightness adjustment is continuous; **false** indicates the opposite. Default value: **false**|
| displayId  | number | Yes  | ID of the display. Value range: [0, 10000].|

**Error codes**

For details about the error codes, see [Brightness Error Codes](errorcode-brightness.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 4700101 | Failed to connect to the service. |

**Example:**

```js
try {
    brightness.setValue(128, true, 0);
} catch(err) {
    console.error('set brightness failed, err: ' + err);
}
```
