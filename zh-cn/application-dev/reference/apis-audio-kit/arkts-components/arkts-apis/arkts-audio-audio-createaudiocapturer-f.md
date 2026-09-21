# createAudioCapturer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## createAudioCapturer

```TypeScript
function createAudioCapturer(options: AudioCapturerOptions, callback: AsyncCallback<AudioCapturer>): void
```

创建音频采集器。使用callback异步回调。

当设置Mic音频源（即SourceType为SOURCE_TYPE_MIC、SOURCE_TYPE_VOICE_RECOGNITION、SOURCE_TYPE_VOICE_COMMUNICATION、SOURCE_TYPE_VOICE_MESSAGE、SOURCE_TYPE_CAMCORDER）时需要ohos.permission.MICROPHONE权限。

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AudioCapturerOptions](arkts-audio-audio-audiocaptureroptions-i.md) | 是 | 配置音频采集器。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AudioCapturer](arkts-audio-audio-audiocapturer-i.md)&gt; | 是 | 回调函数。当创建音频采集器成功，err为undefined，data为创建的音频采集器对象；否则为错误对象。<br>异常将返回error对象：<br>返回错误码6800301：表示参数校验异常、权限校验异常或系统处理异常（具体错误查看系统日志）。<br>返回错误码6800101：表示必选参数为空或参数类型错误。 |

**示例**

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


<a id="createaudiocapturer-2"></a>

## createAudioCapturer

```TypeScript
function createAudioCapturer(options: AudioCapturerOptions): Promise<AudioCapturer>
```

创建音频采集器。使用Promise异步回调。

当设置Mic音频源（即SourceType为SOURCE_TYPE_MIC、SOURCE_TYPE_VOICE_RECOGNITION、SOURCE_TYPE_VOICE_COMMUNICATION、SOURCE_TYPE_VOICE_MESSAGE、SOURCE_TYPE_CAMCORDER）时需要ohos.permission.MICROPHONE权限。

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AudioCapturerOptions](arkts-audio-audio-audiocaptureroptions-i.md) | 是 | 配置音频采集器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioCapturer](arkts-audio-audio-audiocapturer-i.md)&gt; | Promise对象，成功将返回音频采集器对象，异常将返回error对象。  返回错误码6800301：表示参数校验异常、权限校验异常或系统处理异常（具体错误查看系统日志）。  返回错误码6800101：表示必选参数为空或参数类型错误。 |

**示例**

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
