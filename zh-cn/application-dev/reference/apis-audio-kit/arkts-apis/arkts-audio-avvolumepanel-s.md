# AVVolumePanel

音量面板，可用于在当前应用内展示音量调节面板。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## volumeLevel

```TypeScript
volumeLevel?: number
```

通过音量面板设置的音量值。

该值应介于当前设备音量的最小值和最大值之间。

如果该值大于当前设备音量的最大值，则视为设置最大音量值。

如果该值小于当前设备音量的最小值，则视为设置最小音量值。

获取设备的最大值、最小值和当前值，可参考[AudioVolumeGroupManager](arkts-audio-audiovolumegroupmanager-i.md)。

**类型：** number

**起始版本：** 12

**装饰器类型：** @Prop

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## volumeParameter

```TypeScript
volumeParameter?: AVVolumePanelParameter
```

设置音量面板的自定义参数。

如果不设置该参数，则为系统音量条。

**类型：** AVVolumePanelParameter

**起始版本：** 12

**装饰器类型：** @Prop

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

