# createAudioRenderer

## createAudioRenderer

```TypeScript
function createAudioRenderer(options: AudioRendererOptions, callback: AsyncCallback<AudioRenderer>): void
```

获取音频渲染器。使用callback异步回调。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

<!--Device-audio-function createAudioRenderer(options: AudioRendererOptions, callback: AsyncCallback<AudioRenderer>): void--><!--Device-audio-function createAudioRenderer(options: AudioRendererOptions, callback: AsyncCallback<AudioRenderer>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AudioRendererOptions](arkts-audio-audio-audiorendereroptions-i.md) | 是 | 配置渲染器。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AudioRenderer](arkts-audio-audio-audiorenderer-i.md)&gt; | 是 | 回调函数。当获取音频渲染器成功，err为undefined，data为获取到的音频渲染器对象；否则为错误对象。 |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

let audioStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000, // 采样率。
  channels: audio.AudioChannel.CHANNEL_2, // 通道。
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE, // 采样格式。
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW // 编码格式。
};

let audioRendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // 音频流使用类型：音乐。根据业务场景配置，参考StreamUsage。
  rendererFlags: 0 // 音频渲染器标志。
};

let audioRendererOptions: audio.AudioRendererOptions = {
  streamInfo: audioStreamInfo,
  rendererInfo: audioRendererInfo
};

let audioRenderer: audio.AudioRenderer;

audio.createAudioRenderer(audioRendererOptions,(err, data) => {
  if (err) {
    console.error(`AudioRenderer Created: Error: ${err}`);
  } else {
    console.info('AudioRenderer Created: SUCCESS');
    audioRenderer = data;
  }
});
```


## createAudioRenderer

```TypeScript
function createAudioRenderer(options: AudioRendererOptions, callback: AsyncCallback<AudioRenderer | null>): void
```

Obtains an [AudioRenderer](arkts-audio-audio-audiorenderer-i.md#AudioRenderer) instance. This method uses a promise to return the renderer instance. The AudioRenderer instance is used to play streaming audio data. When using AudioRenderer apis, there are many instructions for application to achieve better performance and lower power consumption: In music or audiobook background playback situation, you can have low power consumption by following this best practices document Low-Power Rules in Music Playback Scenarios. And for navigation situation, you can follow Low-Power Rules in Navigation and Positioning Scenarios. Application developer should also be careful when app goes to background, please check if your audio playback is still needed, see Audio Resources. And avoiding to send silence audio data continuously to waste system resources, otherwise system will take control measures when this behavior is detected, see Audio Playback. If you want to use AudioRenderer api to implement a music playback application, there are also many interactive scenes to consider, see Developing an Audio Application.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-audio-function createAudioRenderer(options: AudioRendererOptions, callback: AsyncCallback<AudioRenderer | null>): void--><!--Device-audio-function createAudioRenderer(options: AudioRendererOptions, callback: AsyncCallback<AudioRenderer | null>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AudioRendererOptions](arkts-audio-audio-audiorendereroptions-i.md) | 是 | Renderer configurations. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AudioRenderer](arkts-audio-audio-audiorenderer-i.md) \| null&gt; | 是 | Callback used to return the audio renderer instance, or null when an error happens. |


## createAudioRenderer

```TypeScript
function createAudioRenderer(options: AudioRendererOptions): Promise<AudioRenderer>
```

获取音频渲染器。使用Promise异步回调。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

<!--Device-audio-function createAudioRenderer(options: AudioRendererOptions): Promise<AudioRenderer>--><!--Device-audio-function createAudioRenderer(options: AudioRendererOptions): Promise<AudioRenderer>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AudioRendererOptions](arkts-audio-audio-audiorendereroptions-i.md) | 是 | 配置渲染器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioRenderer](arkts-audio-audio-audiorenderer-i.md)&gt; | Promise对象，返回音频渲染器对象。 |

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

let audioRendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // 音频流使用类型：音乐。根据业务场景配置，参考StreamUsage。
  rendererFlags: 0 // 音频渲染器标志。
};

let audioRendererOptions: audio.AudioRendererOptions = {
  streamInfo: audioStreamInfo,
  rendererInfo: audioRendererInfo
};

let audioRenderer: audio.AudioRenderer;

audio.createAudioRenderer(audioRendererOptions).then((data) => {
  audioRenderer = data;
  console.info('AudioFrameworkRenderLog: AudioRenderer Created : SUCCESS');
}).catch((err: BusinessError) => {
  console.error(`AudioFrameworkRenderLog: AudioRenderer Created : ERROR : ${err}`);
});
```


## createAudioRenderer

```TypeScript
function createAudioRenderer(options: AudioRendererOptions): Promise<AudioRenderer | null>
```

Obtains an [AudioRenderer](arkts-audio-audio-audiorenderer-i.md#AudioRenderer) instance. This method uses a promise to return the renderer instance. The AudioRenderer instance is used to play streaming audio data. When using AudioRenderer apis, there are many instructions for application to achieve better performance and lower power consumption: In music or audiobook background playback situation, you can have low power consumption by following this best practices document Low-Power Rules in Music Playback Scenarios. And for navigation situation, you can follow Low-Power Rules in Navigation and Positioning Scenarios. Application developer should also be careful when app goes to background, please check if your audio playback is still needed, see Audio Resources. And avoiding to send silence audio data continuously to waste system resources, otherwise system will take control measures when this behavior is detected, see Audio Playback. If you want to use AudioRenderer api to implement a music playback application, there are also many interactive scenes to consider, see Developing an Audio Application.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-audio-function createAudioRenderer(options: AudioRendererOptions): Promise<AudioRenderer | null>--><!--Device-audio-function createAudioRenderer(options: AudioRendererOptions): Promise<AudioRenderer | null>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AudioRendererOptions](arkts-audio-audio-audiorendereroptions-i.md) | 是 | Renderer configurations. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioRenderer](arkts-audio-audio-audiorenderer-i.md) \| null&gt; | Promise used to return the audio renderer instance, or null when an error happens. |

