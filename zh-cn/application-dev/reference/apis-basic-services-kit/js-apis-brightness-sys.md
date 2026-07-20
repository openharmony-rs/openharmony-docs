# @ohos.brightness (屏幕亮度)(系统接口)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->

该模块提供屏幕亮度的设置接口，支持设置指定亮度值及连续调节亮度，适用于需要在应用中动态控制屏幕亮度的场景，可实现屏幕亮度的精细化管理。

> **说明：**
>
> - 本模块首批接口从 API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口为系统接口。

## 导入模块

```js
import { brightness } from '@kit.BasicServicesKit';
```

## brightness.setValue

setValue(value: number): void

设置系统的屏幕亮度。适用于需要固定屏幕亮度的场景，例如阅读应用、视频播放应用、夜间模式等。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager

**参数：**

| 参数名 | 类型   | 必填 | 说明                    |
| ------ | ------ | ---- | ----------------------- |
| value  | number | 是   | 亮度的值。取值范围：(0, 255]。超出时会设置为系统定义的亮度最小或最大值。 |

**错误码：**

以下错误码的详细介绍请参见[屏幕亮度错误码](errorcode-brightness.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4700101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**示例：**

```js
try {
    brightness.setValue(128);
} catch (err) {
    console.error(`Failed to set brightness. Code: ${err.code}, message: ${err.message}`);
}
```

## brightness.setValue<sup>11+</sup>

setValue(value: number, continuous: boolean): void

设置系统的屏幕亮度。用于连续调节亮度的场景，在连续调节亮度过程中，设置continuous为true可减少不必要的系统亮度刷新，结束时设置continuous为false恢复正常刷新模式，从而提升连续调节时的流畅度。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager

**参数：**

| 参数名 | 类型   | 必填 | 说明                    |
| ------ | ------ | ---- | ----------------------- |
| value  | number | 是   | 亮度的值。取值范围：(0, 255]。超出时会设置为系统定义的亮度最小或最大值。 |
| continuous  | boolean | 是   | 亮度调节是否连续。true表示亮度调节连续，false表示亮度调节不连续，默认为false。 |

**错误码：**

以下错误码的详细介绍请参见[屏幕亮度错误码](errorcode-brightness.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 4700101 | Failed to connect to the service. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 202     | Permission verification failed. A non-system application calls a system API.  |

**示例：**

```js
try {
    brightness.setValue(128, true);
} catch (err) {
    console.error(`Failed to set brightness. Code: ${err.code}, message: ${err.message}`);
}
```