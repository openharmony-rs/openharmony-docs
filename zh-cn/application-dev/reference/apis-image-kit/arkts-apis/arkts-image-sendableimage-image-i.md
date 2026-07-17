# Image

提供基本的图像操作，包括获取图像信息、读写图像数据。调用[readNextImage](arkts-image-sendableimage-imagereceiver-i.md#readnextimage-1)和[readLatestImage](arkts-image-sendableimage-imagereceiver-i.md#readlatestimage-1)接口时会返回Image。继承自[ISendable](../../../../arkts-utils/arkts-sendable.md#isendable)。

由于图片占用内存较大，所以当Image实例使用完成后，应主动调用[release](arkts-image-sendableimage-pixelmap-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**继承/实现关系：** Image extends [lang.ISendable](../../apis-arkts/arkts-apis/arkts-arkts-lang-isendable-i.md)

**起始版本：** 12

<!--Device-sendableImage-interface Image extends lang.ISendable--><!--Device-sendableImage-interface Image extends lang.ISendable-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## getComponent

```TypeScript
getComponent(componentType: image.ComponentType): Promise<image.Component>
```

根据图像的组件类型从图像中获取组件缓存。使用Promise异步回调。getComponent是线程不安全的。

**起始版本：** 12

<!--Device-Image-getComponent(componentType: image.ComponentType): Promise<image.Component>--><!--Device-Image-getComponent(componentType: image.ComponentType): Promise<image.Component>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| componentType | image.ComponentType | 是 | 图像的组件类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<image.Component> | Promise实例，用于异步返回组件缓冲区。 |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

async function GetComponent() {
  let size: image.Size = {
    height: 8192,
    width: 8
  }
  let receiver: sendableImage.ImageReceiver = sendableImage.createImageReceiver(size, image.ImageFormat.JPEG, 8);
  let img = await receiver.readNextImage();
  img.getComponent(image.ComponentType.JPEG).then((component: image.Component) => {
    console.info('Succeeded in getting an image component.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to get an image component. Code: ${error.code}, message: ${error.message}.`);
  })
}

```

## release

```TypeScript
release(): Promise<void>
```

释放当前图像。使用Promise异步回调。

在接收另一个图像前必须先释放对应资源。

由于图片占用内存较大，所以当Image实例使用完成后，应主动调用该方法及时释放内存。

释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 12

<!--Device-Image-release(): Promise<void>--><!--Device-Image-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | promise返回操作结果。 |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

async function Release() {
  let size: image.Size = {
    height: 8192,
    width: 8
  }
  let receiver: sendableImage.ImageReceiver = sendableImage.createImageReceiver(size, image.ImageFormat.JPEG, 8);
  let img = await receiver.readNextImage();
  img.release().then(() => {
    console.info('Succeeded in releasing an image.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release an image. Code: ${error.code}, message: ${error.message}.`);
  })
}

```

## clipRect

```TypeScript
clipRect: Region
```

要裁剪的图像区域。

**类型：** Region

**起始版本：** 12

<!--Device-Image-clipRect: Region--><!--Device-Image-clipRect: Region-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## format

```TypeScript
readonly format: number
```

图像格式，参考[OH_NativeBuffer_Format](../../../../reference/apis-arkgraphics2d/capi-buffer-common-h.md#oh_nativebuffer_format)。

**类型：** number

**起始版本：** 12

<!--Device-Image-readonly format: number--><!--Device-Image-readonly format: number-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## size

```TypeScript
readonly size: Size
```

图像大小。

如果Image对象所存储的是相机预览流数据（YUV图像数据），那么获取到的size中的宽和高分别对应YUV图像的宽和高。

如果Image对象所存储的是相机拍照流数据（JPEG图像数据），由于已是编码后的文件，size中的宽等于JPEG文件大小，高等于1。

Image对象所存储的数据是预览流还是拍照流，取决于应用将receiver中的surfaceId传给相机的是previewOutput还是captureOutput。

相机预览与拍照最佳实践请参考[双路预览(ArkTS)](../../../../media/camera/camera-dual-channel-preview.md)与[拍照实践(ArkTS)](../../../../media/camera/camera-shooting-case.md)。

**类型：** Size

**起始版本：** 12

<!--Device-Image-readonly size: Size--><!--Device-Image-readonly size: Size-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## timestamp

```TypeScript
readonly timestamp: number
```

图像时间戳。时间戳以纳秒为单位，通常是单调递增的。时间戳的具体含义和基准取决于图像的生产者，在相机预览/拍照场景，生产者就是相机。来自不同生产者的图像的时间戳可能有不同的含义和基准，因此可能无法进行比较。如果要获取某张照片的生成时间，可以通过[getImageProperty](arkts-image-image-imagesource-i.md#getimageproperty-1)接口读取相关的EXIF信息。

**类型：** number

**起始版本：** 12

<!--Device-Image-readonly timestamp: number--><!--Device-Image-readonly timestamp: number-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

