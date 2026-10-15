# AudioCapturerOptions

```TypeScript
interface AudioCapturerOptions
```

音频采集器选项信息。

**起始版本：** 8

<!--Device-audio-interface AudioCapturerOptions--><!--Device-audio-interface AudioCapturerOptions-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## actualUsingAppTokenId

```TypeScript
actualUsingAppTokenId?: number
```

实际使用该录音流的应用TokenId，用于在点亮麦克风隐私指示器时，显示正确的应用信息。如果未指定该字段，默认使用调用方应用的TokenId。设置该字段时，调用方必须具有ohos.permission.AUDIO_USER_MICROPHONE_INDICATOR权限，否则[createAudioCapturer](arkts-audio-audio-createaudiocapturer-f.md)失败。

**类型：** number

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturerOptions-actualUsingAppTokenId?: int--><!--Device-AudioCapturerOptions-actualUsingAppTokenId?: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## playbackCaptureUid

```TypeScript
playbackCaptureUid?: number
```

应用UID，用于音视频通话播放采集。

此参数仅在[AudioCapturerOptions](./arkts-apis-audio-i.md#audiocaptureroptions).playbackCaptureMode设置为[AudioPlaybackCaptureMode](arkts-audio-audio-audioplaybackcapturemode-e.md).MODE_ONLY_VOIP时生效。在其他模式下，此参数将被忽略。

SystemCapability.Multimedia.Audio.PlaybackCapture

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturerOptions-playbackCaptureUid?: int--><!--Device-AudioCapturerOptions-playbackCaptureUid?: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

**系统接口：** 此接口为系统接口。

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

<!--Device-AudioCapturerOptions-preferredInputDevice?: AudioDeviceDescriptor--><!--Device-AudioCapturerOptions-preferredInputDevice?: AudioDeviceDescriptor-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。
