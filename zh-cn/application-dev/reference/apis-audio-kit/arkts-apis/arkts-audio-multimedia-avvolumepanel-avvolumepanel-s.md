# AVVolumePanel

音量面板，可用于在当前应用内展示音量调节面板。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct AVVolumePanel--><!--Device-unnamed-export declare struct AVVolumePanel-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## build

```TypeScript
build(): void
```

用于构造组件的建造接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**装饰器类型：** @Builder

<!--Device-AVVolumePanel-build(): void--><!--Device-AVVolumePanel-build(): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## volumeLevel

```TypeScript
volumeLevel?: int
```

通过音量面板设置的音量值。 该值应介于当前设备音量的最小值和最大值之间。 如果该值大于当前设备音量的最大值，则视为设置最大音量值。 如果该值小于当前设备音量的最小值，则视为设置最小音量值。 获取设备的最大值、最小值和当前值，可参考[AudioVolumeGroupManager]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVVolumePanel-volumeLevel?: int--><!--Device-AVVolumePanel-volumeLevel?: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## volumeParameter

```TypeScript
volumeParameter?: AVVolumePanelParameter
```

设置音量面板的自定义参数。 如果不设置该参数，则为系统音量条。

**类型：** AVVolumePanelParameter

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVVolumePanel-volumeParameter?: AVVolumePanelParameter--><!--Device-AVVolumePanel-volumeParameter?: AVVolumePanelParameter-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

