# VolumeEvent

音量改变时，应用接收的事件。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## updateUi

```TypeScript
updateUi: boolean
```

标识是否会显示系统本身的音量条，true表示会显示系统音量条，false表示不会显示系统音量条。

若应用内含自定义音量条，建议根据此参数动态控制其显示：当updateUi为true时不显示自定义音量条，为false时显示自定义音量条，从而避免出现系统本身音量条与应用自定义音量条同时显示或不显示的问题。

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

**类型：** [AudioVolumeMode](arkts-audio-audio-audiovolumemode-e.md)

**起始版本：** 19

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## volumeType

```TypeScript
volumeType: AudioVolumeType
```

音频音量类型。

**类型：** [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume
