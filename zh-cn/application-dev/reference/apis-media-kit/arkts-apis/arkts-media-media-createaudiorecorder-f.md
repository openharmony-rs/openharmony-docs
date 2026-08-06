# createAudioRecorder

## createAudioRecorder

```TypeScript
function createAudioRecorder(): AudioRecorder
```

创建音频录制的实例来控制音频的录制。一台设备只允许创建一个录制实例。 > **说明：** > > 从API version 6开始支持，从API version 9开始废弃，建议使用 > [createAVRecorder]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替代。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 9

**替代接口：** [media.createAVRecorder](arkts-media-media-createavrecorder-f.md#createavrecorder)(callback:

<!--Device-media-function createAudioRecorder(): AudioRecorder--><!--Device-media-function createAudioRecorder(): AudioRecorder-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回AudioRecorder类实例，失败时返回null。可用于录制音频媒体。 |

**示例：**

```TypeScript
let audioRecorder: media.AudioRecorder = media.createAudioRecorder();
```

