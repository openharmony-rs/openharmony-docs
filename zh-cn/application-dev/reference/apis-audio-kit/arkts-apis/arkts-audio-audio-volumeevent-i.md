# VolumeEvent

音量改变时，应用接收到的事件。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-audio-interface VolumeEvent--><!--Device-audio-interface VolumeEvent-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## updateUi

```TypeScript
updateUi: boolean
```

是否在UI中显示音量变化。true表示显示，false表示不显示。

**类型：** boolean

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-VolumeEvent-updateUi: boolean--><!--Device-VolumeEvent-updateUi: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## volume

```TypeScript
volume: int
```

音量等级，可设置范围通过调用getMinVolume和getMaxVolume方法获取。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-VolumeEvent-volume: int--><!--Device-VolumeEvent-volume: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## volumeMode

```TypeScript
volumeMode?: AudioVolumeMode
```

音频的音量模式。默认值为SYSTEM\_GLOBAL。

**类型：** AudioVolumeMode

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-VolumeEvent-volumeMode?: AudioVolumeMode--><!--Device-VolumeEvent-volumeMode?: AudioVolumeMode-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## volumeType

```TypeScript
volumeType: AudioVolumeType
```

音频音量类型。

**类型：** AudioVolumeType

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-VolumeEvent-volumeType: AudioVolumeType--><!--Device-VolumeEvent-volumeType: AudioVolumeType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

