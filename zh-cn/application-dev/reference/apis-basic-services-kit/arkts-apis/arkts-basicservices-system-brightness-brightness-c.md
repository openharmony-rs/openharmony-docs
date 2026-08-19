# Brightness

提供屏幕亮度、模式的查询、调节接口，以及屏幕常亮的设置接口。

**起始版本：** 3

**废弃版本：** 7

<!--Device-unnamed-export default class Brightness--><!--Device-unnamed-export default class Brightness-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## 导入模块

```TypeScript
import { Brightness, BrightnessModeResponse, BrightnessResponse, GetBrightnessModeOptions, GetBrightnessOptions, SetBrightnessModeOptions, SetBrightnessOptions, SetKeepScreenOnOptions } from '@kit.BasicServicesKit';
```

## getMode

```TypeScript
static getMode(options?: GetBrightnessModeOptions): void
```

获取设备当前的屏幕亮度模式。

**起始版本：** 3

**废弃版本：** 7

<!--Device-Brightness-static getMode(options?: GetBrightnessModeOptions): void--><!--Device-Brightness-static getMode(options?: GetBrightnessModeOptions): void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GetBrightnessModeOptions](arkts-basicservices-system-brightness-getbrightnessmodeoptions-i.md) | 否 | 获取屏幕亮度模式的参数对象。可选，默认为空。不传入此参数时，将无法通过回调接收模式查询结果。 |

## getValue

```TypeScript
static getValue(options?: GetBrightnessOptions): void
```

获取设备当前的屏幕亮度值。

**起始版本：** 3

**废弃版本：** 7

<!--Device-Brightness-static getValue(options?: GetBrightnessOptions): void--><!--Device-Brightness-static getValue(options?: GetBrightnessOptions): void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GetBrightnessOptions](arkts-basicservices-system-brightness-getbrightnessoptions-i.md) | 否 | 获取屏幕亮度的参数对象。可选，默认为空。不传入此参数时，将无法通过回调接收亮度查询结果。 |

## setKeepScreenOn

```TypeScript
static setKeepScreenOn(options?: SetKeepScreenOnOptions): void
```

设置屏幕是否保持常亮状态，开启常亮模式推荐在onShow()阶段调用。 注意： - 除Lite Wearable外，从API version 7开始不再维护，建议使用[window.setWindowKeepScreenOn()](../../../reference/apis-arkui/arkts-apis-window-Window.md#setwindowkeepscreenon)替代。 - 在Lite Wearable上，该接口仅能阻止系统无活动超时灭屏（自动），无法阻止用户主动操作（如盖屏）、常亮时刻结束等导致的灭屏。

**起始版本：** 3

**废弃版本：** 7

**替代接口：** setWindowKeepScreenOn

<!--Device-Brightness-static setKeepScreenOn(options?: SetKeepScreenOnOptions): void--><!--Device-Brightness-static setKeepScreenOn(options?: SetKeepScreenOnOptions): void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SetKeepScreenOnOptions](arkts-basicservices-system-brightness-setkeepscreenonoptions-i.md) | 否 | 设置屏幕常亮的参数对象。可选，默认为空。不传入此参数时，无法设置屏幕常亮状态，接口调用无实际效果。 |

## setMode

```TypeScript
static setMode(options?: SetBrightnessModeOptions): void
```

设置设备当前的屏幕亮度模式。支持手动调节（mode=0）和自动调节（mode=1）两种模式。详见SetBrightnessModeOptions中mode参数说明。

**起始版本：** 3

**废弃版本：** 7

<!--Device-Brightness-static setMode(options?: SetBrightnessModeOptions): void--><!--Device-Brightness-static setMode(options?: SetBrightnessModeOptions): void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SetBrightnessModeOptions](arkts-basicservices-system-brightness-setbrightnessmodeoptions-i.md) | 否 | 设置屏幕亮度模式的参数对象。可选，默认为空。不传入此参数时，无法设置亮度模式，接口调用无实际效果。 |

## setValue

```TypeScript
static setValue(options?: SetBrightnessOptions): void
```

设置设备当前的屏幕亮度值。设置的亮度值会被系统校正：超出1-255范围的值自动调整至有效范围，小数截断为整数。详见SetBrightnessOptions中value参数说明。

**起始版本：** 3

**废弃版本：** 7

**替代接口：** [setValue](arkts-basicservices-brightness-setvalue-f-sys.md)

<!--Device-Brightness-static setValue(options?: SetBrightnessOptions): void--><!--Device-Brightness-static setValue(options?: SetBrightnessOptions): void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SetBrightnessOptions](arkts-basicservices-system-brightness-setbrightnessoptions-i.md) | 否 | 设置屏幕亮度的参数对象。可选，默认为空。不传入此参数时，无法设置亮度值，接口调用无实际效果。 |

