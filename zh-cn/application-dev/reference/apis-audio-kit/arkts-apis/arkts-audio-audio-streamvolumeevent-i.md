# StreamVolumeEvent

音频流音量变化时，应用接收到的事件。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## previousVolume

```TypeScript
previousVolume?: number
```

变化前的音量值。 取值限定为整数。

**类型：** number

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## streamUsage

```TypeScript
streamUsage: StreamUsage
```

音量发生变化的音频流。

**类型：** [StreamUsage](arkts-audio-audio-streamusage-e.md)

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## updateUi

```TypeScript
updateUi: boolean
```

标识是否会显示系统本身的音量条，true表示会显示系统音量条，false表示不会显示系统音量条。若应用内含自定义音量条，建议根据此参数动态控制其显示：当updateUi为true时不显示自定义音量条，为false时显示自定义音量条，从而避免出现系统本身音量条与应用自定义音量条同时显示或不显示的问题。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## volume

```TypeScript
volume: number
```

音量值。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Volume
