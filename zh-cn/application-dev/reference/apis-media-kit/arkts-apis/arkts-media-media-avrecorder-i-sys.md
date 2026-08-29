# AVRecorder

AVRecorder是音视频录制管理类，用于音视频录制的全流程管理，支持音频录制、视频录制及音视频混合录制，可灵活配置编码参数、添加水印、设置元数据、监听录制状态和错误事件等。 适用于录制音视频并保存到文件的场景，包括需要在音频流打断期间保持录制连续性、实时监控音频振幅等场景。 在调用AVRecorder的方法前，需要先调用 [createAVRecorder](arkts-media-media-createavrecorder-f.md)接口构建一个AVRecorder实例。 典型录制流程： [createAVRecorder](arkts-media-media-createavrecorder-f.md) → [prepare](arkts-media-media-avrecorder-i.md#prepare) → [getInputSurface](arkts-media-media-avrecorder-i.md#getinputsurface)（纯视频/音视频录制时） → [start](arkts-media-media-avrecorder-i.md#start) → [pause](arkts-media-media-avrecorder-i.md#pause)/[resume](arkts-media-media-avrecorder-i.md#resume) → [stop](arkts-media-media-avrecorder-i.md#stop) → [release](arkts-media-media-avrecorder-i.md#release)。音视频录制示例可参考：[音频录制开发指导](../../../media/media/using-avrecorder-for-recording.md)、 [视频录制开发指导](../../../media/media/video-recording.md)。

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

## getInputMetaSurface

```TypeScript
getInputMetaSurface(type: MetaSourceType): Promise<string>
```

获取指定元数据源类型的输入元数据surface。必须在prepare完成后和start之前调用。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [MetaSourceType](arkts-media-media-metasourcetype-e-sys.md) | 是 | 元数据源类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;string&gt; | Promise对象，返回输入surface id字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called from Non-System applications. Return by promise. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.  2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## isWatermarkSupported

```TypeScript
isWatermarkSupported(): Promise<boolean>
```

查询设备是否支持硬件数字水印。使用Promise异步回调。可以在prepare()、start()或pause()事件触发后调用。

**起始版本：** 13

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;boolean&gt; | Promise对象，返回查询结果。true表示设备支持硬件数字水印，false表示不支持。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.isWatermarkSupported().then((isWatermarkSupported: boolean) => {
  console.info(`Succeeded in get, isWatermarkSupported: ${isWatermarkSupported}`);
}).catch((error: BusinessError) => {
  console.error(`Failed to get and catch error is ${error.message}`);
});
```

## setWatermark

```TypeScript
setWatermark(watermark: image.PixelMap, config: WatermarkConfig): Promise<void>
```

为AVRecorder设置水印。使用Promise异步回调。只能在prepare()事件触发后且start()事件触发前调用。

**起始版本：** 13

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| watermark | image.PixelMap | 是 | 水印图片。 |
| config | [WatermarkConfig](arkts-media-media-watermarkconfig-i-sys.md) | 是 | 水印配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
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
