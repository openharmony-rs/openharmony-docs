# PixelMap

The **PixelMap** class provides APIs to read or write image data and obtain image information. Before calling any API in PixelMap, you must use [image.createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap-2)to create a PixelMap object. Currently, the maximum size of a serialized PixelMap is 128 MB. A larger size will cause a display failure. The size is calculated as follows: Width x Height x [Bytes per pixel](arkts-image-image-pixelmapformat-e.md).Since API version 11, PixelMap supports cross-thread calls through [Worker](../../apis-arkts/arkts-apis/arkts-worker.md). If a PixelMap object is invoked by another thread through [Worker](../../apis-arkts/arkts-apis/arkts-worker.md), all APIs of the PixelMap object cannot be called in the original thread. Otherwise, error 501 is reported, indicating that the server cannot complete the request.Before calling any API in PixelMap, you can use [image.createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap-2)to pass pixel data to create a PixelMap object, or use [ImageSource](arkts-multimedia-image.md) to decode an image to a PixelMap object.To develop an atomic service, use [ImageSource](arkts-multimedia-image.md) to create a PixelMap object.Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](arkts-image-image-pixelmap-i.md#release-2) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**起始版本：** 7

<!--Device-image-interface PixelMap--><!--Device-image-interface PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## applyColorSpace

```TypeScript
applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager, callback: AsyncCallback<void>): void
```

Performs color space conversion (CSC) on the image pixel color based on a given color space. This API uses an asynchronous callback to return the result.

**起始版本：** 11

<!--Device-PixelMap-applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager, callback: AsyncCallback<void>): void--><!--Device-PixelMap-applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetColorSpace | colorSpaceManager.ColorSpaceManager | 是 | Target color space. SRGB, DCI_P3, DISPLAY_P3,and ADOBE_RGB_1998 are supported. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | Callback used to return the result. If the operation is successful,**err** is **undefined**; otherwise, **err** is an error object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980104](../errorcode-image.md#62980104-图片初始化错误) | Failed to initialize the internal object. |
| [62980108](../errorcode-image.md#62980108-图片颜色转换错误) | Failed to convert the color space. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |

## applyColorSpace

```TypeScript
applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager): Promise<void>
```

Performs Color Space Converters (CSC) on the image pixel color based on a given color space. This API uses a promise to return the result.

**起始版本：** 11

<!--Device-PixelMap-applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager): Promise<void>--><!--Device-PixelMap-applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetColorSpace | colorSpaceManager.ColorSpaceManager | 是 | Target color space. SRGB, DCI_P3, DISPLAY_P3,and ADOBE_RGB_1998 are supported. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980104](../errorcode-image.md#62980104-图片初始化错误) | Failed to initialize the internal object. |
| [62980108](../errorcode-image.md#62980108-图片颜色转换错误) | Failed to convert the color space. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |

## applyCrop

```TypeScript
applyCrop(region: Region): Promise<void>
```

Crops the PixelMap.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-applyCrop(region: Region): Promise<void>--><!--Device-PixelMap-applyCrop(region: Region): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | [Region](arkts-image-image-region-i.md) | 是 | The region to crop. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600204](../errorcode-image.md#7600204-无效的区域) | The specified region is invalid or out of range. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory.Possible causes: 1. Failed to process pixel data. 2. The system is out of memory. |

## applyCropSync

```TypeScript
applyCropSync(region: Region): void
```

Crops the PixelMap.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-applyCropSync(region: Region): void--><!--Device-PixelMap-applyCropSync(region: Region): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | [Region](arkts-image-image-region-i.md) | 是 | The region to crop. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600204](../errorcode-image.md#7600204-无效的区域) | The specified region is invalid or out of range. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory.Possible causes: 1. Failed to process pixel data. 2. The system is out of memory. |

## applyFlip

```TypeScript
applyFlip(horizontal: boolean, vertical: boolean): Promise<void>
```

Flips the PixelMap in the horizontal and/or vertical directions.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-applyFlip(horizontal: boolean, vertical: boolean): Promise<void>--><!--Device-PixelMap-applyFlip(horizontal: boolean, vertical: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontal | boolean | 是 | Whether to flip horizontally. |
| vertical | boolean | 是 | Whether to flip vertically. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory. Possible cause: The system is out of memory. |

## applyFlipSync

```TypeScript
applyFlipSync(horizontal: boolean, vertical: boolean): void
```

Flips the PixelMap in the horizontal and/or vertical directions.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-applyFlipSync(horizontal: boolean, vertical: boolean): void--><!--Device-PixelMap-applyFlipSync(horizontal: boolean, vertical: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontal | boolean | 是 | Whether to flip horizontally. |
| vertical | boolean | 是 | Whether to flip vertically. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory. Possible cause: The system is out of memory. |

## applyRotate

```TypeScript
applyRotate(angle: number): Promise<void>
```

Rotates the PixelMap.

Note: YUV format PixelMaps only support rotation angles that are multiples of 90 degrees.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-applyRotate(angle: double): Promise<void>--><!--Device-PixelMap-applyRotate(angle: double): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | The rotation angle in degrees. Unit: Degree. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory.Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

## applyRotateSync

```TypeScript
applyRotateSync(angle: number): void
```

Rotates the PixelMap.

Note: YUV format PixelMaps only support rotation angles that are multiples of 90 degrees.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-applyRotateSync(angle: double): void--><!--Device-PixelMap-applyRotateSync(angle: double): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | The rotation angle in degrees. Unit: Degree. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory.Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

## applyScale

```TypeScript
applyScale(x: number, y: number, level?: AntiAliasingLevel): Promise<void>
```

Scales the PixelMap in the horizontal and/or vertical dimensions.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-applyScale(x: double, y: double, level?: AntiAliasingLevel): Promise<void>--><!--Device-PixelMap-applyScale(x: double, y: double, level?: AntiAliasingLevel): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | The scale ratio of width. Unit: Percentage. |
| y | number | 是 | The scale ratio of height. Unit: Percentage. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | 否 | The anti-aliasing algorithm to be used. Default value: NONE. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory.Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

## applyScaleSync

```TypeScript
applyScaleSync(x: number, y: number, level?: AntiAliasingLevel): void
```

Scales the PixelMap in the horizontal and/or vertical dimensions.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-applyScaleSync(x: double, y: double, level?: AntiAliasingLevel): void--><!--Device-PixelMap-applyScaleSync(x: double, y: double, level?: AntiAliasingLevel): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | The scale ratio of width. Unit: Percentage. |
| y | number | 是 | The scale ratio of height. Unit: Percentage. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | 否 | The anti-aliasing algorithm to be used. Default value: NONE. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory.Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

## applyTranslate

```TypeScript
applyTranslate(x: number, y: number): Promise<void>
```

Repositions the PixelMap in the horizontal and/or vertical directions.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-applyTranslate(x: double, y: double): Promise<void>--><!--Device-PixelMap-applyTranslate(x: double, y: double): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | The distance in pixels to move in the horizontal direction. Unit: px. |
| y | number | 是 | The distance in pixels to move in the vertical direction. Unit: px. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory.Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

## applyTranslateSync

```TypeScript
applyTranslateSync(x: number, y: number): void
```

Repositions the PixelMap in the horizontal and/or vertical directions.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-applyTranslateSync(x: double, y: double): void--><!--Device-PixelMap-applyTranslateSync(x: double, y: double): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | The distance in pixels to move in the horizontal direction. Unit: px. |
| y | number | 是 | The distance in pixels to move in the vertical direction. Unit: px. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory.Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

## clone

```TypeScript
clone(): Promise<PixelMap>
```

Copies this PixelMap object. This API uses a promise to return the result.

**起始版本：** 18

<!--Device-PixelMap-clone(): Promise<PixelMap>--><!--Device-PixelMap-clone(): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PixelMap> | Promise used to return the PixelMap object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [501](../errorcode-image.md#501-无法调用接口) | Resource unavailable. |
| [62980102](../errorcode-image.md#62980102-图片分配内存错误) | Image malloc abnormal. This status code is thrown when an error occurs during the process of copying data. |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | Image YUV And ASTC types are not supported. |
| [62980104](../errorcode-image.md#62980104-图片初始化错误) | Image initialization abnormal.This status code is thrown when an error occurs during the process of creating empty pixelmap. |
| [62980106](../errorcode-image.md#62980106-图片数据太大) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |

## cloneSync

```TypeScript
cloneSync(): PixelMap
```

Copies this PixelMap object. This API returns the result synchronously.

**起始版本：** 18

<!--Device-PixelMap-cloneSync(): PixelMap--><!--Device-PixelMap-cloneSync(): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | PixelMap object. If the operation fails, an error is thrown. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [501](../errorcode-image.md#501-无法调用接口) | Resource unavailable. |
| [62980102](../errorcode-image.md#62980102-图片分配内存错误) | Image malloc abnormal. This status code is thrown when an error occurs during the process of copying data. |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | Image YUV And ASTC types are not supported. |
| [62980104](../errorcode-image.md#62980104-图片初始化错误) | Image initialization abnormal.This status code is thrown when an error occurs during the process of creating empty pixelmap. |
| [62980106](../errorcode-image.md#62980106-图片数据太大) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |

## convertPixelFormat

```TypeScript
convertPixelFormat(targetPixelFormat: PixelMapFormat): Promise<void>
```

The method is used for the transformation of the image formats. Pixel data will be changed by calling this method.

**起始版本：** 12

<!--Device-PixelMap-convertPixelFormat(targetPixelFormat: PixelMapFormat): Promise<void>--><!--Device-PixelMap-convertPixelFormat(targetPixelFormat: PixelMapFormat): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetPixelFormat | [PixelMapFormat](arkts-image-image-pixelmapformat-e.md) | 是 | The pixel format for pixelmap conversion. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid input parameter. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980274](../errorcode-image.md#62980274-图片转换失败) | The conversion failed. |
| [62980276](../errorcode-image.md#62980276-不支持图片转换目标类型) | The type to be converted is an unsupported target pixel format. |
| [62980178](../errorcode-image.md#62980178-pixelmap创建失败) | Failed to create the pixelmap. |

## createAlphaPixelmap

```TypeScript
createAlphaPixelmap(): Promise<PixelMap>
```

Creates a PixelMap object that contains only the alpha channel information. This object can be used for the shadow effect. It is invalid for YUV images. This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use {@link extractAlphaPixelMap} instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-createAlphaPixelmap(): Promise<PixelMap>--><!--Device-PixelMap-createAlphaPixelmap(): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PixelMap> | Promise used to return the PixelMap object. |

## createAlphaPixelmap

```TypeScript
createAlphaPixelmap(callback: AsyncCallback<PixelMap>): void
```

Creates a PixelMap object that contains only the alpha channel information. This object can be used for the shadow effect. It is invalid for YUV images. This API returns the result through a callback.

Starting from API 26.0.0, it is recommended to use {@link extractAlphaPixelMap} instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-createAlphaPixelmap(callback: AsyncCallback<PixelMap>): void--><!--Device-PixelMap-createAlphaPixelmap(callback: AsyncCallback<PixelMap>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<PixelMap> | 是 | Callback used to return the result. If the operation is successful,**err** is undefined and **data** is the PixelMap object obtained; otherwise, **err** is an error object. |

## createAlphaPixelmapSync

```TypeScript
createAlphaPixelmapSync(): PixelMap
```

Creates a PixelMap object that contains only the alpha channel information. This object can be used for the shadow effect. This API returns the result synchronously. It is invalid for YUV images.

Starting from API 26.0.0, it is recommended to use {@link extractAlphaPixelMapSync} instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-createAlphaPixelmapSync(): PixelMap--><!--Device-PixelMap-createAlphaPixelmapSync(): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | PixelMap object. If the operation fails, an error is thrown. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## createCroppedAndScaledPixelMap

```TypeScript
createCroppedAndScaledPixelMap(region: Region, x: number, y: number, level?: AntiAliasingLevel): Promise<PixelMap>
```

Creates an image that has been cropped and resized based on the specified cropping area, scale factors of the width and height, and anti-aliasing level. This API uses a promise to return the result.

**起始版本：** 22

<!--Device-PixelMap-createCroppedAndScaledPixelMap(region: Region, x: double, y: double, level?: AntiAliasingLevel): Promise<PixelMap>--><!--Device-PixelMap-createCroppedAndScaledPixelMap(region: Region, x: double, y: double, level?: AntiAliasingLevel): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | [Region](arkts-image-image-region-i.md) | 是 | Area to crop. It must be within the original image's dimension (in pixels). |
| x | number | 是 | Scale factor of the width. It must not be **0**. |
| y | number | 是 | Scale factor of the height. It must not be **0**. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | 否 | Anti-aliasing level. Default value: **NONE**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PixelMap> | Promise used to return the PixelMap object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | The PixelMap has been released. |
| [7600204](../errorcode-image.md#7600204-无效的区域) | Invalid region. |
| [7600205](../errorcode-image.md#7600205-不支持的内存格式或像素格式) | Unsupported memory format or pixel format. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Memory alloc failed. |

## createCroppedAndScaledPixelMapSync

```TypeScript
createCroppedAndScaledPixelMapSync(region: Region, x: number, y: number, level?: AntiAliasingLevel): PixelMap
```

Creates an image that has been cropped and resized based on the specified cropping area, scale factors of the width and height, and anti-aliasing level. This API returns the result synchronously.

**起始版本：** 22

<!--Device-PixelMap-createCroppedAndScaledPixelMapSync(region: Region, x: double, y: double, level?: AntiAliasingLevel): PixelMap--><!--Device-PixelMap-createCroppedAndScaledPixelMapSync(region: Region, x: double, y: double, level?: AntiAliasingLevel): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | [Region](arkts-image-image-region-i.md) | 是 | Area to crop. It must be within the original image's dimension (in pixels). |
| x | number | 是 | Scale factor of the width. It must not be **0**. |
| y | number | 是 | Scale factor of the height. It must not be **0**. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | 否 | Anti-aliasing level. Default value: **NONE**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | PixelMap object. If the operation fails, an error is thrown. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | The PixelMap has been released. |
| [7600204](../errorcode-image.md#7600204-无效的区域) | Invalid region. |
| [7600205](../errorcode-image.md#7600205-不支持的内存格式或像素格式) | Unsupported memory format or pixel format. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Memory alloc failed. |

## createScaledPixelMap

```TypeScript
createScaledPixelMap(x: number, y: number, level?: AntiAliasingLevel): Promise<PixelMap>
```

Creates an image that has been resized based on the specified anti-aliasing level and the scale factors of the width and height. This API uses a promise to return the result.

**起始版本：** 18

<!--Device-PixelMap-createScaledPixelMap(x: double, y: double, level?: AntiAliasingLevel): Promise<PixelMap>--><!--Device-PixelMap-createScaledPixelMap(x: double, y: double, level?: AntiAliasingLevel): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | Scale factor of the width. |
| y | number | 是 | Scale factor of the height. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | 否 | Anti-aliasing level. The default value is **AntiAliasingLevel.NONE**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PixelMap> | Promise used to return the PixelMap object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## createScaledPixelMapSync

```TypeScript
createScaledPixelMapSync(x: number, y: number, level?: AntiAliasingLevel): PixelMap
```

Creates an image that has been resized based on the specified anti-aliasing level and the scale factors of the width and height. This API returns the result synchronously.

**起始版本：** 18

<!--Device-PixelMap-createScaledPixelMapSync(x: double, y: double, level?: AntiAliasingLevel): PixelMap--><!--Device-PixelMap-createScaledPixelMapSync(x: double, y: double, level?: AntiAliasingLevel): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | Scale factor of the width. |
| y | number | 是 | Scale factor of the height. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | 否 | Anti-aliasing level. The default value is **AntiAliasingLevel.NONE**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | PixelMap object. If the operation fails, an error is thrown. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## crop

```TypeScript
crop(region: Region, callback: AsyncCallback<void>): void
```

Crops this image based on a given size. This API uses an asynchronous callback to return the result.

Starting from API 26.0.0, it is recommended to use {@link applyCrop} instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-crop(region: Region, callback: AsyncCallback<void>): void--><!--Device-PixelMap-crop(region: Region, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | [Region](arkts-image-image-region-i.md) | 是 | Size of the image after cropping. The value cannot exceed the width or height of the image. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | Callback used to return the result. If the operation is successful,**err** is **undefined**; otherwise, **err** is an error object. |

## crop

```TypeScript
crop(region: Region): Promise<void>
```

Crops a PixelMap based on a given size. This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use {@link applyCrop} instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-crop(region: Region): Promise<void>--><!--Device-PixelMap-crop(region: Region): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | [Region](arkts-image-image-region-i.md) | 是 | Size of the image after cropping. The value cannot exceed the width or height of the image. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise that returns no value. |

## cropSync

```TypeScript
cropSync(region: Region): void
```

Crops this image based on a given size. This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use {@link applyCropSync} instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-cropSync(region: Region): void--><!--Device-PixelMap-cropSync(region: Region): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | [Region](arkts-image-image-region-i.md) | 是 | Size of the image after cropping. The value cannot exceed the width or height of the image. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## extractAlphaPixelMap

```TypeScript
extractAlphaPixelMap(): Promise<PixelMap>
```

Extracts the alpha channel from the current PixelMap to create a new ALPHA_U8 format PixelMap.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-extractAlphaPixelMap(): Promise<PixelMap>--><!--Device-PixelMap-extractAlphaPixelMap(): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PixelMap> | A Promise of the new ALPHA_U8 format PixelMap. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The current PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The current PixelMap has been passed across threads. |
| [7600305](../errorcode-image.md#7600305-创建pixelmap失败) | Failed to create the PixelMap.Possible cause: Current PixelMap data is corrupted. |
| [7600306](../errorcode-image.md#7600306-数据转换失败) | Failed to convert the data.Possible causes: 1. Failed to perform pixel format conversion. 2. The system is out of memory. |

## extractAlphaPixelMapSync

```TypeScript
extractAlphaPixelMapSync(): PixelMap
```

Extracts the alpha channel from the current PixelMap to create a new ALPHA_U8 format PixelMap.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-extractAlphaPixelMapSync(): PixelMap--><!--Device-PixelMap-extractAlphaPixelMapSync(): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | A new ALPHA_U8 format PixelMap. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The current PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The current PixelMap has been passed across threads. |
| [7600305](../errorcode-image.md#7600305-创建pixelmap失败) | Failed to create the PixelMap.Possible cause: Current PixelMap data is corrupted. |
| [7600306](../errorcode-image.md#7600306-数据转换失败) | Failed to convert the data.Possible causes: 1. Failed to perform pixel format conversion. 2. The system is out of memory. |

## flip

```TypeScript
flip(horizontal: boolean, vertical: boolean, callback: AsyncCallback<void>): void
```

Flips this image horizontally or vertically, or both. This API uses an asynchronous callback to return the result.

Starting from API 26.0.0, it is recommended to use {@link applyFlip} instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-flip(horizontal: boolean, vertical: boolean, callback: AsyncCallback<void>): void--><!--Device-PixelMap-flip(horizontal: boolean, vertical: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontal | boolean | 是 | Whether to flip the image horizontally. **true** to flip the image horizontally,**false** otherwise. |
| vertical | boolean | 是 | Whether to flip the image vertically. **true** to flip the image vertically,**false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | Callback used to return the result. If the operation is successful,**err** is **undefined**; otherwise, **err** is an error object. |

## flip

```TypeScript
flip(horizontal: boolean, vertical: boolean): Promise<void>
```

Flips a PixelMap based on a given angle. This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use {@link applyFlip} instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-flip(horizontal: boolean, vertical: boolean): Promise<void>--><!--Device-PixelMap-flip(horizontal: boolean, vertical: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontal | boolean | 是 | Whether to flip the image horizontally. **true** to flip the image horizontally,**false** otherwise. |
| vertical | boolean | 是 | Whether to flip the image vertically. **true** to flip the image vertically,**false** otherwise. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise that returns no value. |

## flipSync

```TypeScript
flipSync(horizontal: boolean, vertical: boolean): void
```

Flips this image horizontally or vertically, or both. This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use {@link applyFlipSync} instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-flipSync(horizontal: boolean, vertical: boolean): void--><!--Device-PixelMap-flipSync(horizontal: boolean, vertical: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontal | boolean | 是 | Whether to flip the image horizontally. **true** to flip the image horizontally,**false** otherwise. |
| vertical | boolean | 是 | Whether to flip the image vertically. **true** to flip the image vertically,**false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## getBytesNumberPerRow

```TypeScript
getBytesNumberPerRow(): number
```

Obtains the number of bytes per row of this image. Unit: bytes.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-getBytesNumberPerRow(): int--><!--Device-PixelMap-getBytesNumberPerRow(): int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Number of bytes per row. |

## getColorSpace

```TypeScript
getColorSpace(): colorSpaceManager.ColorSpaceManager
```

Obtains the color space of this image.

**起始版本：** 10

<!--Device-PixelMap-getColorSpace(): colorSpaceManager.ColorSpaceManager--><!--Device-PixelMap-getColorSpace(): colorSpaceManager.ColorSpaceManager-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| colorSpaceManager.ColorSpaceManager | Color space obtained. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980101](../errorcode-image.md#62980101-图片输入数据错误) | The image data is abnormal. |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | The image data is not supported. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |

## getDensity

```TypeScript
getDensity(): number
```

Obtains the pixel density of this image. Unit: ppi (pixels/inch)

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-getDensity(): int--><!--Device-PixelMap-getDensity(): int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Pixel density, in ppi. |

## getImageInfo

```TypeScript
getImageInfo(): Promise<ImageInfo>
```

Obtains the image information of a PixelMap. This API uses a promise to return the result.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-getImageInfo(): Promise<ImageInfo>--><!--Device-PixelMap-getImageInfo(): Promise<ImageInfo>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ImageInfo> | Promise used to return the image information. |

## getImageInfo

```TypeScript
getImageInfo(callback: AsyncCallback<ImageInfo>): void
```

Obtains the image information. This API uses an asynchronous callback to return the result.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-getImageInfo(callback: AsyncCallback<ImageInfo>): void--><!--Device-PixelMap-getImageInfo(callback: AsyncCallback<ImageInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<ImageInfo> | 是 | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the image information obtained; otherwise, **err** is an error object. |

## getImageInfoSync

```TypeScript
getImageInfoSync(): ImageInfo
```

Obtains the image information. This API returns the result synchronously.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-getImageInfoSync(): ImageInfo--><!--Device-PixelMap-getImageInfoSync(): ImageInfo-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageInfo](arkts-image-image-imageinfo-i.md) | Image information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## getMetadata

```TypeScript
getMetadata(key: HdrMetadataKey): HdrMetadataValue
```

Obtains the value of the metadata with a given key in this PixelMap.

**起始版本：** 12

<!--Device-PixelMap-getMetadata(key: HdrMetadataKey): HdrMetadataValue--><!--Device-PixelMap-getMetadata(key: HdrMetadataKey): HdrMetadataValue-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md) | 是 | Key of the HDR metadata. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HdrMetadataValue](arkts-image-image-hdrmetadatavalue-t.md) | Value of the metadata with the given key. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource unavailable. |
| [62980173](../errorcode-image.md#62980173-dma内存空间错误) | The DMA memory does not exist. |
| [62980302](../errorcode-image.md#62980302-内存拷贝失败) | Memory copy failed. Possibly caused by invalid metadata value. |

## getPixelBytesNumber

```TypeScript
getPixelBytesNumber(): number
```

Obtains the total number of bytes of this image. Unit: bytes.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-getPixelBytesNumber(): int--><!--Device-PixelMap-getPixelBytesNumber(): int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Total number of bytes. |

## getUniqueId

```TypeScript
getUniqueId(): number
```

Obtains the unique ID of this PixelMap.

**起始版本：** 22

<!--Device-PixelMap-getUniqueId(): int--><!--Device-PixelMap-getUniqueId(): int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Unique ID. The value is a positive integer. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | The PixelMap has been released. |

## isReleased

```TypeScript
isReleased(): boolean
```

Checks whether this PixelMap object is released. If released, any attempt to access the internal data of this object will fail.

> **NOTE**  
>  
> Release occurs when an ArkTS object relinquishes control over its associated native object. The memory occupied  
> by the native object is reclaimed only after all managing ArkTS objects have relinquished their control.

**起始版本：** 22

<!--Device-PixelMap-isReleased(): boolean--><!--Device-PixelMap-isReleased(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for whether the PixelMap object is released. **true** if released; **false** otherwise. |

## marshalling

```TypeScript
marshalling(sequence: rpc.MessageSequence): void
```

Marshals this PixelMap object and writes it to a MessageSequence object.

**起始版本：** 10

<!--Device-PixelMap-marshalling(sequence: rpc.MessageSequence): void--><!--Device-PixelMap-marshalling(sequence: rpc.MessageSequence): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sequence | rpc.MessageSequence | 是 | MessageSequence object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980097](../errorcode-image.md#62980097-pixelmap序列化传输失败) | IPC error. Possible cause: 1.IPC communication failed. 2. Image upload exception.3. Decode process exception. 4. Insufficient memory. |

## opacity

```TypeScript
opacity(rate: number, callback: AsyncCallback<void>): void
```

Sets an opacity rate for this image. This API uses an asynchronous callback to return the result. It is invalid for YUV images.

Starting from API 26.0.0, it is recommended to use {@link setOpacity} instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-opacity(rate: double, callback: AsyncCallback<void>): void--><!--Device-PixelMap-opacity(rate: double, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | number | 是 | Opacity rate. The value range is (0,1]. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | Callback used to return the result. If the operation is successful,**err** is **undefined**; otherwise, **err** is an error object. |

## opacity

```TypeScript
opacity(rate: number): Promise<void>
```

Sets an opacity rate for this image. It is invalid for YUV images. This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use {@link setOpacity} instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-opacity(rate: double): Promise<void>--><!--Device-PixelMap-opacity(rate: double): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | number | 是 | Opacity rate. The value range is (0,1]. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise that returns no value. |

## opacitySync

```TypeScript
opacitySync(rate: number): void
```

Sets an opacity rate for this image. This API returns the result synchronously. It is invalid for YUV images.

Starting from API 26.0.0, it is recommended to use {@link setOpacitySync} instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-opacitySync(rate: double): void--><!--Device-PixelMap-opacitySync(rate: double): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | number | 是 | Opacity rate. The value range is (0,1]. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## readAllPixelsToBuffer

```TypeScript
readAllPixelsToBuffer(dst: ArrayBuffer): Promise<void>
```

Reads all the pixel data from the PixelMap and writes the data to a buffer.The resulting data will be in the same pixel format as the PixelMap.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-readAllPixelsToBuffer(dst: ArrayBuffer): Promise<void>--><!--Device-PixelMap-readAllPixelsToBuffer(dst: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | The buffer to receive the pixel data from the PixelMap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible cause: Size of the buffer is too small. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Failed to copy the memory. |

## readAllPixelsToBufferSync

```TypeScript
readAllPixelsToBufferSync(dst: ArrayBuffer): void
```

Reads all the pixel data from the PixelMap and writes the data to a buffer.The resulting data will be in the same pixel format as the PixelMap.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-readAllPixelsToBufferSync(dst: ArrayBuffer): void--><!--Device-PixelMap-readAllPixelsToBufferSync(dst: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | The buffer to receive the pixel data from the PixelMap. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible cause: Size of the buffer is too small. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Failed to copy the memory. |

## readPixels

```TypeScript
readPixels(area: PositionArea): Promise<void>
```

Reads the pixels in the area specified by [PositionArea](arkts-image-image-positionarea-i.md).region of this PixelMap object in the BGRA_8888 format and writes the data to the [PositionArea](arkts-image-image-positionarea-i.md).pixels buffer. This API uses a promise to return the result.You can use a formula to calculate the size of the memory to be applied for based on **PositionArea**.YUV region calculation formula: region to read (region.size{width * height}) * 1.5 (1 * Y component + 0.25 * U component + 0.25 * V component)RGBA region calculation formula: region to read (region.size{width * height}) * 4 (1 * R component + 1 * G component + 1 * B component + 1 * A component)

Starting from API 26.0.0, it is recommended to use {@link readPixelsToArea} instead for better exception handling capabilities.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-readPixels(area: PositionArea): Promise<void>--><!--Device-PixelMap-readPixels(area: PositionArea): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area from which the pixels will be read. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise that returns no value. |

## readPixels

```TypeScript
readPixels(area: PositionArea, callback: AsyncCallback<void>): void
```

Reads the pixels in the area specified by [PositionArea](arkts-image-image-positionarea-i.md).region of this PixelMap object in the BGRA_8888 format and writes the data to the [PositionArea](arkts-image-image-positionarea-i.md).pixels buffer. This API uses an asynchronous callback to return the result.You can use a formula to calculate the size of the memory to be applied for based on **PositionArea**.YUV region calculation formula: region to read (region.size{width * height}) * 1.5 (1 * Y component + 0.25 * U component + 0.25 * V component)RGBA region calculation formula: region to read (region.size{width * height}) * 4 (1 * R component + 1 * G component + 1 * B component + 1 * A component)

Starting from API 26.0.0, it is recommended to use {@link readPixelsToArea} instead for better exception handling capabilities.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-readPixels(area: PositionArea, callback: AsyncCallback<void>): void--><!--Device-PixelMap-readPixels(area: PositionArea, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area from which the pixels will be read. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | Callback used to return the result. If the operation is successful,**err** is **undefined**; otherwise, **err** is an error object. |

## readPixelsSync

```TypeScript
readPixelsSync(area: PositionArea): void
```

Reads the pixels in the area specified by [PositionArea](arkts-image-image-positionarea-i.md).region of this PixelMap object in the BGRA_8888 format and writes the data to the [PositionArea](arkts-image-image-positionarea-i.md).pixels buffer. This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use {@link readPixelsToAreaSync} instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-readPixelsSync(area: PositionArea): void--><!--Device-PixelMap-readPixelsSync(area: PositionArea): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area from which the pixels will be read. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## readPixelsToArea

```TypeScript
readPixelsToArea(area: PositionArea): Promise<void>
```

Reads pixel data from a certain area of the PixelMap to a buffer. The resulting data will be in BGRA_8888 format.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-readPixelsToArea(area: PositionArea): Promise<void>--><!--Device-PixelMap-readPixelsToArea(area: PositionArea): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area of the PixelMap to read the data.Data will be read from the PixelMap and copied into PositionArea.pixels. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter.Possible causes: 1. PositionArea.pixels is too small. 2. PositionArea.region is out of range. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Failed to copy the memory. |

## readPixelsToAreaSync

```TypeScript
readPixelsToAreaSync(area: PositionArea): void
```

Reads pixel data from a certain area of the PixelMap to a buffer. The resulting data will be in BGRA_8888 format.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-readPixelsToAreaSync(area: PositionArea): void--><!--Device-PixelMap-readPixelsToAreaSync(area: PositionArea): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area of the PixelMap to read the data.Data will be read from the PixelMap and copied into PositionArea.pixels. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter.Possible causes: 1. PositionArea.pixels is too small. 2. PositionArea.region is out of range. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Failed to copy the memory. |

## readPixelsToBuffer

```TypeScript
readPixelsToBuffer(dst: ArrayBuffer): Promise<void>
```

Reads the pixels of this PixelMap object based on the PixelMap's pixel format and writes the data to the buffer.This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use {@link readAllPixelsToBuffer} instead for better exception handling capabilities.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-readPixelsToBuffer(dst: ArrayBuffer): Promise<void>--><!--Device-PixelMap-readPixelsToBuffer(dst: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | Buffer to which the pixels will be written. The buffer size is obtained by calling [getPixelBytesNumber](arkts-image-image-pixelmap-i.md#getpixelbytesnumber-1). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise that returns no value. |

## readPixelsToBuffer

```TypeScript
readPixelsToBuffer(dst: ArrayBuffer, callback: AsyncCallback<void>): void
```

Reads the pixels of this PixelMap object based on the PixelMap's pixel format and writes the data to the buffer.This API uses an asynchronous callback to return the result.

Starting from API 26.0.0, it is recommended to use {@link readAllPixelsToBuffer} instead for better exception handling capabilities.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-readPixelsToBuffer(dst: ArrayBuffer, callback: AsyncCallback<void>): void--><!--Device-PixelMap-readPixelsToBuffer(dst: ArrayBuffer, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | Buffer to which the pixels will be written. The buffer size is obtained by calling [getPixelBytesNumber](arkts-image-image-pixelmap-i.md#getpixelbytesnumber-1). |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | Callback used to return the result. If the operation is successful,**err** is **undefined**; otherwise, **err** is an error object. |

## readPixelsToBufferSync

```TypeScript
readPixelsToBufferSync(dst: ArrayBuffer): void
```

Reads the pixels of this PixelMap object based on the PixelMap's pixel format and writes the data to the buffer.This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use {@link readAllPixelsToBufferSync} instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-readPixelsToBufferSync(dst: ArrayBuffer): void--><!--Device-PixelMap-readPixelsToBufferSync(dst: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | Buffer to which the pixels will be written. The buffer size is obtained by calling [getPixelBytesNumber](arkts-image-image-pixelmap-i.md#getpixelbytesnumber-1). |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases this PixelMap instance. After the release, any attempt to access the internal data of this object will fail. This API uses an asynchronous callback to return the result.Images occupy a large amount of memory. When you finish using a PixelMap instance, call this API to free the memory promptly.Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

> **NOTE**  
>  
> Release occurs when an ArkTS object relinquishes control over its associated native object. The memory occupied  
> by the native object is reclaimed only after all managing ArkTS objects have relinquished their control.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-release(callback: AsyncCallback<void>): void--><!--Device-PixelMap-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | Callback used to return the result. If the operation is successful,**err** is **undefined**; otherwise, **err** is an error object. |

## release

```TypeScript
release(): Promise<void>
```

Releases this PixelMap instance. After the release, any attempt to access the internal data of this object will fail. This API uses a promise to return the result.Images occupy a large amount of memory. When you finish using a PixelMap instance, call this API to free the memory promptly.Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

> **NOTE**  
>  
> Release occurs when an ArkTS object relinquishes control over its associated native object. The memory occupied  
> by the native object is reclaimed only after all managing ArkTS objects have relinquished their control.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-release(): Promise<void>--><!--Device-PixelMap-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise that returns no value. |

## rotate

```TypeScript
rotate(angle: number, callback: AsyncCallback<void>): void
```

Rotates this image based on a given angle. This API uses an asynchronous callback to return the result.

Starting from API 26.0.0, it is recommended to use {@link applyRotate} instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-rotate(angle: double, callback: AsyncCallback<void>): void--><!--Device-PixelMap-rotate(angle: double, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | Angle to rotate. Unit: degrees. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | Callback used to return the result. If the operation is successful,**err** is **undefined**; otherwise, **err** is an error object. |

## rotate

```TypeScript
rotate(angle: number): Promise<void>
```

Rotates a PixelMap based on a given angle. This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use {@link applyRotate} instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-rotate(angle: double): Promise<void>--><!--Device-PixelMap-rotate(angle: double): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | Angle to rotate. Unit: degrees. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise that returns no value. |

## rotateSync

```TypeScript
rotateSync(angle: number): void
```

Rotates this image based on a given angle. This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use {@link applyRotateSync} instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-rotateSync(angle: double): void--><!--Device-PixelMap-rotateSync(angle: double): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | Angle to rotate. Unit: degrees. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## scale

```TypeScript
scale(x: number, y: number, callback: AsyncCallback<void>): void
```

Scales this image based on the scale factors of the width and height. This API uses an asynchronous callback to return the result.

Starting from API 26.0.0, it is recommended to use {@link applyScale} instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-scale(x: double, y: double, callback: AsyncCallback<void>): void--><!--Device-PixelMap-scale(x: double, y: double, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | Scale factor of the width. |
| y | number | 是 | Scale factor of the height. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | Callback used to return the result. If the operation is successful,**err** is **undefined**; otherwise, **err** is an error object. |

## scale

```TypeScript
scale(x: number, y: number): Promise<void>
```

Scales this image based on the scale factors of the width and height. This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use {@link applyScale} instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-scale(x: double, y: double): Promise<void>--><!--Device-PixelMap-scale(x: double, y: double): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | Scale factor of the width. |
| y | number | 是 | Scale factor of the height. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise that returns no value. |

## scale

```TypeScript
scale(x: number, y: number, level: AntiAliasingLevel): Promise<void>
```

Scales this image based on the specified anti-aliasing level and the scale factors for the width and height. This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use {@link applyScale} instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-scale(x: double, y: double, level: AntiAliasingLevel): Promise<void>--><!--Device-PixelMap-scale(x: double, y: double, level: AntiAliasingLevel): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | Scale factor of the width. |
| y | number | 是 | Scale factor of the height. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | 是 | Anti-aliasing level. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## scaleSync

```TypeScript
scaleSync(x: number, y: number): void
```

Scales this image based on the scale factors of the width and height. This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use {@link applyScaleSync} instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-scaleSync(x: double, y: double): void--><!--Device-PixelMap-scaleSync(x: double, y: double): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | Scale factor of the width. |
| y | number | 是 | Scale factor of the height. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## scaleSync

```TypeScript
scaleSync(x: number, y: number, level: AntiAliasingLevel): void
```

Scales this image based on the specified anti-aliasing level and the scale factors for the width and height. This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use {@link applyScaleSync} instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-scaleSync(x: double, y: double, level: AntiAliasingLevel): void--><!--Device-PixelMap-scaleSync(x: double, y: double, level: AntiAliasingLevel): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | Scale factor of the width. |
| y | number | 是 | Scale factor of the height. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | 是 | Anti-aliasing level. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## setColorSpace

```TypeScript
setColorSpace(colorSpace: colorSpaceManager.ColorSpaceManager): void
```

Set color space of pixel map.

This method is only used to set the colorspace property of pixelmap, while all pixel data remains the same after calling this method.If you want to change colorspace for all pixels, use method {@Link #applyColorSpace(colorSpaceManager.ColorSpaceManager)} or{@Link #applyColorSpace(colorSpaceManager.ColorSpaceManager, AsyncCallback<void>)}.

**起始版本：** 12

<!--Device-PixelMap-setColorSpace(colorSpace: colorSpaceManager.ColorSpaceManager): void--><!--Device-PixelMap-setColorSpace(colorSpace: colorSpaceManager.ColorSpaceManager): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorSpace | colorSpaceManager.ColorSpaceManager | 是 | The color space for pixel map. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | If the image parameter invalid. |

## setMemoryNameSync

```TypeScript
setMemoryNameSync(name: string): void
```

Sets a memory name for this PixelMap.

**起始版本：** 13

<!--Device-PixelMap-setMemoryNameSync(name: string): void--><!--Device-PixelMap-setMemoryNameSync(name: string): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | Memory name, which can be set only for a PixelMap with the DMA or ASHMEM memory format.The name length for DMA memory settings should be within the range of 1 to 255 bytes. For ASHMEM memory settings, the name length should be within the range of 1 to 244 bytes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.The length of the input parameter is too long.2.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource unavailable. |
| [62980286](../errorcode-image.md#62980286-pixelmap设置内存标识符失败) | Memory format not supported. |

## setMetadata

```TypeScript
setMetadata(key: HdrMetadataKey, value: HdrMetadataValue): Promise<void>
```

Sets the value for the metadata with a given key in this PixelMap. This API uses a promise to return the result.

**起始版本：** 12

<!--Device-PixelMap-setMetadata(key: HdrMetadataKey, value: HdrMetadataValue): Promise<void>--><!--Device-PixelMap-setMetadata(key: HdrMetadataKey, value: HdrMetadataValue): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md) | 是 | Key of the HDR metadata. |
| value | [HdrMetadataValue](arkts-image-image-hdrmetadatavalue-t.md) | 是 | Value of the metadata. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource unavailable. |
| [62980173](../errorcode-image.md#62980173-dma内存空间错误) | The DMA memory does not exist. |
| [62980302](../errorcode-image.md#62980302-内存拷贝失败) | Memory copy failed. Possibly caused by invalid metadata value. |

## setOpacity

```TypeScript
setOpacity(value: number): Promise<void>
```

Sets opacity of the PixelMap. Every pixel will be set to the same opacity value.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-setOpacity(value: double): Promise<void>--><!--Device-PixelMap-setOpacity(value: double): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | The target opacity value to be set. Unit: Percentage, Value range: (0,1].The valid range is (0.0, 1.0] where 1.0 is fully opaque and becoming transparent as it approaches 0.0. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible cause: The specified value is out of range. |
| [7600207](../errorcode-image.md#7600207-不支持的数据格式) | Unsupported data format. Possible cause: Alpha type is not supported. |

## setOpacitySync

```TypeScript
setOpacitySync(value: number): void
```

Sets opacity of the PixelMap. Every pixel will be set to the same opacity value.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-setOpacitySync(value: double): void--><!--Device-PixelMap-setOpacitySync(value: double): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | The target opacity value to be set. Unit: Percentage, Value range: (0,1].The valid range is (0.0, 1.0] where 1.0 is fully opaque and becoming transparent as it approaches 0.0. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible cause: The specified value is out of range. |
| [7600207](../errorcode-image.md#7600207-不支持的数据格式) | Unsupported data format. Possible cause: Alpha type is not supported. |

## setTransferDetached

```TypeScript
setTransferDetached(detached: boolean): void
```

Sets whether to detach from the original thread when this PixelMap is transmitted across threads. This API applies to the scenario where the PixelMap needs to be released immediately.

**起始版本：** 12

<!--Device-PixelMap-setTransferDetached(detached: boolean): void--><!--Device-PixelMap-setTransferDetached(detached: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| detached | boolean | 是 | Whether to detach from the original thread. **true** to detach, **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## toSdr

```TypeScript
toSdr(): Promise<void>
```

Convert pixelmap to standard dynamic range.

**起始版本：** 12

<!--Device-PixelMap-toSdr(): Promise<void>--><!--Device-PixelMap-toSdr(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980137](../errorcode-image.md#62980137-图片操作无效) | Invalid image operation. |

## translate

```TypeScript
translate(x: number, y: number, callback: AsyncCallback<void>): void
```

Translates this image based on given coordinates. This API uses an asynchronous callback to return the result.The size of the translated image is changed to width+X and height+Y. It is recommended that the new width and height not exceed the width and height of the screen.

Starting from API 26.0.0, it is recommended to use {@link applyTranslate} instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-translate(x: double, y: double, callback: AsyncCallback<void>): void--><!--Device-PixelMap-translate(x: double, y: double, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | X coordinate to translate, in px. |
| y | number | 是 | Y coordinate to translate, in px. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | Callback used to return the result. If the operation is successful,**err** is **undefined**; otherwise, **err** is an error object. |

## translate

```TypeScript
translate(x: number, y: number): Promise<void>
```

Translates a PixelMap based on given coordinates. This API uses a promise to return the result.The size of the translated image is changed to width+X and height+Y. It is recommended that the new width and height not exceed the width and height of the screen.

Starting from API 26.0.0, it is recommended to use {@link applyTranslate} instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-translate(x: double, y: double): Promise<void>--><!--Device-PixelMap-translate(x: double, y: double): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | X coordinate to translate, in px. |
| y | number | 是 | Y coordinate to translate, in px. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise that returns no value. |

## translateSync

```TypeScript
translateSync(x: number, y: number): void
```

Translates this image based on given coordinates. This API returns the result synchronously.The size of the translated image is changed to width+X and height+Y. It is recommended that the new width and height not exceed the width and height of the screen.

Starting from API 26.0.0, it is recommended to use {@link applyTranslateSync} instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-translateSync(x: double, y: double): void--><!--Device-PixelMap-translateSync(x: double, y: double): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | X coordinate to translate, in px. |
| y | number | 是 | Y coordinate to translate, in px. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## unmarshalling

```TypeScript
unmarshalling(sequence: rpc.MessageSequence): Promise<PixelMap>
```

Unmarshals a MessageSequence object to obtain a PixelMap object. To create a PixelMap object in synchronous mode,use [createPixelMapFromParcel](arkts-image-image-createpixelmapfromparcel-f.md#createpixelmapfromparcel-1).

**起始版本：** 10

<!--Device-PixelMap-unmarshalling(sequence: rpc.MessageSequence): Promise<PixelMap>--><!--Device-PixelMap-unmarshalling(sequence: rpc.MessageSequence): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sequence | rpc.MessageSequence | 是 | MessageSequence object that stores the PixelMap information. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PixelMap> | Promise used to return the PixelMap object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980097](../errorcode-image.md#62980097-pixelmap序列化传输失败) | IPC error. Possible cause: 1.IPC communication failed. 2. Image upload exception.3. Decode process exception. 4. Insufficient memory. |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception.2. Decoding process exception. 3. Insufficient memory. |

## writeAllPixelsFromBuffer

```TypeScript
writeAllPixelsFromBuffer(src: ArrayBuffer): Promise<void>
```

Reads the pixel data from a buffer and writes the data to the PixelMap.The source data must be in the same pixel format as the PixelMap.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-writeAllPixelsFromBuffer(src: ArrayBuffer): Promise<void>--><!--Device-PixelMap-writeAllPixelsFromBuffer(src: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | The buffer that contains pixel data to be written to the PixelMap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is not editable or is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible cause: Size of the buffer is too small. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Failed to copy the memory. |

## writeAllPixelsFromBufferSync

```TypeScript
writeAllPixelsFromBufferSync(src: ArrayBuffer): void
```

Reads the pixel data from a buffer and writes the data to the PixelMap.The source data must be in the same pixel format as the PixelMap.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-writeAllPixelsFromBufferSync(src: ArrayBuffer): void--><!--Device-PixelMap-writeAllPixelsFromBufferSync(src: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | The buffer that contains pixel data to be written to the PixelMap. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is not editable or is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible cause: Size of the buffer is too small. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Failed to copy the memory. |

## writeBufferToPixels

```TypeScript
writeBufferToPixels(src: ArrayBuffer): Promise<void>
```

Reads the pixels in the buffer based on the PixelMap's pixel format and writes the data to this PixelMap object.This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use {@link writeAllPixelsFromBuffer} instead for better exception handling capabilities.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-writeBufferToPixels(src: ArrayBuffer): Promise<void>--><!--Device-PixelMap-writeBufferToPixels(src: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | Buffer from which the pixels are read. The buffer size is obtained by calling [getPixelBytesNumber](arkts-image-image-pixelmap-i.md#getpixelbytesnumber-1). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise that returns no value. |

## writeBufferToPixels

```TypeScript
writeBufferToPixels(src: ArrayBuffer, callback: AsyncCallback<void>): void
```

Reads the pixels in the buffer based on the PixelMap's pixel format and writes the data to this PixelMap object.This API uses an asynchronous callback to return the result.

Starting from API 26.0.0, it is recommended to use {@link writeAllPixelsFromBuffer} instead for better exception handling capabilities.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-writeBufferToPixels(src: ArrayBuffer, callback: AsyncCallback<void>): void--><!--Device-PixelMap-writeBufferToPixels(src: ArrayBuffer, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | Buffer from which the pixels are read. The buffer size is obtained by calling [getPixelBytesNumber](arkts-image-image-pixelmap-i.md#getpixelbytesnumber-1). |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | Callback used to return the result. If the pixels in the buffer are successfully written to the PixelMap, **err** is **undefined**; otherwise, **err** is an error object. |

## writeBufferToPixelsSync

```TypeScript
writeBufferToPixelsSync(src: ArrayBuffer): void
```

Reads the pixels in the buffer based on the PixelMap's pixel format and writes the data to this PixelMap object.This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use {@link writeAllPixelsFromBufferSync} instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-writeBufferToPixelsSync(src: ArrayBuffer): void--><!--Device-PixelMap-writeBufferToPixelsSync(src: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | Buffer from which the pixels are read. The buffer size is obtained by calling [getPixelBytesNumber](arkts-image-image-pixelmap-i.md#getpixelbytesnumber-1). |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## writePixels

```TypeScript
writePixels(area: PositionArea): Promise<void>
```

Reads the pixels in the [PositionArea](arkts-image-image-positionarea-i.md).region buffer in the BGRA_8888 format and writes the data to the area specified by [PositionArea](arkts-image-image-positionarea-i.md).pixels in this PixelMap object. This API uses a promise to return the result.You can use a formula to calculate the size of the memory to be applied for based on **PositionArea**.YUV region calculation formula: region to read (region.size{width * height}) * 1.5 (1 * Y component + 0.25 * U component + 0.25 * V component)RGBA region calculation formula: region to read (region.size{width * height}) * 4 (1 * R component + 1 * G component + 1 * B component + 1 * A component)

Starting from API 26.0.0, it is recommended to use {@link writePixelsFromArea} instead for better exception handling capabilities.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-writePixels(area: PositionArea): Promise<void>--><!--Device-PixelMap-writePixels(area: PositionArea): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area to which the pixels will be written. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise that returns no value. |

## writePixels

```TypeScript
writePixels(area: PositionArea, callback: AsyncCallback<void>): void
```

Reads the pixels in the [PositionArea](arkts-image-image-positionarea-i.md).region buffer in the BGRA_8888 format and writes the data to the area specified by [PositionArea](arkts-image-image-positionarea-i.md).pixels in this PixelMap object. This API uses an asynchronous callback to return the result.You can use a formula to calculate the size of the memory to be applied for based on **PositionArea**.YUV region calculation formula: region to read (region.size{width * height}) * 1.5 (1 * Y component + 0.25 * U component + 0.25 * V component)RGBA region calculation formula: region to read (region.size{width * height}) * 4 (1 * R component + 1 * G component + 1 * B component + 1 * A component)

Starting from API 26.0.0, it is recommended to use {@link writePixelsFromArea} instead for better exception handling capabilities.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-writePixels(area: PositionArea, callback: AsyncCallback<void>): void--><!--Device-PixelMap-writePixels(area: PositionArea, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area to which the pixels will be written. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | Callback used to return the result. If the operation is successful,**err** is **undefined**; otherwise, **err** is an error object. |

## writePixelsFromArea

```TypeScript
writePixelsFromArea(area: PositionArea): Promise<void>
```

Writes data from a buffer to a certain area of the PixelMap. The source data must be in BGRA_8888 format.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-writePixelsFromArea(area: PositionArea): Promise<void>--><!--Device-PixelMap-writePixelsFromArea(area: PositionArea): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area of the PixelMap to write the data.Data will be copied from PositionArea.pixels to the PixelMap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is not editable or is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter.Possible causes: 1. PositionArea.pixels is too small. 2. PositionArea.region is out of range. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Failed to copy the memory. |

## writePixelsFromAreaSync

```TypeScript
writePixelsFromAreaSync(area: PositionArea): void
```

Writes data from a buffer to a certain area of the PixelMap. The source data must be in BGRA_8888 format.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-writePixelsFromAreaSync(area: PositionArea): void--><!--Device-PixelMap-writePixelsFromAreaSync(area: PositionArea): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area of the PixelMap to write the data.Data will be copied from PositionArea.pixels to the PixelMap. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is not editable or is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter.Possible causes: 1. PositionArea.pixels is too small. 2. PositionArea.region is out of range. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Failed to copy the memory. |

## writePixelsSync

```TypeScript
writePixelsSync(area: PositionArea): void
```

Reads the pixels in the [PositionArea](arkts-image-image-positionarea-i.md).region buffer in the BGRA_8888 format and writes the data to the area specified by [PositionArea](arkts-image-image-positionarea-i.md).pixels in this PixelMap object. This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use {@link writePixelsFromAreaSync} instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-writePixelsSync(area: PositionArea): void--><!--Device-PixelMap-writePixelsSync(area: PositionArea): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area to which the pixels will be written. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

## isEditable

```TypeScript
readonly isEditable: boolean
```

Whether the image pixels are editable. **true** if editable, **false** otherwise. The value **false** provides better image rendering and transmission performance.<br>This API can be used in atomic services since API version 11.<br>This API can be used in ArkTS widgets since API version 12.

**类型：** boolean

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PixelMap-readonly isEditable: boolean--><!--Device-PixelMap-readonly isEditable: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## isStrideAlignment

```TypeScript
readonly isStrideAlignment: boolean
```

Whether the row data of the image is memory aligned. The value **true** means that the row data is memory-aligned, and there may be blank bytes padded at the end of each row to meet alignment requirements. The value **false** means that the row data is not memory-aligned, and rows are packed contiguously with no padding bytes at the end.

**类型：** boolean

**起始版本：** 11

<!--Device-PixelMap-readonly isStrideAlignment: boolean--><!--Device-PixelMap-readonly isStrideAlignment: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

