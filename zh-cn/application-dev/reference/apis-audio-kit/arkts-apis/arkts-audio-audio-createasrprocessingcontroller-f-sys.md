# createAsrProcessingController（系统接口）

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## createAsrProcessingController

```TypeScript
function createAsrProcessingController(audioCapturer: AudioCapturer): AsrProcessingController
```

Create ASR processing controller on one audio capturer.

**起始版本：** 12

<!--Device-audio-function createAsrProcessingController(audioCapturer: AudioCapturer): AsrProcessingController--><!--Device-audio-function createAsrProcessingController(audioCapturer: AudioCapturer): AsrProcessingController-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| audioCapturer | [AudioCapturer](arkts-audio-audio-audiocapturer-i-sys.md) | 是 | The audio capturer whose ASR processing will be controlled. The source type of this capturer must be {@link SourceType#SOURCE_TYPE_VOICE_RECOGNITION}. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AsrProcessingController](arkts-audio-audio-asrprocessingcontroller-i-sys.md) | ASR Processing Controller. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation not allowed. e.g. the source type of the input audio capturer is not{@link SourceType#SOURCE_TYPE_VOICE_RECOGNITION} or {@link SourceType#SOURCE_TYPE_WAKEUP}, or this audio capturer is already released. |

**示例：**

```TypeScript
import { audio } from '@kit.AudioKit';

let audioStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_2,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW
};

let audioCapturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC,
  capturerFlags: 0
};

let audioCapturerOptions: audio.AudioCapturerOptions = {
  streamInfo: audioStreamInfo,
  capturerInfo: audioCapturerInfo
};

audio.createAudioCapturer(audioCapturerOptions, (err, data) => {
  if (err) {
    console.error(`AudioCapturer Created : Error: ${err}`);
  } else {
    console.info('AudioCapturer Created : Success : SUCCESS');
    let audioCapturer = data;
    let asrProcessingController = audio.createAsrProcessingController(audioCapturer);
    console.info('AsrProcessingController Created : Success : SUCCESS');
  }
});

```

