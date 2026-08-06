# AuxiliaryPicture

AuxiliaryPicture类，用于读取或写入图像的辅助图数据以及获取图像的辅助图信息。目前支持的辅助图类型可参考[AuxiliaryPictureType]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 。 在调用AuxiliaryPicture的方法前，需要通过[image.createAuxiliaryPicture]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_或Picture的 [getAuxiliaryPicture]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_创建一个AuxiliaryPicture实例。 由于图片占用内存较大，所以当AuxiliaryPicture对象使用完成后，应主动调用[release]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_方法及时释放对象。释放时应确保该实例的所有异步方法 均执行完成，且后续不再使用该对象。 > **说明：** > > - 本Interface首批接口从API version 13开始支持。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-image-interface AuxiliaryPicture--><!--Device-image-interface AuxiliaryPicture-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## getAuxiliaryPictureInfo

```TypeScript
getAuxiliaryPictureInfo(): AuxiliaryPictureInfo
```

获取有关此辅助图的图像信息。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

<!--Device-AuxiliaryPicture-getAuxiliaryPictureInfo(): AuxiliaryPictureInfo--><!--Device-AuxiliaryPicture-getAuxiliaryPictureInfo(): AuxiliaryPictureInfo-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回辅助图图像信息。 |

## getAuxiliaryPictureInfo

```TypeScript
getAuxiliaryPictureInfo(): AuxiliaryPictureInfo | undefined
```

Obtains the information about this auxiliary picture.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AuxiliaryPicture-getAuxiliaryPictureInfo(): AuxiliaryPictureInfo | undefined--><!--Device-AuxiliaryPicture-getAuxiliaryPictureInfo(): AuxiliaryPictureInfo | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns the auxiliary picture information. If the operation fails, |

## getMetadata

```TypeScript
getMetadata(metadataType: MetadataType): Promise<Metadata>
```

从辅助图中获取元数据。使用Promise异步回调。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

<!--Device-AuxiliaryPicture-getMetadata(metadataType: MetadataType): Promise<Metadata>--><!--Device-AuxiliaryPicture-getMetadata(metadataType: MetadataType): Promise<Metadata>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| metadataType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 元数据类型，用于获取对应类型的元数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Metadata&gt; | Promise对象，返回元数据的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [7600202](../errorcode-image.md#7600202-不支持的元数据读写) | Unsupported metadata. Possible causes: 1. Unsupported metadata type. 2. The metadata type does not match the auxiliary picture type. |

## getMetadata

```TypeScript
getMetadata(metadataType: MetadataType): Promise<Metadata | undefined>
```

Obtains the metadata of auxiliary picture.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AuxiliaryPicture-getMetadata(metadataType: MetadataType): Promise<Metadata | undefined>--><!--Device-AuxiliaryPicture-getMetadata(metadataType: MetadataType): Promise<Metadata | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| metadataType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The type of metadata. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Metadata \| undefined&gt; | Return the metadata of auxiliary picture. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600202](../errorcode-image.md#7600202-不支持的元数据读写) | Unsupported metadata. Possible causes: 1. Unsupported metadata type. 2. The metadata type does not match the auxiliary picture type. |

## getType

```TypeScript
getType(): AuxiliaryPictureType
```

获取辅助图的类型。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

<!--Device-AuxiliaryPicture-getType(): AuxiliaryPictureType--><!--Device-AuxiliaryPicture-getType(): AuxiliaryPictureType-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 操作成功，返回辅助图的类型。 |

## getType

```TypeScript
getType(): AuxiliaryPictureType | undefined
```

Obtains the type of auxiliary picture.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AuxiliaryPicture-getType(): AuxiliaryPictureType | undefined--><!--Device-AuxiliaryPicture-getType(): AuxiliaryPictureType | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns the type of auxiliary picture. |

## readPixelsToBuffer

```TypeScript
readPixelsToBuffer(): Promise<ArrayBuffer>
```

读取图像像素映射数据并将数据写入ArrayBuffer。使用Promise异步回调。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

<!--Device-AuxiliaryPicture-readPixelsToBuffer(): Promise<ArrayBuffer>--><!--Device-AuxiliaryPicture-readPixelsToBuffer(): Promise<ArrayBuffer>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise对象。返回辅助图像素数据。 |

## readPixelsToBuffer

```TypeScript
readPixelsToBuffer(): Promise<ArrayBuffer | undefined>
```

Reads image pixel map data and writes the data to an ArrayBuffer. This method uses a promise to return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AuxiliaryPicture-readPixelsToBuffer(): Promise<ArrayBuffer | undefined>--><!--Device-AuxiliaryPicture-readPixelsToBuffer(): Promise<ArrayBuffer | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ArrayBuffer \| undefined&gt; | A Promise instance used to return the pixel map data. |

## release

```TypeScript
release():void
```

释放辅助图对象，无返回值。 由于图片占用内存较大，所以当AuxiliaryPicture对象使用完成后，应主动调用该方法，及时释放内存。 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-AuxiliaryPicture-release():void--><!--Device-AuxiliaryPicture-release():void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## setAuxiliaryPictureInfo

```TypeScript
setAuxiliaryPictureInfo(info: AuxiliaryPictureInfo): void
```

设置辅助图的图像信息。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-AuxiliaryPicture-setAuxiliaryPictureInfo(info: AuxiliaryPictureInfo): void--><!--Device-AuxiliaryPicture-setAuxiliaryPictureInfo(info: AuxiliaryPictureInfo): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 辅助图的图像信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |

## setMetadata

```TypeScript
setMetadata(metadataType: MetadataType, metadata: Metadata): Promise<void>
```

设置辅助图元数据。使用Promise异步回调。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-AuxiliaryPicture-setMetadata(metadataType: MetadataType, metadata: Metadata): Promise<void>--><!--Device-AuxiliaryPicture-setMetadata(metadataType: MetadataType, metadata: Metadata): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| metadataType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 元数据的类型，用于设置对应的元数据。 |
| metadata | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 元数据对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [7600202](../errorcode-image.md#7600202-不支持的元数据读写) | Unsupported metadata. Possible causes: 1. Unsupported metadata type. 2. The metadata type does not match the auxiliary picture type. |

## writePixelsFromBuffer

```TypeScript
writePixelsFromBuffer(data: ArrayBuffer): Promise<void>
```

读取ArrayBuffer中的辅助图片数据，并将数据写入AuxiliaryPicture对象。使用Promise异步回调。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-AuxiliaryPicture-writePixelsFromBuffer(data: ArrayBuffer): Promise<void>--><!--Device-AuxiliaryPicture-writePixelsFromBuffer(data: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | ArrayBuffer | 是 | 辅助图像素数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |

