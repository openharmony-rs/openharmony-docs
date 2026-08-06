# VibratePreset

预置振动类型。当调用 [vibrator.startVibration\_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_9+\_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 或 [vibrator.startVibration\_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_9+\_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 时，[VibrateEffect\_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_9+\_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_参数的值可以为VibratePreset，表示触发预置振动类型。适用于交互反馈类的短振场景（如点击、长按、滑动 、拖拽等），为确保与系统整体振感反馈体验风格一致，推荐使用此类型。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-vibrator-interface VibratePreset--><!--Device-vibrator-interface VibratePreset-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## count

```TypeScript
count?: int
```

可选参数，振动的重复次数。默认值：1。取值范围：正整数。使用场景：适用于需要多次重复同一振动效果的交互反馈场景，如连续点击提醒。不填写时默认重复1次。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-VibratePreset-count?: int--><!--Device-VibratePreset-count?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## effectId

```TypeScript
effectId: string
```

预置的振动效果ID。字符串最大长度64，超出部分截取前64个字符。使用场景：不同设备预置的振动效果可能不同，建议先通过 [vibrator.isSupportEffect]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_或 [vibrator.isSupportEffectSync]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_查询是否支持。取值可参考[EffectId]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_ 和[HapticFeedback]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_中定义的值。

**类型：** string

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-VibratePreset-effectId: string--><!--Device-VibratePreset-effectId: string-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## intensity

```TypeScript
intensity?: int
```

可选参数，振动调节强度。取值范围：(0,100]区间内所有整数。默认值：100。使用场景：适用于需要调节振动强度的交互反馈场景。不填写时默认使用最大强度。若振动效果不支持强度调节或设备不支持时，则按默认强度振动。

**类型：** int

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-VibratePreset-intensity?: int--><!--Device-VibratePreset-intensity?: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## type

```TypeScript
type: 'preset'
```

值为'preset'，按照预置振动效果触发马达振动。固定值，不可更改。

**类型：** 'preset'

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-VibratePreset-type: 'preset'--><!--Device-VibratePreset-type: 'preset'-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

