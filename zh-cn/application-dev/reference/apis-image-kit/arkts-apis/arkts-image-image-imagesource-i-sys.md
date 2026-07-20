# ImageSource

ImageSource类，用于获取图片相关信息。

在调用ImageSource的方法前，需要先通过[image.createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-1)构建一个ImageSource实例。

ImageSource的所有方法均不支持并发调用。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 6

<!--Device-image-interface ImageSource--><!--Device-image-interface ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

<a id="createwidegamutsdrpixelmap"></a>
## createWideGamutSdrPixelMap

```TypeScript
createWideGamutSdrPixelMap(): Promise<PixelMap>
```

创建SDR的PixelMap对象。当图片为带有3通道GainMap的HDR图片时，会将其基础图扩展为BT.2020色域的SDR图。使用Promise异步回调。

> **说明：**  
>  
> - 对SDR图片源，按图片自带的色彩空间解码，输出SDR图。  
>  
> - 对带有单通道GainMap的HDR图片源，解码其基础图（SDR图），忽略GainMap。  
>  
> - 对带有3通道GainMap的HDR图片源，解码其基础图（SDR图），并将输出SDR图的色域扩展为  
> [ColorSpace](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspace-e.md).DISPLAY_BT2020_SRGB。

**起始版本：** 20

<!--Device-ImageSource-createWideGamutSdrPixelMap(): Promise<PixelMap>--><!--Device-ImageSource-createWideGamutSdrPixelMap(): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap&gt; | Promise对象，返回PixelMap。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700101](../errorcode-image.md#7700101-图片源存在问题) | Bad source. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |
| [7700103](../errorcode-image.md#7700103-图片太大) | Image too large. |
| [7700301](../errorcode-image.md#7700301-解码失败) | Decoding failed. |

**示例：**

```TypeScript
async function CreateWideGamutSdrPixelMap(context: Context) {
  // 此处'sdr.jpg'仅作示例，请开发者自行替换。
  let filePath: string = context.filesDir + "/sdr.jpg";
  let sdrImageSource = image.createImageSource(filePath);
  let pixelmap = sdrImageSource.createWideGamutSdrPixelMap();
  if (pixelmap != undefined) {
    console.info('Succeeded in creating sdr pixelMap object.');
  } else {
    console.error('Failed to create pixelMap.');
  }

  // 此处'singleChannelGainmapFilePath.jpg'仅作示例，请开发者自行替换。
  let singleChannelGainmapFilePath: string = context.filesDir + "/singleChannelGainmapFilePath.jpg";
  let singleChannelGainmapImageSource = image.createImageSource(singleChannelGainmapFilePath);
  let singleChannelGainmapPixelmap = singleChannelGainmapImageSource.createWideGamutSdrPixelMap();
  if (singleChannelGainmapPixelmap != undefined) {
    console.info('Succeeded in creating sdr pixelMap object by using singleChannelGainmapImageSource.');
  } else {
    console.error('Failed to create pixelMap.');
  }
  // 此处'threeChannelGainmapFilePath.jpg'仅作示例，请开发者自行替换。
  let threeChannelGainmapFilePath: string = context.filesDir + "/threeChannelGainmapFilePath.jpg";
  let threeChannelGainmapImageSource = image.createImageSource(threeChannelGainmapFilePath);
  let threeChannelGainmapPixelmap = threeChannelGainmapImageSource.createWideGamutSdrPixelMap();
  if (threeChannelGainmapPixelmap != undefined) {
    console.info('Succeeded in creating sdr pixelMap using DISPLAY_BT2020_SRGB.');
  } else {
    console.error('Failed to create pixelMap.');
  }
}

```

<a id="isjpegprogressive"></a>
## isJpegProgressive

```TypeScript
isJpegProgressive(): Promise<boolean>
```

判断Jpeg图片是否是渐进式图片。使用Promise异步回调。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageSource-isJpegProgressive(): Promise<boolean>--><!--Device-ImageSource-isJpegProgressive(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示Jpeg图片是渐进式；返回false表示Jpeg图片不是渐进式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700101](../errorcode-image.md#7700101-图片源存在问题) | Bad source. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function IsJpegProgressive(imageSource : image.ImageSource) {
  imageSource.isJpegProgressive()
    .then((isProgressive: boolean) => {
      console.info("isJpegProgressive: " + isProgressive);
    }).catch((error: BusinessError) => {
      console.error(`Failed to obtain the jpeg image isprogressive error.code is ${error.code}, message is ${error.message}`);
    })
}

```

<a id="modifyimageallproperties"></a>
## modifyImageAllProperties

```TypeScript
modifyImageAllProperties(records: Record<string, string|null>): Promise<void>
```

批量修改图片属性。使用Promise异步回调。

Exif属性中除"JPEGInterchangeFormat"/"JPEGInterchangeFormatLength"/"GIFLoopCount"字段外，其他均支持修改。

> **说明：**  
>  
> - 调用该接口修改属性会改变属性字节长度，建议通过传入文件描述符来创建[image.createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-1)实例或通过传入的uri创建  
> [image.createImageSource](arkts-image-image-createimagesource-f.md#createimagesource-1)实例。  
>  
> - 支持修改JPEG、PNG、HEIF和WEBP文件类型的图片属性，图片需要包含Exif信息。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageSource-modifyImageAllProperties(records: Record<string, string|null>): Promise<void>--><!--Device-ImageSource-modifyImageAllProperties(records: Record<string, string|null>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| records | Record&lt;string, string\|null&gt; | 是 | 包含图片属性名和属性值的键值对集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |
| [7700202](../errorcode-image.md#7700202-不支持的元数据) | Unsupported metadata. For example, the property key is not supported,or the property value is invalid. |
| [7700304](../errorcode-image.md#7700304-图片信息写入文件失败) | Failed to write image properties to the file. |

**示例：**

```TypeScript
async function ModifyImageAllProperties(imageSource: image.ImageSource) {
  try {
    let record: Record<string, string | null> = {
      "HwMnotePhysicalAperture": "13",
    }
    await imageSource.modifyImageAllProperties(record);
  } catch (err) {
    console.error('[modifyImageAllProperties]', `modify image property failed.err: ${err.code}, errorMessage: ${err.message}`);
  }
}

```

