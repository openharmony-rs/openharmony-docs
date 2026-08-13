# createAudioCapturer

## createAudioCapturer

```TypeScript
function createAudioCapturer(options: AudioCapturerOptions, callback: AsyncCallback<AudioCapturer>): void
```

获取音频采集器。使用callback异步回调。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

<!--Device-audio-function createAudioCapturer(options: AudioCapturerOptions, callback: AsyncCallback<AudioCapturer>): void--><!--Device-audio-function createAudioCapturer(options: AudioCapturerOptions, callback: AsyncCallback<AudioCapturer>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AudioCapturerOptions](arkts-audio-audio-audiocaptureroptions-i.md) | 是 | 配置音频采集器。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AudioCapturer](arkts-audio-audio-audiocapturer-i.md)&gt; | 是 | 回调函数。当获取音频采集器成功，err为undefined，data为获取到的音频采集器对象；否则为错误对象。异常将返回 error对象： &lt;br&gt;错误码6800301：表示参数校验异常、权限校验异常或系统处理异常（具体错误查看系统日志）。 &lt;br&gt;错误码6800101：表示必选参数为空或参数类型错误。 |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

let audioStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000, // 采样率。
  channels: audio.AudioChannel.CHANNEL_2, // 通道。
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE, // 采样格式。
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW // 编码格式。
};

let audioCapturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // 音源类型：Mic音频源。根据业务场景配置，参考SourceType。
  capturerFlags: 0 // 音频采集器标志。
};

let audioCapturerOptions: audio.AudioCapturerOptions = {
  streamInfo: audioStreamInfo,
  capturerInfo: audioCapturerInfo
};

let audioCapturer: audio.AudioCapturer;

audio.createAudioCapturer(audioCapturerOptions, (err, data) => {
  if (err) {
    console.error(`AudioCapturer Created : Error: ${err}`);
  } else {
    console.info('AudioCapturer Created : SUCCESS');
    audioCapturer = data;
  }
});
```


## createAudioCapturer

```TypeScript
function createAudioCapturer(options: AudioCapturerOptions, callback: AsyncCallback<AudioCapturer | null>): void
```

Obtains an [AudioCapturer](arkts-audio-audio-audiocapturer-i.md#AudioCapturer) instance. This method uses an asynchronous callback to return the capturer instance. Using [AudioCapturer](arkts-audio-audio-audiocapturer-i.md#AudioCapturer) to record audio will need permission according to different Sourcetype in options parameter, like MICROPHONE for the most microphone recording cases.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-audio-function createAudioCapturer(options: AudioCapturerOptions, callback: AsyncCallback<AudioCapturer | null>): void--><!--Device-audio-function createAudioCapturer(options: AudioCapturerOptions, callback: AsyncCallback<AudioCapturer | null>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AudioCapturerOptions](arkts-audio-audio-audiocaptureroptions-i.md) | 是 | Capturer configurations. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AudioCapturer](arkts-audio-audio-audiocapturer-i.md) \| null&gt; | 是 | Callback used to return the audio capturer instance, or null if any error occurs. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio system internal error, such as system crash. |


## createAudioCapturer

```TypeScript
function createAudioCapturer(options: AudioCapturerOptions): Promise<AudioCapturer>
```

获取音频采集器。使用Promise异步回调。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

<!--Device-audio-function createAudioCapturer(options: AudioCapturerOptions): Promise<AudioCapturer>--><!--Device-audio-function createAudioCapturer(options: AudioCapturerOptions): Promise<AudioCapturer>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AudioCapturerOptions](arkts-audio-audio-audiocaptureroptions-i.md) | 是 | 配置音频采集器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioCapturer](arkts-audio-audio-audiocapturer-i.md)&gt; | Promise对象，成功将返回音频采集器对象，异常将返回error对象： &lt;br&gt;错误码6800301：表示参数校验异常、权限校验异常或系统处理异常（具体错误查看系统日志）。 &lt;br&gt;错误码6800101：表示必选参数为空或参数类型错误。 |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000, // 采样率。
  channels: audio.AudioChannel.CHANNEL_2, // 通道。
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE, // 采样格式。
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW // 编码格式。
};

let audioCapturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // 音源类型：Mic音频源。根据业务场景配置，参考SourceType。
  capturerFlags: 0 // 音频采集器标志。
};

let audioCapturerOptions:audio.AudioCapturerOptions = {
  streamInfo: audioStreamInfo,
  capturerInfo: audioCapturerInfo
};

let audioCapturer: audio.AudioCapturer;

audio.createAudioCapturer(audioCapturerOptions).then((data) => {
  audioCapturer = data;
  console.info('AudioCapturer Created : SUCCESS');
}).catch((err: BusinessError) => {
  console.error(`AudioCapturer Created : ERROR : ${err}`);
});
```


## createAudioCapturer

```TypeScript
function createAudioCapturer(options: AudioCapturerOptions): Promise<AudioCapturer | null>
```

Obtains an [AudioCapturer](arkts-audio-audio-audiocapturer-i.md#AudioCapturer) instance. This method uses a promise to return the capturer instance. Using [AudioCapturer](arkts-audio-audio-audiocapturer-i.md#AudioCapturer) to record audio will need permission according to different Sourcetype in options parameter, like MICROPHONE for the most microphone recording cases.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-audio-function createAudioCapturer(options: AudioCapturerOptions): Promise<AudioCapturer | null>--><!--Device-audio-function createAudioCapturer(options: AudioCapturerOptions): Promise<AudioCapturer | null>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AudioCapturerOptions](arkts-audio-audio-audiocaptureroptions-i.md) | 是 | Capturer configurations. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioCapturer](arkts-audio-audio-audiocapturer-i.md) \| null&gt; | Promise used to return the audio capturer instance, or null if any error occurs. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio system internal error, such as system crash. |

