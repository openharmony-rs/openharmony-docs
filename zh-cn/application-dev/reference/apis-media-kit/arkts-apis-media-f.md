# Functions
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @wang-haizhou6-->
<!--Designer: @HmQQQ-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { media } from '@kit.MediaKit';
```

## media.createAVPlayer<sup>9+</sup>

ArkTS-Dyn: createAVPlayer(callback: AsyncCallback\<AVPlayer>): void

ArkTS-Sta: createAVPlayer(callback: AsyncCallback\<AVPlayer | undefined>): void

创建音视频播放实例。使用callback异步回调。

> **说明：**
>
> - 推荐单个应用创建的音视频播放实例（即音频、视频、音视频三类相加）不超过16个。<!--Del-->
> - 可创建的音视频播放实例数量依赖于设备芯片的支持情况，如芯片支持创建的数量少于上述情况，请以芯片规格为准。如RK3568推荐单个应用创建6个以内的音视频播放实例。<!--DelEnd-->
> - 应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，否则在一定情况下可能导致系统终止应用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                  | 必填 | 说明                                                         |
| -------- | ------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | ArkTS-Dyn: AsyncCallback\<[AVPlayer](arkts-apis-media-AVPlayer.md)><br>ArkTS-Sta: AsyncCallback\<[AVPlayer](arkts-apis-media-AVPlayer.md) \| undefined> | 是   | 回调函数。异步返回AVPlayer实例，失败时返回null。可用于音视频播放。 |

**错误码：**

以下错误码的详细介绍请参见[Media错误码](errorcode-media.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 5400101  | No memory. Return by callback. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let avPlayer: media.AVPlayer;
media.createAVPlayer((error: BusinessError, video: media.AVPlayer) => {
  if (video) {
    avPlayer = video;
    console.info('Succeeded in creating AVPlayer');
  } else {
    console.error(`Failed to create AVPlayer, error message:${error.message}`);
  }
});
```

## media.createAVPlayer<sup>9+</sup>

ArkTS-Dyn: createAVPlayer(): Promise\<AVPlayer>

ArkTS-Sta: createAVPlayer(): Promise\<AVPlayer | undefined>

异步方式创建音视频播放实例。使用Promise异步回调。

> **说明：**
>
> - 推荐单个应用创建的音视频播放实例（即音频、视频、音视频三类相加）不超过16个。<!--Del-->
> - 可创建的音视频播放实例数量依赖于设备芯片的支持情况，如芯片支持创建的数量少于上述情况，请以芯片规格为准。如RK3568推荐单个应用创建6个以内的音视频播放实例。<!--DelEnd-->
> - 应用需要按照实际业务需求合理使用AVPlayer对象，按需创建并及时释放，避免持有过多AVPlayer实例导致内存消耗过大，导致系统终止应用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| ArkTS-Dyn: Promise\<[AVPlayer](arkts-apis-media-AVPlayer.md)><br>ArkTS-Sta: Promise\<[AVPlayer](arkts-apis-media-AVPlayer.md) \| undefined> | Promise对象。成功时异步返回AVPlayer实例，可用于音视频播放。失败时返回null。 |

**错误码：**

以下错误码的详细介绍请参见[Media错误码](errorcode-media.md)。

| 错误码ID | 错误信息                      |
| -------- | ----------------------------- |
| 5400101  | No memory. Return by promise. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let avPlayer: media.AVPlayer;
media.createAVPlayer().then((video: media.AVPlayer) => {
  if (video) {
    avPlayer = video;
    console.info('Succeeded in creating AVPlayer');
  } else {
    console.error('Failed to create AVPlayer');
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to create AVPlayer, error message:${error.message}`);
});
```

## media.createAVRecorder<sup>9+</sup>

ArkTS-Dyn: createAVRecorder(callback: AsyncCallback\<AVRecorder>): void

ArkTS-Sta: createAVRecorder(callback: AsyncCallback\<AVRecorder | undefined>): void

创建音视频录制实例。使用callback异步回调。

> **说明：**
>
> 应用可创建多个音视频录制实例，但由于设备共用音频通路，一个设备仅能有一个实例进行音频录制。创建第二个实例录制音频时，将会因为音频通路冲突导致创建失败。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                       | 必填 | 说明                                                         |
| -------- | ------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | ArkTS-Dyn: AsyncCallback\<[AVRecorder](arkts-apis-media-AVRecorder.md)><br>ArkTS-Sta: AsyncCallback\<[AVRecorder](arkts-apis-media-AVRecorder.md) \| undefined> | 是   | 回调函数，返回AVRecorder实例，可用于录制音视频媒体。失败时返回null。 |

**错误码：**

以下错误码的详细介绍请参见[Media错误码](errorcode-media.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 5400101  | No memory. Return by callback. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
let avRecorder: media.AVRecorder;

media.createAVRecorder((error: BusinessError, recorder: media.AVRecorder) => {
  if (recorder) {
    avRecorder = recorder;
    console.info('Succeeded in creating AVRecorder');
  } else {
    console.error(`Failed to create AVRecorder, error message:${error.message}`);
  }
});
```

## media.createAVRecorder<sup>9+</sup>

ArkTS-Dyn: createAVRecorder(): Promise\<AVRecorder>

ArkTS-Sta: createAVRecorder(): Promise\<AVRecorder | undefined>

创建音视频录制实例。使用Promise异步回调。

> **说明：**
>
> 应用可创建多个音视频录制实例，但由于设备共用音频通路，一个设备仅能有一个实例进行音频录制。创建第二个实例录制音频时，将会因为音频通路冲突导致创建失败。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                 | 说明                                                         |
| ------------------------------------ | ------------------------------------------------------------ |
| ArkTS-Dyn: Promise\<[AVRecorder](arkts-apis-media-AVRecorder.md)><br>ArkTS-Sta: Promise\<[AVRecorder](arkts-apis-media-AVRecorder.md) \| undefined> | Promise对象，返回AVRecorder实例，可用于录制音视频媒体。失败时返回null。 |

**错误码：**

以下错误码的详细介绍请参见[Media错误码](errorcode-media.md)。

| 错误码ID | 错误信息                      |
| -------- | ----------------------------- |
| 5400101  | No memory. Return by promise. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
let avRecorder: media.AVRecorder;
media.createAVRecorder().then((recorder: media.AVRecorder) => {
  if (recorder) {
    avRecorder = recorder;
    console.info('Succeeded in creating AVRecorder');
  } else {
    console.error('Failed to create AVRecorder');
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to create AVRecorder, error message:${error.message}`);
});
```

## media.createAVTranscoder<sup>12+</sup>

ArkTS-Dyn: createAVTranscoder(): Promise\<AVTranscoder>

ArkTS-Sta: createAVTranscoder(): Promise\<AVTranscoder | undefined>

创建视频转码实例。使用Promise异步回调。

> **说明：**
>
> 可创建的视频转码实例不能超过2个。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| ArkTS-Dyn: Promise\<[AVTranscoder](arkts-apis-media-AVTranscoder.md)><br>ArkTS-Sta: Promise\<[AVTranscoder](arkts-apis-media-AVTranscoder.md) \| undefined> | Promise对象。异步返回AVTranscoder实例，失败时返回null。可用于视频转码。 |

**错误码：**

以下错误码的详细介绍请参见[Media错误码](errorcode-media.md)。

| 错误码ID | 错误信息                      |
| -------- | ----------------------------- |
| 5400101  | No memory. Return by promise. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let avTranscoder: media.AVTranscoder | undefined = undefined;
media.createAVTranscoder().then((transcoder: media.AVTranscoder) => {
  if (transcoder) {
    avTranscoder = transcoder;
    console.info('Succeeded in creating AVTranscoder');
  } else {
    console.error('Failed to create AVTranscoder');
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to create AVTranscoder, error message:${error.message}`);
});
```

## media.createAVMetadataExtractor<sup>11+</sup>

ArkTS-Dyn: createAVMetadataExtractor(callback: AsyncCallback\<AVMetadataExtractor>): void

ArkTS-Sta: createAVMetadataExtractor(callback: AsyncCallback\<AVMetadataExtractor | undefined>): void

创建AVMetadataExtractor实例。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                  | 必填 | 说明                                                         |
| -------- | ------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | ArkTS-Dyn: AsyncCallback\<[AVMetadataExtractor](arkts-apis-media-AVMetadataExtractor.md)><br>ArkTS-Sta: AsyncCallback\<[AVMetadataExtractor](arkts-apis-media-AVMetadataExtractor.md) \| undefined> | 是   | 回调函数。当创建AVMetadataExtractor实例成功，err为undefined，data为获取到的AVMetadataExtractor实例，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[Media错误码](errorcode-media.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 5400101  | No memory. Returned by callback. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let avMetadataExtractor: media.AVMetadataExtractor;
media.createAVMetadataExtractor((error: BusinessError, extractor: media.AVMetadataExtractor) => {
  if (extractor) {
    avMetadataExtractor = extractor;
    console.info('Succeeded in creating AVMetadataExtractor');
  } else {
    console.error(`Failed to create AVMetadataExtractor, error message:${error.message}`);
  }
});
```

## media.createAVMetadataExtractor<sup>11+</sup>

ArkTS-Dyn: createAVMetadataExtractor(): Promise\<AVMetadataExtractor>

ArkTS-Sta: createAVMetadataExtractor(): Promise\<AVMetadataExtractor | undefined>

创建AVMetadataExtractor实例。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明                                     |
| -------------- | ---------------------------------------- |
| ArkTS-Dyn: Promise\<[AVMetadataExtractor](arkts-apis-media-AVMetadataExtractor.md)><br>ArkTS-Sta: Promise\<[AVMetadataExtractor](arkts-apis-media-AVMetadataExtractor.md) \| undefined>  | Promise对象。异步返回元数据获取类对象（AVMetadataExtractor）。 |

**错误码：**

以下错误码的详细介绍请参见[Media错误码](errorcode-media.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 5400101  | No memory. Returned by promise. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let avMetadataExtractor: media.AVMetadataExtractor;
media.createAVMetadataExtractor().then((extractor: media.AVMetadataExtractor) => {
  if (extractor) {
    avMetadataExtractor = extractor;
    console.info('Succeeded in creating AVMetadataExtractor');
  } else {
    console.error(`Failed to create AVMetadataExtractor`);
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to create AVMetadataExtractor, error message:${error.message}`);
});
```

## media.createSoundPool<sup>10+</sup>

ArkTS-Dyn: createSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo, callback: AsyncCallback\<SoundPool>): void

ArkTS-Sta: createSoundPool(maxStreams: int, audioRenderInfo: audio.AudioRendererInfo, callback: AsyncCallback\<SoundPool | undefined>): void

创建音频池实例。使用callback异步回调。

> **说明：**
>
> - API version 18以下版本，创建的SoundPool对象底层为单实例模式，一个应用进程只能够创建1个SoundPool实例。
> - API version 18及API version 18以上版本，创建的SoundPool对象底层为多实例模式，一个应用进程最多能够创建128个SoundPool实例。

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                            | 必填 | 说明                                                         |
| -------- | ----------------------------------------------- | ---- | ------------------------------------------------------------ |
| maxStreams | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | soundPool实例的最大播放的流数，设置范围为1-32的正整数。 |
| audioRenderInfo | [audio.AudioRendererInfo](../apis-audio-kit/arkts-apis-audio-i.md#audiorendererinfo8)  | 是   | 音频播放参数信息。其中audioRenderInfo中的参数usage取值为STREAM_USAGE_UNKNOWN，STREAM_USAGE_MUSIC，STREAM_USAGE_MOVIE，STREAM_USAGE_AUDIOBOOK时，SoundPool播放短音时为混音模式，不会打断其他音频播放。SoundPool支持将rendererFlags设置为1用于低时延通路播放。 |
| callback | ArkTS-Dyn: AsyncCallback<[SoundPool](js-apis-inner-multimedia-soundPool.md)><br>ArkTS-Sta: AsyncCallback<[SoundPool](js-apis-inner-multimedia-soundPool.md) \| undefined> | 是   | 回调函数。异步返回SoundPool实例，失败时返回null。用于音频池实例的加载播放功能。 |

**错误码：**

以下错误码的详细介绍请参见[Media错误码](errorcode-media.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 5400101  | No memory. Return by callback. |

**示例：**

```js
import { audio } from '@kit.AudioKit';

let soundPool: media.SoundPool;
let audioRendererInfo: audio.AudioRendererInfo = {
  usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
  rendererFlags : 0
};

media.createSoundPool(5, audioRendererInfo, (error, soundPool_: media.SoundPool) => {
  if (error) {
    console.error(`Failed to createSoundPool`);
    return;
  } else {
    soundPool = soundPool_;
    console.info(`Succeeded in createSoundPool`);
  }
});
```

## media.createSoundPool<sup>10+</sup>

ArkTS-Dyn: createSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo): Promise\<SoundPool>

ArkTS-Sta: createSoundPool(maxStreams: int, audioRenderInfo: audio.AudioRendererInfo): Promise\<SoundPool | undefined>

创建音频池实例。使用Promise异步回调。

> **说明：**
>
> - API version 18以下版本，创建的SoundPool对象底层为单实例模式，一个应用进程只能够创建1个SoundPool实例。
> - API version 18及API version 18以上版本，创建的SoundPool对象底层为多实例模式，一个应用进程最多能够创建128个SoundPool实例。

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                            | 必填 | 说明                                                         |
| -------- | ----------------------------------------------- | ---- | ------------------------------------------------------------ |
| maxStreams | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | soundPool实例的最大播放的流数，设置范围为1-32的正整数。 |
| audioRenderInfo | [audio.AudioRendererInfo](../apis-audio-kit/arkts-apis-audio-i.md#audiorendererinfo8)  | 是   | 音频播放参数信息 |

**返回值：**

| 类型                                      | 说明                                                         |
| ----------------------------------------- | ------------------------------------------------------------ |
| ArkTS-Dyn: Promise<[SoundPool](js-apis-inner-multimedia-soundPool.md)><br>ArkTS-Sta: Promise<[SoundPool](js-apis-inner-multimedia-soundPool.md) \| undefined> | Promise对象。异步返回SoundPool实例，失败时返回null。用于音频池实例的加载播放功能。 |

**错误码：**

以下错误码的详细介绍请参见[Media错误码](errorcode-media.md)。

| 错误码ID | 错误信息                      |
| -------- | ----------------------------- |
| 5400101  | No memory. Return by promise. |

**示例：**

```js
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let soundPool: media.SoundPool;
let audioRendererInfo: audio.AudioRendererInfo = {
  usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
  rendererFlags : 0
};

media.createSoundPool(5, audioRendererInfo).then((soundpool_: media.SoundPool) => {
  if (soundpool_) {
    soundPool = soundpool_;
    console.info('Succeeded in creating SoundPool');
  } else {
    console.error('Failed to create SoundPool');
  }
}, (error: BusinessError) => {
  console.error(`soundpool catchCallback, error message:${error.message}`);
});
```

## media.createAVScreenCaptureRecorder<sup>12+</sup>

ArkTS-Dyn: createAVScreenCaptureRecorder(): Promise\<AVScreenCaptureRecorder>

ArkTS-Sta: createAVScreenCaptureRecorder(): Promise\<AVScreenCaptureRecorder | undefined>

创建屏幕录制实例，使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ArkTS-Dyn: Promise\<[AVScreenCaptureRecorder](arkts-apis-media-AVScreenCaptureRecorder.md)><br>ArkTS-Sta: Promise\<[AVScreenCaptureRecorder](arkts-apis-media-AVScreenCaptureRecorder.md) \| undefined> | Promise对象，返回AVScreenCaptureRecorder实例，失败时返回null。可用于进行屏幕录制。 |

**错误码：**

以下错误码的详细介绍请参见[Media错误码](errorcode-media.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 5400101  | No memory. Return by promise. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let avScreenCaptureRecorder: media.AVScreenCaptureRecorder;
media.createAVScreenCaptureRecorder().then((captureRecorder: media.AVScreenCaptureRecorder) => {
  if (captureRecorder) {
    avScreenCaptureRecorder = captureRecorder;
    console.info('Succeeded in createAVScreenCaptureRecorder');
  } else {
    console.error('Failed to createAVScreenCaptureRecorder');
  }
}).catch((error: BusinessError) => {
  console.error(`createAVScreenCaptureRecorder catchCallback, error message:${error.message}`);
});
```

## media.createAVImageGenerator<sup>12+</sup>

ArkTS-Dyn: createAVImageGenerator(callback: AsyncCallback\<AVImageGenerator>): void

ArkTS-Sta: createAVImageGenerator(callback: AsyncCallback\<AVImageGenerator | undefined>): void

创建AVImageGenerator实例。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                  | 必填 | 说明                                                         |
| -------- | ------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | ArkTS-Dyn: AsyncCallback\<[AVImageGenerator](arkts-apis-media-AVImageGenerator.md)><br>ArkTS-Sta: AsyncCallback\<[AVImageGenerator](arkts-apis-media-AVImageGenerator.md) \| undefined> | 是   | 回调函数。异步返回AVImageGenerator实例，失败时返回null。可用于获取视频缩略图。 |

**错误码：**

以下错误码的详细介绍请参见[Media错误码](errorcode-media.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 5400101  | No memory. Returned by callback. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let avImageGenerator: media.AVImageGenerator;
media.createAVImageGenerator((error: BusinessError, generator: media.AVImageGenerator) => {
  if (generator) {
    avImageGenerator = generator;
    console.info('Succeeded in creating AVImageGenerator');
  } else {
    console.error(`Failed to create AVImageGenerator, error message:${error.message}`);
  }
});
```

## media.createAVImageGenerator<sup>12+</sup>

ArkTS-Dyn: createAVImageGenerator(): Promise\<AVImageGenerator>

ArkTS-Sta: createAVImageGenerator(): Promise\<AVImageGenerator | undefined>

创建AVImageGenerator对象。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| ArkTS-Dyn: Promise\<[AVImageGenerator](arkts-apis-media-AVImageGenerator.md)><br>ArkTS-Sta: Promise\<[AVImageGenerator](arkts-apis-media-AVImageGenerator.md) \| undefined> | Promise对象。异步返回AVImageGenerator实例，失败时返回null。可用于获取视频缩略图。 |

**错误码：**

以下错误码的详细介绍请参见[Media错误码](errorcode-media.md)。

| 错误码ID | 错误信息                      |
| -------- | ----------------------------- |
| 5400101  | No memory. Returned by promise. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let avImageGenerator: media.AVImageGenerator;
media.createAVImageGenerator().then((generator: media.AVImageGenerator) => {
  if (generator) {
    avImageGenerator = generator;
    console.info('Succeeded in creating AVImageGenerator');
  } else {
    console.error('Failed to create AVImageGenerator');
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to create AVImageGenerator, error message:${error.message}`);
});
```

## media.createMediaSourceWithUrl<sup>12+</sup>

ArkTS-Dyn: createMediaSourceWithUrl(url: string, headers?: Record\<string, string>): MediaSource

ArkTS-Sta: createMediaSourceWithUrl(url: string, headers?: Record\<string, string>): MediaSource | undefined

创建流媒体预下载媒体来源实例方法。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型     | 必填 | 说明                 |
| -------- | -------- | ---- | -------------------- |
| url | string | 是   | - 流媒体预下载媒体来源url，支持的流媒体格式：HLS、HTTP-FLV、Dash、Https。<br> - 本地m3u8的fd路径。  |
| headers | Record\<string, string> | 否   | 支持流媒体预下载HttpHeader自定义。不传时为网络请求默认的HttpHeader。 |

**返回值：**

| 类型           | 说明                                       |
| -------------- | ------------------------------------------ |
| ArkTS-Dyn: [MediaSource](arkts-apis-media-MediaSource.md)<br>ArkTS-Sta: [MediaSource](arkts-apis-media-MediaSource.md) \| undefined | MediaSource返回值。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Media错误码](errorcode-media.md)。

| 错误码ID | 错误信息                                  |
| -------- | ----------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      |
| 5400101  | No memory.  |

**示例1：**

```ts
let headers: Record<string, string> = {"User-Agent" : "User-Agent-Value"};
let mediaSource : media.MediaSource = media.createMediaSourceWithUrl("http://xxx",  headers);
```

**示例2：**

<!--code_no_check-->
```ts
import { media } from "@kit.MediaKit";

async function test(context: Context){
    // this.getUIContext().getHostContext();
    let mgr = context?.resourceManager;
    if (!mgr) {
        return;
    }
    let fileDescriptor = await mgr.getRawFd("xxx.m3u8");

    let fd: string = fileDescriptor.fd.toString();
    let offset: string = fileDescriptor.offset.toString();
    let length: string = fileDescriptor.length.toString();
    let fdUrl: string = "fd://" + fd + "?offset=" + offset + "&size=" + length;

    let mediaSource: media.MediaSource = media.createMediaSourceWithUrl(fdUrl);
}

```

## media.createMediaSourceWithStreamData<sup>19+</sup>

ArkTS-Dyn: createMediaSourceWithStreamData(streams: Array\<MediaStream>): MediaSource

ArkTS-Sta: createMediaSourceWithStreamData(streams: Array\<MediaStream>): MediaSource | undefined

创建流媒体多码率媒体来源实例方法，当前仅支持HTTP-FLV协议格式多码率。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                 | 必填 | 说明                                                  |
| ------- | ------------------------------------ | ---- | ----------------------------------------------------- |
| streams | Array<[MediaStream](arkts-apis-media-i.md#mediastream19)> | 是 | 可设置MediaStream数组，支持的流媒体格式：HTTP-FLV。 |

**返回值：**

| 类型                          | 说明                |
| ----------------------------- | ------------------- |
| ArkTS-Dyn: [MediaSource](arkts-apis-media-MediaSource.md)<br>ArkTS-Sta: [MediaSource](arkts-apis-media-MediaSource.md) \| undefined | 返回MediaSource，用于媒体资源设置。 |

**示例：**

```ts
let streams : Array<media.MediaStream> = [];
streams.push({url: "http://xxx/480p.flv", width: 854, height: 480, bitrate: 800000});
streams.push({url: "http://xxx/720p.flv", width: 1280, height: 720, bitrate: 2000000});
streams.push({url: "http://xxx/1080p.flv", width: 1920, height: 1080, bitrate: 2000000});
let mediaSource : media.MediaSource = media.createMediaSourceWithStreamData(streams);
```

## media.createMediaSourceWithFd

createMediaSourceWithFd(fdSrc: AVFileDescriptor): MediaSource | undefined

通过文件描述符创建媒体源。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名  | 类型                                 | 必填 | 说明                                                  |
| ------- | ------------------------------------ | ---- | ----------------------------------------------------- |
| fdSrc | [AVFileDescriptor](arkts-apis-media-i.md#avfiledescriptor9) | 是 | 媒体文件描述符。 |

**返回值：**

| 类型                          | 说明                |
| ----------------------------- | ------------------- |
| [MediaSource](arkts-apis-media-MediaSource.md) \| undefined | 返回MediaSource，用于媒体资源设置。 |

**示例：**

```ts
import { common } from '@kit.AbilityKit';

let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let fdSrc = await context.resourceManager.getRawFd('xxx.mp4');
let mediaSource : media.MediaSource | undefined = media.createMediaSourceWithFd(fdSrc);
```

## media.createMediaSourceWithDataSource

createMediaSourceWithDataSource(dataSrc: AVDataSrcDescriptor): MediaSource | undefined

通过自定义数据源创建媒体源。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名  | 类型                                 | 必填 | 说明                                                  |
| ------- | ------------------------------------ | ---- | ----------------------------------------------------- |
| dataSrc | [AVDataSrcDescriptor](arkts-apis-media-i.md#avdatasrcdescriptor10) | 是 | 流式媒体资源描述符。 |

**返回值：**

| 类型                          | 说明                |
| ----------------------------- | ------------------- |
| [MediaSource](arkts-apis-media-MediaSource.md) \| undefined | 返回MediaSource，用于媒体资源设置。 |

**示例：**

```ts
import { common } from '@kit.AbilityKit';
import { fileIo as fs, ReadOptions } from '@kit.CoreFileKit';

let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let fileDescriptor = await context.resourceManager.getRawFd('xxx.mp4');
let file = fs.openSync("xxx.mp4");
let dataSrc: media.AVDataSrcDescriptor = {
  fileSize: fileDescriptor.length,
  callback: (buf: ArrayBuffer, length: number, pos?: number) => {
    let readLen = 0;
    if (pos) {
      let option: ReadOptions = {
        offset: pos,
        length: length,
      };
      readLen = fs.readSync(file.fd, buf, option);
    }
    return readLen > 0 ? readLen : -1;
  }
}
let mediaSource : media.MediaSource | undefined = media.createMediaSourceWithDataSource(dataSrc);
```

## media.createAudioPlayer<sup>(deprecated)</sup>

createAudioPlayer(): AudioPlayer

同步方式创建音频播放实例。

> **说明：**
> 从API version 6开始支持，从API version 9开始废弃，建议使用[createAVPlayer](#mediacreateavplayer9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**ArkTS-Dyn起始版本：** 6

**返回值：**

| 类型                        | 说明                                                         |
| --------------------------- | ------------------------------------------------------------ |
| [AudioPlayer](arkts-apis-media-AudioPlayer.md) | 返回AudioPlayer类实例，失败时返回null。可用于音频播放、暂停、停止等操作。 |

**示例：**

```ts
let audioPlayer: media.AudioPlayer = media.createAudioPlayer();
```

## media.createVideoPlayer<sup>(deprecated)</sup>

createVideoPlayer(callback: AsyncCallback\<VideoPlayer>): void

异步方式创建视频播放实例，使用callback异步回调。

> **说明：**
> 从API version 8开始支持，从API version 9开始废弃，建议使用[createAVPlayer](#mediacreateavplayer9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名   | 类型                                       | 必填 | 说明                                                         |
| -------- | ------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback<[VideoPlayer](arkts-apis-media-VideoPlayer.md)> | 是   | 回调函数。创建VideoPlayer实例成功时，err为undefined，data为获取到的VideoPlayer实例，否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let videoPlayer: media.VideoPlayer;
media.createVideoPlayer((error: BusinessError, video: media.VideoPlayer) => {
  if (video) {
    videoPlayer = video;
    console.info('Succeeded in creating VideoPlayer');
  } else {
    console.error(`Failed to create VideoPlayer, error:${error}`);
  }
});
```

## media.createVideoPlayer<sup>(deprecated)</sup>

createVideoPlayer(): Promise\<VideoPlayer>

异步方式创建视频播放实例，通过Promise获取返回值。

> **说明：**
> 从API version 8开始支持，从API version 9开始废弃，建议使用[createAVPlayer](#mediacreateavplayer9-1)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Multimedia.Media.VideoPlayer

**ArkTS-Dyn起始版本：** 8

**返回值：**

| 类型                                 | 说明                                                         |
| ------------------------------------ | ------------------------------------------------------------ |
| Promise<[VideoPlayer](arkts-apis-media-VideoPlayer.md)> | Promise对象。异步返回VideoPlayer实例，失败时返回null。可用于管理和播放视频媒体。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let videoPlayer: media.VideoPlayer;
media.createVideoPlayer().then((video: media.VideoPlayer) => {
  if (video) {
    videoPlayer = video;
    console.info('Succeeded in creating VideoPlayer');
  } else {
    console.error('Failed to create VideoPlayer');
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to create VideoPlayer, error:${error}`);
});
```

## media.createAudioRecorder<sup>(deprecated)</sup>

createAudioRecorder(): AudioRecorder

创建音频录制的实例来控制音频的录制。一台设备只允许创建一个录制实例。

> **说明：**
> 从API version 6开始支持，从API version 9开始废弃，建议使用[createAVRecorder](#mediacreateavrecorder9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

**ArkTS-Dyn起始版本：** 6

**返回值:**

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| [AudioRecorder](arkts-apis-media-AudioRecorder.md) | 返回AudioRecorder类实例，失败时返回null。可用于录制音频媒体。 |

**示例：**

```ts
let audioRecorder: media.AudioRecorder = media.createAudioRecorder();
```

