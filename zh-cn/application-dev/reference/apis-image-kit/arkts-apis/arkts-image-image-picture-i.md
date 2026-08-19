# Picture

Picture类，一些包含特殊信息的图片可以解码为Picture（也可以称为多图对象）。多图对象一般包含主图、辅助图和元数据。其中主图包含图像的大部分信息，主要用于显示图像内容；辅助图用于存储与主图相关但不同的数据，展示图像更丰富 的信息；元数据一般用来存储关于图像文件的信息。多图对象类用于读取或写入多图对象。在调用Picture的方法前，需要先通过[image.createPicture](arkts-image-image-createpicture-f.md)创建一个 Picture实例。 由于图片占用内存较大，所以当Picture实例使用完成后，应主动调用[release](#release)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 > **说明：** > > - 本Interface首批接口从API version 13开始支持。

**起始版本：** 23

<!--Device-image-interface Picture--><!--Device-image-interface Picture-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## getAuxiliaryPicture

```TypeScript
getAuxiliaryPicture(type: AuxiliaryPictureType): AuxiliaryPicture | null
```

根据类型获取辅助图。

**起始版本：** 23

<!--Device-Picture-getAuxiliaryPicture(type: AuxiliaryPictureType): AuxiliaryPicture | null--><!--Device-Picture-getAuxiliaryPicture(type: AuxiliaryPictureType): AuxiliaryPicture | null-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [AuxiliaryPictureType](arkts-image-image-auxiliarypicturetype-e.md) | 是 | 辅助图类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AuxiliaryPicture](arkts-image-image-auxiliarypicture-i.md) | 返回AuxiliaryPicture对象，如果没有则返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

## getGainmapPixelmap

```TypeScript
getGainmapPixelmap(): PixelMap | null
```

获取增益图的pixelmap。

**起始版本：** 23

<!--Device-Picture-getGainmapPixelmap(): PixelMap | null--><!--Device-Picture-getGainmapPixelmap(): PixelMap | null-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | 返回Pixelmap对象，如果没有则返回null。 |

## getHdrComposedPixelmap

```TypeScript
getHdrComposedPixelmap(): Promise<PixelMap>
```

合成HDR图并获取HDR图的pixelmap。使用Promise异步回调。

**起始版本：** 13

<!--Device-Picture-getHdrComposedPixelmap(): Promise<PixelMap>--><!--Device-Picture-getHdrComposedPixelmap(): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap&gt; | Promise对象，返回PixelMap。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600901](../errorcode-image.md#7600901-未知错误) | Inner unknown error. Please check the logs for detailed information. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation. e.g.,1. The picture does not has a gainmap. 2. MainPixelMap's allocator type is not DMA. |

## getHdrComposedPixelmap

```TypeScript
getHdrComposedPixelmap(): Promise<PixelMap | undefined>
```

Obtains the hdr pixel map. This method uses a promise to return the PixelMap object.

**起始版本：** 23

<!--Device-Picture-getHdrComposedPixelmap(): Promise<PixelMap | undefined>--><!--Device-Picture-getHdrComposedPixelmap(): Promise<PixelMap | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap \| undefined&gt; | A Promise instance used to return the PixelMap object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600901](../errorcode-image.md#7600901-未知错误) | Unknown error. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation. |

## getHdrComposedPixelmapWithOptions

```TypeScript
getHdrComposedPixelmapWithOptions(options?: HdrComposeOptions): Promise<PixelMap | undefined>
```

合成HDR图像并返回HDR图像的PixelMap，支持传入合成参数（如PixelMapFormat等）。使用Promise异步回调。 调用该接口的Picture对象中必须包含主图、增益图和元数据。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Picture-getHdrComposedPixelmapWithOptions(options?: HdrComposeOptions): Promise<PixelMap | undefined>--><!--Device-Picture-getHdrComposedPixelmapWithOptions(options?: HdrComposeOptions): Promise<PixelMap | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [HdrComposeOptions](arkts-image-image-hdrcomposeoptions-i.md) | 否 | 合成HDR的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap \| undefined&gt; | Promise对象，返回PixelMap或undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation. |

## getMainPixelmap

```TypeScript
getMainPixelmap(): PixelMap
```

获取主图的pixelmap。

**起始版本：** 13

<!--Device-Picture-getMainPixelmap(): PixelMap--><!--Device-Picture-getMainPixelmap(): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | 同步返回PixelMap对象。 |

## getMainPixelmap

```TypeScript
getMainPixelmap(): PixelMap | undefined
```

Obtains the pixel map of the main image.

**起始版本：** 23

<!--Device-Picture-getMainPixelmap(): PixelMap | undefined--><!--Device-Picture-getMainPixelmap(): PixelMap | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | Returns the pixel map. |

## getMetadata

```TypeScript
getMetadata(metadataType: MetadataType): Promise<Metadata>
```

获取主图的元数据。使用Promise异步回调。

**起始版本：** 13

<!--Device-Picture-getMetadata(metadataType: MetadataType): Promise<Metadata>--><!--Device-Picture-getMetadata(metadataType: MetadataType): Promise<Metadata>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| metadataType | [MetadataType](arkts-image-image-metadatatype-e.md) | 是 | 元数据类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Metadata&gt; | Promise对象。返回元数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [7600202](../errorcode-image.md#7600202-不支持的元数据读写) | Unsupported metadata. Possible causes: 1. Unsupported metadata type. 2. The metadata type does not match the auxiliary picture type. |

## getMetadata

```TypeScript
getMetadata(metadataType: MetadataType): Promise<Metadata | undefined>
```

Obtains the metadata of main picture.

**起始版本：** 23

<!--Device-Picture-getMetadata(metadataType: MetadataType): Promise<Metadata | undefined>--><!--Device-Picture-getMetadata(metadataType: MetadataType): Promise<Metadata | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| metadataType | [MetadataType](arkts-image-image-metadatatype-e.md) | 是 | The type of metadata. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Metadata \| undefined&gt; | Return the metadata of main picture. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600202](../errorcode-image.md#7600202-不支持的元数据读写) | Unsupported metadata. Possible causes: Unsupported metadata type. |

## hdrComposeToMainPixelmap

```TypeScript
hdrComposeToMainPixelmap(): Promise<void>
```

将Picture对象的主图和增益图合成为HDR图，合成后原Picture的主图被替换为HDR图，原Picture的增益图被删除。使用Promise异步回调。 调用该接口的Picture对象中必须包含主图、增益图。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Picture-hdrComposeToMainPixelmap(): Promise<void>--><!--Device-Picture-hdrComposeToMainPixelmap(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation. e.g.,1. The picture does not have a gainmap. 2. pixelMap's allocator type is not DMA. |

## marshalling

```TypeScript
marshalling(sequence: rpc.MessageSequence): void
```

将picture序列化后写入MessageSequence。

**起始版本：** 23

<!--Device-Picture-marshalling(sequence: rpc.MessageSequence): void--><!--Device-Picture-marshalling(sequence: rpc.MessageSequence): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sequence | rpc.MessageSequence | 是 | 新创建的MessageSequence。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980097](../errorcode-image.md#62980097-pixelmap序列化传输失败) | IPC error. Possible cause: 1.IPC communication failed. 2. Image upload exception. 3. Decode process exception. 4. Insufficient memory. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

## release

```TypeScript
release(): void
```

释放picture对象。 由于图片占用内存较大，所以当Picture对象使用完成后，应主动调用该方法及时释放内存。 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 23

<!--Device-Picture-release(): void--><!--Device-Picture-release(): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## setAuxiliaryPicture

```TypeScript
setAuxiliaryPicture(type: AuxiliaryPictureType, auxiliaryPicture: AuxiliaryPicture): void
```

设置辅助图。

**起始版本：** 23

<!--Device-Picture-setAuxiliaryPicture(type: AuxiliaryPictureType, auxiliaryPicture: AuxiliaryPicture): void--><!--Device-Picture-setAuxiliaryPicture(type: AuxiliaryPictureType, auxiliaryPicture: AuxiliaryPicture): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [AuxiliaryPictureType](arkts-image-image-auxiliarypicturetype-e.md) | 是 | 辅助图类型。 |
| auxiliaryPicture | [AuxiliaryPicture](arkts-image-image-auxiliarypicture-i.md) | 是 | 辅助图对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

## setMainPixelmap

```TypeScript
setMainPixelmap(pixelmap: PixelMap): void
```

设置图片的PixelMap对象。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Picture-setMainPixelmap(pixelmap: PixelMap): void--><!--Device-Picture-setMainPixelmap(pixelmap: PixelMap): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelmap | PixelMap | 是 | PixelMap对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700204](../errorcode-image.md#7700204-无效参数) | 参数错误。 |

## setMetadata

```TypeScript
setMetadata(metadataType: MetadataType, metadata: Metadata): Promise<void>
```

设置主图的元数据。使用Promise异步回调。

**起始版本：** 23

<!--Device-Picture-setMetadata(metadataType: MetadataType, metadata: Metadata): Promise<void>--><!--Device-Picture-setMetadata(metadataType: MetadataType, metadata: Metadata): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| metadataType | [MetadataType](arkts-image-image-metadatatype-e.md) | 是 | 元数据类型。 |
| metadata | Metadata | 是 | 元数据对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [7600202](../errorcode-image.md#7600202-不支持的元数据读写) | Unsupported metadata. Possible causes: 1. Unsupported metadata type. 2. The metadata type does not match the auxiliary picture type. |

