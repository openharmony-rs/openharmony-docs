# createMicInAudioCapturer（系统接口）

## createMicInAudioCapturer

```TypeScript
function createMicInAudioCapturer(config: AudioCapturerMicInConfig): Promise<AudioCapturer | null>
```

获取一个特殊的[AudioCapturer](arkts-audio-audio-audiocapturer-i.md#AudioCapturer)实例。该方法使用promise返回录音实例。 此捕获可用于记录Mic-In音频数据和回声参考信号，以便应用处理算法。 Mic-In音频数据和回声参考信号将根据应用程序设置的配置被放入一个或多个缓冲。 当应用程序处于后台时，不允许创建录音实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MICROPHONE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-audio-function createMicInAudioCapturer(config: AudioCapturerMicInConfig): Promise<AudioCapturer | null>--><!--Device-audio-function createMicInAudioCapturer(config: AudioCapturerMicInConfig): Promise<AudioCapturer | null>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [AudioCapturerMicInConfig](arkts-audio-audio-audiocapturermicinconfig-i-sys.md) | 是 | Capturer configuration, see [AudioCapturerMicInConfig](arkts-audio-audio-audiocapturermicinconfig-i-sys.md#AudioCapturerMicInConfig（系统接口）) for details. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioCapturer](arkts-audio-audio-audiocapturer-i.md) \| null&gt; | Promise用于返回录音实例。 如果出现错误，则返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied, including background recording. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio system internal error, such as system process crash. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Capturer creation is not supported, may caused by following problems: &lt;br&gt; 1. Source type is unsupported for this capturer, only [SOURCE_TYPE_UNPROCESSED_VOICE_ASSISTANT](arkts-audio-audio-sourcetype-e-sys.md#SOURCE_TYPE_UNPROCESSED_VOICE_ASSISTANT) and [SOURCE_TYPE_VOICE_RECOGNITION](arkts-audio-audio-sourcetype-e.md#SOURCE_TYPE_VOICE_RECOGNITION) are supported currently. &lt;br&gt; 2. Echo reference signal's config is unsupported, echo reference's sampling rate and format must be the same as MicIn audio data currently. |

## 示例

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

