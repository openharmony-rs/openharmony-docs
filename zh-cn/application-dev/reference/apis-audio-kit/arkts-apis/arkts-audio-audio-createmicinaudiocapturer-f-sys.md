# createMicInAudioCapturer（系统接口）

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## createMicInAudioCapturer

```TypeScript
function createMicInAudioCapturer(config: AudioCapturerMicInConfig): Promise<AudioCapturer | null>
```

获取音频采集器。使用Promise异步回调。

> **说明：**
> 
> - 此采集器可用于同时录制麦克风输入（Mic-In）音频数据和回声参考信号，供应用层进行算法处理。
> 
> - 麦克风输入音频数据和回声参考信号会根据应用层设置的配置，被放入同一个缓冲区或多个独立缓冲区中。
> 
> - 仅允许使用[SourceType](arkts-audio-audio-sourcetype-e.md)为SOURCE_TYPE_UNPROCESSED_VOICE_ASSISTANT类型的音源输入
> ，其他类型的音源输入将被系统拒绝。此外，当应用处于后台运行状态时，不允许创建该采集器实例。

**起始版本：** 23

**需要权限：** ohos.permission.MICROPHONE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [AudioCapturerMicInConfig](arkts-audio-audio-audiocapturermicinconfig-i-sys.md) | 是 | 配置音频采集器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioCapturer](arkts-audio-audio-audiocapturer-i.md) \| null&gt; | Promise对象，成功将返回音频采集器对象，失败时将返回包含错误信息的error对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied, including background recording. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Capturer creation is not supported, may caused by following problems:   1. Source type is unsupported for this capturer, only [SOURCE_TYPE_UNPROCESSED_VOICE_ASSISTANT](arkts-audio-audio-sourcetype-e-sys.md#source_type_unprocessed_voice_assistant) and [SOURCE_TYPE_VOICE_RECOGNITION](arkts-audio-audio-sourcetype-e.md#source_type_voice_recognition) are supported currently.   2. Echo reference signal's config is unsupported, echo reference's sampling rate and format must be the same as MicIn audio data currently. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio system internal error, such as system process crash. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioEcStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000, // 采样率。
  channels: audio.AudioChannel.CHANNEL_2, // 通道。
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE, // 采样格式。
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW // 编码格式。
};

let audioCapturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_UNPROCESSED_VOICE_ASSISTANT, // 音源类型：Mic音频源。SourceType需为SOURCE_TYPE_UNPROCESSED_VOICE_ASSISTANT。
  capturerFlags: 0 // 音频采集器标志。
};

let audioMicInStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000, // 采样率。
  channels: audio.AudioChannel.CHANNEL_2, // 通道。
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE, // 采样格式。
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW // 编码格式。
};

let audioCapturerMicInConfig: audio.AudioCapturerMicInConfig = {
  ecStreamInfo: audioEcStreamInfo,
  capturerInfo: audioCapturerInfo,
  micInStreamInfo: audioMicInStreamInfo
};

let audioCapturer: audio.AudioCapturer | null = null;

audio.createMicInAudioCapturer(audioCapturerMicInConfig).then((data) => {
  audioCapturer = data;
  console.info('AudioCapturer Created : SUCCESS');
}).catch((err: BusinessError) => {
  console.error(`AudioCapturer Created : ERROR : ${err}`);
});
```
