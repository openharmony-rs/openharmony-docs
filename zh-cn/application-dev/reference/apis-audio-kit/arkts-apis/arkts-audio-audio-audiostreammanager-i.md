# AudioStreamManager

音频流管理。 在使用AudioStreamManager的接口之前，需先通过[getStreamManager](arkts-audio-audio-audiomanager-i.md#getstreammanager) 获取AudioStreamManager实例。

> **说明：**

> - 本Interface首批接口从API version 9开始支持。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Core

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getAudioEffectInfoArray

```TypeScript
getAudioEffectInfoArray(usage: StreamUsage, callback: AsyncCallback<AudioEffectInfoArray>): void
```

获取当前音效模式的信息。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| usage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | 是 | 音频流使用类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AudioEffectInfoArray](arkts-audio-audio-audioeffectinfoarray-t.md)&gt; | 是 | 回调函数。当获取当前音效模式的信息成功，err为undefined，data为获取到的当前音效模式的信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getAudioEffectInfoArray(audio.StreamUsage.STREAM_USAGE_MUSIC, (err: BusinessError, audioEffectInfoArray: audio.AudioEffectInfoArray) => {
  if (err) {
    console.error(`Failed to obtain the audio effect info array. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the audio effect info array, audioEffectInfoArray: ${JSON.stringify(audioEffectInfoArray)}.`);
});
```

## getAudioEffectInfoArray

```TypeScript
getAudioEffectInfoArray(usage: StreamUsage): Promise<AudioEffectInfoArray>
```

获取当前音效模式的信息。使用Promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| usage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | 是 | 音频流使用类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioEffectInfoArray](arkts-audio-audio-audioeffectinfoarray-t.md)&gt; | Promise对象，返回当前音效模式的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getAudioEffectInfoArray(audio.StreamUsage.STREAM_USAGE_MUSIC).then((audioEffectInfoArray: audio.AudioEffectInfoArray) => {
  console.info(`Succeeded in obtaining the audio effect info array, audioEffectInfoArray: ${JSON.stringify(audioEffectInfoArray)}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the audio effect info array. Code: ${err.code}, message: ${err.message}`);
});
```

## getAudioEffectInfoArraySync

```TypeScript
getAudioEffectInfoArraySync(usage: StreamUsage): AudioEffectInfoArray
```

获取当前音效模式的信息。同步返回结果。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| usage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | 是 | 音频流使用类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioEffectInfoArray](arkts-audio-audio-audioeffectinfoarray-t.md) | 返回当前音效模式的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioEffectInfoArray = audioStreamManager.getAudioEffectInfoArraySync(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in obtaining the audio effect info array, audioEffectInfoArray: ${JSON.stringify(audioEffectInfoArray)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the audio effect info array. Code: ${error.code}, message: ${error.message}`);
}
```

## getCurrentAudioCapturerInfoArray

```TypeScript
getCurrentAudioCapturerInfoArray(callback: AsyncCallback<AudioCapturerChangeInfoArray>): void
```

获取当前音频采集器的信息。使用callback异步回调。

> **说明：**
> 
> 该接口返回的音频采集器信息，可能包含系统内部音频录制流，如语音唤醒、蜂窝通话等。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AudioCapturerChangeInfoArray](arkts-audio-audio-audiocapturerchangeinfoarray-t.md)&gt; | 是 | 回调函数。当获取当前音频采集器的信息成功，err为undefined，data为获取到的当前音频采集器的信息 ；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getCurrentAudioCapturerInfoArray((err: BusinessError, audioCapturerChangeInfoArray: audio.AudioCapturerChangeInfoArray) => {
  if (err) {
    console.error(`Failed to obtain current audio capturer info array. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining current audio capturer info array, audioCapturerChangeInfoArray: ${JSON.stringify(audioCapturerChangeInfoArray)}.`);
});
```

## getCurrentAudioCapturerInfoArray

```TypeScript
getCurrentAudioCapturerInfoArray(): Promise<AudioCapturerChangeInfoArray>
```

获取当前音频采集器的信息。使用Promise异步回调。

> **说明：**
> 
> 该接口返回的音频采集器信息，可能包含系统内部音频录制流，如语音唤醒、蜂窝通话等。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioCapturerChangeInfoArray](arkts-audio-audio-audiocapturerchangeinfoarray-t.md)&gt; | Promise对象，返回当前音频采集器信息。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getCurrentAudioCapturerInfoArray().then((audioCapturerChangeInfoArray: audio.AudioCapturerChangeInfoArray) => {
  console.info(`Succeeded in obtaining current audio capturer info array, audioCapturerChangeInfoArray: ${JSON.stringify(audioCapturerChangeInfoArray)}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain current audio capturer info array. Code: ${err.code}, message: ${err.message}`);
});
```

## getCurrentAudioCapturerInfoArraySync

```TypeScript
getCurrentAudioCapturerInfoArraySync(): AudioCapturerChangeInfoArray
```

获取当前音频采集器的信息。同步返回结果。

> **说明：**
> 
> 该接口返回的音频采集器信息，可能包含系统内部音频录制流，如语音唤醒、蜂窝通话等。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioCapturerChangeInfoArray](arkts-audio-audio-audiocapturerchangeinfoarray-t.md) | 返回当前音频采集器信息。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioCapturerChangeInfoArray = audioStreamManager.getCurrentAudioCapturerInfoArraySync();
  console.info(`Succeeded in obtaining current audio capturer info array, audioCapturerChangeInfoArray: ${JSON.stringify(audioCapturerChangeInfoArray)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain current audio capturer info array. Code: ${error.code}, message: ${error.message}`);
}
```

## getCurrentAudioRendererInfoArray

```TypeScript
getCurrentAudioRendererInfoArray(callback: AsyncCallback<AudioRendererChangeInfoArray>): void
```

获取当前音频渲染器的信息。使用callback异步回调。

> **说明：**
> 
> 该接口返回的音频渲染器信息，可能包含系统内部音频播放流，如蜂窝通话、超声波等。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AudioRendererChangeInfoArray](arkts-audio-audio-audiorendererchangeinfoarray-t.md)&gt; | 是 | 回调函数。当获取当前音频渲染器的信息成功，err为undefined，data为获取到的当前音频渲染器的信息 ；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getCurrentAudioRendererInfoArray((err: BusinessError, audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray) => {
  if (err) {
    console.error(`Failed to obtain current audio renderer info array. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining current audio renderer info array, audioRendererChangeInfoArray: ${JSON.stringify(audioRendererChangeInfoArray)}.`);
});
```

## getCurrentAudioRendererInfoArray

```TypeScript
getCurrentAudioRendererInfoArray(): Promise<AudioRendererChangeInfoArray>
```

获取当前音频渲染器的信息。使用Promise异步回调。

> **说明：**
> 
> 该接口返回的音频渲染器信息，可能包含系统内部音频播放流，如蜂窝通话、超声波等。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioRendererChangeInfoArray](arkts-audio-audio-audiorendererchangeinfoarray-t.md)&gt; | Promise对象，返回当前音频渲染器信息。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.getCurrentAudioRendererInfoArray().then((audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray) => {
  console.info(`Succeeded in obtaining current audio renderer info array, audioRendererChangeInfoArray: ${JSON.stringify(audioRendererChangeInfoArray)}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain current audio renderer info array. Code: ${err.code}, message: ${err.message}`);
});
```

## getCurrentAudioRendererInfoArraySync

```TypeScript
getCurrentAudioRendererInfoArraySync(): AudioRendererChangeInfoArray
```

获取当前音频渲染器的信息。同步返回结果。

> **说明：**
> 
> 该接口返回的音频渲染器信息，可能包含系统内部音频播放流，如蜂窝通话、超声波等。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioRendererChangeInfoArray](arkts-audio-audio-audiorendererchangeinfoarray-t.md) | 返回当前音频渲染器信息。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray = audioStreamManager.getCurrentAudioRendererInfoArraySync();
  console.info(`Succeeded in obtaining current audio renderer info array, audioRendererChangeInfoArray: ${JSON.stringify(audioRendererChangeInfoArray)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain current audio renderer info array. Code: ${error.code}, message: ${error.message}`);
}
```

## isAcousticEchoCancelerSupported

```TypeScript
isAcousticEchoCancelerSupported(sourceType: SourceType): boolean
```

查询指定的音源类型是否支持回声消除。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sourceType | SourceType | 是 | 音源类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持回声消除。true表示支持回声消除，false表示不支持回声消除。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isAcousticEchoCancelerSupported = audioStreamManager.isAcousticEchoCancelerSupported(audio.SourceType.SOURCE_TYPE_LIVE);
  console.info(`Succeeded in checking whether acoustic echo canceler is supported, isAcousticEchoCancelerSupported: ${isAcousticEchoCancelerSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether acoustic echo canceler is supported. Code: ${error.code}, message: ${error.message}`);
}
```

## isActive

```TypeScript
isActive(volumeType: AudioVolumeType, callback: AsyncCallback<boolean>): void
```

获取指定音频流活跃状态。使用callback异步回调。

> **说明：**
> 
> 从API version 9开始支持，从API version 20开始废弃，建议使用
> [isStreamActive](#isstreamactive)替代。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [isStreamActive](#isstreamactive)

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频流类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。当获取指定音频流活跃状态成功，err为undefined，data为true表示活跃，false表示不活跃；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.isActive(audio.AudioVolumeType.MEDIA, (err: BusinessError, value: boolean) => {
  if (err) {
    console.error(`Failed to check whether the stream is active. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in checking whether the stream is active, isActive: ${value}.`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.isActive(audio.AudioVolumeType.MEDIA, (err: BusinessError, value: boolean) => {
  if (err) {
    console.error(`Failed to check whether the stream is active. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in checking whether the stream is active, isActive: ${value}.`);
});
```

## isActive

```TypeScript
isActive(volumeType: AudioVolumeType): Promise<boolean>
```

获取指定音频流是否为活跃状态。使用Promise异步回调。

> **说明：**
> 
> 从API version 9开始支持，从API version 20开始废弃，建议使用
> [isStreamActive](#isstreamactive)替代。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [isStreamActive](#isstreamactive)

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频流类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;boolean&gt; | Promise对象。返回true表示流状态为活跃；返回false表示流状态不活跃。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.isActive(audio.AudioVolumeType.MEDIA).then((value: boolean) => {
  console.info(`Succeeded in checking whether the stream is active, isActive: ${value}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to check whether the stream is active. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioStreamManager.isActive(audio.AudioVolumeType.MEDIA).then((value: boolean) => {
  console.info(`Succeeded in checking whether the stream is active, isActive: ${value}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to check whether the stream is active. Code: ${err.code}, message: ${err.message}`);
});
```

## isActiveSync

```TypeScript
isActiveSync(volumeType: AudioVolumeType): boolean
```

获取指定音频流是否为活跃状态。同步返回结果。

> **说明：**
> 
> 从API version 10开始支持，从API version 20开始废弃，建议使用
> [isStreamActive](#isstreamactive)替代。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** [isStreamActive](#isstreamactive)

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频流类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 流的活跃状态。返回true表示活跃，返回false表示不活跃。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let value: boolean = audioStreamManager.isActiveSync(audio.AudioVolumeType.MEDIA);
  console.info(`Succeeded in checking whether the stream is active, isActive: ${value}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether the stream is active. Code: ${error.code}, message: ${error.message}`);
}
```

## isAudioLoopbackSupported

```TypeScript
isAudioLoopbackSupported(mode: AudioLoopbackMode): boolean
```

查询当前系统是否支持指定的音频返听模式。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AudioLoopbackMode](arkts-audio-audio-audioloopbackmode-e.md) | 是 | 音频返听模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持指定的音频返听模式。true表示支持，false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isAudioLoopbackSupported = audioStreamManager.isAudioLoopbackSupported(audio.AudioLoopbackMode.HARDWARE);
  console.info(`Succeeded in checking whether audio loopback is supported, isAudioLoopbackSupported: ${isAudioLoopbackSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether audio loopback is supported. Code: ${error.code}, message: ${error.message}`);
}
```

## isDirectPlaybackSupported

```TypeScript
isDirectPlaybackSupported(streamInfo: AudioStreamInfo, usage: StreamUsage): boolean
```

查询指定音频流信息和使用场景下是否支持直通播放。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamInfo | [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) | 是 | 音频流信息，用于描述基础音频格式。 |
| usage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | 是 | 音频流使用场景，用于决定音频设备和通路类型的选择结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持直通播放。true表示支持，false表示不支持。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let streamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_2,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW,
  channelLayout: audio.AudioChannelLayout.CH_LAYOUT_STEREO
};

try {
  let isSupported = audioStreamManager.isDirectPlaybackSupported(streamInfo, audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in checking whether direct playback is supported, isDirectPlaybackSupported: ${isSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether direct playback is supported. Code: ${error.code}, message: ${error.message}`);
}
```

## isFastPlaybackSupported

```TypeScript
isFastPlaybackSupported(streamInfo: AudioStreamInfo, usage: StreamUsage): boolean
```

查询指定音频流信息和使用场景下是否支持低时延播放。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamInfo | [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) | 是 | 音频流信息，用于描述基础音频格式。 |
| usage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | 是 | 音频流使用场景，用于决定音频设备和通路类型的选择结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持低时延播放。true表示支持，false表示不支持。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let streamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_2,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW,
  channelLayout: audio.AudioChannelLayout.CH_LAYOUT_STEREO
};

try {
  let isSupported = audioStreamManager.isFastPlaybackSupported(streamInfo, audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in checking whether fast playback is supported, isFastPlaybackSupported: ${isSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether fast playback is supported. Code: ${error.code}, message: ${error.message}`);
}
```

## isFastRecordingSupported

```TypeScript
isFastRecordingSupported(streamInfo: AudioStreamInfo, source: SourceType): boolean
```

查询指定音频流信息和音源类型下是否支持低时延录制。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamInfo | [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) | 是 | 音频流信息，用于描述基础音频格式。 |
| source | SourceType | 是 | 音源类型，用于决定音频设备和通路类型的选择结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持低时延录制。true表示支持，false表示不支持。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let streamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_2,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW,
  channelLayout: audio.AudioChannelLayout.CH_LAYOUT_STEREO
};

try {
  let isSupported = audioStreamManager.isFastRecordingSupported(streamInfo, audio.SourceType.SOURCE_TYPE_MIC);
  console.info(`Succeeded in checking whether fast recording is supported, isFastRecordingSupported: ${isSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether fast recording is supported. Code: ${error.code}, message: ${error.message}`);
}
```

## isIntelligentNoiseReductionEnabledForCurrentDevice

```TypeScript
isIntelligentNoiseReductionEnabledForCurrentDevice(sourceType: SourceType): boolean
```

查询指定的音源类型智能降噪开关是否打开。

**起始版本：** 21

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sourceType | SourceType | 是 | 表示音源类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 智能降噪开关的状态。true表示打开，false表示关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isSupport = audioStreamManager.isIntelligentNoiseReductionEnabledForCurrentDevice(audio.SourceType.SOURCE_TYPE_LIVE);
  console.info(`Succeeded in checking whether intelligent noise reduction is enabled for the current device, isIntelligentNoiseReductionEnabled: ${isSupport}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether intelligent noise reduction is enabled for the current device. Code: ${error.code}, message: ${error.message}`);
}
```

## isMultichannelPlaybackSupported

```TypeScript
isMultichannelPlaybackSupported(streamInfo: AudioStreamInfo, usage: StreamUsage): boolean
```

查询指定音频流信息和使用场景下是否支持多声道播放。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamInfo | [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) | 是 | 音频流信息，用于描述基础音频格式。 |
| usage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | 是 | 音频流使用场景，用于决定音频设备和通路类型的选择结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持多声道播放。true表示支持，false表示不支持。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let streamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_3,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW,
  channelLayout: audio.AudioChannelLayout.CH_LAYOUT_2POINT1
};

try {
  let isSupported = audioStreamManager.isMultichannelPlaybackSupported(streamInfo, audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in checking whether multichannel playback is supported, isMultichannelPlaybackSupported: ${isSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether multichannel playback is supported. Code: ${error.code}, message: ${error.message}`);
}
```

## isOffloadPlaybackSupported

```TypeScript
isOffloadPlaybackSupported(streamInfo: AudioStreamInfo, usage: StreamUsage): boolean
```

查询指定音频流信息和使用场景下是否支持低功耗通路播放。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamInfo | [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) | 是 | 音频流信息，用于描述基础音频格式。 |
| usage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | 是 | 音频流使用场景，用于决定音频设备和通路类型的选择结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持低功耗通路播放。true表示支持，false表示不支持。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let streamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_2,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW,
  channelLayout: audio.AudioChannelLayout.CH_LAYOUT_STEREO
};

try {
  let isSupported = audioStreamManager.isOffloadPlaybackSupported(streamInfo, audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in checking whether offload playback is supported, isOffloadPlaybackSupported: ${isSupported}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether offload playback is supported. Code: ${error.code}, message: ${error.message}`);
}
```

## isRecordingAvailable

```TypeScript
isRecordingAvailable(capturerInfo: AudioCapturerInfo): boolean
```

检查传入的音频采集器信息中音源类型的录制是否可以启动成功。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capturerInfo | [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md) | 是 | 音频采集器信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 代表录制是否可以启动成功。true表示成功，false表示失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

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

audio.createAudioCapturer(audioCapturerOptions, (err: BusinessError, audioCapturer: audio.AudioCapturer) => {
  if (err) {
    console.error(`Failed to create AudioCapturer. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in creating AudioCapturer.');
  try {
    let isRecordingAvailable = audioStreamManager.isRecordingAvailable(audioCapturerInfo);
    console.info(`Succeeded in checking whether recording is available, isRecordingAvailable: ${isRecordingAvailable}.`);
  } catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to check whether recording is available. Code: ${error.code}, message: ${error.message}`);
  }
});
```

## isStreamActive

```TypeScript
isStreamActive(streamUsage: StreamUsage): boolean
```

获取指定音频流是否为活跃状态。同步返回结果。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamUsage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | 是 | 音频流使用类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 流是否处于活跃状态。返回true表示活跃，返回false表示不活跃。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isStreamActive = audioStreamManager.isStreamActive(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in checking whether the stream is active, isStreamActive: ${isStreamActive}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether the stream is active. Code: ${error.code}, message: ${error.message}`);
}
```

## off('audioRendererChange')

```TypeScript
off(type: 'audioRendererChange', callback?: Callback<AudioRendererChangeInfoArray>): void
```

取消监听音频渲染器更改事件。使用callback异步回调。

> **说明：**
> 
> 该接口返回的音频渲染器信息，可能包含系统内部音频播放流，如蜂窝通话、超声波等。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioRendererChange' | 是 | 事件回调类型，支持的事件为'audioRendererChange'，当取消监听音频渲染器更改事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioRendererChangeInfoArray](arkts-audio-audio-audiorendererchangeinfoarray-t.md)&gt; | 否 | 回调函数，返回当前音频渲染器信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off('audioCapturerChange')

```TypeScript
off(type: 'audioCapturerChange', callback?: Callback<AudioCapturerChangeInfoArray>): void
```

取消监听音频采集器更改事件。使用callback异步回调。

> **说明：**
> 
> 该接口返回的音频采集器信息，可能包含系统内部音频录制流，如语音唤醒、蜂窝通话等。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioCapturerChange' | 是 | 事件回调类型，支持的事件为'audioCapturerChange'，当取消监听音频采集器更改事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioCapturerChangeInfoArray](arkts-audio-audio-audiocapturerchangeinfoarray-t.md)&gt; | 否 | 回调函数，返回当前音频采集器信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('audioRendererChange')

```TypeScript
on(type: 'audioRendererChange', callback: Callback<AudioRendererChangeInfoArray>): void
```

监听音频渲染器更改事件（当音频播放流状态变化或设备变化时触发）。使用callback异步回调。

> **说明：**
> 
> 该接口返回的音频渲染器信息，可能包含系统内部音频播放流，如蜂窝通话、超声波等。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioRendererChange' | 是 | 事件回调类型，支持的事件为'audioRendererChange'，当音频播放流状态变化或设备变化时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioRendererChangeInfoArray](arkts-audio-audio-audiorendererchangeinfoarray-t.md)&gt; | 是 | 回调函数，返回当前音频渲染器信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('audioCapturerChange')

```TypeScript
on(type: 'audioCapturerChange', callback: Callback<AudioCapturerChangeInfoArray>): void
```

监听音频采集器更改事件（当音频录制流状态变化或设备变化时触发）。使用callback异步回调。

> **说明：**
> 
> 该接口返回的音频采集器信息，可能包含系统内部音频录制流，如语音唤醒、蜂窝通话等。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioCapturerChange' | 是 | 事件回调类型，支持的事件为'audioCapturerChange'，当音频录制流状态变化或设备变化时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioCapturerChangeInfoArray](arkts-audio-audio-audiocapturerchangeinfoarray-t.md)&gt; | 是 | 回调函数，返回当前音频采集器信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
