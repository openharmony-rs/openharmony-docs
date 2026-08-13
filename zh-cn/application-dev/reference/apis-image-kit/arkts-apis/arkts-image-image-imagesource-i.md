# ImageSource

ImageSource类，用于获取图片相关信息。 在调用ImageSource的方法前，需要先通过[image.createImageSource](arkts-image-image-createimagesource-f.md#createImageSource)构建一个ImageSource实例。 ImageSource的所有方法均不支持并发调用。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](#release)方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-image-interface ImageSource--><!--Device-image-interface ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## createImageRawData

```TypeScript
createImageRawData(): Promise<ImageRawData>
```

获取图片原始数据。使用Promise异步回调。目前仅支持获取DNG图片类型的原始数据。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageSource-createImageRawData(): Promise<ImageRawData>--><!--Device-ImageSource-createImageRawData(): Promise<ImageRawData>-End-->

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

## createPicture

```TypeScript
createPicture(options?: DecodingOptionsForPicture): Promise<Picture>
```

通过图片解码参数创建Picture对象。使用Promise异步回调。 由于图片占用内存较大，所以当Picture对象使用完成后，应主动调用[release](arkts-image-image-picture-i.md#release)方法，及时释放内存。 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**废弃版本：** -1

<!--Device-ImageSource-createPicture(options?: DecodingOptionsForPicture): Promise<Picture>--><!--Device-ImageSource-createPicture(options?: DecodingOptionsForPicture): Promise<Picture>-End-->

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

## createPicture

```TypeScript
createPicture(options?: DecodingOptionsForPicture): Promise<Picture | undefined>
```

Creates a Picture object based on image decoding parameters. This method uses a promise to return the object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-createPicture(options?: DecodingOptionsForPicture): Promise<Picture | undefined>--><!--Device-ImageSource-createPicture(options?: DecodingOptionsForPicture): Promise<Picture | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptionsForPicture](arkts-image-image-decodingoptionsforpicture-i.md) | 否 | Image decoding parameters. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Picture](arkts-image-image-picture-i.md) \| undefined&gt; | A Promise instance used to return the Picture object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700301](../errorcode-image.md#7700301-解码失败) | Failed to decode image. |

## createPictureAtIndex

```TypeScript
createPictureAtIndex(index: int): Promise<Picture>
```

通过指定序号的图片创建Picture对象。使用Promise异步回调。 > **说明：** > > - 支持GIF和HEIF&lt;sup&gt;23+&lt;/sup&gt;图像序列格式。从API版本26.0.0开始，增加支持AVIS格式。 > > - 由于图片占用内存较大，所以当Picture对象使用完成后，应主动调用[release](arkts-image-image-picture-i.md#release)方法，及时释放内存。 > > - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-ImageSource-createPictureAtIndex(index: int): Promise<Picture>--><!--Device-ImageSource-createPictureAtIndex(index: int): Promise<Picture>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 解码图片序号。图片序号有效的取值范围为：[0, (帧数-1)]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Picture](arkts-image-image-picture-i.md)&gt; | Promise对象，返回Picture。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700101](../errorcode-image.md#7700101-图片源存在问题) | Bad source. |
| [7700103](../errorcode-image.md#7700103-图片太大) | Image too large. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |
| [7700301](../errorcode-image.md#7700301-解码失败) | Decoding failed. |
| [7700203](../errorcode-image.md#7700203-不支持的选项) | Unsupported options. For example, index is invalid. |

## createPictureAtIndex

```TypeScript
createPictureAtIndex(index : int): Promise<Picture | undefined>
```

Decodes an image at the specified index into a Picture object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-createPictureAtIndex(index : int): Promise<Picture | undefined>--><!--Device-ImageSource-createPictureAtIndex(index : int): Promise<Picture | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | Image index. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Picture](arkts-image-image-picture-i.md) \| undefined&gt; | Promise that returns the Picture object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700101](../errorcode-image.md#7700101-图片源存在问题) | Bad source. |
| [7700103](../errorcode-image.md#7700103-图片太大) | Image too large. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |
| [7700301](../errorcode-image.md#7700301-解码失败) | Decoding failed. |
| [7700203](../errorcode-image.md#7700203-不支持的选项) | Unsupported options. For example, index is invalid. |

## createPixelMap

```TypeScript
createPixelMap(options?: DecodingOptions): Promise<PixelMap>
```

通过图片解码参数创建PixelMap对象。使用Promise异步回调。 从API version 15开始，推荐使用[createPixelMapUsingAllocator](arkts-image-image-createpixelmapusingallocator-f.md#createPixelMapUsingAllocator)，该接口可以指定输出pixelMap的 内存类型[AllocatorType](arkts-image-image-allocatortype-e.md#AllocatorType)，详情请参考 [图片解码内存优化(ArkTS)](../../../media/image/image-allocator-type.md)。 > **说明：** > > - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。 > > - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。 > > - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageSource-createPixelMap(options?: DecodingOptions): Promise<PixelMap>--><!--Device-ImageSource-createPixelMap(options?: DecodingOptions): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 否 | 解码参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap&gt; | Promise对象，返回PixelMap。 |

## createPixelMap

```TypeScript
createPixelMap(options?: DecodingOptions): Promise<PixelMap | undefined>
```

Creates a PixelMap object based on image decoding parameters. This method uses a promise to return the object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-createPixelMap(options?: DecodingOptions): Promise<PixelMap | undefined>--><!--Device-ImageSource-createPixelMap(options?: DecodingOptions): Promise<PixelMap | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 否 | Image decoding parameters. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap \| undefined&gt; | A Promise instance used to return the PixelMap object. |

## createPixelMap

```TypeScript
createPixelMap(callback: AsyncCallback<PixelMap>): void
```

通过默认参数创建PixelMap对象。使用callback异步回调。 从API version 15开始，推荐使用[createPixelMapUsingAllocator](arkts-image-image-createpixelmapusingallocator-f.md#createPixelMapUsingAllocator)，该接口可以指定输出pixelMap的 内存类型[AllocatorType](arkts-image-image-allocatortype-e.md#AllocatorType)，详情请参考 [图片解码内存优化(ArkTS)](../../../media/image/image-allocator-type.md)。 > **说明：** > > - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。 > > - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。 > > - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageSource-createPixelMap(callback: AsyncCallback<PixelMap>): void--><!--Device-ImageSource-createPixelMap(callback: AsyncCallback<PixelMap>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;PixelMap&gt; | 是 | 回调函数，当创建PixelMap对象成功，err为undefined，data为获取到的PixelMap对象；否则为错误对象。 |

## createPixelMap

```TypeScript
createPixelMap(callback: AsyncCallback<PixelMap | undefined>): void
```

Creates a PixelMap object. This method uses a callback to return the object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-createPixelMap(callback: AsyncCallback<PixelMap | undefined>): void--><!--Device-ImageSource-createPixelMap(callback: AsyncCallback<PixelMap | undefined>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;PixelMap \| undefined&gt; | 是 | Callback used to return the PixelMap object. |

## createPixelMap

```TypeScript
createPixelMap(options: DecodingOptions, callback: AsyncCallback<PixelMap>): void
```

通过图片解码参数创建PixelMap对象。使用callback异步回调。 从API version 15开始，推荐使用[createPixelMapUsingAllocator](arkts-image-image-createpixelmapusingallocator-f.md#createPixelMapUsingAllocator)，该接口可以指定输出pixelMap的 内存类型[AllocatorType](arkts-image-image-allocatortype-e.md#AllocatorType)，详情请参考 [图片解码内存优化(ArkTS)](../../../media/image/image-allocator-type.md)。 > **说明：** > > - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。 > > - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。 > > - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageSource-createPixelMap(options: DecodingOptions, callback: AsyncCallback<PixelMap>): void--><!--Device-ImageSource-createPixelMap(options: DecodingOptions, callback: AsyncCallback<PixelMap>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 是 | 解码参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;PixelMap&gt; | 是 | 回调函数，当创建PixelMap对象成功，err为undefined，data为获取到的PixelMap对象；否则为错误对象。 |

## createPixelMap

```TypeScript
createPixelMap(options: DecodingOptions, callback: AsyncCallback<PixelMap | undefined>): void
```

Creates a PixelMap object based on image decoding parameters. This method uses a callback to return the object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-createPixelMap(options: DecodingOptions, callback: AsyncCallback<PixelMap | undefined>): void--><!--Device-ImageSource-createPixelMap(options: DecodingOptions, callback: AsyncCallback<PixelMap | undefined>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 是 | Image decoding parameters. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;PixelMap \| undefined&gt; | 是 | Callback used to return the PixelMap object. |

## createPixelMapList

```TypeScript
createPixelMapList(options?: DecodingOptions): Promise<Array<PixelMap>>
```

通过图片解码参数创建PixelMap数组。使用Promise异步回调。 针对动态图（如Gif、Webp），该接口会返回每帧图片数据；针对静态图，该接口会返回唯一的一帧图片数据。 > **说明：** > > - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。 > > - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。 > > - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。 > > - 此接口会一次性解码全部帧，当帧数过多或单帧图像过大时（如2000×3000像素的100帧GIF动图），会占用较大内存，造成系统内存紧张，此种情况推荐使用Image组件显示动图，Image组件采用逐帧解码，占用内存比此接 > 口少。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-createPixelMapList(options?: DecodingOptions): Promise<Array<PixelMap>>--><!--Device-ImageSource-createPixelMapList(options?: DecodingOptions): Promise<Array<PixelMap>>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 否 | 解码参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;PixelMap&gt;&gt; | 异步返回PixelMap数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980099](../errorcode-image.md#62980099-共享内存数据异常) | The shared memory data is abnormal. |
| [62980101](../errorcode-image.md#62980101-图片输入数据错误) | The image data is abnormal. |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | The image data is not supported. |
| [62980137](../errorcode-image.md#62980137-图片操作无效) | Invalid media operation. |
| [62980106](../errorcode-image.md#62980106-图片数据太大) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| [62980109](../errorcode-image.md#62980109-裁剪错误) | Failed to crop the image. |
| [62980173](../errorcode-image.md#62980173-dma内存空间错误) | The DMA memory does not exist. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980174](../errorcode-image.md#62980174-dma内存数据异常) | The DMA memory data is abnormal. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |
| [62980118](../errorcode-image.md#62980118-创建插件失败) | Failed to create the image plugin. |

## createPixelMapList

```TypeScript
createPixelMapList(callback: AsyncCallback<Array<PixelMap>>): void
```

通过默认参数创建PixelMap数组。使用callback异步回调。 针对动态图（如Gif、Webp），该接口会返回每帧图片数据；针对静态图，该接口会返回唯一的一帧图片数据。 > **说明：** > > - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。 > > - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。 > > - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。 > > - 此接口会一次性解码全部帧，当帧数过多或单帧图像过大时，会占用较大内存，造成系统内存紧张，此种情况推荐使用Image组件显示动图，Image组件采用逐帧解码，占用内存比此接口少。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-createPixelMapList(callback: AsyncCallback<Array<PixelMap>>): void--><!--Device-ImageSource-createPixelMapList(callback: AsyncCallback<Array<PixelMap>>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;PixelMap&gt;&gt; | 是 | 回调函数，当创建PixelMap对象数组成功，err为undefined，data为获取到的PixelMap对象数组；否 则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980099](../errorcode-image.md#62980099-共享内存数据异常) | The shared memory data is abnormal. |
| [62980101](../errorcode-image.md#62980101-图片输入数据错误) | The image data is abnormal. |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | The image data is not supported. |
| [62980137](../errorcode-image.md#62980137-图片操作无效) | Invalid media operation. |
| [62980106](../errorcode-image.md#62980106-图片数据太大) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| [62980109](../errorcode-image.md#62980109-裁剪错误) | Failed to crop the image. |
| [62980173](../errorcode-image.md#62980173-dma内存空间错误) | The DMA memory does not exist. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980174](../errorcode-image.md#62980174-dma内存数据异常) | The DMA memory data is abnormal. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |
| [62980118](../errorcode-image.md#62980118-创建插件失败) | Failed to create the image plugin. |

## createPixelMapList

```TypeScript
createPixelMapList(options: DecodingOptions, callback: AsyncCallback<Array<PixelMap>>): void
```

通过图片解码参数创建PixelMap数组。使用callback异步回调。 针对动态图（如Gif、Webp），该接口会返回每帧图片数据；针对静态图，该接口会返回唯一的一帧图片数据。 > **说明：** > > - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。 > > - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。 > > - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。 > > - 此接口会一次性解码全部帧，当帧数过多或单帧图像过大时，会占用较大内存，造成系统内存紧张，此种情况推荐使用Image组件显示动图，Image组件采用逐帧解码，占用内存比此接口少。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-createPixelMapList(options: DecodingOptions, callback: AsyncCallback<Array<PixelMap>>): void--><!--Device-ImageSource-createPixelMapList(options: DecodingOptions, callback: AsyncCallback<Array<PixelMap>>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 是 | 解码参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;PixelMap&gt;&gt; | 是 | 回调函数，当创建PixelMap对象数组成功，err为undefined，data为获取到的PixelMap对象数组；否 则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980099](../errorcode-image.md#62980099-共享内存数据异常) | The shared memory data is abnormal. |
| [62980101](../errorcode-image.md#62980101-图片输入数据错误) | The image data is abnormal. |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | The image data is not supported. |
| [62980137](../errorcode-image.md#62980137-图片操作无效) | Invalid media operation. |
| [62980106](../errorcode-image.md#62980106-图片数据太大) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| [62980109](../errorcode-image.md#62980109-裁剪错误) | Failed to crop the image. |
| [62980173](../errorcode-image.md#62980173-dma内存空间错误) | The DMA memory does not exist. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980174](../errorcode-image.md#62980174-dma内存数据异常) | The DMA memory data is abnormal. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |
| [62980118](../errorcode-image.md#62980118-创建插件失败) | Failed to create the image plugin. |

## createPixelMapSync

```TypeScript
createPixelMapSync(options?: DecodingOptions): PixelMap
```

通过图片解码参数同步创建PixelMap对象。 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。 从API version 15开始，推荐使用[createPixelMapUsingAllocatorSync](arkts-image-image-createpixelmapusingallocatorsync-f.md#createPixelMapUsingAllocatorSync)，该接口可以指定输出 pixelMap的内存类型[AllocatorType](arkts-image-image-allocatortype-e.md#AllocatorType)，详情请参考 [图片解码内存优化(ArkTS)](../../../media/image/image-allocator-type.md)。 > **说明：** > > 该方法为同步方法，调用时会阻塞当前线程，不建议在主线程中调用，否则可能导致应用卡顿、掉帧或响应延迟。具体场景参考 > [耗时任务并发场景简介](../../../arkts-utils/time-consuming-task-overview.md)。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ImageSource-createPixelMapSync(options?: DecodingOptions): PixelMap--><!--Device-ImageSource-createPixelMapSync(options?: DecodingOptions): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 否 | 解码参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | 用于同步返回创建结果。 |

## createPixelMapSync

```TypeScript
createPixelMapSync(options?: DecodingOptions): PixelMap | undefined
```

Create a PixelMap object based on image decoding parameters synchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-createPixelMapSync(options?: DecodingOptions): PixelMap | undefined--><!--Device-ImageSource-createPixelMapSync(options?: DecodingOptions): PixelMap | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 否 | Image decoding parameters. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | Return the PixelMap. If decoding fails, return undefined. |

## createPixelMapUsingAllocator

```TypeScript
createPixelMapUsingAllocator(options?: DecodingOptions, allocatorType?: AllocatorType): Promise<PixelMap>
```

使用指定的分配器根据图像解码参数异步创建PixelMap对象。使用Promise异步回调。接口使用详情请参考 [图片解码内存优化(ArkTS)](../../../media/image/image-allocator-type.md)。 > **说明：** > > - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。 > > - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。 > > - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**废弃版本：** -1

<!--Device-ImageSource-createPixelMapUsingAllocator(options?: DecodingOptions, allocatorType?: AllocatorType): Promise<PixelMap>--><!--Device-ImageSource-createPixelMapUsingAllocator(options?: DecodingOptions, allocatorType?: AllocatorType): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 否 | 解码参数。 |
| allocatorType | [AllocatorType](arkts-image-image-allocatortype-e.md) | 否 | 用于图像解码的内存类型。默认值为AllocatorType.AUTO。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap&gt; | Promise对象，返回PixelMap。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700101](../errorcode-image.md#7700101-图片源存在问题) | Bad source. e.g.,1. Image has invalid width or height. 2. Image source incomplete. 3. Read image data failed. 4. Codec create failed. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types; 3.Parameter verification failed. |
| [7700103](../errorcode-image.md#7700103-图片太大) | Image too large. This status code is thrown when an error occurs during the process of checking size. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported mimetype. |
| [7700301](../errorcode-image.md#7700301-解码失败) | Failed to decode image. |
| [7700302](../errorcode-image.md#7700302-内存分配失败) | Failed to allocate memory. |
| [7700201](../errorcode-image.md#7700201-不支持的内存分配类型) | Unsupported allocator type, e.g., use share memory to decode a HDR image as only DMA supported hdr metadata. |
| [7700203](../errorcode-image.md#7700203-不支持的选项) | Unsupported options, e.g, cannot convert image into desired pixel format. |

## createPixelMapUsingAllocator

```TypeScript
createPixelMapUsingAllocator(options?: DecodingOptions, allocatorType?: AllocatorType)
      : Promise<PixelMap | undefined>
```

Creates a PixelMap based on decoding parameters, the memory type used by the PixelMap can be specified by allocatorType. By default, the system selects the memory type based on the image type, image size, platform capability, etc. When processing the PixelMap returned by this interface, please always consider the impact of stride.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-createPixelMapUsingAllocator(options?: DecodingOptions, allocatorType?: AllocatorType)      : Promise<PixelMap | undefined>--><!--Device-ImageSource-createPixelMapUsingAllocator(options?: DecodingOptions, allocatorType?: AllocatorType)      : Promise<PixelMap | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 否 | Image decoding parameters. |
| allocatorType | [AllocatorType](arkts-image-image-allocatortype-e.md) | 否 | Indicate which memory type will be used by the returned PixelMap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap \| undefined&gt; | A Promise instance used to return the PixelMap object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700101](../errorcode-image.md#7700101-图片源存在问题) | Bad source. |
| [7700103](../errorcode-image.md#7700103-图片太大) | Image too large. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported mimetype. |
| [7700301](../errorcode-image.md#7700301-解码失败) | Failed to decode image. |
| [7700302](../errorcode-image.md#7700302-内存分配失败) | Failed to allocate memory. |
| [7700201](../errorcode-image.md#7700201-不支持的内存分配类型) | Unsupported allocator type. For example, use share memory to decode HDR image as only DMA supported HDR metadata. |
| [7700203](../errorcode-image.md#7700203-不支持的选项) | Unsupported options, For example, unsupported desiredPixelFormat causes a failure in converting an imagge into the desired pixel format. |

## createPixelMapUsingAllocatorSync

```TypeScript
createPixelMapUsingAllocatorSync(options?: DecodingOptions, allocatorType?: AllocatorType): PixelMap
```

根据指定的分配器同步创建一个基于图像解码参数的PixelMap对象。接口使用详情请参考[图片解码内存优化(ArkTS)](../../../media/image/image-allocator-type.md)。 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。 > **说明：** > > 该方法为同步方法，调用时会阻塞当前线程，不建议在主线程中调用，否则可能导致应用卡顿、掉帧或响应延迟。具体场景参考 > [耗时任务并发场景简介](../../../arkts-utils/time-consuming-task-overview.md)。

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**废弃版本：** -1

<!--Device-ImageSource-createPixelMapUsingAllocatorSync(options?: DecodingOptions, allocatorType?: AllocatorType): PixelMap--><!--Device-ImageSource-createPixelMapUsingAllocatorSync(options?: DecodingOptions, allocatorType?: AllocatorType): PixelMap-End-->

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
| [7700101](../errorcode-image.md#7700101-图片源存在问题) | Bad source. e.g.,1. Image has invalid width or height. 2. Image source incomplete. 3. Read image data failed. 4. Codec create failed. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types; 3.Parameter verification failed. |
| [7700103](../errorcode-image.md#7700103-图片太大) | Image too large. This status code is thrown when an error occurs during the process of checking size. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported mimetype. |
| [7700301](../errorcode-image.md#7700301-解码失败) | Failed to decode image. |
| [7700302](../errorcode-image.md#7700302-内存分配失败) | Failed to allocate memory. |
| [7700201](../errorcode-image.md#7700201-不支持的内存分配类型) | Unsupported allocator type, e.g., use share memory to decode a HDR image as only DMA supported hdr metadata. |
| [7700203](../errorcode-image.md#7700203-不支持的选项) | Unsupported options, e.g, cannot convert image into desired pixel format. |

## createPixelMapUsingAllocatorSync

```TypeScript
createPixelMapUsingAllocatorSync(options?: DecodingOptions, allocatorType?: AllocatorType): PixelMap | undefined
```

Creates a PixelMap based on decoding parameters synchronously, the memory type used by the PixelMap can be specified by allocatorType. By default, the system selects the memory type based on the image type, image size, platform capability, etc. When processing the PixelMap returned by this interface, please always consider the impact of stride.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-createPixelMapUsingAllocatorSync(options?: DecodingOptions, allocatorType?: AllocatorType): PixelMap | undefined--><!--Device-ImageSource-createPixelMapUsingAllocatorSync(options?: DecodingOptions, allocatorType?: AllocatorType): PixelMap | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptions](arkts-image-image-decodingoptions-i.md) | 否 | Image decoding parameters. |
| allocatorType | [AllocatorType](arkts-image-image-allocatortype-e.md) | 否 | Indicate which memory type will be used by the returned PixelMap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | Return the PixelMap. If decoding fails, return undefined. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700101](../errorcode-image.md#7700101-图片源存在问题) | Bad source. |
| [7700103](../errorcode-image.md#7700103-图片太大) | Image too large. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |
| [7700301](../errorcode-image.md#7700301-解码失败) | Failed to decode image. |
| [7700302](../errorcode-image.md#7700302-内存分配失败) | Failed to allocate memory. |
| [7700201](../errorcode-image.md#7700201-不支持的内存分配类型) | Unsupported allocator type. For example, use share memory to decode HDR image as only DMA supported HDR metadata. |
| [7700203](../errorcode-image.md#7700203-不支持的选项) | Unsupported options, For example, unsupported desiredPixelFormat cause a failure in converting an image into the desired pixel format. |

## createThumbnail

```TypeScript
createThumbnail(options?: DecodingOptionsForThumbnail): Promise<PixelMap | undefined>
```

通过图片解码参数创建缩略图PixelMap对象。使用Promise异步回调。 当前支持对JPEG和HEIF格式的图片创建缩略图PixelMap对象。 优先解码图片文件中包含的缩略图。若图片文件中没有缩略图，则对原图进行解码。 > **说明：** > > - 不支持在同一个ImageSource实例上并发调用。 > > - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。 > > - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageSource-createThumbnail(options?: DecodingOptionsForThumbnail): Promise<PixelMap | undefined>--><!--Device-ImageSource-createThumbnail(options?: DecodingOptionsForThumbnail): Promise<PixelMap | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptionsForThumbnail](arkts-image-image-decodingoptionsforthumbnail-i.md) | 否 | 解码参数，控制是否生成缩略图以及生成缩略图的目标尺寸。 &lt;br&gt;默认表现： &lt;br&gt;- 当图像有缩略图时，解码原始缩略图，返回的PixelMap对象的宽和高与原缩略图保持一致。 &lt;br&gt;- 当原图文件无缩略图时，对原图进行解码后，根据解码参数options下采样生成缩略图，生成后的缩略图PixelMap对象宽和高都限制在512像素以内。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap \| undefined&gt; | Promise对象，返回PixelMap。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700103](../errorcode-image.md#7700103-图片太大) | Image too large. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported mimetype. |
| [7700305](../errorcode-image.md#7700305-缩略图生成失败) | Thumbnail generation failed. |
| [7700301](../errorcode-image.md#7700301-解码失败) | Decode failed. |
| [7700204](../errorcode-image.md#7700204-无效参数) | Invalid parameter, e.g, invalid generate size. |
| [7700303](../errorcode-image.md#7700303-图片不包含缩略图数据) | Image does not carry thumbnail data. |

## createThumbnailSync

```TypeScript
createThumbnailSync(options?: DecodingOptionsForThumbnail): PixelMap | undefined
```

通过图片解码参数同步创建缩略图。返回创建结果对应的[PixelMap](arkts-image-image-pixelmap-i.md#PixelMap)对象。 当前支持对JPEG和HEIF格式的图片创建缩略图PixelMap对象。 优先解码图片文件中包含的缩略图。若图片文件中没有缩略图，则对原图进行解码。 > **说明：** > > - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法，及时释放内存。 > > - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。 > > - 该方法为同步方法，调用时会阻塞当前线程，不建议在主线程中调用，否则可能导致应用卡顿、掉帧或响应延迟。具体场景参考 > [耗时任务并发场景简介](../../../arkts-utils/time-consuming-task-overview.md)。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageSource-createThumbnailSync(options?: DecodingOptionsForThumbnail): PixelMap | undefined--><!--Device-ImageSource-createThumbnailSync(options?: DecodingOptionsForThumbnail): PixelMap | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DecodingOptionsForThumbnail](arkts-image-image-decodingoptionsforthumbnail-i.md) | 否 | 解码参数，控制是否生成缩略图以及生成缩略图的目标尺寸。 &lt;br&gt;默认表现： &lt;br&gt;- 当图像有缩略图时，解码原始缩略图，返回的PixelMap对象的宽和高与原缩略图保持一致。 &lt;br&gt;- 当原图文件无缩略图时，对原图进行解码后，根据解码参数options下采样生成缩略图，生成后的缩略图PixelMap对象宽和高都限制在512像素以内。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | 用于同步返回创建结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700103](../errorcode-image.md#7700103-图片太大) | Image too large. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported mimetype. |
| [7700305](../errorcode-image.md#7700305-缩略图生成失败) | Thumbnail generation failed. |
| [7700301](../errorcode-image.md#7700301-解码失败) | Decode failed. |
| [7700204](../errorcode-image.md#7700204-无效参数) | Invalid parameter, e.g, invalid generate size. |
| [7700303](../errorcode-image.md#7700303-图片不包含缩略图数据) | Image does not carry thumbnail data. |

## getDelayTimeList

```TypeScript
getDelayTimeList(): Promise<Array<int>>
```

获取图像延迟时间数组。使用Promise异步回调。此接口仅用于gif图片和webp图片。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-getDelayTimeList(): Promise<Array<int>>--><!--Device-ImageSource-getDelayTimeList(): Promise<Array<int>>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;int&gt;&gt; | Promise对象，返回延迟时间数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980149](../errorcode-image.md#62980149-图片参数无效) | Invalid MIME type for the image source. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |
| [62980118](../errorcode-image.md#62980118-创建插件失败) | Failed to create the image plugin. |
| [62980122](../errorcode-image.md#62980122-解码图片头异常) | Failed to decode the image header. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980110](../errorcode-image.md#62980110-图片源数据错误) | The image source data is incorrect. |

## getDelayTimeList

```TypeScript
getDelayTimeList(callback: AsyncCallback<Array<int>>): void
```

获取图像延迟时间数组。使用callback异步回调。此接口仅用于gif图片和webp图片。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-getDelayTimeList(callback: AsyncCallback<Array<int>>): void--><!--Device-ImageSource-getDelayTimeList(callback: AsyncCallback<Array<int>>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;int&gt;&gt; | 是 | 回调函数，当获取图像延迟时间数组成功，err为undefined，data为获取到的图像延时时间数组；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980149](../errorcode-image.md#62980149-图片参数无效) | Invalid MIME type for the image source. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |
| [62980118](../errorcode-image.md#62980118-创建插件失败) | Failed to create the image plugin. |
| [62980122](../errorcode-image.md#62980122-解码图片头异常) | Failed to decode the image header. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980110](../errorcode-image.md#62980110-图片源数据错误) | The image source data is incorrect. |

## getDisposalTypeList

```TypeScript
getDisposalTypeList(): Promise<Array<int>>
```

获取图像帧过渡模式数组。使用Promise异步回调。此接口仅用于gif图片。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-getDisposalTypeList(): Promise<Array<int>>--><!--Device-ImageSource-getDisposalTypeList(): Promise<Array<int>>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;int&gt;&gt; | Promise对象，返回帧过渡模式数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980101](../errorcode-image.md#62980101-图片输入数据错误) | The image data is abnormal. |
| [62980149](../errorcode-image.md#62980149-图片参数无效) | Invalid MIME type for the image source. |
| [62980137](../errorcode-image.md#62980137-图片操作无效) | Invalid media operation. |

## getFrameCount

```TypeScript
getFrameCount(): Promise<int>
```

获取图像帧数。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-getFrameCount(): Promise<int>--><!--Device-ImageSource-getFrameCount(): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回图像帧数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980113](../errorcode-image.md#62980113-图片未知格式) | Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted. |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980112](../errorcode-image.md#62980112-图片格式不匹配) | The image format does not match. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |
| [62980118](../errorcode-image.md#62980118-创建插件失败) | Failed to create the image plugin. |
| [62980137](../errorcode-image.md#62980137-图片操作无效) | Invalid media operation. |
| [62980122](../errorcode-image.md#62980122-解码图片头异常) | Failed to decode the image header. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |

## getFrameCount

```TypeScript
getFrameCount(callback: AsyncCallback<int>): void
```

获取图像帧数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-getFrameCount(callback: AsyncCallback<int>): void--><!--Device-ImageSource-getFrameCount(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | 回调函数，当获取图像帧数成功，err为undefined，data为获取到的图像帧数；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980113](../errorcode-image.md#62980113-图片未知格式) | Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted. |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980112](../errorcode-image.md#62980112-图片格式不匹配) | The image format does not match. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |
| [62980118](../errorcode-image.md#62980118-创建插件失败) | Failed to create the image plugin. |
| [62980137](../errorcode-image.md#62980137-图片操作无效) | Invalid media operation. |
| [62980122](../errorcode-image.md#62980122-解码图片头异常) | Failed to decode the image header. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |

## getImageInfo

```TypeScript
getImageInfo(index: int, callback: AsyncCallback<ImageInfo>): void
```

获取指定序号的图片信息。使用callback异步回调。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageSource-getImageInfo(index: int, callback: AsyncCallback<ImageInfo>): void--><!--Device-ImageSource-getImageInfo(index: int, callback: AsyncCallback<ImageInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 创建ImageSource时的序号。默认值为0，表示第一张图片。当取值为N时，表示第N+1张图片。单帧图片场景中index取值只能为0，动图等多帧图片场景中index的取值范围为： [0, (帧数-1)]。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ImageInfo](arkts-image-image-imageinfo-i.md)&gt; | 是 | 回调函数。当获取图片信息成功，err为undefined，data为获取到的图片信息；否则为错误对象。 |

## getImageInfo

```TypeScript
getImageInfo(index: int, callback: AsyncCallback<ImageInfo | undefined>): void
```

Obtains information about an image with the specified sequence number and uses a callback to return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-getImageInfo(index: int, callback: AsyncCallback<ImageInfo | undefined>): void--><!--Device-ImageSource-getImageInfo(index: int, callback: AsyncCallback<ImageInfo | undefined>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | Sequence number of an image. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ImageInfo](arkts-image-image-imageinfo-i.md) \| undefined&gt; | 是 | Callback used to return the image information. |

## getImageInfo

```TypeScript
getImageInfo(callback: AsyncCallback<ImageInfo>): void
```

获取图片信息。使用callback异步回调。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageSource-getImageInfo(callback: AsyncCallback<ImageInfo>): void--><!--Device-ImageSource-getImageInfo(callback: AsyncCallback<ImageInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ImageInfo](arkts-image-image-imageinfo-i.md)&gt; | 是 | 回调函数。当获取图片信息成功，err为undefined，data为获取到的图片信息；否则为错误对象。 |

## getImageInfo

```TypeScript
getImageInfo(callback: AsyncCallback<ImageInfo | undefined>): void
```

Obtains information about this image and uses a callback to return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-getImageInfo(callback: AsyncCallback<ImageInfo | undefined>): void--><!--Device-ImageSource-getImageInfo(callback: AsyncCallback<ImageInfo | undefined>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ImageInfo](arkts-image-image-imageinfo-i.md) \| undefined&gt; | 是 | Callback used to return the image information. |

## getImageInfo

```TypeScript
getImageInfo(index?: int): Promise<ImageInfo>
```

获取图片信息。使用Promise异步回调。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageSource-getImageInfo(index?: int): Promise<ImageInfo>--><!--Device-ImageSource-getImageInfo(index?: int): Promise<ImageInfo>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 否 | 创建ImageSource时的序号。默认值为0，表示第一张图片。当取值为N时，表示第N+1张图片。单帧图片场景中index取值只能为0，动图等多帧图片场景中index的取值范围为： [0, (帧数-1)]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ImageInfo](arkts-image-image-imageinfo-i.md)&gt; | Promise对象，返回获取到的图片信息。 |

## getImageInfo

```TypeScript
getImageInfo(index?: int): Promise<ImageInfo | undefined>
```

Get image information from image source.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-getImageInfo(index?: int): Promise<ImageInfo | undefined>--><!--Device-ImageSource-getImageInfo(index?: int): Promise<ImageInfo | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 否 | Sequence number of an image. If this parameter is not specified, the default value 0 is used. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ImageInfo](arkts-image-image-imageinfo-i.md) \| undefined&gt; | A Promise instance used to return the image information. |

## getImageInfoSync

```TypeScript
getImageInfoSync(index?: int): ImageInfo
```

获取指定序号的图片信息，使用同步形式返回图片信息。 > **说明：** > > 该方法为同步方法，调用时会阻塞当前线程，不建议在主线程中调用，否则可能导致应用卡顿、掉帧或响应延迟。具体场景参考 > [耗时任务并发场景简介](../../../arkts-utils/time-consuming-task-overview.md)。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ImageSource-getImageInfoSync(index?: int): ImageInfo--><!--Device-ImageSource-getImageInfoSync(index?: int): ImageInfo-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 否 | 创建ImageSource时的序号。默认值为0，表示第一张图片。当取值为N时，表示第N+1张图片。单帧图片场景中index取值只能为0，动图等多帧图片场景中index的取值范围为： [0, (帧数-1)]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageInfo](arkts-image-image-imageinfo-i.md) | 同步返回获取到的图片信息。 |

## getImageInfoSync

```TypeScript
getImageInfoSync(index?: int): ImageInfo | undefined
```

Get image information from image source synchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-getImageInfoSync(index?: int): ImageInfo | undefined--><!--Device-ImageSource-getImageInfoSync(index?: int): ImageInfo | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 否 | Index of sequence image. If this parameter is specified, default value is 0 &lt;br&gt;The value range is all integers. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageInfo](arkts-image-image-imageinfo-i.md) | The image information. |

## getImageProperties

```TypeScript
getImageProperties(key: Array<PropertyKey>): Promise<Record<PropertyKey, string|null>>
```

批量获取图片中的指定属性键的值。使用Promise异步回调。 该接口仅支持JPEG、PNG、HEIF、WEBP&lt;sup&gt;23+&lt;/sup&gt;和DNG&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ImageSource-getImageProperties(key: Array<PropertyKey>): Promise<Record<PropertyKey, string|null>>--><!--Device-ImageSource-getImageProperties(key: Array<PropertyKey>): Promise<Record<PropertyKey, string|null>>-End-->

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
| [62980113](../errorcode-image.md#62980113-图片未知格式) | Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified; 2 .Incorrect parameter types; 3.Parameter verification failed; |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |
| [62980110](../errorcode-image.md#62980110-图片源数据错误) | The image source data is incorrect. |

## getImageProperties

```TypeScript
getImageProperties(key: Array<PropertyKey>): Promise<Record<string, string|null>>
```

Obtains the value of properties in an image. This method uses a promise to return the property values in array of records.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-getImageProperties(key: Array<PropertyKey>): Promise<Record<string, string|null>>--><!--Device-ImageSource-getImageProperties(key: Array<PropertyKey>): Promise<Record<string, string|null>>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | Array&lt;[PropertyKey](arkts-image-image-propertykey-e.md)&gt; | 是 | Name of the properties whose value is to be obtained. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, string \| null&gt;&gt; | Array of Records instance used to return the property values. If the operation fails, the null is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980113](../errorcode-image.md#62980113-图片未知格式) | Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted. |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980116](../errorcode-image.md#62980116-解码失败) | Failed to decode the image. |
| [62980110](../errorcode-image.md#62980110-图片源数据错误) | The image source data is incorrect. |

## getImageProperty

```TypeScript
getImageProperty(key: PropertyKey, options?: ImagePropertyOptions): Promise<string>
```

获取图片中给定索引处图像的指定属性键的值。使用Promise异步回调。 该接口仅支持JPEG、PNG、HEIF&lt;sup&gt;12+&lt;/sup&gt;、WEBP&lt;sup&gt;23+&lt;/sup&gt;和DNG&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-getImageProperty(key: PropertyKey, options?: ImagePropertyOptions): Promise<string>--><!--Device-ImageSource-getImageProperty(key: PropertyKey, options?: ImagePropertyOptions): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [PropertyKey](arkts-image-image-propertykey-e.md) | 是 | 图片属性名。 |
| options | [ImagePropertyOptions](arkts-image-image-imagepropertyoptions-i.md) | 否 | 图片属性，包括图片序号与默认属性值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回图片属性值，如获取失败则返回属性默认值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980113](../errorcode-image.md#62980113-图片未知格式) | Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified; 2 .Incorrect parameter types;3.Parameter verification failed; |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980112](../errorcode-image.md#62980112-图片格式不匹配) | The image format does not match. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | The image data is not supported. |
| [62980135](../errorcode-image.md#62980135-图片属性值无效) | The EXIF value is invalid. |
| [62980118](../errorcode-image.md#62980118-创建插件失败) | Failed to create the image plugin. |
| [62980123](../errorcode-image.md#62980123-图片不支持exif解码) | The image does not support EXIF decoding. |
| [62980122](../errorcode-image.md#62980122-解码图片头异常) | Failed to decode the image header. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980110](../errorcode-image.md#62980110-图片源数据错误) | The image source data is incorrect. |

## getImageProperty

```TypeScript
getImageProperty(key: string, options?: GetImagePropertyOptions): Promise<string>
```

获取图片中给定索引处图像的指定属性键的值。使用Promise异步回调。 该接口仅支持JPEG、PNG、HEIF&lt;sup&gt;12+&lt;/sup&gt;和WEBP&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。 > **说明：** > > 从API version 7开始支持，从API version 11废弃，建议使用 > [getImageProperty](#getImageProperty)代 > 替。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 11

**替代接口：** [getImageProperty](#getImageProperty)(key: PropertyKey, options?: ImagePropertyOptions)

<!--Device-ImageSource-getImageProperty(key: string, options?: GetImagePropertyOptions): Promise<string>--><!--Device-ImageSource-getImageProperty(key: string, options?: GetImagePropertyOptions): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 图片属性名。 |
| options | [GetImagePropertyOptions](arkts-image-image-getimagepropertyoptions-i.md) | 否 | 图片属性，包括图片序号与默认属性值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回图片属性值，如获取失败则返回属性默认值。 |

## getImageProperty

```TypeScript
getImageProperty(key: string, callback: AsyncCallback<string>): void
```

获取图片中给定索引处图像的指定属性键的值。使用callback异步回调。 该接口仅支持JPEG、PNG、HEIF&lt;sup&gt;12+&lt;/sup&gt;和WEBP&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。 > **说明：** > > 从API version 7开始支持，从API version 11废弃，建议使用 > [getImageProperty](#getImageProperty)代 > 替。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 11

**替代接口：** [getImageProperty](#getImageProperty)(key: PropertyKey, options?: ImagePropertyOptions)

<!--Device-ImageSource-getImageProperty(key: string, callback: AsyncCallback<string>): void--><!--Device-ImageSource-getImageProperty(key: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 图片属性名。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 回调函数，当获取图片属性值成功，err为undefined，data为获取到的图片属性值；否则为错误对象。 |

## getImageProperty

```TypeScript
getImageProperty(key: string, options: GetImagePropertyOptions, callback: AsyncCallback<string>): void
```

获取图片指定属性键的值。使用callback异步回调。 该接口仅支持JPEG、PNG、HEIF&lt;sup&gt;12+&lt;/sup&gt;和WEBP&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。 > **说明：** > > 从API version 7开始支持，从API version 11废弃，建议使用 > [getImageProperty](#getImageProperty)代 > 替。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 11

**替代接口：** [getImageProperty](#getImageProperty)(key: PropertyKey, options?: ImagePropertyOptions)

<!--Device-ImageSource-getImageProperty(key: string, options: GetImagePropertyOptions, callback: AsyncCallback<string>): void--><!--Device-ImageSource-getImageProperty(key: string, options: GetImagePropertyOptions, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 图片属性名。 |
| options | [GetImagePropertyOptions](arkts-image-image-getimagepropertyoptions-i.md) | 是 | 图片属性，包括图片序号与默认属性值。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 回调函数，当获取图片属性值成功，err为undefined，data为获取到的图片属性值；否则为错误对象。 |

## getImagePropertySync

```TypeScript
getImagePropertySync(key: PropertyKey): string
```

获取图片Exif指定属性键的值，使用同步形式返回结果。 > **说明：** > > - 该方法仅支持JPEG、PNG、HEIF、WEBP&lt;sup&gt;23+&lt;/sup&gt;和DNG&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。 > > - Exif信息是图片的元数据，包含拍摄时间、相机型号、光圈、焦距、ISO等。 > > - 该方法为同步方法，调用时会阻塞当前线程，不建议在主线程中调用，否则可能导致应用卡顿、掉帧或响应延迟。具体场景参考 > [耗时任务并发场景简介](../../../arkts-utils/time-consuming-task-overview.md)。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-ImageSource-getImagePropertySync(key: PropertyKey): string--><!--Device-ImageSource-getImagePropertySync(key: PropertyKey): string-End-->

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

## getImagePropertySync

```TypeScript
getImagePropertySync(key: PropertyKey): string | undefined
```

Obtains the value of a property in the image.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-getImagePropertySync(key: PropertyKey): string | undefined--><!--Device-ImageSource-getImagePropertySync(key: PropertyKey): string | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [PropertyKey](arkts-image-image-propertykey-e.md) | 是 | Property name. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Value of the property. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700101](../errorcode-image.md#7700101-图片源存在问题) | Bad source. e.g.,1. Image has invalid width or height. 2. Image source incomplete. 3. Read image data failed. 4. Codec create failed. |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |
| [7700202](../errorcode-image.md#7700202-不支持的元数据) | Unsupported metadata. For example, key is not supported. |

## modifyImageProperties

```TypeScript
modifyImageProperties(records: Record<PropertyKey, string|null>): Promise<void>
```

批量通过指定的键修改图片属性的值。使用Promise异步回调。 该接口仅支持JPEG、PNG、HEIF和WEBP&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。 > **说明：** > > - 调用modifyImageProperties修改属性会改变属性字节长度，使用buffer创建的ImageSource调用modifyImageProperties会导致buffer内容覆盖，目前buffer创建的 > ImageSource不支持调用此接口，请改用fd或path创建的ImageSource。 > > - 调用modifyImageProperties接口修改Exif字段时，必须确保对应的图片文件有写权限，否则会导致字段修改不成功。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ImageSource-modifyImageProperties(records: Record<PropertyKey, string|null>): Promise<void>--><!--Device-ImageSource-modifyImageProperties(records: Record<PropertyKey, string|null>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| records | Record&lt;[PropertyKey](arkts-image-image-propertykey-e.md), string \| null&gt; | 是 | 包含图片属性名和属性值的数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified; 2 .Incorrect parameter types; 3.Parameter verification failed; |
| [62980146](../errorcode-image.md#62980146-图片属性值写入文件失败) | The EXIF data failed to be written to the file. |
| [62980135](../errorcode-image.md#62980135-图片属性值无效) | The EXIF value is invalid. |
| [62980123](../errorcode-image.md#62980123-图片不支持exif解码) | The image does not support EXIF decoding. |

## modifyImageProperties

```TypeScript
modifyImageProperties(records: Record<string, string|null>): Promise<void>
```

Modify the value of properties in an image with the specified keys.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-modifyImageProperties(records: Record<string, string|null>): Promise<void>--><!--Device-ImageSource-modifyImageProperties(records: Record<string, string|null>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| records | Record&lt;string, string \| null&gt; | 是 | Array of the property Records whose values are to be modified. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980146](../errorcode-image.md#62980146-图片属性值写入文件失败) | The EXIF data failed to be written to the file. |
| [62980135](../errorcode-image.md#62980135-图片属性值无效) | The EXIF value is invalid. |
| [62980123](../errorcode-image.md#62980123-图片不支持exif解码) | The image does not support EXIF decoding. |

## modifyImagePropertiesEnhanced

```TypeScript
modifyImagePropertiesEnhanced(records: Record<string, string | null>): Promise<void>
```

批量修改图片属性。使用Promise异步回调。 > **说明：** > > - 调用该接口修改属性会改变属性字节长度，建议通过传入文件描述符来创建[image.createImageSource](arkts-image-image-createimagesource-f.md#createImageSource)实例或通过传入的uri创建 > [image.createImageSource](arkts-image-image-createimagesource-f.md#createImageSource)实例。 > > - 该方法在内存中完成批量数据修改后会一次性写入文件，相比 > [modifyImageProperties](#modifyImageProperties) > 更高效。 > > - 支持修改JPEG、PNG、HEIF和WEBP文件类型的图片属性，图片需要包含Exif信息。 > > - 调用modifyImagePropertiesEnhanced接口修改Exif字段时，必须确保对应的图片文件有写权限，否则会导致字段修改不成功。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-modifyImagePropertiesEnhanced(records: Record<string, string | null>): Promise<void>--><!--Device-ImageSource-modifyImagePropertiesEnhanced(records: Record<string, string | null>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| records | Record&lt;string, string \| null&gt; | 是 | 包含图片属性名和属性值的键值对集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |
| [7700304](../errorcode-image.md#7700304-图片信息写入文件失败) | Failed to write image properties to the file. |
| [7700202](../errorcode-image.md#7700202-不支持的元数据) | Unsupported metadata. For example, the property key is not supported, or the property value is invalid. |

## modifyImageProperty

```TypeScript
modifyImageProperty(key: PropertyKey, value: string): Promise<void>
```

通过指定的键修改图片属性的值。使用Promise异步回调。 该接口仅支持JPEG、PNG、HEIF&lt;sup&gt;12+&lt;/sup&gt;和WEBP&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。 > **说明：** > > - 调用modifyImageProperty修改属性会改变属性字节长度，使用buffer创建的ImageSource调用modifyImageProperty会导致buffer内容覆盖，目前buffer创建的 > ImageSource不支持调用此接口，请改用fd或path创建的ImageSource。 > > - 调用modifyImageProperty接口修改Exif字段时，必须确保对应的图片文件有写权限，否则会导致字段修改不成功。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-modifyImageProperty(key: PropertyKey, value: string): Promise<void>--><!--Device-ImageSource-modifyImageProperty(key: PropertyKey, value: string): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [PropertyKey](arkts-image-image-propertykey-e.md) | 是 | 图片属性名。 |
| value | string | 是 | 属性值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified; 2 .Incorrect parameter types; |
| [62980146](../errorcode-image.md#62980146-图片属性值写入文件失败) | The EXIF data failed to be written to the file. |
| [62980133](../errorcode-image.md#62980133-图片属性赋值超出范围) | The EXIF data is out of range. |
| [62980135](../errorcode-image.md#62980135-图片属性值无效) | The EXIF value is invalid. |
| [62980123](../errorcode-image.md#62980123-图片不支持exif解码) | The image does not support EXIF decoding. |

## modifyImageProperty

```TypeScript
modifyImageProperty(key: string, value: string): Promise<void>
```

通过指定的键修改图片属性的值。使用Promise异步回调。 该接口仅支持JPEG、PNG、HEIF&lt;sup&gt;12+&lt;/sup&gt;和WEBP&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。 > **说明：** > > - 调用modifyImageProperty修改属性会改变属性字节长度，使用buffer创建的ImageSource调用modifyImageProperty会导致buffer内容覆盖，目前buffer创建的 > ImageSource不支持调用此接口，请改用fd或path创建的ImageSource。 > > - 从API version 9开始支持，从API version 11废弃，建议使用 > [modifyImageProperty](#modifyImageProperty)代替。 > > - 调用modifyImageProperty接口修改Exif字段时，必须确保对应的图片文件有写权限，否则会导致字段修改不成功。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 11

**替代接口：** [modifyImageProperty](#modifyImageProperty)(key: PropertyKey, value: string)

<!--Device-ImageSource-modifyImageProperty(key: string, value: string): Promise<void>--><!--Device-ImageSource-modifyImageProperty(key: string, value: string): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 图片属性名。 |
| value | string | 是 | 属性值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

## modifyImageProperty

```TypeScript
modifyImageProperty(key: string, value: string, callback: AsyncCallback<void>): void
```

通过指定的键修改图片属性的值。使用callback异步回调。 仅支持JPEG、PNG、HEIF&lt;sup&gt;12+&lt;/sup&gt;和WEBP&lt;sup&gt;23+&lt;/sup&gt;（不同硬件设备支持情况不同）文件，且需要包含Exif信息。 > **说明：** > > - 调用modifyImageProperty修改属性会改变属性字节长度，使用buffer创建的ImageSource调用modifyImageProperty会导致buffer内容覆盖，目前buffer创建的 > ImageSource不支持调用此接口，请改用fd或path创建的ImageSource。 > > - 从API version 9开始支持，从API version 11废弃，建议使用 > [modifyImageProperty](#modifyImageProperty)代替。 > > - 调用modifyImageProperty接口修改Exif字段时，必须确保对应的图片文件有写权限，否则会导致字段修改不成功。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 11

**替代接口：** [modifyImageProperty](#modifyImageProperty)(key: PropertyKey, value: string)

<!--Device-ImageSource-modifyImageProperty(key: string, value: string, callback: AsyncCallback<void>): void--><!--Device-ImageSource-modifyImageProperty(key: string, value: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 图片属性名。 |
| value | string | 是 | 属性值。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，当修改图片属性值成功，err为undefined，否则为错误对象。 |

## readImageMetadata

```TypeScript
readImageMetadata(propertyKeys?: string[], index?: int): Promise<ImageMetadata>
```

读取图像源的元数据，使用propertyKeys指定元数据字段。使用Promise异步回调。 该接口仅支持JPEG、PNG、HEIF、WebP、DNG、GIF、TIFF、HEIFS、JFIF和AVIS（不同硬件设备支持情况不同）文件，且需要包含Exif信息。 > **说明：** > > 读取DNG格式图片时，该接口对部分propertyKeys有特殊处理。以下字段的字符串取值请参考[PropertyKey](arkts-image-image-propertykey-e.md#PropertyKey)中的值： > > - NewSubfileType、ImageWidth、ImageLength、DefaultCropSize、Orientation、Compression、PhotometricInterpretation、 > PlanarConfiguration、RowsPerStrip、StripOffsets、StripByteCounts、SamplesPerPixel、BitsPerSample、YCbCrCoefficients、 > YCbCrSubSampling、YCbCrPositioning、ReferenceBlackWhite、XResolution、YResolution、ResolutionUnit字段：返回主图相关的字段值。 > > - ImageUniqueID字段：根据规范进行校验，不符合规范时会返回空字符串。 > > - ExifVersion、FlashpixVersion、ColorSpace字段：当图片中不存在该标签时，返回错误码。 > > - DNGVersion字段：当版本号小于1.0.0.0时，统一返回1.0.0.0。 > > - GPSVersionID字段：当没有有效的GPS数据时，会清除GPS版本号并返回0。 > > - GPSAltitudeRef字段：当未设置GPSAltitude时，会设置为0xFFFFFFFF。 > > - ISOSpeedRatings字段：当该标签值为0或65535时，会优先使用推荐曝光指数，若不存在则依次使用标准输出灵敏度、ISO速度、曝光指数。 > > - 从API version 24开始，支持读取DNG元数据。要查询的属性的具体信息请参考[DngPropertyKey](arkts-image-image-dngpropertykey-e.md#DngPropertyKey)。 > > - 从API version 24开始，支持读取HEIFS元数据。要查询的属性的具体信息请参考[HeifsPropertyKey](arkts-image-image-heifspropertykey-e.md#HeifsPropertyKey)。 > > - 从API版本26.0.0开始，支持读取PNG元数据。要查询的属性的具体信息请参考[PngPropertyKey](arkts-image-image-pngpropertykey-e.md#PngPropertyKey)。 > > - 从API版本26.0.0开始，支持读取JFIF元数据。要查询的属性的具体信息请参考[JfifPropertyKey](arkts-image-image-jfifpropertykey-e.md#JfifPropertyKey)。 > > - 从API版本26.0.0开始，支持读取TIFF元数据。要查询的属性的具体信息请参考[TiffPropertyKey](arkts-image-image-tiffpropertykey-e.md#TiffPropertyKey)。 > > - 从API版本26.0.0开始，支持读取GIF元数据。要查询的属性的具体信息请参考[GifPropertyKey](arkts-image-image-gifpropertykey-e.md#GifPropertyKey)。 > > - 从API版本26.0.0开始，支持读取JPEG、PNG、GIF、DNG、TIFF格式图片的XMP元数据。XMP元数据的操作方法可以参考 > [XMPMetadata](../../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md)。 > > - 从API版本26.0.0开始，支持读取AVIS元数据。要查询的属性的具体信息请参考[AvisPropertyKey](arkts-image-image-avispropertykey-e.md#AvisPropertyKey)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageSource-readImageMetadata(propertyKeys?: string[], index?: int): Promise<ImageMetadata>--><!--Device-ImageSource-readImageMetadata(propertyKeys?: string[], index?: int): Promise<ImageMetadata>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propertyKeys | string[] | 否 | 图片属性名的数组。若未指定propertyKeys，则返回所有支持的元数据。 |
| index | int | 否 | 感兴趣的索引，默认值为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ImageMetadata](arkts-image-image-imagemetadata-i.md)&gt; | Promise对象，返回ImageMetadata对象，其中含有图片属性名对应的metadata对象，通过ImageMetadata中的metadata对 象可以获取图片属性值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |
| [7700204](../errorcode-image.md#7700204-无效参数) | Invalid parameter. Possible causes: 1. The index is negative. 2. The index is greater than or equal to the number of frames in the image. |
| [7700202](../errorcode-image.md#7700202-不支持的元数据) | Unsupported metadata. |

## readImageMetadataByType

```TypeScript
readImageMetadataByType(metadataTypes?: MetadataType[], index?: int): Promise<ImageMetadata>
```

读取图像源的元数据，使用metadataTypes指定元数据类型。若未指定metadataTypes，则返回所有支持的元数据。使用Promise异步回调。 该接口仅支持JPEG、PNG、HEIF、WebP、DNG、GIF、TIFF、HEIFS、JFIF和AVIS（不同硬件设备支持情况不同）文件。 > **说明：** > > - EXIF_METADATA元数据类型适用于JPEG、PNG、HEIF、WEBP和DNG格式图片。 > > - HEIFS_METADATA元数据类型适用于HEIFS格式图片。 > > - 当传入的MetadataType与图片格式无法匹配时，返回错误码7700102。 > > - 从API version 24开始，支持读取DNG元数据。要查询的属性的具体信息请参考[DngPropertyKey](arkts-image-image-dngpropertykey-e.md#DngPropertyKey)。 > > - 从API version 24开始，支持读取HEIFS元数据。要查询的属性的具体信息请参考[HeifsPropertyKey](arkts-image-image-heifspropertykey-e.md#HeifsPropertyKey)。 > > - 从API版本26.0.0开始，支持读取PNG元数据。要查询的属性的具体信息请参考[PngPropertyKey](arkts-image-image-pngpropertykey-e.md#PngPropertyKey)。 > > - 从API版本26.0.0开始，支持读取JFIF元数据。要查询的属性的具体信息请参考[JfifPropertyKey](arkts-image-image-jfifpropertykey-e.md#JfifPropertyKey)。 > > - 从API版本26.0.0开始，支持读取TIFF元数据。要查询的属性的具体信息请参考[TiffPropertyKey](arkts-image-image-tiffpropertykey-e.md#TiffPropertyKey)。 > > - 从API版本26.0.0开始，支持读取GIF元数据。要查询的属性的具体信息请参考[GifPropertyKey](arkts-image-image-gifpropertykey-e.md#GifPropertyKey)。 > > - 从API版本26.0.0开始，支持读取JPEG、PNG、GIF、DNG、TIFF格式图片的XMP元数据。XMP元数据的操作方法可以参考 > [XMPMetadata](../../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md)。 > > - 从API版本26.0.0开始，支持读取AVIS元数据。要查询的属性的具体信息请参考[AvisPropertyKey](arkts-image-image-avispropertykey-e.md#AvisPropertyKey)。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageSource-readImageMetadataByType(metadataTypes?: MetadataType[], index?: int): Promise<ImageMetadata>--><!--Device-ImageSource-readImageMetadataByType(metadataTypes?: MetadataType[], index?: int): Promise<ImageMetadata>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| metadataTypes | [MetadataType](arkts-image-image-metadatatype-e.md)[] | 否 | 元数据类型的数组。当该参数缺省时，获取全部支持的元数据。 |
| index | int | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ImageMetadata](arkts-image-image-imagemetadata-i.md)&gt; | Promise对象。返回的ImageMetadata对象中含有对应的metadata对象，通过ImageMetadata中的metadata对象可以获取图 片属性值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |
| [7700204](../errorcode-image.md#7700204-无效参数) | Invalid parameter. Possible causes: 1.The index is negative. 2. The index is greater than or equal to the number of frames in the image. |
| [7700202](../errorcode-image.md#7700202-不支持的元数据) | Unsupported metadata. |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放ImageSource实例。使用callback异步回调。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用该方法，及时释放内存。 释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-release(callback: AsyncCallback<void>): void--><!--Device-ImageSource-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，当资源释放成功，err为undefined，否则为错误对象。 |

## release

```TypeScript
release(): Promise<void>
```

释放ImageSource实例。使用Promise异步回调。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用该方法，及时释放内存。 释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-release(): Promise<void>--><!--Device-ImageSource-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

## updateData

```TypeScript
updateData(buf: ArrayBuffer, isFinished: boolean, offset: int, length: int): Promise<void>
```

更新增量数据。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-updateData(buf: ArrayBuffer, isFinished: boolean, offset: int, length: int): Promise<void>--><!--Device-ImageSource-updateData(buf: ArrayBuffer, isFinished: boolean, offset: int, length: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | 存放增量数据的buffer。 |
| isFinished | boolean | 是 | true表示数据更新完成，当前buffer内存放最后一段数据；false表示数据还未更新完成，需要继续更新。 |
| offset | int | 是 | 即当前buffer中的数据首地址，相对于整个图片文件首地址的偏移量。单位：字节（Byte）。<br>**起始版本：** 11 |
| length | int | 是 | 当前buffer的长度。单位：字节（Byte）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

## updateData

```TypeScript
updateData(
      buf: ArrayBuffer,
      isFinished: boolean,
      offset: int,
      length: int,
      callback: AsyncCallback<void>
    ): void
```

更新增量数据。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-updateData(      buf: ArrayBuffer,      isFinished: boolean,      offset: int,      length: int,      callback: AsyncCallback<void>    ): void--><!--Device-ImageSource-updateData(      buf: ArrayBuffer,      isFinished: boolean,      offset: int,      length: int,      callback: AsyncCallback<void>    ): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | 存放增量数据的buffer。 |
| isFinished | boolean | 是 | true表示数据更新完成，当前buffer内存放最后一段数据；false表示数据还未更新完成，需要继续更新。 |
| offset | int | 是 | 即当前buffer中的数据首地址，相对于整个图片文件首地址的偏移量。单位：字节（Byte）。<br>**起始版本：** 11 |
| length | int | 是 | 当前buffer的长度。单位：字节（Byte）。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，当更新增量数据成功，err为undefined，否则为错误对象。 |

## writeImageMetadata

```TypeScript
writeImageMetadata(imageMetadata: ImageMetadata): Promise<void>
```

批量修改图片属性。使用Promise异步回调。 > **说明：** > > - 调用该接口修改属性会改变属性字节长度，建议通过传入文件描述符来创建[image.createImageSource](arkts-image-image-createimagesource-f.md#createImageSource)实例或通过传入的uri创建 > [image.createImageSource](arkts-image-image-createimagesource-f.md#createImageSource)实例。 > > - 该方法在内存中完成批量数据修改后会一次性写入文件，相比 > [modifyImageProperties](#modifyImageProperties) > 更高效。 > > - 支持修改JPEG、PNG和HEIF文件类型的图片属性，图片需要包含Exif信息。修改属性前，先通过supportedFormats属性查询设备是否支持HEIF格式的Exif读写。 > > - 从API版本26.0.0开始，支持修改JPEG、PNG、GIF格式图片的XMP元数据。XMP元数据的操作方法可以参考 > [XMPMetadata](../../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md)。 > > - 调用writeImageMetadata接口修改Exif字段时，必须确保对应的图片文件有写权限，否则会导致字段修改不成功。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageSource-writeImageMetadata(imageMetadata: ImageMetadata): Promise<void>--><!--Device-ImageSource-writeImageMetadata(imageMetadata: ImageMetadata): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imageMetadata | [ImageMetadata](arkts-image-image-imagemetadata-i.md) | 是 | 图像的元数据集。若imageMetadata中的属性值都为空，则清空所有Exif元数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7700102](../errorcode-image.md#7700102-不支持的mime类型) | Unsupported MIME type. |
| [7700204](../errorcode-image.md#7700204-无效参数) | Invalid parameter. Possible causes: The imageSource object is released. |
| [7700202](../errorcode-image.md#7700202-不支持的元数据) | Unsupported metadata. |

## supportedFormats

```TypeScript
readonly supportedFormats: Array<string>
```

支持的图片格式。 包括：PNG、JPEG、BMP、GIF、WebP、DNG、HEIC&lt;sup&gt;12+&lt;/sup&gt;、WBMP&lt;sup&gt;23+&lt;/sup&gt;、HEIFS&lt;sup&gt;23+&lt;/sup&gt;、TIFF&lt;sup&gt;23+&lt;/sup&gt;。从API版本2 6.0.0开始，增加支持AVIF、AVIS格式。 部分格式的解码能力依赖于具体的设备硬件，建议在调用前使用[image.getImageSourceSupportedFormats](arkts-image-image-getimagesourcesupportedformats-f.md#getImageSourceSupportedFormats)接口， 动态查询当前设备上的解码能力。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ImageSource-readonly supportedFormats: Array<string>--><!--Device-ImageSource-readonly supportedFormats: Array<string>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

