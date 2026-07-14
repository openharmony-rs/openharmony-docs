# createAudioRecorder

## createAudioRecorder

```TypeScript
function createAudioRecorder(): AudioRecorder
```

创建音频录制的实例来控制音频的录制。一台设备只允许创建一个录制实例。

> **说明：**
> > 从API version 6开始支持，从API version 9开始废弃，建议使用
> [createAVRecorder](arkts-media-createavrecorder-f.md#createavrecorder-1)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** createAVRecorder(callback:

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AudioRecorder | 返回AudioRecorder类实例，失败时返回null。可用于录制音频媒体。 |

**示例：**

```TypeScript
let audioRecorder: media.AudioRecorder = media.createAudioRecorder();

```

