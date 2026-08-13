# Vibrator

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** [vibrator/vibrator](arkts-vibrator.md#@ohos.vibrator)

**需要权限：** ohos.permission.VIBRATE

<!--Device-unnamed-export default class Vibrator--><!--Device-unnamed-export default class Vibrator-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice.Lite

## vibrate

```TypeScript
static vibrate(options?: VibrateOptions): void
```

触发设备振动，根据指定的振动模式执行短振动或长振动效果。该接口通过callback方式返回调用结果。 > **说明：** > > 除Lite Wearable外，从API version 8开始，建议使用 > [vibrator.startVibration()](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) > 替代。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** [startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startVibration)(effect: VibrateEffect, attribute: VibrateAttribute, callback: AsyncCallback&lt;void&gt;)

**需要权限：** ohos.permission.VIBRATE

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Vibrator-static vibrate(options?: VibrateOptions): void--><!--Device-Vibrator-static vibrate(options?: VibrateOptions): void-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [VibrateOptions](arkts-sensorservice-system-vibrator-vibrateoptions-i.md) | 否 | 振动配置参数，用于指定振动模式及回调函数。不传时使用默认配置（mode默认为'long'），此时仅触发success和complete回调（无fail回调场景下）。 |

