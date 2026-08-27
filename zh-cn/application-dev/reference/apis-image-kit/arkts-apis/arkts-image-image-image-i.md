# Image

Image类，供ImageReceiver和ImageCreator使用，用于传输图片对象，其实际内容由生产者决定。如相机预览流提供的Image对象存储了YUV数据、相机拍照提供的Image对象存储了JPEG文件。调用[readNextImage](arkts-image-image-imagereceiver-i.md#readnextimage)和 [readLatestImage](arkts-image-image-imagereceiver-i.md#readlatestimage)接口时会返回Image实例。Image的属性仅支持在创建时初始化，后续无法再修改，且其属性不对图片内容产生实际影响，请以图片生产者写入的属性为准，即以向[ImageReceiver](arkts-image-image-imagereceiver-i.md)发送图片数据的发送方实 际写入的内容为准。由于图片占用内存较大，所以当Image实例使用完成后，应主动调用[release](#release)方法及时释放内存。释放时应确保该 实例的所有异步方法均执行完成，且后续不再使用该实例。

> **说明：**
> 
> - 本Interface首批接口从API version 9开始支持。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## getBufferData

```TypeScript
getBufferData(): ImageBufferData | null
```

从图像中获取ImageBufferData。

> **注意：**
> 
> ImageBufferData中的byteBuffer是对内部缓存的浅拷贝，当Image的生命周期结束时，便不能对byteBuffer做任何操作，否则会导致未定义行为。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageBufferData](arkts-image-image-imagebufferdata-i.md) \| null | 获取封装图像数据缓冲区的结构体，获取不到时返回空值。 |

**示例**

```TypeScript
function GetBufferData(img: image.Image) {
  const bufferData = img.getBufferData();
  if (bufferData == null) {
    console.error('Failed to get the bufferData: bufferData is null.');
    return;
  }
  console.info('Succeeded in getting bufferData.');
}
```

## getComponent

```TypeScript
getComponent(componentType: ComponentType, callback: AsyncCallback<Component>): void
```

根据图像的组件类型从图像中获取组件缓存。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| componentType | ComponentType | 是 | 图像的组件类型（目前仅支持ComponentType:JPEG，实际返回格式由生产者决定，如相机）。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Component&gt; | 是 | 回调函数，当返回组件缓冲区成功，err为undefined，data为获取到的组件缓冲区；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetComponent(img : image.Image) {
  img.getComponent(image.ComponentType.JPEG, (err: BusinessError, component: image.Component) => {
    if (err) {
      console.error(`Failed to get the component.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in getting component.');
    }
  })
}
```

## getComponent

```TypeScript
getComponent(componentType: ComponentType): Promise<Component>
```

根据图像的组件类型从图像中获取组件缓存。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| componentType | ComponentType | 是 | 图像的组件类型（目前仅支持ComponentType:JPEG，实际返回格式由生产者决定，如相机）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Component & gt; | Promise对象，返回组件缓冲区。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetComponent(img : image.Image) {
  img.getComponent(image.ComponentType.JPEG).then((component: image.Component) => {
    console.info('Succeeded in getting component.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to get the component.code ${error.code},message is ${error.message}`);
  })
}
```

## getMetadata

```TypeScript
getMetadata(key: HdrMetadataKey): HdrMetadataValue | null
```

根据HDR元数据的类型从图像中获取HDR元数据。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md) | 是 | HDR元数据的关键字，可用于查询对应值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HdrMetadataValue](arkts-image-image-hdrmetadatavalue-t.md) \| null | 返回关键字对应的HDR元数据的值。如果图像没有HDR元数据，返回空值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Memory copy failed. |

**示例**

```TypeScript
async function GetMetadata(img : image.Image) {
  try {
    let staticMetadata = img.getMetadata(image.HdrMetadataKey.HDR_STATIC_METADATA);
    console.info(`getMetadata:${staticMetadata}`);
  } catch (err) {
    console.error('Failed to getMetadata.' + err);
  }
}
```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放当前图像。使用callback异步回调。在接收另一个图像前必须先释放对应资源。由于图片占用内存较大，所以当Image实例使用完成后，应主动调用该方法，及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，当图像释放成功，err为undefined，否则为错误对象。 |

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

释放当前图像。使用Promise异步回调。在接收另一个图像前必须先释放对应资源。由于图片占用内存较大，所以当Image实例使用完成后，应主动调用该方法，及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

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

## clipRect

```TypeScript
clipRect: Region
```

要裁剪的图像区域。恒等于整个图像，不支持修改。

**类型：** Region

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

## colorSpace

```TypeScript
readonly colorSpace: colorSpaceManager.ColorSpace
```

图像色彩空间，色域枚举类型。

**类型：** colorSpaceManager.ColorSpace

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## format

```TypeScript
readonly format: number
```

图像格式，参考 [OH_NativeBuffer_Format](../../../reference/apis-arkgraphics2d/capi-buffer-common-h.md#oh_nativebuffer_format)。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

## size

```TypeScript
readonly size: Size
```

图像大小。如果Image对象所存储的是相机预览流数据（YUV图像数据），那么获取到的size中的宽和高分别对应YUV图像的宽和高。如果Image对象所存储的是相机拍照流数据（JPEG图像数据），由于已是编码后的文件，size中的宽等于JPEG文件大小，高等于1。Image对象所存储的数据是预览流还是拍照流，取决于应用将receiver中的surfaceId通过 [createPreviewOutput](../../apis-camera-kit/arkts-apis/arkts-camera-camera-cameramanager-i.md#createpreviewoutput) 接口还是 [createPhotoOutput](../../apis-camera-kit/arkts-apis/arkts-camera-camera-cameramanager-i.md#createphotooutput) 接口传给相机。相机预览与拍照最佳实践请参考[双路预览(ArkTS)](../../../media/camera/camera-dual-channel-preview.md)与 [拍照实践(ArkTS)](../../../media/camera/camera-shooting-case.md)。

**类型：** Size

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

## timestamp

```TypeScript
readonly timestamp: number
```

图像时间戳。时间戳以纳秒为单位，通常是单调递增的。时间戳的具体含义和基准取决于图像的生产者，在相机预览/拍照场景，生产者就是相机。来自不同生产者的图像的时间戳可能有不同的含义和基准，因此可能无法进行比较。如果要获取某张照片的生 成时间，可以通过 [getImageProperty](arkts-image-image-imagesource-i.md#getimageproperty)接口读 取EXIF时间戳信息。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core
