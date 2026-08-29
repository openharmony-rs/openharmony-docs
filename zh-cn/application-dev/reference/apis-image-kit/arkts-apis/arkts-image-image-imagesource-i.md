# ImageSource

ImageSource类，用于获取图片相关信息。在调用ImageSource的方法前，需要先通过[image.createImageSource](arkts-image-image-createimagesource-f.md)构建一个ImageSource实例。ImageSource的所有方法均不支持并发调用。由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](#release)方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 6

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## createImageRawData

```TypeScript
createImageRawData(): Promise<ImageRawData>
```

获取图片原始数据。使用Promise异步回调。目前仅支持获取DNG图片类型的原始数据。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ImageRawData](arkts-image-image-imagerawdata-i.md)&gt; | Promise对象，返回ImageRawData对象，其中含有数据缓冲区和像素位数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700101](../errorcode-image.md#7700101-图片源存在问题) | Bad source. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function createImageRawData(imageSourceObj: image.ImageSource) {
  await imageSourceObj.createImageRawData().then((data: image.ImageRawData) => {
    console.info(`createImageRawData successfully. length: ${data.buffer.byteLength}, bitPerPixel:${data.bitsPerPixel}`);
    if (data.bitsPerPixel == 16) {
      let array: Uint16Array = new Uint16Array();
      let value: string = "";
      array = new Uint16Array(data.buffer);
      for (let i = 0; i < array.length && i < 10; i++) {
        value += array[i] + ', ';
      }
      console.info(`get dng rawdata is:${value}.`);
    }
  }).catch((error: BusinessError) => {
    console.error(`Failed to create image rawData. error.code is ${error.code}, error.message is ${error.message}`);
  });
}
```

## createPicture

```TypeScript
createPicture(options?: DecodingOptionsForPicture): Promise<Picture>
```

通过图片解码参数创建Picture对象。使用Promise异步回调。由于图片占用内存较大，所以当Picture对象使用完成后，应主动调用[release](arkts-image-image-picture-i.md#release)方法，及时释放内存。释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 13

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptionsForPicture](arkts-image-image-decodingoptionsforpicture-i.md) | 否 | 解码参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Picture](arkts-image-image-picture-i.md)&gt; | Promise对象，返回Picture。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [7700301](../errorcode-image.md#7700301-解码失败) | Decode failed. |
| [7700203](../errorcode-image.md#7700203-不支持的选项) | Unsupported options. For example, unsupported desiredPixelFormat causes a failure in converting an image into the desired pixel format.<br>**适用版本：** 24+ |

**示例**

```TypeScript
async function CreatePicture(imageSourceObj : image.ImageSource) {
  let options: image.DecodingOptionsForPicture = {
    desiredAuxiliaryPictures: [image.AuxiliaryPictureType.GAINMAP] // GAINMAP为需要解码的辅助图类型。 
  };
  let pictureObj: image.Picture = await imageSourceObj.createPicture(options);
  if (pictureObj != null) {
    console.info('Succeeded in creating picture.');
  } else {
    console.error('Failed to create picture.');
  }
}
```

## createPictureAtIndex

```TypeScript
createPictureAtIndex(index: number): Promise<Picture>
```

通过指定序号的图片创建Picture对象。使用Promise异步回调。

> **说明：**
> 
> - 支持GIF和HEIF&lt;sup&gt;23+&lt;/sup&gt;图像序列格式。从API版本26.0.0开始，增加支持AVIS格式。
> 
> - 由于图片占用内存较大，所以当Picture对象使用完成后，应主动调用[release](arkts-image-image-picture-i.md#release)方法，及时释放内存。
> 
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 解码图片序号。图片序号有效的取值范围为：[0, (帧数-1)]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Picture](arkts-image-image-picture-i.md)&gt; | Promise对象，返回Picture。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700101](../errorcode-image.md#7700101-图片源存在问题) | Bad source. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |
| [7700103](../errorcode-image.md#7700103-图片太大) | Image too large. |
| [7700203](../errorcode-image.md#7700203-不支持的选项) | Unsupported options. For example, index is invalid. |
| [7700301](../errorcode-image.md#7700301-解码失败) | Decoding failed. |

**示例**

```TypeScript
async function CreatePictures(imageSourceObj : image.ImageSource) {
  let frameCount: number = await imageSourceObj.getFrameCount();
  for (let index = 0; index < frameCount; index++) {
    try {
      let pictureObj: image.Picture = await imageSourceObj.createPictureAtIndex(index);
      console.info('Succeeded in creating picture for frame: ' + index);
    } catch (e) {
      console.error('Failed to create picture for frame: ' + index);
    }
  }
}
```

## createPixelMap

```TypeScript
createPixelMap(options?: DecodingOptions): Promise<PixelMap>
```

通过图片解码参数创建PixelMap对象。使用Promise异步回调。从API version 15开始，推荐使用[createPixelMapUsingAllocator](arkts-image-image-createpixelmapusingallocator-f.md)，该接口可以指定输出pixelMap的 内存类型[AllocatorType](arkts-image-image-allocatortype-e.md)，详情请参考 [图片解码内存优化(ArkTS)](../../../media/image/image-allocator-type.md)。

> **说明：**
> 
> - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。
> 
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。
> 
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 否 | 解码参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;PixelMap&gt; | Promise对象，返回PixelMap。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMap(imageSourceObj : image.ImageSource) {
  imageSourceObj.createPixelMap().then((pixelMap: image.PixelMap) => {
    console.info('Succeeded in creating pixelMap object through image decoding parameters.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to create pixelMap object through image decoding parameters, error.code ${error.code}, error.message ${error.message}`);
  })
}
```

## createPixelMap

```TypeScript
createPixelMap(callback: AsyncCallback<PixelMap>): void
```

通过默认参数创建PixelMap对象。使用callback异步回调。从API version 15开始，推荐使用[createPixelMapUsingAllocator](arkts-image-image-createpixelmapusingallocator-f.md)，该接口可以指定输出pixelMap的 内存类型[AllocatorType](arkts-image-image-allocatortype-e.md)，详情请参考 [图片解码内存优化(ArkTS)](../../../media/image/image-allocator-type.md)。

> **说明：**
> 
> - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。
> 
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。
> 
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;PixelMap&gt; | 是 | 回调函数，当创建PixelMap对象成功，err为undefined，data为获取到的PixelMap对象；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMap(imageSourceObj : image.ImageSource) {
  imageSourceObj.createPixelMap((err: BusinessError, pixelMap: image.PixelMap) => {
    if (err) {
      console.error(`Failed to create pixelMap.code is ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in creating pixelMap object.');
    }
  })
}
```

## createPixelMap

```TypeScript
createPixelMap(options: DecodingOptions, callback: AsyncCallback<PixelMap>): void
```

通过图片解码参数创建PixelMap对象。使用callback异步回调。从API version 15开始，推荐使用[createPixelMapUsingAllocator](arkts-image-image-createpixelmapusingallocator-f.md)，该接口可以指定输出pixelMap的 内存类型[AllocatorType](arkts-image-image-allocatortype-e.md)，详情请参考 [图片解码内存优化(ArkTS)](../../../media/image/image-allocator-type.md)。

> **说明：**
> 
> - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。
> 
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。
> 
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 是 | 解码参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;PixelMap&gt; | 是 | 回调函数，当创建PixelMap对象成功，err为undefined，data为获取到的PixelMap对象；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMap(imageSourceObj : image.ImageSource) {
  let decodingOptions: image.DecodingOptions = {
    sampleSize: 1,
    editable: true,
    desiredSize: { width: 1, height: 2 },
    rotate: 10,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    desiredRegion: { size: { width: 1, height: 2 }, x: 0, y: 0 },
    // 若解码接口同时传入了desiredSize参数与desiredRegion参数，需进一步传入cropAndScaleStrategy参数指定缩放与裁剪的先后顺序，推荐设置CROP_FIRST。
    cropAndScaleStrategy: image.CropAndScaleStrategy.CROP_FIRST,
    index: 0
  };
  imageSourceObj.createPixelMap(decodingOptions, (err: BusinessError, pixelMap: image.PixelMap) => {
    if (err) {
      console.error(`Failed to create pixelMap.code is ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in creating pixelMap object.');
    }
  })
}
```

## createPixelMapList

```TypeScript
createPixelMapList(options?: DecodingOptions): Promise<Array<PixelMap>>
```

通过图片解码参数创建PixelMap数组。使用Promise异步回调。针对动态图（如Gif、Webp），该接口会返回每帧图片数据；针对静态图，该接口会返回唯一的一帧图片数据。

> **说明：**
> 
> - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。
> 
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。
> 
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。
> 
> - 此接口会一次性解码全部帧，当帧数过多或单帧图像过大时（如2000×3000像素的100帧GIF动图），会占用较大内存，造成系统内存紧张，此种情况推荐使用Image组件显示动图，Image组件采用逐帧解码，占用内存比此接
> 口少。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 否 | 解码参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Array &lt;PixelMap&gt;&gt; | 异步返回PixelMap数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980099](../errorcode-image.md#62980099-共享内存数据异常) | The shared memory data is abnormal. |
| [62980101](../errorcode-image.md#62980101-图片输入数据错误) | The image data is abnormal. |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | The image data is not supported. |
| [62980106](../errorcode-image.md#62980106-图片数据太大) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| [62980109](../errorcode-image.md#62980109-裁剪错误) | Failed to crop the image. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |
| [62980118](../errorcode-image.md#62980118-创建插件失败) | Failed to create the image plugin. |
| [62980137](../errorcode-image.md#62980137-图片操作无效) | Invalid media operation. |
| [62980173](../errorcode-image.md#62980173-dma内存空间错误) | The DMA memory does not exist. |
| [62980174](../errorcode-image.md#62980174-dma内存数据异常) | The DMA memory data is abnormal. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMapList(imageSourceObj : image.ImageSource) {
  let decodeOpts: image.DecodingOptions = {
    sampleSize: 1,
    editable: true,
    desiredSize: { width: 198, height: 202 },
    rotate: 0,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    index: 0,
  };
  imageSourceObj.createPixelMapList(decodeOpts).then((pixelMapList: Array<image.PixelMap>) => {
    console.info('Succeeded in creating pixelMapList object.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create pixelMapList object, error code is ${err}`);
  })
}
```

## createPixelMapList

```TypeScript
createPixelMapList(callback: AsyncCallback<Array<PixelMap>>): void
```

通过默认参数创建PixelMap数组。使用callback异步回调。针对动态图（如Gif、Webp），该接口会返回每帧图片数据；针对静态图，该接口会返回唯一的一帧图片数据。

> **说明：**
> 
> - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。
> 
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。
> 
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。
> 
> - 此接口会一次性解码全部帧，当帧数过多或单帧图像过大时，会占用较大内存，造成系统内存紧张，此种情况推荐使用Image组件显示动图，Image组件采用逐帧解码，占用内存比此接口少。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;PixelMap&gt;&gt; | 是 | 回调函数，当创建PixelMap对象数组成功，err为undefined，data为获取到的PixelMap对象数组；否 则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980099](../errorcode-image.md#62980099-共享内存数据异常) | The shared memory data is abnormal. |
| [62980101](../errorcode-image.md#62980101-图片输入数据错误) | The image data is abnormal. |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | The image data is not supported. |
| [62980106](../errorcode-image.md#62980106-图片数据太大) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| [62980109](../errorcode-image.md#62980109-裁剪错误) | Failed to crop the image. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |
| [62980118](../errorcode-image.md#62980118-创建插件失败) | Failed to create the image plugin. |
| [62980137](../errorcode-image.md#62980137-图片操作无效) | Invalid media operation. |
| [62980173](../errorcode-image.md#62980173-dma内存空间错误) | The DMA memory does not exist. |
| [62980174](../errorcode-image.md#62980174-dma内存数据异常) | The DMA memory data is abnormal. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMapList(imageSourceObj : image.ImageSource) {
  imageSourceObj.createPixelMapList((err: BusinessError, pixelMapList: Array<image.PixelMap>) => {
    if (err) {
      console.error(`Failed to create pixelMapList object, error code is ${err}`);
    } else {
      console.info('Succeeded in creating pixelMapList object.');
    }
  })
}
```

## createPixelMapList

```TypeScript
createPixelMapList(options: DecodingOptions, callback: AsyncCallback<Array<PixelMap>>): void
```

通过图片解码参数创建PixelMap数组。使用callback异步回调。针对动态图（如Gif、Webp），该接口会返回每帧图片数据；针对静态图，该接口会返回唯一的一帧图片数据。

> **说明：**
> 
> - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。
> 
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。
> 
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。
> 
> - 此接口会一次性解码全部帧，当帧数过多或单帧图像过大时，会占用较大内存，造成系统内存紧张，此种情况推荐使用Image组件显示动图，Image组件采用逐帧解码，占用内存比此接口少。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 是 | 解码参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;PixelMap&gt;&gt; | 是 | 回调函数，当创建PixelMap对象数组成功，err为undefined，data为获取到的PixelMap对象数组；否 则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980099](../errorcode-image.md#62980099-共享内存数据异常) | The shared memory data is abnormal. |
| [62980101](../errorcode-image.md#62980101-图片输入数据错误) | The image data is abnormal. |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | The image data is not supported. |
| [62980106](../errorcode-image.md#62980106-图片数据太大) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| [62980109](../errorcode-image.md#62980109-裁剪错误) | Failed to crop the image. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |
| [62980118](../errorcode-image.md#62980118-创建插件失败) | Failed to create the image plugin. |
| [62980137](../errorcode-image.md#62980137-图片操作无效) | Invalid media operation. |
| [62980173](../errorcode-image.md#62980173-dma内存空间错误) | The DMA memory does not exist. |
| [62980174](../errorcode-image.md#62980174-dma内存数据异常) | The DMA memory data is abnormal. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMapList(imageSourceObj : image.ImageSource) {
  let decodeOpts: image.DecodingOptions = {
    sampleSize: 1,
    editable: true,
    desiredSize: { width: 198, height: 202 },
    rotate: 0,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    index: 0,
  };
  imageSourceObj.createPixelMapList(decodeOpts, (err: BusinessError, pixelMapList: Array<image.PixelMap>) => {
    if (err) {
      console.error(`Failed to create pixelMapList object, error code is ${err}`);
    } else {
      console.info('Succeeded in creating pixelMapList object.');
    }
  })
}
```

## createPixelMapSync

```TypeScript
createPixelMapSync(options?: DecodingOptions): PixelMap
```

通过图片解码参数同步创建PixelMap对象。由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。从API version 15开始，推荐使用[createPixelMapUsingAllocatorSync](arkts-image-image-createpixelmapusingallocatorsync-f.md)，该接口可以指定输出 pixelMap的内存类型[AllocatorType](arkts-image-image-allocatortype-e.md)，详情请参考 [图片解码内存优化(ArkTS)](../../../media/image/image-allocator-type.md)。

> **说明：**
> 
> 该方法为同步方法，调用时会阻塞当前线程，不建议在主线程中调用，否则可能导致应用卡顿、掉帧或响应延迟。具体场景参考
> [耗时任务并发场景简介](../../../arkts-utils/time-consuming-task-overview.md)。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 否 | 解码参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | 用于同步返回创建结果。 |

**示例**

```TypeScript
function CreatePixelMapSync(context : Context) {
  // 此处'test.jpg'仅作示例，请开发者自行替换，否则imageSource创建失败会导致后续无法正常执行。
  let filePath: string = context.filesDir + "/test.jpg";
  let imageSource = image.createImageSource(filePath);
  let decodingOptions: image.DecodingOptions = {
    sampleSize: 1,
    editable: true,
    desiredSize: { width: 1, height: 2 },
    rotate: 10,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    desiredRegion: { size: { width: 1, height: 2 }, x: 0, y: 0 },
    // 若解码接口同时传入了desiredSize参数与desiredRegion参数，需进一步传入cropAndScaleStrategy参数指定缩放与裁剪的先后顺序，推荐设置CROP_FIRST。
    cropAndScaleStrategy: image.CropAndScaleStrategy.CROP_FIRST,
    index: 0
  };
  let pixelmap = imageSource.createPixelMapSync(decodingOptions);
  if (pixelmap != undefined) {
    console.info('Succeeded in creating pixelMap object.');
  } else {
    console.error('Failed to create pixelMap.');
  }
}
```

## createPixelMapUsingAllocator

```TypeScript
createPixelMapUsingAllocator(options?: DecodingOptions, allocatorType?: AllocatorType): Promise<PixelMap>
```

使用指定的分配器根据图像解码参数异步创建PixelMap对象。使用Promise异步回调。接口使用详情请参考 [图片解码内存优化(ArkTS)](../../../media/image/image-allocator-type.md)。

> **说明：**
> 
> - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。
> 
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。
> 
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 15

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 否 | 解码参数。 |
| allocatorType | [AllocatorType](arkts-image-image-allocatortype-e.md) | 否 | 用于图像解码的内存类型。默认值为AllocatorType.AUTO。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;PixelMap&gt; | Promise对象，返回PixelMap。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types; 3.Parameter verification failed. |
| [7700101](../errorcode-image.md#7700101-图片源存在问题) | Bad source. e.g.,1. Image has invalid width or height. 2. Image source incomplete. 3. Read image data failed. 4. Codec create failed. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported mimetype. |
| [7700103](../errorcode-image.md#7700103-图片太大) | Image too large. This status code is thrown when an error occurs during the process of checking size. |
| [7700201](../errorcode-image.md#7700201-不支持的内存分配类型) | Unsupported allocator type, e.g., use share memory to decode a HDR image as only DMA supported hdr metadata. |
| [7700203](../errorcode-image.md#7700203-不支持的选项) | Unsupported options, e.g, cannot convert image into desired pixel format. |
| [7700301](../errorcode-image.md#7700301-解码失败) | Failed to decode image. |
| [7700302](../errorcode-image.md#7700302-内存分配失败) | Failed to allocate memory. |

**示例**

```TypeScript
async function CreatePixelMapUsingAllocator(context : Context) {
  // 此处'test.jpg'仅作示例，请开发者自行替换，否则imageSource创建失败会导致后续无法正常执行。
  let filePath: string = context.filesDir + "/test.jpg";
  let imageSource = image.createImageSource(filePath);
  let decodingOptions: image.DecodingOptions = {
    editable: true,
    desiredSize: { width: 3072, height: 4096 },
    rotate: 10,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    desiredRegion: { size: { width: 3072, height: 4096 }, x: 0, y: 0 },
    // 若解码接口同时传入了desiredSize参数与desiredRegion参数，需进一步传入cropAndScaleStrategy参数指定缩放与裁剪的先后顺序，推荐设置CROP_FIRST。
    cropAndScaleStrategy: image.CropAndScaleStrategy.CROP_FIRST,
    index: 0
  };
  let pixelmap = imageSource.createPixelMapUsingAllocator(decodingOptions, image.AllocatorType.AUTO);
  if (pixelmap != undefined) {
    console.info('Succeeded in creating pixelMap object.');
  } else {
    console.error('Failed to create pixelMap.');
  }
}
```

## createPixelMapUsingAllocatorSync

```TypeScript
createPixelMapUsingAllocatorSync(options?: DecodingOptions, allocatorType?: AllocatorType): PixelMap
```

根据指定的分配器同步创建一个基于图像解码参数的PixelMap对象。接口使用详情请参考[图片解码内存优化(ArkTS)](../../../media/image/image-allocator-type.md)。由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

> **说明：**
> 
> 该方法为同步方法，调用时会阻塞当前线程，不建议在主线程中调用，否则可能导致应用卡顿、掉帧或响应延迟。具体场景参考
> [耗时任务并发场景简介](../../../arkts-utils/time-consuming-task-overview.md)。

**起始版本：** 15

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 否 | 解码参数。 |
| allocatorType | [AllocatorType](arkts-image-image-allocatortype-e.md) | 否 | 用于图像解码的内存类型。默认值为AllocatorType.AUTO。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | 用于同步返回创建结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types; 3.Parameter verification failed. |
| [7700101](../errorcode-image.md#7700101-图片源存在问题) | Bad source. e.g.,1. Image has invalid width or height. 2. Image source incomplete. 3. Read image data failed. 4. Codec create failed. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported mimetype. |
| [7700103](../errorcode-image.md#7700103-图片太大) | Image too large. This status code is thrown when an error occurs during the process of checking size. |
| [7700201](../errorcode-image.md#7700201-不支持的内存分配类型) | Unsupported allocator type, e.g., use share memory to decode a HDR image as only DMA supported hdr metadata. |
| [7700203](../errorcode-image.md#7700203-不支持的选项) | Unsupported options, e.g, cannot convert image into desired pixel format. |
| [7700301](../errorcode-image.md#7700301-解码失败) | Failed to decode image. |
| [7700302](../errorcode-image.md#7700302-内存分配失败) | Failed to allocate memory. |

**示例**

```TypeScript
async function CreatePixelMapUsingAllocator(context : Context) {
  // 此处'test.jpg'仅作示例，请开发者自行替换，否则imageSource创建失败会导致后续无法正常执行。
  let filePath: string = context.filesDir + "/test.jpg";
  let imageSource = image.createImageSource(filePath);
  let decodingOptions: image.DecodingOptions = {
    editable: true,
    desiredSize: { width: 3072, height: 4096 },
    rotate: 10,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    desiredRegion: { size: { width: 3072, height: 4096 }, x: 0, y: 0 },
    // 若解码接口同时传入了desiredSize参数与desiredRegion参数，需进一步传入cropAndScaleStrategy参数指定缩放与裁剪的先后顺序，推荐设置CROP_FIRST。
    cropAndScaleStrategy: image.CropAndScaleStrategy.CROP_FIRST,
    index: 0
  };
  let pixelmap = imageSource.createPixelMapUsingAllocatorSync(decodingOptions, image.AllocatorType.AUTO);
  if (pixelmap != undefined) {
    console.info('Succeeded in creating pixelMap object.');
  } else {
    console.error('Failed to create pixelMap.');
  }
}
```

## createThumbnail

```TypeScript
createThumbnail(options?: DecodingOptionsForThumbnail): Promise<PixelMap | undefined>
```

通过图片解码参数创建缩略图PixelMap对象。使用Promise异步回调。当前支持对JPEG和HEIF格式的图片创建缩略图PixelMap对象。优先解码图片文件中包含的缩略图。若图片文件中没有缩略图，则对原图进行解码。

> **说明：**
> 
> - 不支持在同一个ImageSource实例上并发调用。
> 
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。
> 
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptionsForThumbnail](arkts-image-image-decodingoptionsforthumbnail-i.md) | 否 | 解码参数，控制是否生成缩略图以及生成缩略图的目标尺寸。 默认表现：    - 当图像有缩略图时，解码原始缩略图，返回的PixelMap对象的宽和高与原缩略图保持一致。    - 当原图文件无缩略图时，对原图进行解码后，根据解码参数options下采样生成缩略图，生成后的缩略图PixelMap对象宽和高都限制在512像素以内。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;PixelMap \ | undefined&gt; | Promise对象，返回PixelMap。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported mimetype. |
| [7700103](../errorcode-image.md#7700103-图片太大) | Image too large. |
| [7700204](../errorcode-image.md#7700204-无效参数) | Invalid parameter, e.g, invalid generate size. |
| [7700301](../errorcode-image.md#7700301-解码失败) | Decode failed. |
| [7700303](../errorcode-image.md#7700303-图片不包含缩略图数据) | Image does not carry thumbnail data. |
| [7700305](../errorcode-image.md#7700305-缩略图生成失败) | Thumbnail generation failed. |

**示例**

```TypeScript
async function CreateThumbnail(imageSource: image.ImageSource): Promise<image.PixelMap | undefined> {
  try {
    if (!imageSource) {
      console.error('CreateThumbnail: imageSource is null or undefined');
      return undefined;
    }
    const imageInfo = await imageSource.getImageInfo();
    const supportedMimeTypes = ['image/jpeg', 'image/heif', 'image/heic'];
    if (!supportedMimeTypes.includes(imageInfo.mimeType)) {
      console.error(`CreateThumbnail: Unsupported MIME type: ${imageInfo.mimeType}`);
      return undefined;
    }

    const decodingOptions: image.DecodingOptionsForThumbnail = {
      generateThumbnailIfAbsent: true,
      maxGeneratedPixelDimension: 200,
    };

    const pixelmap = await imageSource.createThumbnail(decodingOptions);
    if (pixelmap) {
      console.info('Succeeded in creating thumbnail pixelMap object.');
      return pixelmap;
    } else {
      console.error('Failed to create thumbnail pixelMap.');
      return undefined;
    }
  } catch (error) {
    console.error('CreateThumbnail error:', JSON.stringify(error));
    return undefined;
  }
}
```

## createThumbnailSync

```TypeScript
createThumbnailSync(options?: DecodingOptionsForThumbnail): PixelMap | undefined
```

通过图片解码参数同步创建缩略图。返回创建结果对应的[PixelMap](arkts-image-image-pixelmap-i.md)对象。当前支持对JPEG和HEIF格式的图片创建缩略图PixelMap对象。优先解码图片文件中包含的缩略图。若图片文件中没有缩略图，则对原图进行解码。

> **说明：**
> 
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。
> 
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。
> 
> - 该方法为同步方法，调用时会阻塞当前线程，不建议在主线程中调用，否则可能导致应用卡顿、掉帧或响应延迟。具体场景参考
> [耗时任务并发场景简介](../../../arkts-utils/time-consuming-task-overview.md)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptionsForThumbnail](arkts-image-image-decodingoptionsforthumbnail-i.md) | 否 | 解码参数，控制是否生成缩略图以及生成缩略图的目标尺寸。 默认表现：    - 当图像有缩略图时，解码原始缩略图，返回的PixelMap对象的宽和高与原缩略图保持一致。    - 当原图文件无缩略图时，对原图进行解码后，根据解码参数options下采样生成缩略图，生成后的缩略图PixelMap对象宽和高都限制在512像素以内。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap \| undefined | 用于同步返回创建结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported mimetype. |
| [7700103](../errorcode-image.md#7700103-图片太大) | Image too large. |
| [7700204](../errorcode-image.md#7700204-无效参数) | Invalid parameter, e.g, invalid generate size. |
| [7700301](../errorcode-image.md#7700301-解码失败) | Decode failed. |
| [7700303](../errorcode-image.md#7700303-图片不包含缩略图数据) | Image does not carry thumbnail data. |
| [7700305](../errorcode-image.md#7700305-缩略图生成失败) | Thumbnail generation failed. |

**示例**

```TypeScript
async function CreateThumbnailSync(imageSource: image.ImageSource): Promise<image.PixelMap | undefined> {
  try {
    if (!imageSource) {
      console.error('CreateThumbnailSync: imageSource is null or undefined');
      return undefined;
    }
    const imageInfo = await imageSource.getImageInfo();
    const supportedMimeTypes = ['image/jpeg', 'image/heif', 'image/heic'];
    if (!supportedMimeTypes.includes(imageInfo.mimeType)) {
      console.error(`CreateThumbnailSync: Unsupported MIME type: ${imageInfo.mimeType}`);
      return undefined;
    }

    const decodingOptionsForThumbnail: image.DecodingOptionsForThumbnail = {
      generateThumbnailIfAbsent: true,
      maxGeneratedPixelDimension: 200,
    };

    const pixelmap = imageSource.createThumbnailSync(decodingOptionsForThumbnail);

    if (pixelmap) {
      console.info('Succeeded in creating thumbnail pixelMap object.');
      return pixelmap;
    } else {
      console.error('Failed to create thumbnail pixelMap.');
      return undefined;
    }
  } catch (error) {
    console.error('CreateThumbnailSync error:', JSON.stringify(error));
    return undefined;
  }
}
```

## getDelayTimeList

```TypeScript
getDelayTimeList(): Promise<Array<number>>
```

获取图像延迟时间数组。使用Promise异步回调。此接口仅用于gif图片和webp图片。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Array &lt;number&gt;&gt; | Promise对象，返回延迟时间数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980110](../errorcode-image.md#62980110-图片源数据错误) | The image source data is incorrect. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |
| [62980118](../errorcode-image.md#62980118-创建插件失败) | Failed to create the image plugin. |
| [62980122](../errorcode-image.md#62980122-解码图片头异常) | Failed to decode the image header. |
| [62980149](../errorcode-image.md#62980149-图片参数无效) | Invalid MIME type for the image source. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetDelayTimeList(imageSourceObj : image.ImageSource) {
  imageSourceObj.getDelayTimeList().then((delayTimes: Array<number>) => {
    console.info('Succeeded in getting delayTimes object.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get delayTimes object.code is ${err.code},message is ${err.message}`);
  })
}
```

## getDelayTimeList

```TypeScript
getDelayTimeList(callback: AsyncCallback<Array<number>>): void
```

获取图像延迟时间数组。使用callback异步回调。此接口仅用于gif图片和webp图片。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;number&gt;&gt; | 是 | 回调函数，当获取图像延迟时间数组成功，err为undefined，data为获取到的图像延时时间数组；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980110](../errorcode-image.md#62980110-图片源数据错误) | The image source data is incorrect. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |
| [62980118](../errorcode-image.md#62980118-创建插件失败) | Failed to create the image plugin. |
| [62980122](../errorcode-image.md#62980122-解码图片头异常) | Failed to decode the image header. |
| [62980149](../errorcode-image.md#62980149-图片参数无效) | Invalid MIME type for the image source. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetDelayTimeList(imageSourceObj : image.ImageSource) {
  imageSourceObj.getDelayTimeList((err: BusinessError, delayTimes: Array<number>) => {
    if (err) {
      console.error(`Failed to get delayTimes object.code is ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in getting delayTimes object.');
    }
  })
}
```

## getDisposalTypeList

```TypeScript
getDisposalTypeList(): Promise<Array<number>>
```

获取图像帧过渡模式数组。使用Promise异步回调。此接口仅用于gif图片。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Array &lt;number&gt;&gt; | Promise对象，返回帧过渡模式数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980101](../errorcode-image.md#62980101-图片输入数据错误) | The image data is abnormal. |
| [62980137](../errorcode-image.md#62980137-图片操作无效) | Invalid media operation. |
| [62980149](../errorcode-image.md#62980149-图片参数无效) | Invalid MIME type for the image source. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetDisposalTypeList(imageSourceObj : image.ImageSource) {
  imageSourceObj.getDisposalTypeList().then((disposalTypes: Array<number>) => {
    console.info('Succeeded in getting disposalTypes object.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get disposalTypes object.code ${err.code},message is ${err.message}`);
  })
}
```

## getFrameCount

```TypeScript
getFrameCount(): Promise<number>
```

获取图像帧数。使用Promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象，返回图像帧数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980112](../errorcode-image.md#62980112-图片格式不匹配) | The image format does not match. |
| [62980113](../errorcode-image.md#62980113-图片未知格式) | Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |
| [62980118](../errorcode-image.md#62980118-创建插件失败) | Failed to create the image plugin. |
| [62980122](../errorcode-image.md#62980122-解码图片头异常) | Failed to decode the image header. |
| [62980137](../errorcode-image.md#62980137-图片操作无效) | Invalid media operation. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetFrameCount(imageSourceObj : image.ImageSource) {
  imageSourceObj.getFrameCount().then((frameCount: number) => {
    console.info('Succeeded in getting frame count.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get frame count.code is ${err.code},message is ${err.message}`);
  })
}
```

## getFrameCount

```TypeScript
getFrameCount(callback: AsyncCallback<number>): void
```

获取图像帧数。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，当获取图像帧数成功，err为undefined，data为获取到的图像帧数；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980112](../errorcode-image.md#62980112-图片格式不匹配) | The image format does not match. |
| [62980113](../errorcode-image.md#62980113-图片未知格式) | Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |
| [62980118](../errorcode-image.md#62980118-创建插件失败) | Failed to create the image plugin. |
| [62980122](../errorcode-image.md#62980122-解码图片头异常) | Failed to decode the image header. |
| [62980137](../errorcode-image.md#62980137-图片操作无效) | Invalid media operation. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetFrameCount(imageSourceObj : image.ImageSource) {
  imageSourceObj.getFrameCount((err: BusinessError, frameCount: number) => {
    if (err) {
      console.error(`Failed to get frame count.code is ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in getting frame count.');
    }
  })
}
```

## getImageInfo

```TypeScript
getImageInfo(index: number, callback: AsyncCallback<ImageInfo>): void
```

获取指定序号的图片信息。使用callback异步回调。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 创建ImageSource时的序号。默认值为0，表示第一张图片。当取值为N时，表示第N+1张图片。单帧图片场景中index取值只能为0，动图等多帧图片场景中index的取值范围为： [0, (帧数-1)]。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ImageInfo](arkts-image-image-imageinfo-i.md)&gt; | 是 | 回调函数。当获取图片信息成功，err为undefined，data为获取到的图片信息；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageInfo(imageSourceObj : image.ImageSource) {
  imageSourceObj.getImageInfo(0, (error: BusinessError, imageInfo: image.ImageInfo) => {
    if (error) {
      console.error(`Failed to obtain the image information.code is ${error.code}, message is ${error.message}`);
    } else {
      console.info('Succeeded in obtaining the image information.');
    }
  })
}
```

## getImageInfo

```TypeScript
getImageInfo(callback: AsyncCallback<ImageInfo>): void
```

获取图片信息。使用callback异步回调。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ImageInfo](arkts-image-image-imageinfo-i.md)&gt; | 是 | 回调函数。当获取图片信息成功，err为undefined，data为获取到的图片信息；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageInfo(imageSourceObj : image.ImageSource) {
  imageSourceObj.getImageInfo((err: BusinessError, imageInfo: image.ImageInfo) => {
    if (err) {
      console.error(`Failed to obtain the image information.code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('Succeeded in obtaining the image information.');
    }
  })
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getImageInfo(pixelMap: image.PixelMap) {
  pixelMap.getImageInfo((err: BusinessError, imageInfo: image.ImageInfo) => {
    if (err) {
      console.error(`Failed to obtain information of the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in obtaining information of the PixelMap with size ${imageInfo.size} and pixel format ${imageInfo.pixelFormat}.`);
  });
}
```

## getImageInfo

```TypeScript
getImageInfo(index?: number): Promise<ImageInfo>
```

获取图片信息。使用Promise异步回调。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 否 | 创建ImageSource时的序号。默认值为0，表示第一张图片。当取值为N时，表示第N+1张图片。单帧图片场景中index取值只能为0，动图等多帧图片场景中index的取值范围为： [0, (帧数-1)]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ImageInfo](arkts-image-image-imageinfo-i.md)&gt; | Promise对象，返回获取到的图片信息。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageInfo(imageSourceObj : image.ImageSource) {
  imageSourceObj.getImageInfo(0)
    .then((imageInfo: image.ImageInfo) => {
      console.info('Succeeded in obtaining the image information.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to obtain the image information.code is ${error.code}, message is ${error.message}`);
    })
}
```

## getImageInfoSync

```TypeScript
getImageInfoSync(index?: number): ImageInfo
```

获取指定序号的图片信息，使用同步形式返回图片信息。

> **说明：**
> 
> 该方法为同步方法，调用时会阻塞当前线程，不建议在主线程中调用，否则可能导致应用卡顿、掉帧或响应延迟。具体场景参考
> [耗时任务并发场景简介](../../../arkts-utils/time-consuming-task-overview.md)。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 否 | 创建ImageSource时的序号。默认值为0，表示第一张图片。当取值为N时，表示第N+1张图片。单帧图片场景中index取值只能为0，动图等多帧图片场景中index的取值范围为： [0, (帧数-1)]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageInfo](arkts-image-image-imageinfo-i.md) | 同步返回获取到的图片信息。 |

**示例**

```TypeScript
function GetImageInfoSync(context : Context) {
  // 此处'test.jpg'仅作示例，请开发者自行替换，否则imageSource创建失败会导致后续无法正常执行。
  let filePath: string = context.filesDir + "/test.jpg";
  let imageSource = image.createImageSource(filePath);
  let imageInfo = imageSource.getImageInfoSync(0);
  if (imageInfo == undefined) {
    console.error('Failed to obtain the image information.');
  } else {
    console.info('Succeeded in obtaining the image information.');
    console.info('imageInfo.size.height:' + imageInfo.size.height);
    console.info('imageInfo.size.width:' + imageInfo.size.width);
  }
}
```

## getImageProperties

```TypeScript
getImageProperties(key: Array<PropertyKey>): Promise<Record<PropertyKey, string|null>>
```

批量获取图片中的指定属性键的值。使用Promise异步回调。该接口仅支持JPEG、PNG、HEIF、WEBP&lt;sup&gt;23+&lt;/sup&gt;和DNG&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | Array&lt;[PropertyKey](arkts-image-image-propertykey-e.md)&gt; | 是 | 图片属性名的数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;[PropertyKey](arkts-image-image-propertykey-e.md), string \| null&gt;&gt; | Promise对象，返回图片属性值，如获取失败则返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed; |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980110](../errorcode-image.md#62980110-图片源数据错误) | The image source data is incorrect. |
| [62980113](../errorcode-image.md#62980113-图片未知格式) | Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageProperties(imageSourceObj : image.ImageSource) {
  let key = [image.PropertyKey.IMAGE_WIDTH, image.PropertyKey.IMAGE_LENGTH];
  imageSourceObj.getImageProperties(key).then((data) => {
    console.info(JSON.stringify(data));
  }).catch((err: BusinessError | BusinessError[]) => {
    if (Array.isArray(err)) {
      (err as BusinessError[]).forEach(e => {
        console.error(`Failed to get the properties, error.code ${e.code}, error.message ${e.message}`);
      });
    } else {
      console.error(`Failed to get the properties, error.code ${err.code}, error.message ${err.message}`);
    }
  });
}
```

## getImageProperty

```TypeScript
getImageProperty(key: PropertyKey, options?: ImagePropertyOptions): Promise<string>
```

获取图片中给定索引处图像的指定属性键的值。使用Promise异步回调。该接口仅支持JPEG、PNG、HEIF&lt;sup&gt;12+&lt;/sup&gt;、WEBP&lt;sup&gt;23+&lt;/sup&gt;和DNG&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [PropertyKey](arkts-image-image-propertykey-e.md) | 是 | 图片属性名。 |
| options | [ImagePropertyOptions](arkts-image-image-imagepropertyoptions-i.md) | 否 | 图片属性，包括图片序号与默认属性值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;string&gt; | Promise对象，返回图片属性值，如获取失败则返回属性默认值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types;3.Parameter verification failed; |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | The image data is not supported. |
| [62980110](../errorcode-image.md#62980110-图片源数据错误) | The image source data is incorrect. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980112](../errorcode-image.md#62980112-图片格式不匹配) | The image format does not match. |
| [62980113](../errorcode-image.md#62980113-图片未知格式) | Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980118](../errorcode-image.md#62980118-创建插件失败) | Failed to create the image plugin. |
| [62980122](../errorcode-image.md#62980122-解码图片头异常) | Failed to decode the image header. |
| [62980123](../errorcode-image.md#62980123-图片不支持exif解码) | The image does not support EXIF decoding. |
| [62980135](../errorcode-image.md#62980135-图片属性值无效) | The EXIF value is invalid. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageProperty(imageSourceObj : image.ImageSource) {
  let options: image.ImagePropertyOptions = { index: 0, defaultValue: '9999' }
  imageSourceObj.getImageProperty(image.PropertyKey.BITS_PER_SAMPLE, options)
    .then((data: string) => {
      console.info('Succeeded in getting the value of the specified attribute key of the image.');
    }).catch((error: BusinessError) => {
    console.error(`Failed to get the value of the specified attribute key of the image, error.code ${error.code}, error.message ${error.message}`);
  })
}
```

## getImageProperty

```TypeScript
getImageProperty(key: string, options?: GetImagePropertyOptions): Promise<string>
```

获取图片中给定索引处图像的指定属性键的值。使用Promise异步回调。该接口仅支持JPEG、PNG、HEIF&lt;sup&gt;12+&lt;/sup&gt;和WEBP&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

> **说明：**
> 
> 从API version 7开始支持，从API version 11废弃，建议使用
> [getImageProperty](#getimageproperty)代
> 替。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [getImageProperty](#getimageproperty)(key: PropertyKey, options?: ImagePropertyOptions)

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 图片属性名。 |
| options | [GetImagePropertyOptions](arkts-image-image-getimagepropertyoptions-i.md) | 否 | 图片属性，包括图片序号与默认属性值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;string&gt; | Promise对象，返回图片属性值，如获取失败则返回属性默认值。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageProperty(imageSourceObj : image.ImageSource) {
  imageSourceObj.getImageProperty("BitsPerSample")
    .then((data: string) => {
      console.info('Succeeded in getting the value of the specified attribute key of the image.');
    }).catch((error: BusinessError) => {
    console.error(`Failed to get the value of the specified attribute key of the image, error.code ${error.code}, error.message ${error.message}`);
  })
}
```

## getImageProperty

```TypeScript
getImageProperty(key: string, callback: AsyncCallback<string>): void
```

获取图片中给定索引处图像的指定属性键的值。使用callback异步回调。该接口仅支持JPEG、PNG、HEIF&lt;sup&gt;12+&lt;/sup&gt;和WEBP&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

> **说明：**
> 
> 从API version 7开始支持，从API version 11废弃，建议使用
> [getImageProperty](#getimageproperty)代
> 替。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [getImageProperty](#getimageproperty)(key: PropertyKey, options?: ImagePropertyOptions)

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 图片属性名。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，当获取图片属性值成功，err为undefined，data为获取到的图片属性值；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageProperty(imageSourceObj : image.ImageSource) {
  imageSourceObj.getImageProperty("BitsPerSample", (error: BusinessError, data: string) => {
    if (error) {
      console.error('Failed to get the value of the specified attribute key of the image.');
    } else {
      console.info('Succeeded in getting the value of the specified attribute key of the image.');
    }
  })
}
```

## getImageProperty

```TypeScript
getImageProperty(key: string, options: GetImagePropertyOptions, callback: AsyncCallback<string>): void
```

获取图片指定属性键的值。使用callback异步回调。该接口仅支持JPEG、PNG、HEIF&lt;sup&gt;12+&lt;/sup&gt;和WEBP&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

> **说明：**
> 
> 从API version 7开始支持，从API version 11废弃，建议使用
> [getImageProperty](#getimageproperty)代
> 替。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [getImageProperty](#getimageproperty)(key: PropertyKey, options?: ImagePropertyOptions)

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 图片属性名。 |
| options | [GetImagePropertyOptions](arkts-image-image-getimagepropertyoptions-i.md) | 是 | 图片属性，包括图片序号与默认属性值。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，当获取图片属性值成功，err为undefined，data为获取到的图片属性值；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageProperty(imageSourceObj : image.ImageSource) {
  let property: image.GetImagePropertyOptions = { index: 0, defaultValue: '9999' }
  imageSourceObj.getImageProperty("BitsPerSample", property, (error: BusinessError, data: string) => {
    if (error) {
      console.error('Failed to get the value of the specified attribute key of the image.');
    } else {
      console.info('Succeeded in getting the value of the specified attribute key of the image.');
    }
  })
}
```

## getImagePropertySync

```TypeScript
getImagePropertySync(key: PropertyKey): string
```

获取图片Exif指定属性键的值，使用同步形式返回结果。

> **说明：**
> 
> - 该方法仅支持JPEG、PNG、HEIF、WEBP&lt;sup&gt;23+&lt;/sup&gt;和DNG&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。
> 
> - Exif信息是图片的元数据，包含拍摄时间、相机型号、光圈、焦距、ISO等。
> 
> - 该方法为同步方法，调用时会阻塞当前线程，不建议在主线程中调用，否则可能导致应用卡顿、掉帧或响应延迟。具体场景参考
> [耗时任务并发场景简介](../../../arkts-utils/time-consuming-task-overview.md)。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [PropertyKey](arkts-image-image-propertykey-e.md) | 是 | 图片属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回图片Exif中指定属性键的值（如获取失败则返回属性默认值），各个数据值作用请参考[PropertyKey]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700101](../errorcode-image.md#7700101-图片源存在问题) | Bad source. e.g.,1. Image has invalid width or height. 2. Image source incomplete. 3. Read image data failed. 4. Codec create failed. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |
| [7700202](../errorcode-image.md#7700202-不支持的元数据) | Unsupported metadata. For example, key is not supported. |

**示例**

```TypeScript
function GetImagePropertySync(context : Context) {
  let resourceMgr = context.resourceManager;
  if (resourceMgr == null) {
    return;
  }
  let fd = resourceMgr.getRawFdSync("example.jpg");

  const imageSourceObj = image.createImageSource(fd);
  console.info("getImagePropertySync");
  let bits_per_sample = imageSourceObj.getImagePropertySync(image.PropertyKey.BITS_PER_SAMPLE);
  console.info("bits_per_sample : " + bits_per_sample);
}
```

## modifyImageProperties

```TypeScript
modifyImageProperties(records: Record<PropertyKey, string|null>): Promise<void>
```

批量通过指定的键修改图片属性的值。使用Promise异步回调。该接口仅支持JPEG、PNG、HEIF和WEBP&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

> **说明：**
> 
> - 调用modifyImageProperties修改属性会改变属性字节长度，使用buffer创建的ImageSource调用modifyImageProperties会导致buffer内容覆盖，目前buffer创建的
> ImageSource不支持调用此接口，请改用fd或path创建的ImageSource。
> 
> - 调用modifyImageProperties接口修改Exif字段时，必须确保对应的图片文件有写权限，否则会导致字段修改不成功。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| records | Record&lt;[PropertyKey](arkts-image-image-propertykey-e.md), string \| null&gt; | 是 | 包含图片属性名和属性值的数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed; |
| [62980123](../errorcode-image.md#62980123-图片不支持exif解码) | The image does not support EXIF decoding. |
| [62980135](../errorcode-image.md#62980135-图片属性值无效) | The EXIF value is invalid. |
| [62980146](../errorcode-image.md#62980146-图片属性值写入文件失败) | The EXIF data failed to be written to the file. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function ModifyImageProperties(imageSourceObj : image.ImageSource) {
  let keyValues: Record<PropertyKey, string|null> = {
    [image.PropertyKey.IMAGE_WIDTH] : "1024",
    [image.PropertyKey.IMAGE_LENGTH] : "1024"
  };
  let checkKey = [image.PropertyKey.IMAGE_WIDTH, image.PropertyKey.IMAGE_LENGTH];
  imageSourceObj.modifyImageProperties(keyValues).then(() => {
    imageSourceObj.getImageProperties(checkKey).then((data) => {
      console.info(`Image Width and Image Height:${data}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to modify the Image Width and Image Height, error.code ${err.code}, error.message ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to modify the Image Width and Image Height, error.code ${err.code}, error.message ${err.message}`);
  });
}
```

## modifyImagePropertiesEnhanced

```TypeScript
modifyImagePropertiesEnhanced(records: Record<string, string | null>): Promise<void>
```

批量修改图片属性。使用Promise异步回调。

> **说明：**
> 
> - 调用该接口修改属性会改变属性字节长度，建议通过传入文件描述符来创建[image.createImageSource](arkts-image-image-createimagesource-f.md)实例或通过传入的uri创建
> [image.createImageSource](arkts-image-image-createimagesource-f.md)实例。
> 
> - 该方法在内存中完成批量数据修改后会一次性写入文件，相比
> [modifyImageProperties](#modifyimageproperties)
> 更高效。
> 
> - 支持修改JPEG、PNG、HEIF和WEBP文件类型的图片属性，图片需要包含Exif信息。
> 
> - 调用modifyImagePropertiesEnhanced接口修改Exif字段时，必须确保对应的图片文件有写权限，否则会导致字段修改不成功。

**起始版本：** 22

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| records | Record &lt;string, string \ | null&gt; | 是 | 包含图片属性名和属性值的键值对集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |
| [7700202](../errorcode-image.md#7700202-不支持的元数据) | Unsupported metadata. For example, the property key is not supported, or the property value is invalid. |
| [7700304](../errorcode-image.md#7700304-图片信息写入文件失败) | Failed to write image properties to the file. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function ModifyImagePropertiesEnhanced(imageSourceObj : image.ImageSource) {
  let keyValues: Record<string, string|null> = {
    "ImageWidth" : "1024",
    "ImageLength" : "1024"
  };
  let checkKey = [image.PropertyKey.IMAGE_WIDTH, image.PropertyKey.IMAGE_LENGTH];
  imageSourceObj.modifyImagePropertiesEnhanced(keyValues).then(() => {
    imageSourceObj.getImageProperties(checkKey).then((data) => {
      console.info(`Image Width and Image Height:${data}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to modify the Image Width and Image Height, error.code ${err.code}, error.message ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to modify the Image Width and Image Height, error.code ${err.code}, error.message ${err.message}`);
  });
}
```

## modifyImageProperty

```TypeScript
modifyImageProperty(key: PropertyKey, value: string): Promise<void>
```

通过指定的键修改图片属性的值。使用Promise异步回调。该接口仅支持JPEG、PNG、HEIF&lt;sup&gt;12+&lt;/sup&gt;和WEBP&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

> **说明：**
> 
> - 调用modifyImageProperty修改属性会改变属性字节长度，使用buffer创建的ImageSource调用modifyImageProperty会导致buffer内容覆盖，目前buffer创建的
> ImageSource不支持调用此接口，请改用fd或path创建的ImageSource。
> 
> - 调用modifyImageProperty接口修改Exif字段时，必须确保对应的图片文件有写权限，否则会导致字段修改不成功。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [PropertyKey](arkts-image-image-propertykey-e.md) | 是 | 图片属性名。 |
| value | string | 是 | 属性值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; |
| [62980123](../errorcode-image.md#62980123-图片不支持exif解码) | The image does not support EXIF decoding. |
| [62980133](../errorcode-image.md#62980133-图片属性赋值超出范围) | The EXIF data is out of range. |
| [62980135](../errorcode-image.md#62980135-图片属性值无效) | The EXIF value is invalid. |
| [62980146](../errorcode-image.md#62980146-图片属性值写入文件失败) | The EXIF data failed to be written to the file. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function ModifyImageProperty(imageSourceObj : image.ImageSource) {
  imageSourceObj.modifyImageProperty(image.PropertyKey.IMAGE_WIDTH, "120").then(() => {
    imageSourceObj.getImageProperty(image.PropertyKey.IMAGE_WIDTH).then((width: string) => {
      console.info(`ImageWidth is :${width}`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to get the Image Width, error.code ${error.code}, error.message ${error.message}`);
    })
  }).catch((error: BusinessError) => {
    console.error(`Failed to modify the Image Width, error.code ${error.code}, error.message ${error.message}`);
  })
}
```

## modifyImageProperty

```TypeScript
modifyImageProperty(key: string, value: string): Promise<void>
```

通过指定的键修改图片属性的值。使用Promise异步回调。该接口仅支持JPEG、PNG、HEIF&lt;sup&gt;12+&lt;/sup&gt;和WEBP&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

> **说明：**
> 
> - 调用modifyImageProperty修改属性会改变属性字节长度，使用buffer创建的ImageSource调用modifyImageProperty会导致buffer内容覆盖，目前buffer创建的
> ImageSource不支持调用此接口，请改用fd或path创建的ImageSource。
> 
> - 从API version 9开始支持，从API version 11废弃，建议使用
> [modifyImageProperty](#modifyimageproperty)代替。
> 
> - 调用modifyImageProperty接口修改Exif字段时，必须确保对应的图片文件有写权限，否则会导致字段修改不成功。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [modifyImageProperty](#modifyimageproperty)(key: PropertyKey, value: string)

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 图片属性名。 |
| value | string | 是 | 属性值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function ModifyImageProperty(imageSourceObj : image.ImageSource) {
  imageSourceObj.modifyImageProperty("ImageWidth", "120").then(() => {
    imageSourceObj.getImageProperty("ImageWidth").then((width: string) => {
      console.info(`ImageWidth is :${width}`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to get the Image Width, error.code ${error.code}, error.message ${error.message}`);
    })
  }).catch((error: BusinessError) => {
    console.error(`Failed to modify the Image Width, error.code ${error.code}, error.message ${error.message}`);
  })
}
```

## modifyImageProperty

```TypeScript
modifyImageProperty(key: string, value: string, callback: AsyncCallback<void>): void
```

通过指定的键修改图片属性的值。使用callback异步回调。仅支持JPEG、PNG、HEIF&lt;sup&gt;12+&lt;/sup&gt;和WEBP&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

> **说明：**
> 
> - 调用modifyImageProperty修改属性会改变属性字节长度，使用buffer创建的ImageSource调用modifyImageProperty会导致buffer内容覆盖，目前buffer创建的
> ImageSource不支持调用此接口，请改用fd或path创建的ImageSource。
> 
> - 从API version 9开始支持，从API version 11废弃，建议使用
> [modifyImageProperty](#modifyimageproperty)代替。
> 
> - 调用modifyImageProperty接口修改Exif字段时，必须确保对应的图片文件有写权限，否则会导致字段修改不成功。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [modifyImageProperty](#modifyimageproperty)(key: PropertyKey, value: string)

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 图片属性名。 |
| value | string | 是 | 属性值。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，当修改图片属性值成功，err为undefined，否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function ModifyImageProperty(imageSourceObj : image.ImageSource) {
  imageSourceObj.modifyImageProperty("ImageWidth", "120", (err: BusinessError) => {
    if (err) {
      console.error(`Failed to modify the Image Width.code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('Succeeded in modifying the Image Width.');
    }
  })
}
```

## readImageMetadata

```TypeScript
readImageMetadata(propertyKeys?: string[], index?: number): Promise<ImageMetadata>
```

读取图像源的元数据，使用propertyKeys指定元数据字段。使用Promise异步回调。该接口仅支持JPEG、PNG、HEIF、WebP、DNG、GIF、TIFF、HEIFS、JFIF和AVIS（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

> **说明：**
> 
> 读取DNG格式图片时，该接口对部分propertyKeys有特殊处理。以下字段的字符串取值请参考[PropertyKey](arkts-image-image-propertykey-e.md)中的值：
> 
> - NewSubfileType、ImageWidth、ImageLength、DefaultCropSize、Orientation、Compression、PhotometricInterpretation、
> PlanarConfiguration、RowsPerStrip、StripOffsets、StripByteCounts、SamplesPerPixel、BitsPerSample、YCbCrCoefficients、
> YCbCrSubSampling、YCbCrPositioning、ReferenceBlackWhite、XResolution、YResolution、ResolutionUnit字段：返回主图相关的字段值。
> 
> - ImageUniqueID字段：根据规范进行校验，不符合规范时会返回空字符串。
> 
> - ExifVersion、FlashpixVersion、ColorSpace字段：当图片中不存在该标签时，返回错误码。
> 
> - DNGVersion字段：当版本号小于1.0.0.0时，统一返回1.0.0.0。
> 
> - GPSVersionID字段：当没有有效的GPS数据时，会清除GPS版本号并返回0。
> 
> - GPSAltitudeRef字段：当未设置GPSAltitude时，会设置为0xFFFFFFFF。
> 
> - ISOSpeedRatings字段：当该标签值为0或65535时，会优先使用推荐曝光指数，若不存在则依次使用标准输出灵敏度、ISO速度、曝光指数。
> 
> 该接口支持读取以下格式的元数据：
> 
> - 从API version 24开始，支持读取DNG元数据。要查询的属性的具体信息请参考[DngPropertyKey](arkts-image-image-dngpropertykey-e.md)。
> 
> - 从API version 24开始，支持读取HEIFS元数据。要查询的属性的具体信息请参考[HeifsPropertyKey](arkts-image-image-heifspropertykey-e.md)。
> 
> - 从API版本26.0.0开始，支持读取PNG元数据。要查询的属性的具体信息请参考[PngPropertyKey](arkts-image-image-pngpropertykey-e.md)。
> 
> - 从API版本26.0.0开始，支持读取JFIF元数据。要查询的属性的具体信息请参考[JfifPropertyKey](arkts-image-image-jfifpropertykey-e.md)。
> 
> - 从API版本26.0.0开始，支持读取TIFF元数据。要查询的属性的具体信息请参考[TiffPropertyKey](arkts-image-image-tiffpropertykey-e.md)。
> 
> - 从API版本26.0.0开始，支持读取GIF元数据。要查询的属性的具体信息请参考[GifPropertyKey](arkts-image-image-gifpropertykey-e.md)。
> 
> - 从API版本26.0.0开始，支持读取JPEG、PNG、GIF、DNG、TIFF格式图片的XMP元数据。XMP元数据的操作方法可以参考
> [XMPMetadata](arkts-image-image-xmpmetadata-c.md)。
> 
> - 从API版本26.0.0开始，支持读取AVIS元数据。要查询的属性的具体信息请参考[AvisPropertyKey](arkts-image-image-avispropertykey-e.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propertyKeys | string[] | 否 | 图片属性名的数组。若未指定propertyKeys，则返回所有支持的元数据。 |
| index | number | 否 | 感兴趣的索引，默认值为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ImageMetadata](arkts-image-image-imagemetadata-i.md)&gt; | Promise对象，返回ImageMetadata对象，其中含有图片属性名对应的metadata对象，通过ImageMetadata中的metadata对 象可以获取图片属性值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |
| [7700202](../errorcode-image.md#7700202-不支持的元数据) | Unsupported metadata. |
| [7700204](../errorcode-image.md#7700204-无效参数) | Invalid parameter. Possible causes: 1. The index is negative. 2. The index is greater than or equal to the number of frames in the image. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function ReadImageMetadata(imageSourceObj : image.ImageSource) {
  let propertyKeys = ["ImageWidth", "HwMnoteIsXmageSupported"];
  await imageSourceObj.readImageMetadata(propertyKeys).then((metaData: image.ImageMetadata) => {
    if (metaData != undefined && metaData.exifMetadata != undefined &&
      metaData.makerNoteHuaweiMetadata != undefined) {
      console.info("ImageWidth: " + metaData.exifMetadata.imageWidth +
        " HwMnoteIsXmageSupported: " + metaData.makerNoteHuaweiMetadata.isXmageSupported);
    }
  }).catch((error: BusinessError) => {
    console.error(`Failed to read image metadata. error.code is ${error.code}, error.message is ${error.message}`);
  })
}
```

## readImageMetadataByType

```TypeScript
readImageMetadataByType(metadataTypes?: MetadataType[], index?: number): Promise<ImageMetadata>
```

读取图像源的元数据，使用metadataTypes指定元数据类型。若未指定metadataTypes，则返回所有支持的元数据。使用Promise异步回调。该接口仅支持JPEG、PNG、HEIF、WebP、DNG、GIF、TIFF、HEIFS、JFIF和AVIS（不同硬件设备支持情况不同）文件。

> **说明：**
> 
> - EXIF_METADATA元数据类型适用于JPEG、PNG、HEIF、WEBP和DNG格式图片。
> 
> - HEIFS_METADATA元数据类型适用于HEIFS格式图片。
> 
> - 当传入的MetadataType与图片格式无法匹配时，返回错误码7700102。
> 
> - 从API version 24开始，支持读取DNG元数据。要查询的属性的具体信息请参考[DngPropertyKey](arkts-image-image-dngpropertykey-e.md)。
> 
> - 从API version 24开始，支持读取HEIFS元数据。要查询的属性的具体信息请参考[HeifsPropertyKey](arkts-image-image-heifspropertykey-e.md)。
> 
> - 从API版本26.0.0开始，支持读取PNG元数据。要查询的属性的具体信息请参考[PngPropertyKey](arkts-image-image-pngpropertykey-e.md)。
> 
> - 从API版本26.0.0开始，支持读取JFIF元数据。要查询的属性的具体信息请参考[JfifPropertyKey](arkts-image-image-jfifpropertykey-e.md)。
> 
> - 从API版本26.0.0开始，支持读取TIFF元数据。要查询的属性的具体信息请参考[TiffPropertyKey](arkts-image-image-tiffpropertykey-e.md)。
> 
> - 从API版本26.0.0开始，支持读取GIF元数据。要查询的属性的具体信息请参考[GifPropertyKey](arkts-image-image-gifpropertykey-e.md)。
> 
> - 从API版本26.0.0开始，支持读取JPEG、PNG、GIF、DNG、TIFF格式图片的XMP元数据。XMP元数据的操作方法可以参考
> [XMPMetadata](arkts-image-image-xmpmetadata-c.md)。
> 
> - 从API版本26.0.0开始，支持读取AVIS元数据。要查询的属性的具体信息请参考[AvisPropertyKey](arkts-image-image-avispropertykey-e.md)。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| metadataTypes | [MetadataType](arkts-image-image-metadatatype-e.md)[] | 否 | 元数据类型的数组。当该参数缺省时，获取全部支持的元数据。 |
| index | number | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ImageMetadata](arkts-image-image-imagemetadata-i.md)&gt; | Promise对象。返回的ImageMetadata对象中含有对应的metadata对象，通过ImageMetadata中的metadata对象可以获取图 片属性值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |
| [7700202](../errorcode-image.md#7700202-不支持的元数据) | Unsupported metadata. |
| [7700204](../errorcode-image.md#7700204-无效参数) | Invalid parameter. Possible causes: 1.The index is negative. 2. The index is greater than or equal to the number of frames in the image. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

async function ReadImageMetadataByType(imageSource : image.ImageSource, type: image.MetadataType) {
  let types: image.MetadataType[] = [type];
  await imageSource.readImageMetadataByType(types, 0).then((metaData: image.ImageMetadata) => {
    if (metaData != undefined && metaData.exifMetadata != undefined) {
      console.info("ImageWidth: " + metaData.exifMetadata.imageWidth);
    }
  }).catch((error: BusinessError) => {
    console.error(`Failed to read image metadata by type. error.code is ${error.code}, error.message is ${error.message}`);
  })
}
```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放ImageSource实例。使用callback异步回调。由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用该方法，及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 6

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，当资源释放成功，err为undefined，否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(img : image.Image) {
  img.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release the image instance.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in releasing the image instance.');
    }
  })
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(creator : image.ImageCreator) {
  creator.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release the creator.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in releasing creator.');
    }
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Release() {
  const imagePackerObj: image.ImagePacker = image.createImagePacker();
  imagePackerObj.release((err: BusinessError)=>{
    if (err) {
      console.error(`Failed to release image packaging.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in releasing image packaging.');
    }
  })
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(receiver : image.ImageReceiver) {
  receiver.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release the receiver.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in releasing the receiver.');
    }
  })
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(imageSourceObj : image.ImageSource) {
  imageSourceObj.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release the image source instance.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in releasing the image source instance.');
    }
  })
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function release(pixelMap: image.PixelMap) {
  pixelMap.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release the PixelMap object. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in releasing the PixelMap object.');
  });
}
```

## release

```TypeScript
release(): Promise<void>
```

释放ImageSource实例。使用Promise异步回调。由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用该方法，及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 6

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(img : image.Image) {
  img.release().then(() => {
    console.info('Succeeded in releasing the image instance.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release the image instance.code ${error.code},message is ${error.message}`);
  })
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(creator : image.ImageCreator) {
  creator.release().then(() => {
    console.info('Succeeded in releasing creator.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release the creator.code ${error.code},message is ${error.message}`);
  })
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Release() {
  const imagePackerObj: image.ImagePacker = image.createImagePacker();
  imagePackerObj.release().then(() => {
    console.info('Succeeded in releasing image packaging.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release image packaging.code ${error.code},message is ${error.message}`);
  })
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(receiver : image.ImageReceiver) {
  receiver.release().then(() => {
    console.info('Succeeded in releasing the receiver.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release the receiver.code ${error.code},message is ${error.message}`);
  })
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(imageSourceObj : image.ImageSource) {
  imageSourceObj.release().then(() => {
    console.info('Succeeded in releasing the image source instance.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release the image source instance.code ${error.code},message is ${error.message}`);
  })
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function release(pixelMap: image.PixelMap) {
  pixelMap.release().then(() => {
    console.info('Succeeded in releasing the PixelMap object.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to release the PixelMap object. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## updateData

```TypeScript
updateData(buf: ArrayBuffer, isFinished: boolean, offset: number, length: number): Promise<void>
```

更新增量数据。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | 存放增量数据的buffer。 |
| isFinished | boolean | 是 | true表示数据更新完成，当前buffer内存放最后一段数据；false表示数据还未更新完成，需要继续更新。 |
| offset | number | 是 | 即当前buffer中的数据首地址，相对于整个图片文件首地址的偏移量。单位：字节（Byte）。<br>**起始版本：** 11 |
| length | number | 是 | 当前buffer的长度。单位：字节（Byte）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function UpdateDatay(imageSourceObj : image.ImageSource) {
  const array: ArrayBuffer = new ArrayBuffer(100);
  imageSourceObj.updateData(array, false, 0, 10).then(() => {
    console.info('Succeeded in updating data.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to update data.code is ${err.code},message is ${err.message}`);
  })
}
```

## updateData

```TypeScript
updateData(
      buf: ArrayBuffer,
      isFinished: boolean,
      offset: number,
      length: number,
      callback: AsyncCallback<void>
    ): void
```

更新增量数据。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | 存放增量数据的buffer。 |
| isFinished | boolean | 是 | true表示数据更新完成，当前buffer内存放最后一段数据；false表示数据还未更新完成，需要继续更新。 |
| offset | number | 是 | 即当前buffer中的数据首地址，相对于整个图片文件首地址的偏移量。单位：字节（Byte）。<br>**起始版本：** 11 |
| length | number | 是 | 当前buffer的长度。单位：字节（Byte）。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，当更新增量数据成功，err为undefined，否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function UpdateDatay(imageSourceObj : image.ImageSource) {
  const array: ArrayBuffer = new ArrayBuffer(100);
  imageSourceObj.updateData(array, false, 0, 10, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to update data.code is ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in updating data.');
    }
  })
}
```

## writeImageMetadata

```TypeScript
writeImageMetadata(imageMetadata: ImageMetadata): Promise<void>
```

批量修改图片属性。使用Promise异步回调。

> **说明：**
> 
> - 调用该接口修改属性会改变属性字节长度，建议通过传入文件描述符来创建[image.createImageSource](arkts-image-image-createimagesource-f.md)实例或通过传入的uri创建
> [image.createImageSource](arkts-image-image-createimagesource-f.md)实例。
> 
> - 该方法在内存中完成批量数据修改后会一次性写入文件，相比
> [modifyImageProperties](#modifyimageproperties)
> 更高效。
> 
> - 支持修改JPEG、PNG和HEIF文件类型的图片属性，图片需要包含Exif信息。修改属性前，先通过supportedFormats属性查询设备是否支持HEIF格式的Exif读写。
> 
> - 从API版本26.0.0开始，支持修改JPEG、PNG、GIF格式图片的XMP元数据。XMP元数据的操作方法可以参考
> [XMPMetadata](arkts-image-image-xmpmetadata-c.md)。
> 
> - 调用writeImageMetadata接口修改Exif字段时，必须确保对应的图片文件有写权限，否则会导致字段修改不成功。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imageMetadata | [ImageMetadata](arkts-image-image-imagemetadata-i.md) | 是 | 图像的元数据集。若imageMetadata中的属性值都为空，则清空所有Exif元数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |
| [7700202](../errorcode-image.md#7700202-不支持的元数据) | Unsupported metadata. |
| [7700204](../errorcode-image.md#7700204-无效参数) | Invalid parameter. Possible causes: The imageSource object is released. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function WriteImageMetadata(imageSourceObj : image.ImageSource) {
  let propertyKeys = ["ImageWidth", "HwMnoteIsXmageSupported"];
  let metaData = await imageSourceObj.readImageMetadata(propertyKeys);
  if (metaData != undefined && metaData.exifMetadata != undefined) {
    metaData.exifMetadata.imageLength = 3072;
  }
  await imageSourceObj.writeImageMetadata(metaData).then(() => {
    console.info(`Succeeded in writing image metadata.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to write image metadata. error.code is ${error.code}, error.message is ${error.message}`);
  });
}
```

## supportedFormats

```TypeScript
readonly supportedFormats: Array<string>
```

支持的图片格式。包括：PNG、JPEG、BMP、GIF、WebP、DNG、HEIC&lt;sup&gt;12+&lt;/sup&gt;、WBMP&lt;sup&gt;23+&lt;/sup&gt;、HEIFS&lt;sup&gt;23+&lt;/sup&gt;、TIFF&lt;sup&gt;23+&lt;/sup&gt;。从API版本2 6.0.0开始，增加支持AVIF、AVIS格式。部分格式的解码能力依赖于具体的设备硬件，建议在调用前使用[image.getImageSourceSupportedFormats](arkts-image-image-getimagesourcesupportedformats-f.md)接口， 动态查询当前设备上的解码能力。

**类型：** Array&lt;string&gt;

**起始版本：** 6

**系统能力：** SystemCapability.Multimedia.Image.ImageSource
