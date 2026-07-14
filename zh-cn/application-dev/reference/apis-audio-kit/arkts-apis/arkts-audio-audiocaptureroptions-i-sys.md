# AudioCapturerOptions

音频采集器选项信息。

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## preferredInputDevice

```TypeScript
preferredInputDevice?: AudioDeviceDescriptor
```

当前audio capturer的偏好输入设备。此设备必须为输入设备，并且{@link captureInfo}的source type必须为{@link SourceType#SOURCE_TYPE_RECONGITION} 或
{@link SourceType#SOURCE_TYPE_VOICE_TRANSCRIPTION}。否则，此参数将会被忽略。如果调用者未指定偏好设备，则系统会自动选择一个设备。如果调用者指定了偏好设备取创建语音识别或者语音转写流：
1. 如果设备在线，当前audiocapturer会使用偏好设备；如果运行过程中，偏好设备下线，则系统会自动选择一个录音设备；
2. 如果设备不在线，当前audiocapturer会自动选择一个录音设备；如果运行过程中，偏好设备上线，则会自动切换到偏好设备上。
调用者可以通过{@link AudioCapturer#getCurrentAudioCapturerChangeInfo}查询当前实际使用的录音设备。

**类型：** AudioDeviceDescriptor

**起始版本：** 22

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

