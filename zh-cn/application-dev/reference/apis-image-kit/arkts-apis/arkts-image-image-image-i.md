# Image

Image类，供ImageReceiver和ImageCreator使用，用于传输图片对象，其实际内容由生产者决定。如相机预览流提供的Image对象存储了YUV数据、相机拍照提供的Image对象存储了JPEG文件。

调用[readNextImage](arkts-image-image-imagereceiver-i.md#readnextimage-1)和[readLatestImage](arkts-image-image-imagereceiver-i.md#readlatestimage-1)接口时会返回Image实例。

Image的属性仅支持在创建时初始化，后续无法再修改，且其属性不对图片内容产生实际影响，请以图片生产者写入的属性为准，即以向[ImageReceiver](arkts-image-image-imagereceiver-i.md)发送图片数据的发送方实际写入的内容为准。

由于图片占用内存较大，所以当Image实例使用完成后，应主动调用[release](arkts-image-image-image-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

> **说明：**  
>  
> - 本Interface首批接口从API version 9开始支持。

**起始版本：** 9

<!--Device-image-interface Image--><!--Device-image-interface Image-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

<a id="getbufferdata"></a>
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

<!--Device-Image-getBufferData(): ImageBufferData | null--><!--Device-Image-getBufferData(): ImageBufferData | null-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageBufferData](arkts-image-image-imagebufferdata-i.md) | 获取封装图像数据缓冲区的结构体，获取不到时返回空值。 |

<a id="getcomponent"></a>
## getComponent

```TypeScript
getComponent(componentType: ComponentType, callback: AsyncCallback<Component>): void
```

根据图像的组件类型从图像中获取组件缓存。使用callback异步回调。

**起始版本：** 9

<!--Device-Image-getComponent(componentType: ComponentType, callback: AsyncCallback<Component>): void--><!--Device-Image-getComponent(componentType: ComponentType, callback: AsyncCallback<Component>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| componentType | [ComponentType](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-update-componenttype-e-sys.md) | 是 | 图像的组件类型（目前仅支持ComponentType:JPEG，实际返回格式由生产者决定，如相机）。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Component&gt; | 是 | 回调函数，当返回组件缓冲区成功，err为undefined，data为获取到的组件缓冲区；否则为错误对象。 |

<a id="getcomponent-1"></a>
## getComponent

```TypeScript
getComponent(componentType: ComponentType): Promise<Component>
```

根据图像的组件类型从图像中获取组件缓存。使用Promise异步回调。

**起始版本：** 9

<!--Device-Image-getComponent(componentType: ComponentType): Promise<Component>--><!--Device-Image-getComponent(componentType: ComponentType): Promise<Component>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| componentType | [ComponentType](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-update-componenttype-e-sys.md) | 是 | 图像的组件类型（目前仅支持ComponentType:JPEG，实际返回格式由生产者决定，如相机）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Component&gt; | Promise对象，返回组件缓冲区。 |

<a id="getmetadata"></a>
## getMetadata

```TypeScript
getMetadata(key: HdrMetadataKey): HdrMetadataValue | null
```

根据HDR元数据的类型从图像中获取HDR元数据。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Image-getMetadata(key: HdrMetadataKey): HdrMetadataValue | null--><!--Device-Image-getMetadata(key: HdrMetadataKey): HdrMetadataValue | null-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md) | 是 | HDR元数据的关键字，可用于查询对应值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HdrMetadataValue](arkts-image-image-hdrmetadatavalue-t.md) | 返回关键字对应的HDR元数据的值。如果图像没有HDR元数据，返回空值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Memory copy failed. |

<a id="release"></a>
## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放当前图像。使用callback异步回调。

在接收另一个图像前必须先释放对应资源。

由于图片占用内存较大，所以当Image实例使用完成后，应主动调用该方法，及时释放内存。

释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

<!--Device-Image-release(callback: AsyncCallback<void>): void--><!--Device-Image-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，当图像释放成功，err为undefined，否则为错误对象。 |

<a id="release-1"></a>
## release

```TypeScript
release(): Promise<void>
```

释放当前图像。使用Promise异步回调。

在接收另一个图像前必须先释放对应资源。

由于图片占用内存较大，所以当Image实例使用完成后，应主动调用该方法，及时释放内存。

释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

<!--Device-Image-release(): Promise<void>--><!--Device-Image-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

## clipRect

```TypeScript
clipRect: Region
```

要裁剪的图像区域。恒等于整个图像，不支持修改。

**类型：** Region

**起始版本：** 9

<!--Device-Image-clipRect: Region--><!--Device-Image-clipRect: Region-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## colorSpace

```TypeScript
readonly colorSpace: colorSpaceManager.ColorSpace
```

图像色彩空间，色域枚举类型。

**类型：** colorSpaceManager.ColorSpace

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Image-readonly colorSpace: colorSpaceManager.ColorSpace--><!--Device-Image-readonly colorSpace: colorSpaceManager.ColorSpace-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## format

```TypeScript
readonly format: number
```

图像格式，参考[OH_NativeBuffer_Format](docroot://reference/apis-arkgraphics2d/capi-buffer-common-h.md#oh_nativebuffer_format)。

**类型：** number

**起始版本：** 9

<!--Device-Image-readonly format: int--><!--Device-Image-readonly format: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## size

```TypeScript
readonly size: Size
```

图像大小。

如果Image对象所存储的是相机预览流数据（YUV图像数据），那么获取到的size中的宽和高分别对应YUV图像的宽和高。

如果Image对象所存储的是相机拍照流数据（JPEG图像数据），由于已是编码后的文件，size中的宽等于JPEG文件大小，高等于1。

Image对象所存储的数据是预览流还是拍照流，取决于应用将receiver中的surfaceId通过[createPreviewOutput](@ohos.multimedia.camera:camera.CameraManager.createPreviewOutput(profile: Profile, surfaceId: string))接口还是[createPhotoOutput](@ohos.multimedia.camera:camera.CameraManager.createPhotoOutput(profile: Profile, surfaceId: string))接口传给相机。

相机预览与拍照最佳实践请参考[双路预览(ArkTS)](docroot://media/camera/camera-dual-channel-preview.md)与[拍照实践(ArkTS)](docroot://media/camera/camera-shooting-case.md)。

**类型：** Size

**起始版本：** 9

<!--Device-Image-readonly size: Size--><!--Device-Image-readonly size: Size-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## timestamp

```TypeScript
readonly timestamp: number
```

图像时间戳。时间戳以纳秒为单位，通常是单调递增的。时间戳的具体含义和基准取决于图像的生产者，在相机预览/拍照场景，生产者就是相机。来自不同生产者的图像的时间戳可能有不同的含义和基准，因此可能无法进行比较。如果要获取某张照片的生成时间，可以通过[getImageProperty](arkts-image-image-imagesource-i.md#getimageproperty-1)接口读取EXIF时间戳信息。

**类型：** number

**起始版本：** 12

<!--Device-Image-readonly timestamp: long--><!--Device-Image-readonly timestamp: long-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

