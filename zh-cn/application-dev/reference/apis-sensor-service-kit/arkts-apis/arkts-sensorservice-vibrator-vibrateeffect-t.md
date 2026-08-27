# VibrateEffect

```TypeScript
type VibrateEffect = VibrateTime | VibratePreset | VibrateFromFile | VibrateFromPattern
```

马达振动效果，支持以下四种：在调用 [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md) 或 [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md) 接口时，此参数的四种类型表示以四种不同的形式触发振动。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.MiscDevice

| 类型 | 说明 |
| --- | --- |
| [VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md) | 按照指定时长触发马达振动。适用于仅需控制振动时长的基础场景。 从API version 11开始，该接口支持在原子化服务中使用。 |
| [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md) | 按照预置振动类型触发马达振动。适用于交互反馈类的短振场景，推荐使用以确保与系统整体振感反馈体验风格一致。 |
| [VibrateFromFile](arkts-sensorservice-vibrator-vibratefromfile-i.md) | 按照自定义振动配置文件触发马达振动。适用于需要精细振动控制的复杂场景。 |
| [VibrateFromPattern](arkts-sensorservice-vibrator-vibratefrompattern-i.md) | 按照自定义振动效果触发马达振动。适用于需要灵活组合振动事件的场景。 |
