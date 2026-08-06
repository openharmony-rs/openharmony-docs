# Brightness

该模块提供屏幕亮度和模式的查询、调节接口。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 7

<!--Device-unnamed-export default class Brightness--><!--Device-unnamed-export default class Brightness-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## getMode

```TypeScript
static getMode(options?: GetBrightnessModeOptions): void
```

获得当前屏幕亮度模式。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 7

<!--Device-Brightness-static getMode(options?: GetBrightnessModeOptions): void--><!--Device-Brightness-static getMode(options?: GetBrightnessModeOptions): void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 获取屏幕亮度模式的参数对象。可选，默认为空。 |

## getValue

```TypeScript
static getValue(options?: GetBrightnessOptions): void
```

获得设备当前的屏幕亮度值。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 7

<!--Device-Brightness-static getValue(options?: GetBrightnessOptions): void--><!--Device-Brightness-static getValue(options?: GetBrightnessOptions): void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 获取屏幕亮度的参数对象。可选，默认为空。 |

## setKeepScreenOn

```TypeScript
static setKeepScreenOn(options?: SetKeepScreenOnOptions): void
```

设置屏幕是否保持常亮状态，开启常亮模式推荐在onShow()阶段调用。 注意： - 除Lite Wearable外，从API version 7开始不再维护，建议使用\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_替代。 - 在Lite Wearable上，该接口仅能阻止系统无活动超时灭屏（自动），无法阻止用户主动操作（如盖屏）、常亮时刻结束等导致的灭屏。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 7

**替代接口：** @ohos.window:Window.setWindowKeepScreenOn

<!--Device-Brightness-static setKeepScreenOn(options?: SetKeepScreenOnOptions): void--><!--Device-Brightness-static setKeepScreenOn(options?: SetKeepScreenOnOptions): void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 设置屏幕常亮的参数对象。可选，默认为空。 |

## setMode

```TypeScript
static setMode(options?: SetBrightnessModeOptions): void
```

设置设备当前的屏幕亮度模式。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 7

<!--Device-Brightness-static setMode(options?: SetBrightnessModeOptions): void--><!--Device-Brightness-static setMode(options?: SetBrightnessModeOptions): void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 设置屏幕亮度模式的参数对象。可选，默认为空。 |

## setValue

```TypeScript
static setValue(options?: SetBrightnessOptions): void
```

设置设备当前的屏幕亮度值。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 7

**替代接口：** [@ohos.brightness:brightness.setValue](arkts-basicservices-brightness-setvalue-f-sys.md#setvalue)

<!--Device-Brightness-static setValue(options?: SetBrightnessOptions): void--><!--Device-Brightness-static setValue(options?: SetBrightnessOptions): void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 设置屏幕亮度的参数对象。可选，默认为空。 |

