# HapticFeedback

简单而通用的振动效果。根据各设备的马达器件不同，同一振动效果的频率会有差异，但效果的频率趋向是统一的。这几种振动效果是EffectId参数的具体值，使用方法参考 [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 或[vibrator.stopVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-stopvibration-f.md#stopVibration)接口下发 [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md#VibratePreset)形式振动的示例代码。 > **说明：**> > 由于设备存在多样性，建议使用预置效果前先使用 > [vibrator.isSupportEffect](arkts-sensorservice-vibrator-issupporteffect-f.md#isSupportEffect)&lt; &gt; sup>10+&lt;/sup&gt;或[vibrator.isSupportEffectSync](arkts-sensorservice-vibrator-issupporteffectsync-f.md#isSupportEffectSync)接口查询当前设备是否支持该预置效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-vibrator-enum HapticFeedback--><!--Device-vibrator-enum HapticFeedback-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## EFFECT_SOFT

```TypeScript
EFFECT_SOFT = 'haptic.effect.soft'
```

较松散的振动效果，频率偏低。适用于轻柔触觉反馈场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HapticFeedback-EFFECT_SOFT = 'haptic.effect.soft'--><!--Device-HapticFeedback-EFFECT_SOFT = 'haptic.effect.soft'-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## EFFECT_HARD

```TypeScript
EFFECT_HARD = 'haptic.effect.hard'
```

较沉重的振动效果，频率居中。适用于坚定触觉反馈场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HapticFeedback-EFFECT_HARD = 'haptic.effect.hard'--><!--Device-HapticFeedback-EFFECT_HARD = 'haptic.effect.hard'-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## EFFECT_SHARP

```TypeScript
EFFECT_SHARP = 'haptic.effect.sharp'
```

较尖锐的振动效果，频率偏高。适用于警示触觉反馈场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HapticFeedback-EFFECT_SHARP = 'haptic.effect.sharp'--><!--Device-HapticFeedback-EFFECT_SHARP = 'haptic.effect.sharp'-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## EFFECT_NOTICE_SUCCESS

```TypeScript
EFFECT_NOTICE_SUCCESS = 'haptic.notice.success'
```

表达成功通知的振动效果。适用于操作成功提醒场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HapticFeedback-EFFECT_NOTICE_SUCCESS = 'haptic.notice.success'--><!--Device-HapticFeedback-EFFECT_NOTICE_SUCCESS = 'haptic.notice.success'-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## EFFECT_NOTICE_FAILURE

```TypeScript
EFFECT_NOTICE_FAILURE = 'haptic.notice.fail'
```

表达失败通知的振动效果。适用于操作失败提醒场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HapticFeedback-EFFECT_NOTICE_FAILURE = 'haptic.notice.fail'--><!--Device-HapticFeedback-EFFECT_NOTICE_FAILURE = 'haptic.notice.fail'-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## EFFECT_NOTICE_WARNING

```TypeScript
EFFECT_NOTICE_WARNING = 'haptic.notice.warning'
```

表达警告通知的振动效果。适用于风险警告提醒场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HapticFeedback-EFFECT_NOTICE_WARNING = 'haptic.notice.warning'--><!--Device-HapticFeedback-EFFECT_NOTICE_WARNING = 'haptic.notice.warning'-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

