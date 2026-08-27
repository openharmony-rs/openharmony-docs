# AVRecorder

AVRecorder是音视频录制管理类，用于音视频录制的全流程管理，支持音频录制、视频录制及音视频混合录制，可灵活配置编码参数、添加水印、设置元数据、监听录制状态和错误事件等。 适用于录制音视频并保存到文件的场景，包括需要在音频流打断期间保持录制连续性、实时监控音频振幅等场景。 在调用AVRecorder的方法前，需要先调用 [createAVRecorder](arkts-media-media-createavrecorder-f.md)接口构建一个AVRecorder实例。 典型录制流程： [createAVRecorder](arkts-media-media-createavrecorder-f.md) → [prepare](#prepare) → [getInputSurface](#getinputsurface)（纯视频/音视频录制时） → [start](#start) → [pause](#pause)/[resume](#resume) → [stop](#stop) → [release](#release)。音视频录制示例可参考：[音频录制开发指导](../../../media/media/using-avrecorder-for-recording.md)、 [视频录制开发指导](../../../media/media/video-recording.md)。

> **说明：**
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 9开始支持。
> - 相机视频录制功能需配合相机模块使用，相机模块接口的使用详情请参考[相机管理](../../apis-camera-kit/arkts-apis/arkts-multimedia-camera.md)。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## addWatermark

```TypeScript
addWatermark(watermark: image.PixelMap, config: WatermarkConfiguration): Promise<number>
```

添加自定义水印图像到录制视频中。适用于需要在录制视频中嵌入品牌标识、版权信息或时间戳等水印的场景。使用Promise异步回调。  
> **说明：**
> - 应用最多可添加5个水印。
> - 必须在[prepare](#prepare)之前调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| watermark | image.PixelMap | 是 | 水印图像。该图像将作为水印叠加到录制的视频中。 |
| config | [WatermarkConfiguration](arkts-media-media-watermarkconfiguration-i.md) | 是 | 配置视频录制水印的相关参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象，返回所添加水印的编号，取值范围[1, 5]。 |

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
import { image } from '@kit.ImageKit';
import { media } from '@kit.MediaKit';

let watermark: image.PixelMap | undefined = undefined; // 通过image.createImageSource创建ImageSource对象后调用createPixelMap接口（@kit.ImageKit）获取PixelMap。水印图像不能为空。
let watermarkConfig: media.WatermarkConfiguration = { top: 100, left: 100, width: 100, height: 100 };

if (watermark) {
    avRecorder.addWatermark(watermark, watermarkConfig).then((num: number) => {
      console.info(`Succeeded in adding watermark, watermarkNum is ${num}`);
    })
    .catch((error: BusinessError) => {
      console.error(`Failed to add watermark and catch error is: Code: ${error.code}, message: ${error.message}`);
    });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';
import { media } from '@kit.MediaKit';

async function testAddWaterMark() {
  // 创建录屏实例。
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // 其余流程。

  let watermark: image.PixelMap | undefined = undefined; // 可以通过获取本地资源文件并转换为PixelMap，水印图像不能为空。
  let watermarkConfig: media.WatermarkConfiguration = { top: 100, left: 100, width: 100, height: 100 };

  if (watermark && avScreenCaptureRecorder) {
    avScreenCaptureRecorder.addWatermark(watermark, watermarkConfig).then((num: number) => {
      console.info(`Succeeded in adding watermark, watermarkNum is ${num}`);
    })
    .catch((error: BusinessError) => {
      console.error(`Failed to add watermark and catch error is: Code: ${error.code}, message: ${error.message}`);
    });
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';
import { image } from '@kit.ImageKit';

async function test() {
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

  avTranscoder.addWatermark(watermarkPixelMap, watermarkConfig).then((watermarkId: number) => {
    console.info('addWatermark success, watermarkId: ' + watermarkId);
  }).catch((err: BusinessError) => {
    console.error('addWatermark failed and catch error is ' + err.message);
  });
}
```

## getAudioCapturerMaxAmplitude

```TypeScript
getAudioCapturerMaxAmplitude(callback: AsyncCallback<number>): void
```

获取当前音频最大振幅。适用于需要实时监控音频振幅的场景，如录音音量可视化显示、音频质量检测等。使用callback异步回调。必须在[prepare](#prepare) 和[stop](#stop)之间调用。调用接口时，获取到的返回值是上一次获取最大振幅的时刻到当前这段区间内的音频最大振幅。例如，在1s时获取了一次最大振幅，到2s时再获取到的最大振幅是1-2s这个区间内的最大值。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。获取当前音频最大振幅成功时，err为undefined，data为获取到的最大振幅，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let maxAmplitude: number;

avRecorder.getAudioCapturerMaxAmplitude((err: BusinessError, amplitude: number) => {
  if (err) {
    console.error(`Failed to get AudioCapturerMaxAmplitude and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in getting AudioCapturerMaxAmplitude');
    maxAmplitude = amplitude;
  }
});
```

## getAudioCapturerMaxAmplitude

```TypeScript
getAudioCapturerMaxAmplitude(): Promise<number>
```

获取当前音频最大振幅。适用于需要实时监控音频振幅的场景，如录音音量可视化显示、音频质量检测等。使用Promise异步回调。必须在[prepare](#prepare) 和[stop](#stop)之间调用。调用接口时，获取到的返回值是上一次获取最大振幅的时刻到当前这段区间内的音频最大振幅。例如，在1s时获取了一次最大振幅，到2s时再获取到的最大振幅是1-2s这个区间内的最大值。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象，返回获取的当前音频最大振幅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let maxAmplitude: number;

avRecorder.getAudioCapturerMaxAmplitude().then((amplitude: number) => {
  console.info('Succeeded in getting AudioCapturerMaxAmplitude');
  maxAmplitude = amplitude;
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get AudioCapturerMaxAmplitude and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## getAvailableEncoder

```TypeScript
getAvailableEncoder(callback: AsyncCallback<Array<EncoderInfo>>): void
```

获取可用的编码器参数。适用于需要根据设备能力选择合适编码器的场景。使用callback异步回调。必须在非released/error状态下调用。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[EncoderInfo](arkts-media-media-encoderinfo-i.md)&gt;&gt; | 是 | 回调函数。获取可用的编码器参数成功时，err为undefined，data为获取到的编码器参数，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let encoderInfo: media.EncoderInfo;

avRecorder.getAvailableEncoder((err: BusinessError, info: media.EncoderInfo[]) => {
  if (err) {
    console.error(`Failed to get AvailableEncoder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in getting AvailableEncoder');
    if (info.length > 0) {
      encoderInfo = info[0];
    } else {
      console.error('No available encoder');
    }
  }
});
```

## getAvailableEncoder

```TypeScript
getAvailableEncoder(): Promise<Array<EncoderInfo>>
```

获取可用的编码器参数。适用于需要根据设备能力选择合适编码器的场景。使用Promise异步回调。必须在非released/error状态下调用。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[EncoderInfo](arkts-media-media-encoderinfo-i.md)&gt;&gt; | Promise对象，返回获取的可用的编码器参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let encoderInfo: media.EncoderInfo;

avRecorder.getAvailableEncoder().then((info: media.EncoderInfo[]) => {
  console.info('Succeeded in getting AvailableEncoder');
    if (info.length > 0) {
      encoderInfo = info[0];
    } else {
      console.error('No available encoder');
    }
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get AvailableEncoder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## getAVRecorderConfig

```TypeScript
getAVRecorderConfig(callback: AsyncCallback<AVRecorderConfig>): void
```

获取实时的配置参数。适用于需要确认录制配置是否正确应用的场景，如调试录制参数、验证配置生效情况等。使用callback异步回调。

必须在[prepare](#prepare)之后调用。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AVRecorderConfig](arkts-media-media-avrecorderconfig-i.md)&gt; | 是 | 回调函数。获取实时配置的参数成功时，err为undefined，data为获取到的配置参数，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avRecorderConfig: media.AVRecorderConfig;

avRecorder.getAVRecorderConfig((err: BusinessError, config: media.AVRecorderConfig) => {
  if (err) {
    console.error(`Failed to get avRecorderConfig and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in getting AVRecorderConfig');
    avRecorderConfig = config;
  }
});
```

## getAVRecorderConfig

```TypeScript
getAVRecorderConfig(): Promise<AVRecorderConfig>
```

获取实时的配置参数。适用于需要确认录制配置是否正确应用的场景，如调试录制参数、验证配置生效情况等。使用Promise异步回调。

必须在[prepare](#prepare)之后调用。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AVRecorderConfig](arkts-media-media-avrecorderconfig-i.md)&gt; | Promise对象。返回实时配置参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avRecorderConfig: media.AVRecorderConfig;

avRecorder.getAVRecorderConfig().then((config: media.AVRecorderConfig) => {
  console.info('Succeeded in getting AVRecorderConfig');
  avRecorderConfig = config;
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get AVRecorderConfig and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## getCurrentAudioCapturerInfo

```TypeScript
getCurrentAudioCapturerInfo(callback: AsyncCallback<audio.AudioCapturerChangeInfo>): void
```

获取当前音频采集参数。适用于需要确认当前音频采集设备类型或验证音频配置的场景。使用callback异步回调。必须在[prepare](#prepare) 和[stop](#stop)之间调用。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;audio.AudioCapturerChangeInfo&gt; | 是 | 回调函数。当获取音频采集参数成功时，err为undefined，data为获取到的 audio.AudioCapturerChangeInfo，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { audio } from '@kit.AudioKit';

let currentCapturerInfo: audio.AudioCapturerChangeInfo;

avRecorder.getCurrentAudioCapturerInfo((err: BusinessError, capturerInfo: audio.AudioCapturerChangeInfo) => {
  if (err) {
    console.error(`Failed to get CurrentAudioCapturerInfo and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in getting CurrentAudioCapturerInfo');
    currentCapturerInfo = capturerInfo;
  }
});
```

## getCurrentAudioCapturerInfo

```TypeScript
getCurrentAudioCapturerInfo(): Promise<audio.AudioCapturerChangeInfo>
```

获取当前音频采集参数。适用于需要确认当前音频采集设备类型或验证音频配置的场景。使用Promise异步回调。必须在[prepare](#prepare) 和[stop](#stop)之间调用。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;audio.AudioCapturerChangeInfo & gt; | Promise对象，返回获取的当前音频采集参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { audio } from '@kit.AudioKit';

let currentCapturerInfo: audio.AudioCapturerChangeInfo;

avRecorder.getCurrentAudioCapturerInfo().then((capturerInfo: audio.AudioCapturerChangeInfo) => {
  console.info('Succeeded in getting CurrentAudioCapturerInfo');
  currentCapturerInfo = capturerInfo;
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get CurrentAudioCapturerInfo and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## getInputSurface

```TypeScript
getInputSurface(callback: AsyncCallback<string>): void
```

获得录制需要的surface。适用于纯视频或音视频录制时需要获取surface传递视频数据的场景。 相机视频录制功能需配合相机模块使用，详情请参考[相机管理](../apis-camera-kit/arkts-apis-camera.md)。使用callback异步回调。开发者从此surface中获取surfaceBuffer，填入待录制的视频数据。填入视频数据时需携带时间戳（单位ns）和buffer size。时间戳的起始时间以系统启动时间为基准。必须在[prepare](#prepare)和 [start](#start)之间调用。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。当获取surface成功，err为undefined，data为获取到的surfaceId，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

**示例**

```TypeScript
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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let inputSurfaceId: string; // 该inputSurfaceId用于传递给相机接口创建videoOutput。

avRecorder.getInputSurface((err: BusinessError, surfaceId: string) => {
  if (err) {
    console.error(`Failed to do getInputSurface and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in doing getInputSurface');
    inputSurfaceId = surfaceId;
  }
});
```

## getInputSurface

```TypeScript
getInputSurface(): Promise<string>
```

获得录制需要的surface。适用于纯视频或音视频录制时需要获取surface传递视频数据的场景。 相机视频录制功能需配合相机模块使用，详情请参考[相机管理](../apis-camera-kit/arkts-apis-camera.md)。使用callback异步回调。开发者从此surface中获取surfaceBuffer，填入待录制的视频数据。填入视频数据时需携带时间戳（单位ns）和buffer size。时间戳的起始时间以系统启动时间为基准。必须在[prepare](#prepare)和 [start](#start)之间调用。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string & gt; | Promise对象，返回获取的surfaceId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let inputSurfaceId: string; // 该inputSurfaceId用于传递给相机接口创建videoOutput。

avRecorder.getInputSurface().then((surfaceId: string) => {
  console.info('Succeeded in getting InputSurface');
  inputSurfaceId = surfaceId;
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get InputSurface and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## off('stateChange')

```TypeScript
off(type: 'stateChange', callback?: OnAVRecorderStateChangeHandler): void
```

取消订阅录制状态机[AVRecorderState](arkts-media-media-avrecorderstate-t.md)切换的回调事件。使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 录制状态机切换的回调类型，支持的事件：'stateChange'，用户操作和系统都会触发此事件。 |
| callback | [OnAVRecorderStateChangeHandler](arkts-media-media-onavrecorderstatechangehandler-t.md) | 否 | 回调函数，用于接收录制状态机切换事件。 如果指定参数则取消对应callback（callback对象不能是匿名函数），否则取消所有callback。从API version 12开始支持此参数。 |

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消订阅录制错误的回调事件。使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 录制错误的回调类型，支持的事件：'error'。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 否 | 回调函数，用于接收录制错误事件。 如果指定参数则取消对应callback（callback对象不能是匿名函数），否则取消所有callback。从API version 12开始支持此参数。 |

## off('audioCapturerChange')

```TypeScript
off(type: 'audioCapturerChange', callback?: Callback<audio.AudioCapturerChangeInfo>): void
```

取消订阅录音配置变化的回调事件。使用callback异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioCapturerChange' | 是 | 录音配置变化的回调类型，支持的事件：'audioCapturerChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;audio.AudioCapturerChangeInfo&gt; | 否 | 回调函数，用于接收变化后的录音配置全量信息。 如果指定参数则取消对应callback（callback对象不能是匿名函数），否则取消所有callback。从API version 12开始支持此参数。 |

## off('photoAssetAvailable')

```TypeScript
off(type: 'photoAssetAvailable', callback?: Callback<photoAccessHelper.PhotoAsset>): void
```

取消订阅媒体资源创建完成的回调事件。使用callback异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'photoAssetAvailable' | 是 | 媒体资源创建完成的回调类型，支持的事件：'photoAssetAvailable'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;photoAccessHelper.PhotoAsset&gt; | 否 | 回调函数，用于接收系统创建的资源文件对应的PhotoAsset对象。 如果指定参数则取消对应callback（callback对象不能是匿名函数），否则取消所有callback。 |

## on('audioCapturerChange')

```TypeScript
on(type: 'audioCapturerChange', callback: Callback<audio.AudioCapturerChangeInfo>): void
```

订阅录音配置变化的回调事件。当录音配置发生变化时，会触发回调返回变化后的录音配置全量信息。使用callback异步回调。用户只能订阅一个录音配置变化事件的回调方法，当用户重复订阅时，以最后一次订阅的回调接口为准。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioCapturerChange' | 是 | 录音配置变化的回调类型，支持的事件：'audioCapturerChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;audio.AudioCapturerChangeInfo&gt; | 是 | 回调函数，用于接收变化后的录音配置全量信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

## on('photoAssetAvailable')

```TypeScript
on(type: 'photoAssetAvailable', callback: Callback<photoAccessHelper.PhotoAsset>): void
```

订阅媒体资源创建完成的回调事件。当[FileGenerationMode](arkts-media-media-filegenerationmode-e.md)枚举设置为系统创建媒体文件时， [stop](#stop)操作结束后会把 [PhotoAsset](../../apis-media-library-kit/arkts-apis/arkts-file-photoaccesshelper.md)对象回调给应用。使用callback异步回调。用户只能订阅一个媒体资源回调事件的回调方法，当用户重复订阅时，以最后一次订阅的回调接口为准。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'photoAssetAvailable' | 是 | 媒体资源创建完成的回调类型，支持的事件：'photoAssetAvailable'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;photoAccessHelper.PhotoAsset&gt; | 是 | 回调函数，用于接收系统创建的资源文件对应的PhotoAsset对象。 需在prepare配置中将FileGenerationMode设置为系统创建媒体文件模式，stop结束后才会触发此回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## on('stateChange')

```TypeScript
on(type: 'stateChange', callback: OnAVRecorderStateChangeHandler): void
```

订阅录制状态机[AVRecorderState](arkts-media-media-avrecorderstate-t.md)切换的回调事件。 当AVRecorderState发生变化时，会通过回调方法通知用户。用户只能订阅一个回调方法，重复订阅时以最后一次订阅的回调接口为准。使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 录制状态机切换的回调类型，支持的事件：'stateChange'，用户操作和系统都会触发此事件。 |
| callback | [OnAVRecorderStateChangeHandler](arkts-media-media-onavrecorderstatechangehandler-t.md) | 是 | 回调函数，用于接收录制状态机切换事件。 回调参数包括：state（录制状态，类型为AVRecorderState）和reason（状态切换原因，类型为StateChangeReason）。<br>**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

订阅录制错误的回调事件。该事件仅用于错误提示，用户无需停止录制操作。 如果[AVRecorderState](arkts-media-media-avrecorderstate-t.md)也切换至error状态，用户需通过[reset](#reset) 或者[release](#release)接口退出录制操作。使用callback异步回调。用户只能订阅一个错误事件的回调方法，当用户重复订阅时，以最后一次订阅的回调接口为准。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 录制错误的回调类型，支持的事件：'error'。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 回调函数，用于接收录制错误事件。回调参数为err（错误对象，类型为BusinessError，包含错误码code和错误信息message）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.  2. Incorrect parameter types. 3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400104](../errorcode-media.md#5400104-操作超时) | Time out. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. |
| [5400107](../errorcode-media.md#5400107-音频焦点冲突) | Audio interrupted.<br>**适用版本：** 11+ |

## pause

```TypeScript
pause(callback: AsyncCallback<void>): void
```

暂停录制。使用callback异步回调。必须在[start](#start)之后调用，调用成功后进入paused状态， 之后可以通过调用[resume](#resume)接口来恢复录制。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。如果暂停录制成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

**示例**

```TypeScript
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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至playing状态后才能调用。
  avPlayer.pause((err: BusinessError) => {
    if (err) {
      console.error(`Failed to pause. Code:${err.code},message:${err.message}`);
    } else {
      console.info('Succeeded in pausing');
    }
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.pause((err: BusinessError) => {
  if (err) {
    console.error(`Failed to pause AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in pausing');
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.pause((err: BusinessError) => {
  if (err) {
    console.error('Failed to pause!');
  } else {
    console.info('Succeeded in pausing!');
  }
});
```

## pause

```TypeScript
pause(): Promise<void>
```

暂停录制。使用Promise异步回调。必须在[start](#start)之后调用，调用成功后进入paused状态， 之后可以通过调用[resume](#resume)接口来恢复录制。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.pause().then(() => {
  console.info('pause videorecorder success');
}).catch((err: BusinessError) => {
  console.error('pause videorecorder failed and catch error is ' + err.message);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至playing状态后才能调用。
  avPlayer.pause().then(() => {
    console.info('Succeeded in pausing');
  }, (err: BusinessError) => {
    console.error(`Failed to pause. Code:${err.code},message:${err.message}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.pause().then(() => {
  console.info('Succeeded in pausing');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to pause AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.pause().then(() => {
  console.info('Succeeded in pausing');
}).catch((error: BusinessError) => {
  console.error(`video catchCallback, error:${error}`);
});
```

## prepare

```TypeScript
prepare(config: AVRecorderConfig, callback: AsyncCallback<void>): void
```

准备录制。设置音视频录制的参数，并初始化录制上下文。使用callback异步回调。必须在[start](#start)之前调用，调用成功后进入prepared状态， 此时，纯音频录制可直接调用[start](#start)接口开始录制； 纯视频或音视频录制需先调用[getInputSurface](#getinputsurface) 接口获取surface，再调用[start](#start)接口开始录制。

**起始版本：** 9

**需要权限：** ohos.permission.MICROPHONE

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [AVRecorderConfig](arkts-media-media-avrecorderconfig-i.md) | 是 | 配置音视频录制的相关参数。音频录制时需设置audioSourceType，视频录制时需设置videoSourceType。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当prepare接口成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by callback. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.  2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 配置参数以实际硬件设备支持的范围为准。
let avRecorderProfile: media.AVRecorderProfile = {
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
};
let videoMetaData: media.AVMetadata = {
  videoOrientation: '0' // 合理值0、90、180、270，非合理值prepare接口报错。
};
let avRecorderConfig: media.AVRecorderConfig = {
  audioSourceType : media.AudioSourceType.AUDIO_SOURCE_TYPE_MIC,
  videoSourceType : media.VideoSourceType.VIDEO_SOURCE_TYPE_SURFACE_YUV,
  profile : avRecorderProfile,
  url : 'fd://', // 文件需先通过fs.open接口（@kit.FileKit）打开获取文件描述符fd，赋予读写权限，将fd传给此参数，详见文件管理开发指导。
  metadata: videoMetaData,
  location : { latitude : 30, longitude : 130 }
};

avRecorder.prepare(avRecorderConfig, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to prepare and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in preparing');
  }
});
```

## prepare

```TypeScript
prepare(config: AVRecorderConfig): Promise<void>
```

准备录制。设置音视频录制的参数，并初始化录制上下文。使用Promise异步回调。必须在[start](#start)之前调用，调用成功后进入prepared状态，此时，纯音频录制可直接调用[start](#start)接口开始录制； 纯视频或音视频录制需先调用[getInputSurface](#getinputsurface)接口获取surface，再调用[start](#start)接口开始录制。

**起始版本：** 9

**需要权限：** ohos.permission.MICROPHONE

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [AVRecorderConfig](arkts-media-media-avrecorderconfig-i.md) | 是 | 配置音视频录制的相关参数。音频录制时需设置audioSourceType，视频录制时需设置videoSourceType。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by promise. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.  2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 配置参数以实际硬件设备支持的范围为准。
let avRecorderProfile: media.AVRecorderProfile = {
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
};
let videoMetaData: media.AVMetadata = {
  videoOrientation: '0' // 合理值0、90、180、270，非合理值prepare接口报错。
};
let avRecorderConfig: media.AVRecorderConfig = {
  audioSourceType : media.AudioSourceType.AUDIO_SOURCE_TYPE_MIC,
  videoSourceType : media.VideoSourceType.VIDEO_SOURCE_TYPE_SURFACE_YUV,
  profile : avRecorderProfile,
  url : 'fd://',  // 文件需先通过fileIo.open接口（@kit.CoreFileKit）打开获取文件描述符fd，赋予读写权限，将fd传给此参数。
  metadata : videoMetaData,
  location : { latitude : 30, longitude : 130 }
};

avRecorder.prepare(avRecorderConfig).then(() => {
  console.info('Succeeded in preparing');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to prepare and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放音视频录制资源。使用callback异步回调。必须在非released状态下调用，调用成功后进入released状态。与[createAVRecorder](arkts-media-media-createavrecorder-f.md)配对使用，录制流程结束后应调用此接口释放资源。 释放音视频录制资源之后，该AVRecorder实例不能再进行任何操作。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当释放音视频录制资源成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

**示例**

```TypeScript
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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

let avImageGenerator: media.AVImageGenerator | undefined = undefined;

// 释放资源。
media.createAVImageGenerator((err: BusinessError, generator: media.AVImageGenerator) => {
  if (generator) {
    avImageGenerator = generator;
    console.info(`Succeeded in creating AVImageGenerator`);
    avImageGenerator.release((error: BusinessError) => {
      if (error) {
        console.error(`Failed to release, code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info(`Succeeded in releasing`);
    });
  } else {
    console.error(`Failed to create AVImageGenerator, code: ${err.code}, message: ${err.message}`);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建AVMetadataExtractor对象。
  let avMetadataExtractor: media.AVMetadataExtractor = await media.createAVMetadataExtractor();
  avMetadataExtractor.release((error: BusinessError) => {
    if (error) {
      console.error(`Failed to release, code: ${error.code} message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in releasing.`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发除released以外的状态才能调用。
  avPlayer.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release. Code:${err.code},message:${err.message}`);
    } else {
      console.info('Succeeded in releasing');
    }
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.release((err: BusinessError) => {
  if (err) {
    console.error(`Failed to release AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in releasing AVRecorder');
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.release((err: BusinessError) => {
  if (err) {
    console.error('Failed to release!');
  } else {
    console.info('Succeeded in releasing!');
  }
});
```

## release

```TypeScript
release(): Promise<void>
```

释放音视频录制资源。使用Promise异步回调。必须在非released状态下调用，调用成功后进入released状态。与[createAVRecorder](arkts-media-media-createavrecorder-f.md)配对使用，录制流程结束后应调用此接口释放资源。 释放音视频录制资源之后，该AVRecorder实例不能再进行任何操作。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.release().then(() => {
  console.info('release videorecorder success');
}).catch((err: BusinessError) => {
  console.error('release videorecorder failed and catch error is ' + err.message);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

let avImageGenerator: media.AVImageGenerator | undefined = undefined;

// 释放资源。
media.createAVImageGenerator((err: BusinessError, generator: media.AVImageGenerator) => {
  if (generator) {
    avImageGenerator = generator;
    console.info(`Succeeded in creating AVImageGenerator`);
    avImageGenerator.release().then(() => {
      console.info(`Succeeded in releasing.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to release, code: ${error.code}, message: ${error.message}`);
    });
  } else {
    console.error(`Failed to create AVImageGenerator, code: ${err.code}, message: ${err.message}`);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function test() {
  // 创建AVMetadataExtractor对象。
  let avMetadataExtractor: media.AVMetadataExtractor = await media.createAVMetadataExtractor();
  if (avMetadataExtractor) {
    avMetadataExtractor.release().then(() => {
      console.info(`Succeeded in releasing.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to release, code: ${error.code} message: ${error.message}`);
    });
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发除released以外的状态才能调用。
  avPlayer.release().then(() => {
    console.info('Succeeded in releasing');
  }, (err: BusinessError) => {
    console.error(`Failed to release. Code:${err.code},message:${err.message}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.release().then(() => {
  console.info('Succeeded in releasing AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to release AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function testRelease() {
  // 创建录屏实例。
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // 其余流程。

  // 调用release方法。
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.release().then(() => {
      console.info('Succeeded in releasing avScreenCaptureRecorder');
    }).catch((err: BusinessError) => {
      console.error(`Failed to release avScreenCaptureRecorder. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.release().then(() => {
  console.info('Succeeded in releasing');
}).catch((error: BusinessError) => {
  console.error(`video catchCallback, error:${error}`);
});
```

## reset

```TypeScript
reset(callback: AsyncCallback<void>): void
```

重置音视频录制，将录制器恢复至初始状态以便重新配置参数。使用callback异步回调。必须在非released状态下调用，调用成功后进入idle状态。纯音频录制时，需要重新调用[prepare](#prepare)接口 才能重新录制。纯视频录制、音视频录制时，需要重新调用 [prepare](#prepare)和 [getInputSurface](#getinputsurface)接口才能重新录制。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当重置音视频录制成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

**示例**

```TypeScript
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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至initialized/prepared/playing/paused/completed/stopped/error状态后才能调用。
  avPlayer.reset((err: BusinessError) => {
    if (err) {
      console.error(`Failed to reset. Code:${err.code},message:${err.message}`);
    } else {
      console.info('Succeeded in resetting');
    }
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.reset((err: BusinessError) => {
  if (err) {
    console.error(`Failed to reset AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in resetting AVRecorder');
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.reset((err: BusinessError) => {
  if (err) {
    console.error('Failed to reset!');
  } else {
    console.info('Succeeded in resetting!');
  }
});
```

## reset

```TypeScript
reset(): Promise<void>
```

重置音视频录制，将录制器恢复至初始状态以便重新配置参数。使用Promise异步回调。必须在非released状态下调用，调用成功后进入idle状态。纯音频录制时，需要重新调用[prepare](#prepare)接口才能重新录制。 纯视频录制、音视频录制时，需要重新调用[prepare](#prepare)和 [getInputSurface](#getinputsurface)接口才能重新录制。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.reset().then(() => {
  console.info('reset videorecorder success');
}).catch((err: BusinessError) => {
  console.error('reset videorecorder failed and catch error is ' + err.message);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至initialized/prepared/playing/paused/completed/stopped/error状态后才能调用。
  avPlayer.reset().then(() => {
    console.info('Succeeded in resetting');
  }, (err: BusinessError) => {
    console.error(`Failed to reset. Code:${err.code},message:${err.message}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.reset().then(() => {
  console.info('Succeeded in resetting AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to reset AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.reset().then(() => {
  console.info('Succeeded in resetting');
}).catch((error: BusinessError) => {
  console.error(`video catchCallback, error:${error}`);
});
```

## resume

```TypeScript
resume(callback: AsyncCallback<void>): void
```

恢复录制。使用callback异步回调。必须在[pause](#pause)之后调用，调用成功后进入started状态， 之后可以再次调用[pause](#pause)接口暂停录制，或调用 [stop](#stop)接口停止录制。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。如果恢复录制成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

**示例**

```TypeScript
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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.resume((err: BusinessError) => {
  if (err) {
    console.error(`Failed to resume AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in resuming AVRecorder');
  }
});
```

## resume

```TypeScript
resume(): Promise<void>
```

恢复录制。使用Promise异步回调。必须在[pause](#pause)之后调用，调用成功后进入started状态， 之后可以再次调用[pause](#pause)接口暂停录制，或调用[stop](#stop)接口停止录制。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.resume().then(() => {
  console.info('resume videorecorder success');
}).catch((err: BusinessError) => {
  console.error('resume videorecorder failed and catch error is ' + err.message);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.resume().then(() => {
  console.info('Succeeded in resuming AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to resume AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

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

## setMetadata

```TypeScript
setMetadata(metadata: Record<string, string>): void
```

设置录制的元数据信息。适用于需要在录制文件中嵌入自定义元数据（如作者、标题、标签等）的场景。 如果metadata参数与config.metadata.customInfo（参考[prepare()](#prepare)和 [AVRecorderConfig](arkts-media-media-avrecorderconfig-i.md)）中存在相同的键，前者的对应值将覆盖后者。必须在[prepare()](#prepare)和[stop()](#stop)之间调用。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| metadata | Record & lt;string, string & gt; | 是 | 录制的元数据信息。格式为字符串键值对，其中，键需要以`com.openharmony.`开头，否则该键值对将被忽略； 值的长度范围为0-256个字节，否则返回错误码5400108。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 19 - 24 |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory.<br>**适用版本：** 26.0.0+ |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed.<br>**适用版本：** 26.0.0+ |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | Parameter check failed.<br>**适用版本：** 26.0.0+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let metadata: Record<string, string> = {
  'com.openharmony.userdefine': '10',
  'com.openharmony.userdefine2': '20'
};

try {
  avRecorder.setMetadata(metadata);
  console.info('set metadata successfully');
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to set metadata. Code: ${error.code}, message: ${error.message}`);
}
```

## setWillMuteWhenInterrupted

```TypeScript
setWillMuteWhenInterrupted(muteWhenInterrupted: boolean): Promise<void>
```

设置当前录制音频流是否启用静音打断模式。启用后，录制音频流被更高优先级音频打断时将录制静音而非停止录制，适用于需要在打断期间保持录制连续性的场景（如会议录音、语音备忘）。 不启用则保持默认打断模式（音频流被打断时停止录制）。使用Promise异步回调。必须在[prepare()](#prepare)之前调用。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| muteWhenInterrupted | boolean | 是 | 设置当前录制音频流是否启用静音打断模式。true表示启用，音频流被打断时录制静音；false表示不启用，音频流被打断时停止录制。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.setWillMuteWhenInterrupted(true).then(() => {
  console.info('Succeeded in doing setWillMuteWhenInterrupted');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to do setWillMuteWhenInterrupted and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

开始录制。使用callback异步回调。必须在[prepare](#prepare)之后调用， 调用成功后进入started状态。录制视频时，还需在 [getInputSurface](#getinputsurface)接口调用成功后，才能调用此接口。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。如果开始录制成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

**示例**

```TypeScript
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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.start((err: BusinessError) => {
  if (err) {
    console.error(`Failed to start AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in starting AVRecorder');
  }
});
```

## start

```TypeScript
start(): Promise<void>
```

开始录制。使用Promise异步回调。必须在[prepare](#prepare)之后调用，调用成功后进入started状态。录制视频时，还需在 [getInputSurface](#getinputsurface)接口调用成功后，才能调用此接口。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.start().then(() => {
  console.info('start videorecorder success');
}).catch((err: BusinessError) => {
  console.error('start videorecorder failed and catch error is ' + err.message);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.start().then(() => {
  console.info('Succeeded in starting AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to start AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

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

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

停止录制。使用callback异步回调。必须在[start](#start)或 [pause](#pause)之后调用，调用成功后进入stopped状态。 当prepare配置中将FileGenerationMode设置为系统创建媒体文件模式时，本接口调用结束后会触发on('photoAssetAvailable')回调。 纯音频录制时，需要重新调用[prepare](#prepare) 接口才能重新录制；纯视频录制、音视频录制时，需要重新调用 [prepare](#prepare)和 [getInputSurface](#getinputsurface)接口才能重新录制。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。如果停止录制成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

**示例**

```TypeScript
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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/playing/paused/completed状态后才能调用。
  avPlayer.stop((err: BusinessError) => {
    if (err) {
      console.error(`Failed to stop. Code:${err.code},message:${err.message}`);
    } else {
      console.info('Succeeded in stopping');
    }
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.stop((err: BusinessError) => {
  if (err) {
    console.error(`Failed to stop AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in stopping AVRecorder');
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.stop((err: BusinessError) => {
  if (err) {
    console.error('Failed to stop!');
  } else {
    console.info('Succeeded in stopping!');
  }
});
```

## stop

```TypeScript
stop(): Promise<void>
```

停止录制。使用Promise异步回调。必须在[start](#start)或[pause](#pause)之后调用，调用成功后进入stopped状态。 当prepare配置中将FileGenerationMode设置为系统创建媒体文件模式时，本接口调用结束后会触发on('photoAssetAvailable')回调。 纯音频录制时，需要重新调用[prepare](#prepare)接口才能重新录制； 纯视频录制、音视频录制时，需要重新调用[prepare](#prepare)和 [getInputSurface](#getinputsurface)接口才能重新录制。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.stop().then(() => {
  console.info('stop videorecorder success');
}).catch((err: BusinessError) => {
  console.error('stop videorecorder failed and catch error is ' + err.message);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function  test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至prepared/playing/paused/completed状态后才能调用。
  avPlayer.stop().then(() => {
    console.info('Succeeded in stopping');
  }, (err: BusinessError) => {
    console.error(`Failed to stop. Code:${err.code},message:${err.message}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.stop().then(() => {
  console.info('Succeeded in stopping AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to stop AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

videoPlayer.stop().then(() => {
  console.info('Succeeded in stopping');
}).catch((error: BusinessError) => {
  console.error(`video catchCallback, error:${error}`);
});
```

## updateRotation

```TypeScript
updateRotation(rotation: number): Promise<void>
```

更新视频旋转角度。适用于设备方向发生变化（如横竖屏切换）时需要动态调整录制视频旋转角度的场景。使用Promise异步回调。必须在[prepare](#prepare)和[start](#start)之间调用。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotation | number | 是 | 旋转角度，单位为度（°）。取值仅支持0°、90°、180°和270°。传入不支持的角度值时，返回错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let rotation = 90;

avRecorder.updateRotation(rotation).then(() => {
  console.info('Succeeded in doing updateRotation');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to do updateRotation and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## state

```TypeScript
readonly state: AVRecorderState
```

音视频录制的状态。

**原子化服务API：** 从API version 12 开始，该接口支持在原子化服务中使用。

**类型：** [AVRecorderState](arkts-media-media-avrecorderstate-t.md)

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder
