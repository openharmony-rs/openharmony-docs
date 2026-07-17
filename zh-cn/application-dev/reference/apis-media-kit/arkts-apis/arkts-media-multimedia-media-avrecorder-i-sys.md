# AVRecorder

音视频录制管理类，用于音视频媒体录制。在调用AVRecorder的方法前，需要先调用[createAVRecorder](arkts-media-media-createavrecorder-f.md#createavrecorder-1)接口构建一个AVRecorder实例。

音视频录制demo可参考：[音频录制开发指导](../../../../media/media/using-avrecorder-for-recording.md)、[视频录制开发指导](../../../../media/media/video-recording.md)。

> **说明：**  
>  
> - 本Interface首批API从API version 9开始支持。  
>  
> - 相机视频录制功能需配合相机模块使用，相机模块接口的使用详情请参考[相机管理](@ohos.multimedia.camera:camera)。

**起始版本：** 9

<!--Device-unnamed-interface AVRecorder--><!--Device-unnamed-interface AVRecorder-End-->

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

<!--Device-AVRecorder-getInputMetaSurface(type: MetaSourceType): Promise<string>--><!--Device-AVRecorder-getInputMetaSurface(type: MetaSourceType): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [MetaSourceType](arkts-media-multimedia-media-metasourcetype-e-sys.md) | 是 | 元数据源类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<string> | Promise对象，返回输入surface id字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called from Non-System applications. Return by promise. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## isWatermarkSupported

```TypeScript
isWatermarkSupported(): Promise<boolean>
```

查询设备是否支持硬件数字水印。使用Promise异步回调。

可以在prepare()、start()或pause()事件触发后调用。

**起始版本：** 13

<!--Device-AVRecorder-isWatermarkSupported(): Promise<boolean>--><!--Device-AVRecorder-isWatermarkSupported(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象，返回查询结果。true表示设备支持硬件数字水印，false表示不支持。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.isWatermarkSupported().then((isWatermarkSupported: boolean) => {
  console.info(`Succeeded in get, isWatermarkSupported: ${isWatermarkSupported}`);
}).catch((error: BusinessError) => {
  console.error(`Failed to get and catch error is ${error.message}`);
});

```

## setMetadata

```TypeScript
setMetadata(metadata: Record<string, string>): void
```

设置录制的元数据信息。如果这些信息的键相同，会覆盖config.metadata.customInfo（参考[prepare()](media.AVRecorder.prepare(config: AVRecorderConfig))和[AVRecorderConfig](@ohos.multimedia.media:media.AVRecorderConfig)）中的值。

该方法只能在[prepare()](media.AVRecorder.prepare(config: AVRecorderConfig))事件成功触发后，且必须在[stop()](media.AVRecorder.stop(callback: AsyncCallback<void>))之前调用。

**起始版本：** 26.0.0

<!--Device-AVRecorder-setMetadata(metadata: Record<string, string>): void--><!--Device-AVRecorder-setMetadata(metadata: Record<string, string>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| metadata | Record<string, string> | 是 | 录制的元数据信息。<br>格式为字符串键值对，其中，键需要以`com.openharmony.`开头，且值的长度不能超过256个字节。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 19 - 24 |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory.<br>**适用版本：** 26.0.0+ |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed.<br>**适用版本：** 26.0.0+ |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | Parameter check failed.<br>**适用版本：** 26.0.0+ |

## setWatermark

```TypeScript
setWatermark(watermark: image.PixelMap, config: WatermarkConfig): Promise<void>
```

为AVRecorder设置水印。使用Promise异步回调。

只能在prepare()事件触发后且start()事件触发前调用。

**起始版本：** 13

<!--Device-AVRecorder-setWatermark(watermark: image.PixelMap, config: WatermarkConfig): Promise<void>--><!--Device-AVRecorder-setWatermark(watermark: image.PixelMap, config: WatermarkConfig): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| watermark | image.PixelMap | 是 | 水印图片。 |
| config | [WatermarkConfig](arkts-media-multimedia-media-watermarkconfig-i-sys.md) | 是 | 水印配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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

