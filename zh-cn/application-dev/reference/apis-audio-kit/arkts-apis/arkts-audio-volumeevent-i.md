# VolumeEvent

音量改变时，应用接收到的事件。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## updateUi

```TypeScript
updateUi: boolean
```

是否在UI中显示音量变化。true表示显示，false表示不显示。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## volume

```TypeScript
volume: number
```

音量等级，可设置范围通过调用getMinVolume和getMaxVolume方法获取。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## volumeMode

```TypeScript
volumeMode?: AudioVolumeMode
```

音频的音量模式。默认值为SYSTEM_GLOBAL。

**类型：** AudioVolumeMode

**起始版本：** 19

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## volumeType

```TypeScript
volumeType: AudioVolumeType
```

音频音量类型。

**类型：** AudioVolumeType

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

