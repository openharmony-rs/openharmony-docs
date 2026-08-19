# AVVolumePanel

音量面板，可用于在当前应用内展示音量调节面板。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare struct AVVolumePanel--><!--Device-unnamed-export declare struct AVVolumePanel-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## 导入模块

```TypeScript
```

## build

```TypeScript
@Builder
  build(): void
```

用于构造组件的建造接口。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AVVolumePanel-@Builder  build(): void--><!--Device-AVVolumePanel-@Builder  build(): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## volumeLevel

```TypeScript
@PropRef
  volumeLevel?: int
```

通过音量面板设置的音量值。 该值应介于当前设备音量的最小值和最大值之间。 如果该值大于当前设备音量的最大值，则视为设置最大音量值。 如果该值小于当前设备音量的最小值，则视为设置最小音量值。 获取设备的最大值、最小值和当前值，可参考[AudioVolumeGroupManager](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audiovolumegroupmanager-i.md)。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AVVolumePanel-@PropRef  volumeLevel?: int--><!--Device-AVVolumePanel-@PropRef  volumeLevel?: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## volumeParameter

```TypeScript
@PropRef
  volumeParameter?: AVVolumePanelParameter
```

设置音量面板的自定义参数。 如果不设置该参数，则为系统音量条。

**类型：** [AVVolumePanelParameter](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-avvolumepanel-avvolumepanelparameter-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AVVolumePanel-@PropRef  volumeParameter?: AVVolumePanelParameter--><!--Device-AVVolumePanel-@PropRef  volumeParameter?: AVVolumePanelParameter-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

