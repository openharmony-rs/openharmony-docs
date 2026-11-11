# @ohos.brightness (Screen Brightness) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=11b7adb16f37a0d932789e8c4a100f25548cb4ae translatedAt=2026-11-06T01:39:21.243Z pushedAt=2026-11-09T02:08:51.756Z nl=1 -->

This module provides APIs for setting the screen brightness, including setting a specified brightness value and continuously adjusting the brightness. It applies to scenarios where the screen brightness needs to be dynamically controlled in an application, enabling fine-grained management of the screen brightness.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs provided by this module are system APIs.

## Modules to Import

```js
import { brightness } from '@kit.BasicServicesKit';
```

## brightness.setValue

setValue(value: number): void

Sets the screen brightness of the system. This API is applicable to scenarios that require a fixed screen brightness, such as reading applications, video playback applications, and night mode. To continuously adjust the brightness, use setValue(value: number, continuous: boolean).

**System API:** This is a system API.

**System capability:** SystemCapability.PowerManager.DisplayPowerManager

**Parameters**

| Name  | Type   | Mandatory | Description                    |
| ------ | ------ | ---- | ----------------------- |
| value  | number | Yes   | Brightness value. Value range: (0, 255]. If the value exceeds the range, it is set to the minimum or maximum brightness defined by the system. |

**Error codes**

For details about the error codes, see [Brightness Error Codes](errorcode-brightness.md) and [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message    |
|---------|---------|
| 4700101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**Example**

```js
try {
    brightness.setValue(128);
} catch (err) {
    console.error(`Failed to set brightness. Code: ${err.code}, message: ${err.message}`);
}
```

## brightness.setValue<sup>11+</sup>

setValue(value: number, continuous: boolean): void

Sets the screen brightness of the system. This API is used in the scenario of continuously adjusting the brightness. During continuous brightness adjustment, set **continuous** to **true** to reduce unnecessary system brightness refreshes, and set it to **false** at the end to restore the normal refresh mode, thereby improving the smoothness of continuous adjustment.

**System API:** This is a system API.

**System capability:** SystemCapability.PowerManager.DisplayPowerManager

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ----------------------- |
| value  | number | Yes  | Brightness value. Value range: (0, 255]. If the value exceeds the range, it is set to the minimum or maximum brightness defined by the system. |
| continuous  | boolean | Yes  | Whether the brightness adjustment is continuous. The value **true** indicates continuous brightness adjustment, and **false** indicates non-continuous brightness adjustment. |

**Error codes**

For details about the error codes, see [Brightness Error Codes](errorcode-brightness.md) and [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message    |
|---------|---------|
| 4700101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**Example**

```js
try {
    brightness.setValue(128, true);
} catch (err) {
    console.error(`Failed to set brightness. Code: ${err.code}, message: ${err.message}`);
}
```

## brightness.setValue

setValue(value: number, continuous: boolean, displayId: number): void

Sets the brightness of a specified screen. This API is used in the scenario of continuously adjusting the brightness. During continuous brightness adjustment, set **continuous** to **true** to reduce unnecessary system brightness refreshes, and set it to **false** at the end to restore the normal refresh mode, thereby improving the smoothness of continuous adjustment.

**Since:** 26.0.1

**Model restriction**: This API can be used only in the stage model.

**System API:** This is a system API.

**System capability:** SystemCapability.PowerManager.DisplayPowerManager

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ----------------------- |
| value  | number | Yes  | Brightness value. The value range is [0, 255]. If the value is out of range, the system-defined minimum or maximum brightness is used. |
| continuous  | boolean | Yes  | Whether the brightness adjustment is continuous. The value **true** indicates continuous brightness adjustment, and **false** indicates non-continuous brightness adjustment. |
| displayId  | number | Yes  | Screen ID. The Value range is [0, 10000]. |

**Error codes**

For details about the error codes, see [Brightness Error Codes](errorcode-brightness.md) and [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message    |
|---------|---------|
| 202     | Permission verification failed. A non-system application calls a system API.  |
| 4700101 | Failed to connect to the service. |

**Example**

```js
try {
    brightness.setValue(128, true, 0);
} catch (err) {
    console.error(`Failed to set brightness. Code: ${err.code}, message: ${err.message}`);
}
```
