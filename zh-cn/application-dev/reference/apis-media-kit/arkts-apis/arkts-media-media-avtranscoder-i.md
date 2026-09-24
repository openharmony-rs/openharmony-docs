# AVTranscoder

```TypeScript
interface AVTranscoder
```

视频转码管理类，用于视频转码。在调用AVTranscoder的方法前，需要先通过[createAVTranscoder()](arkts-media-media-createavtranscoder-f.md)构建一个AVTranscoder实例。

视频转码demo可参考：[视频转码开发指导](../../../media/media/using-avtranscoder-for-transcodering.md)

> **说明：** 
> 
> - 本Interface首批接口从API version 12开始支持。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## addWatermark

```TypeScript
addWatermark(watermark: image.PixelMap, config: WatermarkConfiguration): Promise<number>
```

为视频转码添加水印。使用Promise异步回调。应用最多可以添加5个水印。此接口只能在prepared状态之前调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| watermark | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | 是 | : 水印图像。 |
| config | [WatermarkConfiguration](arkts-media-media-watermarkconfiguration-i.md) | 是 | : 水印配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回添加的水印ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | The parameter check failed, parameter value out of range. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';
import { image } from '@kit.ImageKit';

async function test(context: Context) {
  // 创建转码实例。
  let avTranscoder = await media.createAVTranscoder();
  
  // 配置水印参数。
  let watermarkConfig: media.WatermarkConfiguration = {
      // 根据实际需求配置水印参数，单位为像素（px）。
      top: 40,
      left: 40,
      width: 200,
      height: 300,
  };

  // 获取资源管理器。
  let resourceManager = context.resourceManager;
  // 获取rawfile中水印图片的描述符，'img.png'可替换为实际水印图片文件名。
  let rawFileDescriptor = resourceManager.getRawFdSync('img.png');
  // 根据文件描述符创建ImageSource。
  let watermarkImageSource = image.createImageSource(rawFileDescriptor.fd);

  // 创建水印PixelMap。
  const decodingOptions: image.DecodingOptions = {
    // 可编辑像素。
    editable: true,
    // 像素格式。
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
  };
  const watermarkPixelMap = await watermarkImageSource.createPixelMap(decodingOptions);
  console.info('PixelMap created for watermark');

  // 添加水印。
  avTranscoder.addWatermark(watermarkPixelMap, watermarkConfig).then((watermarkId: number) => {
    console.info('addWatermark success, watermarkId: ' + watermarkId);
  }).catch((err: BusinessError) => {
    console.error('addWatermark failed and catch error is ' + err.message);
  });
}
```

## cancel

```TypeScript
cancel(): Promise<void>
```

取消视频转码。使用Promise异步回调。

需要在[prepare()](#prepare)、[start()](#start)、[pause()](#pause)或[resume()](#resume)事件成功触发后，才能调用cancel方法。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建转码实例。
  let avTranscoder = await media.createAVTranscoder();
  avTranscoder.cancel().then(() => {
    console.info('cancel AVTranscoder success');
  }).catch((err: BusinessError) => {
    console.error('cancel AVTranscoder failed and catch error is ' + err.message);
  });
}
```

## off('complete')

```TypeScript
off(type:'complete', callback?: Callback<void>):void
```

取消注册转码完成事件。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'complete' | 是 | 转码完成事件回调类型，支持的事件：'complete'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 完成事件回调方法。 |

## off('error')

```TypeScript
off(type:'error', callback?: ErrorCallback):void
```

取消注册转码错误事件，取消后不再接收到AVTranscoder的错误事件。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 转码错误事件回调类型'error'。<br>- 'error'：转码过程中发生错误，触发该事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 否 | 错误事件回调方法。 |

**示例**

```TypeScript
import { media } from '@kit.MediaKit';

async function test() {
  // 创建转码实例。
  let avTranscoder = await media.createAVTranscoder();
  avTranscoder.off('error');
}
```

## off('progressUpdate')

```TypeScript
off(type:'progressUpdate', callback?: Callback<number>):void
```

取消注册转码进度更新事件。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'progressUpdate' | 是 | 进度更新事件回调类型，支持的事件：'progressUpdate'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 已注册的进度更新事件回调。由于当前回调注册时，仅会保留最后一次注册的回调，建议此参数缺省。 |

**示例**

```TypeScript
import { media } from '@kit.MediaKit';

async function test() {
  // 创建转码实例。
  let avTranscoder = await media.createAVTranscoder();
  avTranscoder.off('progressUpdate');
}
```

## on('complete')

```TypeScript
on(type:'complete', callback: Callback<void>):void
```

注册转码完成事件，并通过注册的回调方法通知开发者。开发者只能注册一个完成事件的回调方法，当开发者重复注册时，以最后一次注册的回调接口为准。使用callback异步回调。

当AVTranscoder上报complete事件时，当前转码操作已完成，开发者需要通过[release()](#release)退出转码操作。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'complete' | 是 | 完成事件回调类型，支持的事件：'complete'，在转码过程中系统会自动触发此事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数，返回完成事件回调方法。 |

**示例**

```TypeScript
import { media } from '@kit.MediaKit';

async function test() {
  let avTranscoder: media.AVTranscoder | undefined = undefined;
  // 创建转码实例。
  avTranscoder = await media.createAVTranscoder();
  avTranscoder.on('complete', async () => {
    console.info('avTranscoder complete');
    if (avTranscoder != undefined) {
      // 开发者须在此监听转码完成事件。
      // 须等待avTranscoder.release()释放转码实例之后，再对转码后的文件进行转发、上传、转存等处理。
      await avTranscoder.release();
      avTranscoder = undefined;
    }
  });
}
```

## on('error')

```TypeScript
on(type:'error', callback: ErrorCallback):void
```

注册AVTranscoder的错误事件，该事件仅用于错误提示。如果AVTranscoder上报error事件，开发者需要通过[release()](#release)退出转码操作。使用callback异步回调。

开发者只能订阅一个错误事件的回调方法，当开发者重复订阅时，以最后一次订阅的回调接口为准。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 转码错误事件回调类型'error'。<br>'error'：转码过程中发生错误，触发该事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 转码错误事件回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | The parameter check failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400104](../errorcode-media.md#5400104-操作超时) | Time out. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建转码实例。
  let avTranscoder = await media.createAVTranscoder();
  avTranscoder.on('error', (err: BusinessError) => {
    console.error('case avTranscoder.on(error) called, errMessage is ' + err.message);
  });
}
```

## on('progressUpdate')

```TypeScript
on(type:'progressUpdate', callback: Callback<number>):void
```

注册转码进度更新事件，并通过注册的回调方法通知开发者。开发者只能注册一个进度更新事件的回调方法，当开发者重复注册时，以最后一次注册的回调接口为准。使用callback异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'progressUpdate' | 是 | 进度更新事件回调类型，支持的事件：'progressUpdate'，在转码过程中系统会自动触发此事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 回调函数，返回进度更新事件，函数中的参数number，表示当前转码百分比进度。 |

**示例**

```TypeScript
import { media } from '@kit.MediaKit';

async function test() {
  // 创建转码实例。
  let avTranscoder = await media.createAVTranscoder();
  avTranscoder.on('progressUpdate', (progress: number) => {
    console.info('avTranscoder progressUpdate = ' + progress);
  });
}
```

## pause

```TypeScript
pause(): Promise<void>
```

暂停视频转码。使用Promise异步回调。

需要[start()](#start)事件成功触发后，才能调用pause方法，可以通过调用[resume()](#resume)接口来恢复转码。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建转码实例。
  let avTranscoder = await media.createAVTranscoder();
  avTranscoder.pause().then(() => {
    console.info('pause AVTranscoder success');
  }).catch((err: BusinessError) => {
    console.error('pause AVTranscoder failed and catch error is ' + err.message);
  });
}
```

## prepare

```TypeScript
prepare(config: AVTranscoderConfig): Promise<void>
```

进行视频转码的参数设置。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [AVTranscoderConfig](arkts-media-media-avtranscoderconfig-i.md) | 是 | 配置视频转码的相关参数。<!--RP1--><!--RP1End--> |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建转码实例。
  let avTranscoder = await media.createAVTranscoder();
  // 配置参数以实际硬件设备支持的范围为准。
  let avTranscoderConfig: media.AVTranscoderConfig = {
    audioBitrate : 200000,
    audioCodec : media.CodecMimeType.AUDIO_AAC,
    fileFormat : media.ContainerFormatType.CFT_MPEG_4,
    videoBitrate : 3000000,
    videoCodec : media.CodecMimeType.VIDEO_AVC,
  };

  avTranscoder.prepare(avTranscoderConfig).then(() => {
    console.info('prepare success');
  }).catch((err: BusinessError) => {
    console.error('prepare failed and catch error is ' + err.message);
  });
}
```

## release

```TypeScript
release(): Promise<void>
```

释放视频转码资源。使用Promise异步回调。

释放视频转码资源之后，该AVTranscoder实例不能再进行任何操作。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建转码实例。
  let avTranscoder = await media.createAVTranscoder();
  avTranscoder.release().then(() => {
    console.info('release AVTranscoder success');
  }).catch((err: BusinessError) => {
    console.error('release AVTranscoder failed and catch error is ' + err.message);
  });
}
```

## resume

```TypeScript
resume(): Promise<void>
```

恢复视频转码。使用Promise异步回调。

需要在[pause()](#pause)事件成功触发后，才能调用resume方法。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建转码实例。
  let avTranscoder = await media.createAVTranscoder();
  avTranscoder.resume().then(() => {
    console.info('resume AVTranscoder success');
  }).catch((err: BusinessError) => {
    console.error('resume AVTranscoder failed and catch error is ' + err.message);
  });
}
```

## start

```TypeScript
start(): Promise<void>
```

开始视频转码。使用Promise异步回调。

需要[prepare()](#prepare)事件成功触发后，才能调用start方法。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建转码实例。
  let avTranscoder = await media.createAVTranscoder();
  avTranscoder.start().then(() => {
    console.info('start AVTranscoder success');
  }).catch((err: BusinessError) => {
    console.error('start AVTranscoder failed and catch error is ' + err.message);
  });
}
```

## fdDst

```TypeScript
fdDst: number
```

目标媒体文件描述，通过该属性设置数据输出。在创建AVTranscoder实例后，必须设置fdSrc和fdDst属性。

**说明：** 

- 将资源句柄（fd）传递给AVTranscoder实例之后，请不要通过该资源句柄做其他读写操作，包括但不限于将同一个资源句柄传递给多个AVPlayer/AVMetadataExtractor/AVImageGenerator  
/AVTranscoder。  
- 同一时间通过同一个资源句柄读写文件时存在竞争关系，将导致视频转码数据获取异常。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## fdSrc

```TypeScript
fdSrc: AVFileDescriptor
```

源媒体文件描述，通过该属性设置数据源。

**使用示例**：

假设一个连续存储的媒体文件，地址偏移：0，字节长度：100。其文件描述为AVFileDescriptor{ fd = 资源句柄; offset = 0; length = 100; }。

**说明：** 

- 将资源句柄（fd）传递给AVTranscoder实例之后，请不要通过该资源句柄做其他读写操作，包括但不限于将同一个资源句柄传递给多个AVPlayer/AVMetadataExtractor/AVImageGenerator  
/AVTranscoder。  
- 同一时间通过同一个资源句柄读写文件时存在竞争关系，将导致视频转码数据获取异常。

**类型：** [AVFileDescriptor](arkts-media-media-avfiledescriptor-i.md)

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder
