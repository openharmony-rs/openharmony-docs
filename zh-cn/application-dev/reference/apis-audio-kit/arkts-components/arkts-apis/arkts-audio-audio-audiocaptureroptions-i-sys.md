# AudioCapturerOptions

音频采集器选项信息。

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## preferredInputDevice

```TypeScript
preferredInputDevice?: AudioDeviceDescriptor
```

当前音频采集器的偏好输入设备。

此设备必须为输入设备，并且capturerInfo的source type必须为[SOURCE_TYPE_VOICE_RECOGNITION](arkts-apis-audio-e.md#sourcetype8)或SOURCE_TYPE_VOICE_TRANSCRIPTION。否则，此参数将会被忽略。

1. 当调用者未指定偏好设备时，系统会自动选择一个设备。
2. 当调用者指定了偏好设备创建语音识别或者语音转写流时：

（1）设备在线，当前audiocapturer会使用偏好设备；如果运行过程中，偏好设备下线，系统会自动选择一个录音设备。

（2）设备不在线，当前audiocapturer会自动选择一个录音设备；如果运行过程中，偏好设备上线，系统会自动切换到偏好设备上。

3. 调用者可以通过[getCurrentAudioCapturerChangeInfo](arkts-audio-audio-audiocapturer-i.md#getcurrentaudiocapturerchangeinfo)查询当前实际使用的录音设备。

**类型：** [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md)

**起始版本：** 22

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。
