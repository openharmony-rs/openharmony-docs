# @ohos.multimedia.media (媒体服务)(系统接口)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zzs_911-->
<!--Designer: @stupig001-->
<!--Tester: @xdlinc-->
<!--Adviser: @zengyawen-->

媒体子系统为开发者提供一套简单且易于理解的接口，使得开发者能够方便接入系统并使用系统的媒体资源。

> **说明：**
>
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.multimedia.media (媒体服务)](arkts-apis-media.md)。

## 导入模块

```ts
import { media } from '@kit.MediaKit';
```

## media.createVideoRecorder<sup>9+</sup>

createVideoRecorder(callback: AsyncCallback\<VideoRecorder>): void

异步方式创建视频录制实例。通过注册回调函数获取返回值。
一台设备只允许创建一个录制实例。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**参数：**

| 参数名   | 类型                                            | 必填 | 说明                                                         |
| -------- | ----------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback<[VideoRecorder](#videorecorder9)> | 是   | 回调函数。异步返回VideoRecorder实例，失败时返回null。可用于录制视频媒体。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 202  | Not system App. |
| 5400101  | No memory. Return by callback. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let videoRecorder: media.VideoRecorder;
media.createVideoRecorder((error: BusinessError, video: media.VideoRecorder) => {
  if (video != null) {
    videoRecorder = video;
    console.info('video createVideoRecorder success');
  } else {
    console.error(`video createVideoRecorder fail, error message:${error.message}`);
  }
});
```

## media.createVideoRecorder<sup>9+</sup>

createVideoRecorder(): Promise\<VideoRecorder>

异步方式创建视频录制实例。通过Promise获取返回值。
一台设备只允许创建一个录制实例。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**返回值：**

| 类型                                      | 说明                                                         |
| ----------------------------------------- | ------------------------------------------------------------ |
| Promise<[VideoRecorder](#videorecorder9)> | Promise对象。异步返回VideoRecorder实例，失败时返回null。可用于录制视频媒体。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                      |
| -------- | ----------------------------- |
| 5400101  | No memory. Return by promise. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let videoRecorder: media.VideoRecorder;
media.createVideoRecorder().then((video: media.VideoRecorder) => {
  if (video != null) {
    videoRecorder = video;
    console.info('video createVideoRecorder success');
  } else {
    console.error('video createVideoRecorder fail');
  }
}).catch((error: BusinessError) => {
  console.error(`video catchCallback, error message:${error.message}`);
});
```

## media.reportAVScreenCaptureUserChoice<sup>12+</sup>

reportAVScreenCaptureUserChoice(sessionId: number, choice: string): Promise\<void>

上报录屏隐私弹窗的选择结果到ScreenCapture的服务端，用于判断是否开始录屏。如果用户选择“不允许”则不进行录屏，如果用户选择“允许”则开始录屏。

此接口提供给创建弹窗的系统应用调用。

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 该接口为系统接口

**参数：**

| 参数名    | 类型   | 必填 | 说明                                                          |
| --------- | ------ | ---- | ------------------------------------------------------------ |
| sessionId | number | 是   | AVScreenCapture服务会话Id，会由AVScreenCapture拉起隐私弹窗时传给应用。 |
| choice    | string | 是   | 用户的选择内容，包含是否同意录屏、选择的屏幕Id和窗口Id等。可见示例中JsonData样例。|

**返回值：**

| 类型             | 说明                             |
| ---------------- | -------------------------------- |
| Promise\<void> | 异步返回函数执行结果。 |

**错误码：**

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 5400101  | No memory. Return by promise.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

class JsonData {
  public choice: string = 'true';
  public displayId: number | null = -1;
  public missionId: number | null = -1;
  public checkBoxSelected: string = 'true';
  public isInnerAudioBoxSelected: string = 'true';
}
let sessionId: number = 0; // 替换成拉起此进程的sessionId。

try {
  const jsonData: JsonData = {
    choice: 'true',  // 替换成用户的选择内容。
    displayId: -1,   // 替换成用户选择的屏幕Id。
    missionId: -1,   // 替换成用户选择的窗口Id。
    checkBoxSelected: 'true',   // 替换成用户是否开启屏幕保护。
    isInnerAudioBoxSelected: 'true',   // 替换成用户是否开启内部音频录制。
  }
  await media.reportAVScreenCaptureUserChoice(sessionId, JSON.stringify(jsonData));
} catch (error: BusinessError) {
  console.error(`reportAVScreenCaptureUserChoice error, error message: ${error.message}`);
}
```

## media.getAVScreenCaptureConfigurableParameters<sup>20+</sup>

getAVScreenCaptureConfigurableParameters(sessionId: number): Promise\<string>

从服务器获取用户可更改的系统隐私保护和应用隐私保护配置。使用Promise异步回调。

>**注意：**
>
> 此接口仅提供给创建弹窗的系统应用调用。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**参数：**

| 参数名    | 类型   | 必填 | 说明                                                          |
| --------- | ------ | ---- | ------------------------------------------------------------ |
| sessionId | number | 是   | AVScreenCapture服务会话Id，由AVScreenCapture拉起隐私弹窗时传给应用。 |

**返回值：**

| 类型             | 说明                             |
| ---------------- | -------------------------------- |
| Promise\<string> | Promise对象。可用于查询系统隐私保护和应用隐私保护状态。异步返回String对象，失败时返回空字符串。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体错误码](errorcode-media.md)。
| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 202      | Called from Non-System applications. Return by promise.               |
| 5400109  | Sessions not exist. Return by promise.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

let sessionId: number = 0; // 替换成拉起此进程的sessionId。

try {
  let privacyResult: string = await media.getAVScreenCaptureConfigurableParameters(sessionId);
} catch (error: BusinessError) {
  console.error(`getAVScreenCaptureConfigurableParameters error, error message: ${error.message}`);
}
```

## media.getScreenCaptureMonitor<sup>18+</sup>

getScreenCaptureMonitor(): Promise\<ScreenCaptureMonitor>

获取录屏监控模块实例。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 该接口为系统接口。

**返回值：**

| 类型                                      | 说明                                                         |
| ----------------------------------------- | ------------------------------------------------------------ |
| Promise<[ScreenCaptureMonitor](#screencapturemonitor18)> | Promise对象。可用于查询和监听系统录屏状态。<br>异步返回ScreenCaptureMonitor实例，失败时返回null。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[媒体错误码](errorcode-media.md)。

| 错误码ID | 错误信息                      |
| -------- | ----------------------------- |
| 202  | Not System App. |
| 5400101  | No memory. Return by promise. |

**示例：**

```ts
let screenCaptureMonitor: media.ScreenCaptureMonitor;
try {
  screenCaptureMonitor = await media.getScreenCaptureMonitor();
} catch (err) {
  console.error(`getScreenCaptureMonitor failed, error message:${err.message}`);
}
```

## media.createParallelSoundPool<sup>20+</sup>

createParallelSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo): Promise\<SoundPool>

创建音频池实例，通过Promise获取返回值。

使用[createSoundPool](arkts-apis-media-f.md#mediacreatesoundpool10)创建的音频池实例，在重复播放相同音频时，会停止之前的播放并重新开始；而使用createParallelSoundPool创建的实例，在重复播放相同音频时，不会停止之前的音频，而是并行播放。

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名   | 类型                                            | 必填 | 说明                                                         |
| -------- | ----------------------------------------------- | ---- | ------------------------------------------------------------ |
| maxStreams | number | 是   | soundPool实例的最大播放的流数，设置范围为1-32的正整数。 |
| audioRenderInfo | [audio.AudioRendererInfo](../apis-audio-kit/arkts-apis-audio-i.md#audiorendererinfo8)  | 是   | 音频播放参数信息。 |

**返回值：**

| 类型                                      | 说明                                                         |
| ----------------------------------------- | ------------------------------------------------------------ |
| Promise<[SoundPool](js-apis-inner-multimedia-soundPool.md)> | Promise对象。异步返回SoundPool实例，失败时返回null。用于音频池实例的加载播放功能。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                      |
| -------- | ----------------------------- |
| 5400101  | No memory. Return by promise. |
| 202| System API error. Return by promise. |

**示例：**

```js
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let soundPool: media.SoundPool;
let audioRendererInfo: audio.AudioRendererInfo = {
  usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
  rendererFlags : 0
}

media.createParallelSoundPool(5, audioRendererInfo).then((soundpool_: media.SoundPool) => {
  if (soundpool_ != null) {
    soundPool = soundpool_;
    console.info('Succceeded in creating SoundPool');
  } else {
    console.error('Failed to create SoundPool');
  }
}, (error: BusinessError) => {
  console.error(`soundpool catchCallback, error message:${error.message}`);
});
```

## PixelMapParams<sup>11+</sup>

获取视频缩略图时，输出缩略图的格式参数。

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

| 名称     | 类型   |  可读   |   可写    |  说明                   |
| -------- | ------ |   ------| ------ | ---------------------- |
| colorFormat  | [PixelFormat](#pixelformat11) |  是   |  是   | 输出的缩略图颜色格式<br>**系统接口：** 该接口为系统接口      |

## PixelFormat<sup>11+</sup>

获取视频缩略图时，输出的缩略图采用的颜色格式枚举。

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**系统接口：** 该接口为系统接口

| 名称                     | 值              | 说明                                                         |
| ------------------------ | --------------- | ------------------------------------------------------------ |
| RGB_565       | 2   | 表示RGB_565颜色格式。                       |
| RGBA_8888        | 3    | 表示RGBA_8888颜色格式。 |
| RGB_888        | 5    | 表示RGB_888颜色格式。                 |

## AVMetadataExtractor<sup>11+</sup>

> **说明：**
> 元数据获取类，用于从媒体资源中获取元数据。在调用AVMetadataExtractor的方法前，需要先通过[createAVMetadataExtractor()](arkts-apis-media-f.md#mediacreateavmetadataextractor11)构建一个AVMetadataExtractor实例。

### getTimeByFrameIndex<sup>12+</sup>

getTimeByFrameIndex(index: number): Promise\<number>

获取目标视频帧号对应的视频时间戳。仅支持MP4视频文件。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**系统接口：** 该接口为系统接口

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| index  | number | 是   | 视频帧号。 |

**返回值：**

| 类型             | 说明                                |
| ---------------- | ----------------------------------- |
| Promise\<number> | 时间戳的Promise返回值。单位是微秒。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                                       |
| -------- | ---------------------------------------------- |
| 401      | The parameter check failed. Return by promise. |
| 5400102  | Operation not allowed. Returned by promise.    |
| 5400106  | Unsupported format. Returned by promise.       |

**示例：**

```ts
import { media } from '@kit.MediaKit';
import { BusinessError } from '@kit.BasicServicesKit';

avMetadataExtractor.getTimeByFrameIndex(0).then((timeUs: number) => {
  console.info(`Succeeded getTimeByFrameIndex timeUs: ${timeUs}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getTimeByFrameIndex ${err.message}`);
})
```

### getFrameIndexByTime<sup>12+</sup>

getFrameIndexByTime(timeUs: number): Promise\<number>

获取目标视频时间戳对应的视频帧号。仅支持MP4视频文件。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**系统接口：** 该接口为系统接口

**参数：**

| 参数名 | 类型   | 必填 | 说明                     |
| ------ | ------ | ---- | ------------------------ |
| timeUs | number | 是   | 视频时间戳，单位：微秒。 |

**返回值：**

| 类型             | 说明                      |
| ---------------- | ------------------------- |
| Promise\<number> | 视频帧号的Promise返回值。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                                       |
| -------- | ---------------------------------------------- |
| 401      | The parameter check failed. Return by promise. |
| 5400102  | Operation not allowed. Returned by promise.    |
| 5400106  | Unsupported format. Returned by promise.       |

**示例：**

```ts
import { media } from '@kit.MediaKit';
import { BusinessError } from '@kit.BasicServicesKit';

avMetadataExtractor.getFrameIndexByTime(0).then((index: number) => {
  console.info(`Succeeded getFrameIndexByTime index: ${index}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getFrameIndexByTime ${err.message}`);
})
```

## AVRecorder<sup>9+</sup>

音视频录制管理类，用于音视频媒体录制。在调用AVRecorder的方法前，需要先通过[createAVRecorder()](arkts-apis-media-f.md#mediacreateavrecorder9)构建一个AVRecorder实例。

> **说明：**
>
> 使用相机进行视频录制时，需要与相机模块配合，相机模块接口的使用详情见[相机管理](../apis-camera-kit/arkts-apis-camera.md)。

### isWatermarkSupported<sup>13+</sup>

isWatermarkSupported(): Promise\<boolean>

检查当前设备录制是否支持硬件数字水印能力。通过Promise获取返回值。

可在[prepare()](arkts-apis-media-AVRecorder.md#prepare9-1)、[start()](arkts-apis-media-AVRecorder.md#start9)、[paused()](arkts-apis-media-AVRecorder.md#pause9)事件成功触发后调用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**系统接口：** 该接口为系统接口

**返回值：**

| 类型             | 说明                             |
| ---------------- | -------------------------------- |
| Promise\<boolean> | 获取是否支持水印的Promise返回值，支持水印：true，不支持水印：false。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.isWatermarkSupported().then((isWatermarkSupported: boolean) => {
  console.info(`Succeeded in get, isWatermarkSupported: ${isWatermarkSupported}`);
}).catch((error: BusinessError) => {
  console.error(`Failed to get and catch error is ${error.message}`);
});
```

### setWatermark<sup>13+</sup>

setWatermark(watermark: image.PixelMap, config: WatermarkConfig): Promise\<void>

给AVRecorder设置水印图像。通过Promise获取返回值。

当且仅当[prepare()](arkts-apis-media-AVRecorder.md#prepare9-1)事件成功触发后，且在[start()](arkts-apis-media-AVRecorder.md#start9)之前，才能调用setWatermark方法。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**系统接口：** 该接口为系统接口

**参数：**

| 参数名   | 类型                  | 必填 | 说明                         |
| -------- | -------------------- | ---- | --------------------------- |
| watermark | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)      | 是   | 图像PixelMap数据。<br>当前支持规格:<br>-当前仅支持pixelformat为RGBA8888。<br>-原图像为8K时->水印图像限制范围3072x288,原图像为4K时->水印图像限制范围1536x144。 |
| config    | [WatermarkConfig](#watermarkconfig13)   | 是   | 水印的相关配置参数。 |

**返回值：**

| 类型             | 说明                             |
| ---------------- | -------------------------------- |
| Promise\<void> | 异步返回函数执行结果。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                                 |
| -------- | --------------------------------------   |
|   401    | The parameter check failed. Return by promise.            |
|   801    | Capability not supported. Return by promise. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

let watermark: image.PixelMap|undefined = undefined; // need data.
let watermarkConfig: media.WatermarkConfig = { top: 100, left: 100 }

avRecorder.setWatermark(watermark, watermarkConfig).then(() => {
  console.info('Succeeded in setWatermark');
}).catch((error: BusinessError) => {
  console.error(`Failed to setWatermark and catch error is ${error.message}`);
});
```

### setMetadata<sup>18+</sup>
setMetadata(metadata: Record\<string, string\>): void

给AVRecorder的录制文件中设置自定义meta数据。

只有当[prepare()](arkts-apis-media-AVRecorder.md#prepare9-1)事件成功触发后，并在调用[stop()](arkts-apis-media-AVRecorder.md#stop9)方法之前，才能调用setMetadata方法。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**系统接口：** 该接口为系统接口。

**参数：**

| 参数名   | 类型                  | 必填 | 说明                                                                |
| -------- | -------------------- | ---- |-------------------------------------------------------------------|
| metadata | [Record<string, string>]  | 是   | 以键值对形式设置meta数据的tag和value。<br>- 第一个string为meta tag。<br>- 第二个string为meta value。 |

**返回值：**

| 类型            | 说明        |
| --------------- |-----------|
| void | 无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息            |
|-------|-----------------|
| 202   | Not System App. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let meta : Record<string, string> = {
   'com.openharmony.userdefine':'10',
   'com.openharmony.userdefine2':'20'
};

avRecorder.setMetadata(meta);
```

## AVRecorderProfile<sup>9+</sup>

音视频录制的配置文件。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

| 名称             | 类型                                         | 必填 | 说明                                                         |
| ---------------- | -------------------------------------------- | ---- | ------------------------------------------------------------ |
| enableStableQualityMode<sup>18+</sup>            | boolean                        | 否   | 视频录制是否选择稳定质量模式，选择视频录制时选填，enableStableQualityMode默认为false。设置为true时，启用视频编码策略以实现质量稳定的编码。<br>**系统接口：** 该接口为系统接口。|

## VideoRecorder<sup>9+</sup>

> **说明：**
> AVRecorder<sup>9+</sup>发布后，VideoRecorder停止维护，建议使用[AVRecorder](arkts-apis-media-AVRecorder.md)替代。

视频录制管理类，用于录制视频媒体。在调用VideoRecorder的方法前，需要先通过[createVideoRecorder()](#mediacreatevideorecorder9)构建一个[VideoRecorder](#videorecorder9)实例。

### 属性

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

| 名称               | 类型                                   | 可读 | 可写 | 说明             |
| ------------------ | -------------------------------------- | ---- | ---- | ---------------- |
| state<sup>9+</sup> | [VideoRecordState](#videorecordstate9) | 是   | 否   | 视频录制的状态。 |

### prepare<sup>9+</sup>

prepare(config: VideoRecorderConfig, callback: AsyncCallback\<void>): void

异步方式进行视频录制的参数设置。通过注册回调函数获取返回值。

**需要权限：** ohos.permission.MICROPHONE

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                                |
| -------- | -------------------------------------------- | ---- | ----------------------------------- |
| config   | [VideoRecorderConfig](#videorecorderconfig9) | 是   | 配置视频录制的相关参数。            |
| callback | AsyncCallback\<void>                         | 是   | 异步视频录制prepare方法的回调方法。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                                   |
| -------- | ------------------------------------------ |
| 201      | Permission denied. Return by callback.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.       |
| 5400102  | Operation not allowed. Return by callback. |
| 5400105  | Service died. Return by callback.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 配置参数以实际硬件设备支持的范围为准。
let videoProfile: media.VideoRecorderProfile = {
  audioBitrate : 48000,
  audioChannels : 2,
  audioCodec : media.CodecMimeType.AUDIO_AAC,
  audioSampleRate : 48000,
  fileFormat : media.ContainerFormatType.CFT_MPEG_4,
  videoBitrate : 2000000,
  videoCodec : media.CodecMimeType.VIDEO_AVC,
  videoFrameWidth : 640,
  videoFrameHeight : 480,
  videoFrameRate : 30
}

let videoConfig: media.VideoRecorderConfig = {
  audioSourceType : media.AudioSourceType.AUDIO_SOURCE_TYPE_MIC,
  videoSourceType : media.VideoSourceType.VIDEO_SOURCE_TYPE_SURFACE_YUV,
  profile : videoProfile,
  url : 'fd://xx', // 文件需先由调用者创建，并给予适当的权限。
  rotation : 0,
  location : { latitude : 30, longitude : 130 }
}

// asyncallback.
videoRecorder.prepare(videoConfig, (err: BusinessError) => {
  if (err == null) {
    console.info('prepare success');
  } else {
    console.error('prepare failed and error is ' + err.message);
  }
})
```

### prepare<sup>9+</sup>

prepare(config: VideoRecorderConfig): Promise\<void>

异步方式进行视频录制的参数设置。通过Promise获取返回值。

**需要权限：** ohos.permission.MICROPHONE

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**参数：**

| 参数名 | 类型                                         | 必填 | 说明                     |
| ------ | -------------------------------------------- | ---- | ------------------------ |
| config | [VideoRecorderConfig](#videorecorderconfig9) | 是   | 配置视频录制的相关参数。 |

**返回值：**

| 类型           | 说明                                     |
| -------------- | ---------------------------------------- |
| Promise\<void> | 异步视频录制prepare方法的Promise返回值。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                                  |
| -------- | ----------------------------------------- |
| 201      | Permission denied. Return by promise.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.       |
| 5400102  | Operation not allowed. Return by promise. |
| 5400105  | Service died. Return by promise.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 配置参数以实际硬件设备支持的范围为准。
let videoProfile: media.VideoRecorderProfile = {
  audioBitrate : 48000,
  audioChannels : 2,
  audioCodec : media.CodecMimeType.AUDIO_AAC,
  audioSampleRate : 48000,
  fileFormat : media.ContainerFormatType.CFT_MPEG_4,
  videoBitrate : 2000000,
  videoCodec : media.CodecMimeType.VIDEO_AVC,
  videoFrameWidth : 640,
  videoFrameHeight : 480,
  videoFrameRate : 30
}

let videoConfig: media.VideoRecorderConfig = {
  audioSourceType : media.AudioSourceType.AUDIO_SOURCE_TYPE_MIC,
  videoSourceType : media.VideoSourceType.VIDEO_SOURCE_TYPE_SURFACE_YUV,
  profile : videoProfile,
  url : 'fd://xx', // 文件需先由调用者创建，并给予适当的权限。
  rotation : 0,
  location : { latitude : 30, longitude : 130 }
}

// promise.
videoRecorder.prepare(videoConfig).then(() => {
  console.info('prepare success');
}).catch((err: BusinessError) => {
  console.error('prepare failed and catch error is ' + err.message);
});
```

### getInputSurface<sup>9+</sup>

getInputSurface(callback: AsyncCallback\<string>): void

异步方式获得录制需要的surface。通过注册回调函数获取返回值。此surface提供给调用者，调用者从此surface中获取surfaceBuffer，填入相应的数据。

应当注意，填入的视频数据需要携带时间戳（单位ns），buffersize。时间戳的起始时间请以系统启动时间为基准。

只能在[prepare()](#prepare9)接口调用后调用。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**参数：**

| 参数名   | 类型                   | 必填 | 说明                        |
| -------- | ---------------------- | ---- | --------------------------- |
| callback | AsyncCallback\<string> | 是   | 异步获得surface的回调方法。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                                   |
| -------- | ------------------------------------------ |
| 5400102  | Operation not allowed. Return by callback. |
| 5400103  | I/O error. Return by callback.             |
| 5400105  | Service died. Return by callback.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
let surfaceID: string; // 传递给外界的surfaceID。
videoRecorder.getInputSurface((err: BusinessError, surfaceId: string) => {
  if (err == null) {
    console.info('getInputSurface success');
    surfaceID = surfaceId;
  } else {
    console.error('getInputSurface failed and error is ' + err.message);
  }
});
```

### getInputSurface<sup>9+</sup>

getInputSurface(): Promise\<string>;

 异步方式获得录制需要的surface。通过Promise获取返回值。此surface提供给调用者，调用者从此surface中获取surfaceBuffer，填入相应的数据。

应当注意，填入的视频数据需要携带时间戳（单位ns），buffersize。时间戳的起始时间请以系统启动时间为基准。

只能在[prepare()](#prepare9-1)接口调用后调用。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**返回值：**

| 类型             | 说明                             |
| ---------------- | -------------------------------- |
| Promise\<string> | 异步获得surface的Promise返回值。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                                  |
| -------- | ----------------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | I/O error. Return by promise.             |
| 5400105  | Service died. Return by promise.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
let surfaceID: string; // 传递给外界的surfaceID。
videoRecorder.getInputSurface().then((surfaceId: string) => {
  console.info('getInputSurface success');
  surfaceID = surfaceId;
}).catch((err: BusinessError) => {
  console.error('getInputSurface failed and catch error is ' + err.message);
});
```

### start<sup>9+</sup>

start(callback: AsyncCallback\<void>): void

异步方式开始视频录制。通过注册回调函数获取返回值。

在[prepare()](#prepare9)和[getInputSurface()](#getinputsurface9)后调用，需要依赖数据源先给surface传递数据。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**参数：**

| 参数名   | 类型                 | 必填 | 说明                         |
| -------- | -------------------- | ---- | ---------------------------- |
| callback | AsyncCallback\<void> | 是   | 异步开始视频录制的回调方法。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                                   |
| -------- | ------------------------------------------ |
| 5400102  | Operation not allowed. Return by callback. |
| 5400103  | I/O error. Return by callback.             |
| 5400105  | Service died. Return by callback.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.start((err: BusinessError) => {
  if (err == null) {
    console.info('start videorecorder success');
  } else {
    console.error('start videorecorder failed and error is ' + err.message);
  }
});
```

### start<sup>9+</sup>

start(): Promise\<void>

异步方式开始视频录制。通过Promise获取返回值。

在[prepare()](#prepare9-1)和[getInputSurface()](#getinputsurface9-1)后调用，需要依赖数据源先给surface传递数据。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**返回值：**

| 类型           | 说明                                  |
| -------------- | ------------------------------------- |
| Promise\<void> | 异步开始视频录制方法的Promise返回值。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                                  |
| -------- | ----------------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | I/O error. Return by promise.             |
| 5400105  | Service died. Return by promise.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.start().then(() => {
  console.info('start videorecorder success');
}).catch((err: BusinessError) => {
  console.error('start videorecorder failed and catch error is ' + err.message);
});
```

### pause<sup>9+</sup>

pause(callback: AsyncCallback\<void>): void

异步方式暂停视频录制。通过注册回调函数获取返回值。

在[start()](#start9)后调用。可以通过调用[resume()](#resume9)接口来恢复录制。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**参数：**

| 参数名   | 类型                 | 必填 | 说明                         |
| -------- | -------------------- | ---- | ---------------------------- |
| callback | AsyncCallback\<void> | 是   | 异步暂停视频录制的回调方法。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                                   |
| -------- | ------------------------------------------ |
| 5400102  | Operation not allowed. Return by callback. |
| 5400103  | I/O error. Return by callback.             |
| 5400105  | Service died. Return by callback.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.pause((err: BusinessError) => {
  if (err == null) {
    console.info('pause videorecorder success');
  } else {
    console.error('pause videorecorder failed and error is ' + err.message);
  }
});
```

### pause<sup>9+</sup>

pause(): Promise\<void>

异步方式暂停视频录制。通过Promise获取返回值。

在[start()](#start9-1)后调用。可以通过调用[resume()](#resume9-1)接口来恢复录制。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**返回值：**

| 类型           | 说明                                  |
| -------------- | ------------------------------------- |
| Promise\<void> | 异步暂停视频录制方法的Promise返回值。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                                  |
| -------- | ----------------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | I/O error. Return by promise.             |
| 5400105  | Service died. Return by promise.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.pause().then(() => {
  console.info('pause videorecorder success');
}).catch((err: BusinessError) => {
  console.error('pause videorecorder failed and catch error is ' + err.message);
});
```

### resume<sup>9+</sup>

resume(callback: AsyncCallback\<void>): void

异步方式恢复视频录制。通过注册回调函数获取返回值。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**参数：**

| 参数名   | 类型                 | 必填 | 说明                         |
| -------- | -------------------- | ---- | ---------------------------- |
| callback | AsyncCallback\<void> | 是   | 异步恢复视频录制的回调方法。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                                   |
| -------- | ------------------------------------------ |
| 5400102  | Operation not allowed. Return by callback. |
| 5400103  | I/O error. Return by callback.             |
| 5400105  | Service died. Return by callback.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.resume((err: BusinessError) => {
  if (err == null) {
    console.info('resume videorecorder success');
  } else {
    console.error('resume videorecorder failed and error is ' + err.message);
  }
});
```

### resume<sup>9+</sup>

resume(): Promise\<void>

异步方式恢复视频录制。通过Promise获取返回值。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**返回值：**

| 类型           | 说明                                  |
| -------------- | ------------------------------------- |
| Promise\<void> | 异步恢复视频录制方法的Promise返回值。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                                  |
| -------- | ----------------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | I/O error. Return by promise.             |
| 5400105  | Service died. Return by promise.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.resume().then(() => {
  console.info('resume videorecorder success');
}).catch((err: BusinessError) => {
  console.error('resume videorecorder failed and catch error is ' + err.message);
});
```

### stop<sup>9+</sup>

stop(callback: AsyncCallback\<void>): void

异步方式停止视频录制。通过注册回调函数获取返回值。

需要重新调用[prepare()](#prepare9)和[getInputSurface()](#getinputsurface9)接口才能重新录制。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**参数：**

| 参数名   | 类型                 | 必填 | 说明                         |
| -------- | -------------------- | ---- | ---------------------------- |
| callback | AsyncCallback\<void> | 是   | 异步停止视频录制的回调方法。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                                   |
| -------- | ------------------------------------------ |
| 5400102  | Operation not allowed. Return by callback. |
| 5400103  | I/O error. Return by callback.             |
| 5400105  | Service died. Return by callback.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.stop((err: BusinessError) => {
  if (err == null) {
    console.info('stop videorecorder success');
  } else {
    console.error('stop videorecorder failed and error is ' + err.message);
  }
});
```

### stop<sup>9+</sup>

stop(): Promise\<void>

异步方式停止视频录制。通过Promise获取返回值。

需要重新调用[prepare()](#prepare9-1)和[getInputSurface()](#getinputsurface9-1)接口才能重新录制。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**返回值：**

| 类型           | 说明                                  |
| -------------- | ------------------------------------- |
| Promise\<void> | 异步停止视频录制方法的Promise返回值。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                                  |
| -------- | ----------------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | I/O error. Return by promise.             |
| 5400105  | Service died. Return by promise.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.stop().then(() => {
  console.info('stop videorecorder success');
}).catch((err: BusinessError) => {
  console.error('stop videorecorder failed and catch error is ' + err.message);
});
```

### release<sup>9+</sup>

release(callback: AsyncCallback\<void>): void

异步方式释放视频录制资源。通过注册回调函数获取返回值。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**参数：**

| 参数名   | 类型                 | 必填 | 说明                             |
| -------- | -------------------- | ---- | -------------------------------- |
| callback | AsyncCallback\<void> | 是   | 异步释放视频录制资源的回调方法。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 5400105  | Service died. Return by callback. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.release((err: BusinessError) => {
  if (err == null) {
    console.info('release videorecorder success');
  } else {
    console.error('release videorecorder failed and error is ' + err.message);
  }
});
```

### release<sup>9+</sup>

release(): Promise\<void>

异步方式释放视频录制资源。通过Promise获取返回值。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**返回值：**

| 类型           | 说明                                      |
| -------------- | ----------------------------------------- |
| Promise\<void> | 异步释放视频录制资源方法的Promise返回值。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 5400105  | Service died. Return by callback. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.release().then(() => {
  console.info('release videorecorder success');
}).catch((err: BusinessError) => {
  console.error('release videorecorder failed and catch error is ' + err.message);
});
```

### reset<sup>9+</sup>

reset(callback: AsyncCallback\<void>): void

异步方式重置视频录制。通过注册回调函数获取返回值。

需要重新调用[prepare()](#prepare9)和[getInputSurface()](#getinputsurface9)接口才能重新录制。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**参数：**

| 参数名   | 类型                 | 必填 | 说明                         |
| -------- | -------------------- | ---- | ---------------------------- |
| callback | AsyncCallback\<void> | 是   | 异步重置视频录制的回调方法。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 5400103  | I/O error. Return by callback.    |
| 5400105  | Service died. Return by callback. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.reset((err: BusinessError) => {
  if (err == null) {
    console.info('reset videorecorder success');
  } else {
    console.error('reset videorecorder failed and error is ' + err.message);
  }
});
```

### reset<sup>9+</sup>

reset(): Promise\<void>

异步方式重置视频录制。通过Promise获取返回值。

需要重新调用[prepare()](#prepare9-1)和[getInputSurface()](#getinputsurface9-1)接口才能重新录制。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**返回值：**

| 类型           | 说明                                  |
| -------------- | ------------------------------------- |
| Promise\<void> | 异步重置视频录制方法的Promise返回值。 |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 5400103  | I/O error. Return by promise.    |
| 5400105  | Service died. Return by promise. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.reset().then(() => {
  console.info('reset videorecorder success');
}).catch((err: BusinessError) => {
  console.error('reset videorecorder failed and catch error is ' + err.message);
});
```

### on('error')<sup>9+</sup>

on(type: 'error', callback: ErrorCallback): void

开始订阅视频录制错误事件，当上报error错误事件后，用户需处理error事件，退出录制操作。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

**参数：**

| 参数名   | 类型          | 必填 | 说明                                                         |
| -------- | ------------- | ---- | ------------------------------------------------------------ |
| type     | string        | 是   | 录制错误事件回调类型'error'。<br/>-&nbsp;'error'：视频录制过程中发生错误，触发该事件。 |
| callback | [ErrorCallback](../apis-basic-services-kit/js-apis-base.md#errorcallback) | 是   | 录制错误事件回调方法。                                       |

**错误码：**

以下错误码的详细介绍请参见[媒体错误码](errorcode-media.md)

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 5400103  | I/O error. Return by callback.    |
| 5400105  | Service died. Return by callback. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 当获取videoRecordState接口出错时通过此订阅事件上报。
videoRecorder.on('error', (error: BusinessError) => { // 设置'error'事件回调。
  console.error(`audio error called, error: ${error}`);
})
```

## VideoRecordState<sup>9+</sup>

视频录制的状态机。可通过state属性获取当前状态。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

| 名称     | 类型   | 说明                   |
| -------- | ------ | ---------------------- |
| idle     | string | 视频录制空闲。         |
| prepared | string | 视频录制参数设置完成。 |
| playing  | string | 视频正在录制。         |
| paused   | string | 视频暂停录制。         |
| stopped  | string | 视频录制停止。         |
| error    | string | 错误状态。             |

## VideoRecorderConfig<sup>9+</sup>

表示视频录制的参数设置。

通过audioSourceType和videoSourceType区分纯视频录制和音视频录制（纯音频录制请使用[AVRecorder](arkts-apis-media-AVRecorder.md)或[AudioRecorder](arkts-apis-media-AudioRecorder.md)）。纯视频录制时，仅需要设置videoSourceType；音视频录制时，audioSourceType和videoSourceType均需要设置。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

| 名称            | 类型                                           | 必填 | 说明                                                         |
| --------------- | ---------------------------------------------- | ---- | ------------------------------------------------------------ |
| audioSourceType | [AudioSourceType](arkts-apis-media-e.md#audiosourcetype9)           | 否   | 视频录制的音频源类型，选择音频录制时必填。                      |
| videoSourceType | [VideoSourceType](arkts-apis-media-e.md#videosourcetype9)           | 是   | 视频录制的视频源类型。                                       |
| profile         | [VideoRecorderProfile](#videorecorderprofile9) | 是   | 视频录制的profile。                                          |
| rotation        | number                                         | 否   | 录制的视频旋转角度，仅支持0，90，180，270，默认值为0。       |
| location        | [Location](arkts-apis-media-i.md#location)                          | 否   | 录制视频的地理位置，默认不记录地理位置信息。                 |
| url             | string                                         | 是   | 视频输出URL：fd://xx&nbsp;(fd&nbsp;number)<br/>![](figures/zh-cn_image_url.png) |

## VideoRecorderProfile<sup>9+</sup>

视频录制的配置文件。

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 该接口为系统接口

| 名称             | 类型                                         | 必填 | 说明             |
| ---------------- | -------------------------------------------- | ---- | ---------------- |
| audioBitrate     | number                                       | 否   | 音频编码比特率，选择音频录制时必填。 |
| audioChannels    | number                                       | 否   | 音频采集声道数，选择音频录制时必填。 |
| audioCodec       | [CodecMimeType](arkts-apis-media-e.md#codecmimetype8)             | 否   | 音频编码格式，选择音频录制时必填。   |
| audioSampleRate  | number                                       | 否   | 音频采样率，选择音频录制时必填。     |
| fileFormat       | [ContainerFormatType](arkts-apis-media-e.md#containerformattype8) | 是   | 文件的容器格式。 |
| videoBitrate     | number                                       | 是   | 视频编码比特率。 |
| videoCodec       | [CodecMimeType](arkts-apis-media-e.md#codecmimetype8)             | 是   | 视频编码格式。   |
| videoFrameWidth  | number                                       | 是   | 录制视频帧的宽。 |
| videoFrameHeight | number                                       | 是   | 录制视频帧的高。 |
| videoFrameRate   | number                                       | 是   | 录制视频帧率。   |

## WatermarkConfig<sup>13+</sup>

设置给AVRecorder的水印相关配置，该位置以画面的左上角为开始点。

**系统能力：** SystemCapability.Multimedia.Media.Core

**系统接口：** 该接口为系统接口

| 名称      | 类型   | 必填 | 说明             |
| --------- | ------ | ---- | ---------------- |
| top       | number | 是   | 显示位置，距离图像顶部的像素偏移量。 |
| left      | number | 是   | 显示位置，距离图像左部的像素偏移量。 |

## ScreenCaptureMonitor<sup>18+</sup>

录屏状态监控类，用于查询和监听系统录屏的录屏状态。在调用ScreenCaptureMonitor方法前，需要先通过[getScreenCaptureMonitor()](#mediagetscreencapturemonitor18)构建一个[ScreenCaptureMonitor](#screencapturemonitor18)实例。

### 属性

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 该接口为系统接口。

| 名称               | 类型                                   | 可读 | 可写 | 说明             |
| ------------------ | -------------------------------------- | ---- | ---- | ---------------- |
| isSystemScreenRecorderWorking<sup>18+</sup> | boolean | 是   | 否   | 系统录屏是否处于录屏状态。 |

### on('systemScreenRecorder')<sup>18+</sup>

on(type: 'systemScreenRecorder', callback: Callback\<ScreenCaptureEvent>): void

开始订阅系统录屏的录屏状态。当上报ScreenCaptureEvent事件后，用户可以根据ScreenCaptureEvent事件得知系统录屏当前处于开启还是停止的状态。

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 该接口为系统接口。

**参数：**

| 参数名   | 类型          | 必填 | 说明                                                         |
| -------- | ------------- | ---- | ------------------------------------------------------------ |
| type     | string        | 是   | 录屏状态回调类型'systemScreenRecorder'。<br/>-&nbsp;'systemScreenRecorder'：系统录屏应用的录屏状态发生变化，触发该事件。 |
| callback | function | 是   | 系统录屏状态回调。[ScreenCaptureEvent](#screencaptureevent18)表示切换到的状态。                                       |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 202  | Not System App.    |

**示例：**

```ts

// 当系统录屏应用的录屏状态发生变化时通过此订阅事件上报。
screenCaptureMonitor.on('systemScreenRecorder', (event: media.ScreenCaptureEvent) => { 
  // 设置'systemScreenRecorder'事件回调。
  console.info(`system ScreenRecorder event: ${event}`);
})
```

### off('systemScreenRecorder')<sup>18+</sup>

off(type: 'systemScreenRecorder', callback?: Callback\<ScreenCaptureEvent>): void

取消订阅系统录屏的录屏状态。

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 该接口为系统接口。

**参数：**

| 参数名   | 类型          | 必填 | 说明                                                         |
| -------- | ------------- | ---- | ------------------------------------------------------------ |
| type     | string        | 是   | 录屏状态回调类型'systemScreenRecorder'。<br/>-&nbsp;'systemScreenRecorder'：系统录屏应用的录屏状态发生变化，触发该事件。 |
| callback | function | 否   | 系统录屏状态回调。[ScreenCaptureEvent](#screencaptureevent18)表示切换到的状态，不填此参数则会取消最后一次订阅事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 202  | Not System App.    |

**示例：**

```ts
screenCaptureMonitor.off('systemScreenRecorder');   
```

## ScreenCaptureEvent<sup>18+</sup>

系统录屏应用录屏状态的枚举值。

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 该接口为系统接口。

| 名称                     | 值              | 说明                                                         |
| ------------------------ | --------------- | ------------------------------------------------------------ |
| SCREENCAPTURE_STARTED       | 0   | 表示系统录屏应用开始录屏。                       |
| SCREENCAPTURE_STOPPED        | 1    | 表示系统录屏应用停止录屏。 |

## enableDeviceLevelCapture<sup>20+</sup>

用于指定折叠屏PC在折叠状态下录制半块屏幕还是整块屏幕。

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 该接口为系统接口。

enableDeviceLevelCapture是AVScreenCaptureStrategy接口中的一个可选参数，默认值为false。

| 名称                      | 类型    | 必填 | 说明 |
| ------------------------ | ------- | ---- | ---- |
| enableDeviceLevelCapture | boolean | 否   | true表示折叠屏PC在折叠状态下录制整块屏幕，false表示折叠屏PC在折叠状态下录制半块屏幕。 |
