# @ohos.brightness (Screen Brightness) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=25476a1a1eb8d4a9c259b5ea7ce60c9e5a03a4be translatedAt=2026-11-10T04:01:12.673Z pushedAt=2026-11-10T06:13:51.006Z nl=1 -->

This module provides the APIs for setting the screen brightness.

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

Sets the system screen brightness.

**System API**: This is a system API.

**System capability:** SystemCapability.PowerManager.DisplayPowerManager

**Parameters**

| Name | Type   | Mandatory | Description                    |
| ------ | ------ | ---- | ----------------------- |
| value  | number | Yes   | Brightness value. The value ranges from 0 to 255 and must be of the number type. |

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
} catch(err) {
    console.error('set brightness failed, err: ' + err);
}
```

## brightness.setValue<sup>11+</sup>

setValue(value: number, continuous: boolean): void

Sets the screen brightness of the system. This API is used in the scenario of continuous brightness adjustment. During continuous brightness adjustment, set **continuous** to **true**, and set it to **false** when the adjustment ends for better performance.

**System API**: This is a system API.

**System capability:** SystemCapability.PowerManager.DisplayPowerManager

**Parameters**

| Name | Type   | Mandatory | Description                    |
| ------ | ------ | ---- | ----------------------- |
| value  | number | Yes   | Brightness value. The value ranges from 0 to 255. |
| continuous  | boolean | Yes   | Whether the brightness adjustment is continuous. The value **true** indicates continuous brightness adjustment, and **false** indicates non-continuous brightness adjustment. The default value is **false**. |

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
} catch(err) {
    console.error('set brightness failed, err: ' + err);
}
```