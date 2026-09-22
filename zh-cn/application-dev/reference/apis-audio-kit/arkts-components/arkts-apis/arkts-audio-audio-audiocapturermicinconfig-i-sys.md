# AudioCapturerMicInConfig（系统接口）

```TypeScript
interface AudioCapturerMicInConfig
```

音频采集器选项信息，可采集未经任何处理的麦克风输入（mic-in）音频数据。

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## capturerInfo

```TypeScript
capturerInfo: AudioCapturerInfo
```

音频采集器信息。

**类型：** [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## ecStreamInfo

```TypeScript
ecStreamInfo?: AudioStreamInfo
```

回声消除音频流信息。

若未设置此属性，采集器将仅录制麦克风输入的音频流。

**类型：** [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## micInStreamInfo

```TypeScript
micInStreamInfo: AudioStreamInfo
```

麦克风音频流信息。

**类型：** [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## preferredInputDevice

```TypeScript
preferredInputDevice?: AudioDeviceDescriptor
```

当前音频采集器的偏好输入设备。对于该设备有以下要求：

- 此设备必须为输入设备，并且**capturerInfo**中的源类型必须为[SOURCE_TYPE_VOICE_RECOGNITION](arkts-apis-audio-e.md#sourcetype8)、SOURCE_TYPE_VOICE_TRANSCRIPTION或SOURCE_TYPE_UNPROCESSED_VOICE_ASSISTANT，否则此参数将被忽略。  
- 如果用户未指定设备，系统会按当前音频路由策略自动选择可用输入设备。  
- 当用户指定偏好设备时：

1. 如果偏好设备在线，当前音频采集器使用该设备录音；如果录音过程中该设备离线，系统会按当前音频路由策略自动选择其他可用输入设备。
2. 如果偏好设备离线，系统会按当前音频路由策略自动选择其他可用输入设备；如果录音过程中该设备上线，系统会自动切换到偏好设备。

- 用户可通过[getCurrentAudioCapturerChangeInfo](arkts-audio-audio-audiocapturer-i.md#getcurrentaudiocapturerchangeinfo)  
查询当前实际使用的设备。

**类型：** [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## processedStreamInfo

```TypeScript
processedStreamInfo?: AudioStreamInfo
```

处理后的音频流信息。

**类型：** [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。
