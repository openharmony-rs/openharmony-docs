# PixelMap

The **PixelMap** class provides APIs to read or write image data and obtain image information. Before calling any API in PixelMap, you must use [image.createPixelMap](arkts-image-image-createpixelmap-f.md) to create a PixelMap object. Currently, the maximum size of a serialized PixelMap is 128 MB. A larger size will cause a display failure. The size is calculated as follows: Width x Height x [Bytes per pixel](arkts-image-image-pixelmapformat-e.md). Since API version 11, PixelMap supports cross-thread calls through [Worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md). If a PixelMap object is invoked by another thread through [Worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md), all APIs of the PixelMap object cannot be called in the original thread. Otherwise, error 501 is reported, indicating that the server cannot complete the request. Before calling any API in PixelMap, you can use [image.createPixelMap](arkts-image-image-createpixelmap-f.md) to pass pixel data to create a PixelMap object, or use [ImageSource](arkts-multimedia-image.md) to decode an image to a PixelMap object. To develop an atomic service, use [ImageSource](arkts-multimedia-image.md) to create a PixelMap object. Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**起始版本：** 7

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

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetColorSpace | colorSpaceManager.ColorSpaceManager | 是 | Target color space. SRGB, DCI_P3, DISPLAY_P3, and ADOBE_RGB_1998 are supported. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980104](../errorcode-image.md#62980104-图片初始化错误) | Failed to initialize the internal object. |
| [62980108](../errorcode-image.md#62980108-图片颜色转换错误) | Failed to convert the color space. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |

**示例**

```TypeScript
import { colorSpaceManager } from '@kit.ArkGraphics2D';
import { BusinessError } from '@kit.BasicServicesKit';

function applyColorSpace(pixelMap: image.PixelMap) {
  const colorSpaceName = colorSpaceManager.ColorSpace.SRGB;
  const targetColorSpace: colorSpaceManager.ColorSpaceManager = colorSpaceManager.create(colorSpaceName);
  pixelMap.applyColorSpace(targetColorSpace, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to apply color space. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in applying color space.');
  });
}
```

## applyColorSpace

```TypeScript
applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager): Promise<void>
```

Performs Color Space Converters (CSC) on the image pixel color based on a given color space. This API uses a promise to return the result.

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetColorSpace | colorSpaceManager.ColorSpaceManager | 是 | Target color space. SRGB, DCI_P3, DISPLAY_P3, and ADOBE_RGB_1998 are supported. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980104](../errorcode-image.md#62980104-图片初始化错误) | Failed to initialize the internal object. |
| [62980108](../errorcode-image.md#62980108-图片颜色转换错误) | Failed to convert the color space. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |

**示例**

```TypeScript
import { colorSpaceManager } from '@kit.ArkGraphics2D';
import { BusinessError } from '@kit.BasicServicesKit';

function applyColorSpace(pixelMap: image.PixelMap) {
  const colorSpaceName = colorSpaceManager.ColorSpace.SRGB;
  const targetColorSpace: colorSpaceManager.ColorSpaceManager = colorSpaceManager.create(colorSpaceName);
  pixelMap.applyColorSpace(targetColorSpace).then(() => {
    console.info('Succeeded in applying color space.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to apply color space. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## applyCrop

```TypeScript
applyCrop(region: Region): Promise<void>
```

Crops the PixelMap.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | Region | 是 | The region to crop. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600204](../errorcode-image.md#7600204-无效的区域) | The specified region is invalid or out of range. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory. Possible causes: 1. Failed to process pixel data. 2. The system is out of memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyCrop(pixelMap: image.PixelMap) {
  const currSize = pixelMap.getImageInfoSync().size;
  const region: image.Region = { // 裁剪区域设为图像中心四分之一的区域。
    x: currSize.width / 4,
    y: currSize.height / 4,
    size: {
      width: currSize.width / 2,
      height: currSize.height / 2
    }
  };

  pixelMap.applyCrop(region)
    .then(() => {
      console.info('Succeeded in cropping the PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to crop the PixelMap. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## applyCropSync

```TypeScript
applyCropSync(region: Region): void
```

Crops the PixelMap.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | Region | 是 | The region to crop. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600204](../errorcode-image.md#7600204-无效的区域) | The specified region is invalid or out of range. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory. Possible causes: 1. Failed to process pixel data. 2. The system is out of memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyCropSync(pixelMap: image.PixelMap) {
  const currSize = pixelMap.getImageInfoSync().size;
  const region: image.Region = { // 裁剪区域设为图像中心四分之一的区域。
    x: currSize.width / 4,
    y: currSize.height / 4,
    size: {
      width: currSize.width / 2,
      height: currSize.height / 2
    }
  };

  try {
    pixelMap.applyCropSync(region);
    console.info('Succeeded in cropping the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to crop the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## applyFlip

```TypeScript
applyFlip(horizontal: boolean, vertical: boolean): Promise<void>
```

Flips the PixelMap in the horizontal and/or vertical directions.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontal | boolean | 是 | Whether to flip horizontally. |
| vertical | boolean | 是 | Whether to flip vertically. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory. Possible cause: The system is out of memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyFlip(pixelMap: image.PixelMap) {
  const horizontal: boolean = true;
  const vertical: boolean = false;
  pixelMap.applyFlip(horizontal, vertical)
    .then(() => {
      console.info('Succeeded in flipping the PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to flip the PixelMap. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## applyFlipSync

```TypeScript
applyFlipSync(horizontal: boolean, vertical: boolean): void
```

Flips the PixelMap in the horizontal and/or vertical directions.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontal | boolean | 是 | Whether to flip horizontally. |
| vertical | boolean | 是 | Whether to flip vertically. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory. Possible cause: The system is out of memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyFlipSync(pixelMap: image.PixelMap) {
  const horizontal: boolean = true;
  const vertical: boolean = false;
  try {
    pixelMap.applyFlipSync(horizontal, vertical);
    console.info('Succeeded in flipping the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to flip the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## applyRotate

```TypeScript
applyRotate(angle: number): Promise<void>
```

Rotates the PixelMap.Note: YUV format PixelMaps only support rotation angles that are multiples of 90 degrees.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | The rotation angle in degrees. Unit: Degree. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyRotate(pixelMap: image.PixelMap) {
  const angle: number = 90.0;
  pixelMap.applyRotate(angle)
    .then(() => {
      console.info('Succeeded in rotating the PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to rotate the PixelMap. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## applyRotateSync

```TypeScript
applyRotateSync(angle: number): void
```

Rotates the PixelMap.Note: YUV format PixelMaps only support rotation angles that are multiples of 90 degrees.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | The rotation angle in degrees. Unit: Degree. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyRotateSync(pixelMap: image.PixelMap) {
  const angle: number = 90.0;
  try {
    pixelMap.applyRotateSync(angle);
    console.info('Succeeded in rotating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to rotate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## applyScale

```TypeScript
applyScale(x: number, y: number, level?: AntiAliasingLevel): Promise<void>
```

Scales the PixelMap in the horizontal and/or vertical dimensions.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

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
| Promise & lt;void & gt; | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyScale(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.5;
  pixelMap.applyScale(scaleX, scaleY, image.AntiAliasingLevel.LOW)
    .then(() => {
      console.info('Succeeded in scaling the PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## applyScaleSync

```TypeScript
applyScaleSync(x: number, y: number, level?: AntiAliasingLevel): void
```

Scales the PixelMap in the horizontal and/or vertical dimensions.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

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
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyScaleSync(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.5;
  try {
    pixelMap.applyScaleSync(scaleX, scaleY, image.AntiAliasingLevel.LOW);
    console.info('Succeeded in scaling the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## applyTranslate

```TypeScript
applyTranslate(x: number, y: number): Promise<void>
```

Repositions the PixelMap in the horizontal and/or vertical directions.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | The distance in pixels to move in the horizontal direction. Unit: px. |
| y | number | 是 | The distance in pixels to move in the vertical direction. Unit: px. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyTranslate(pixelMap: image.PixelMap) {
  const translateX: number = 50.0;
  const translateY: number = 10.0;
  pixelMap.applyTranslate(translateX, translateY)
    .then(() => {
      console.info('Succeeded in translating the PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to translate the PixelMap. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## applyTranslateSync

```TypeScript
applyTranslateSync(x: number, y: number): void
```

Repositions the PixelMap in the horizontal and/or vertical directions.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | The distance in pixels to move in the horizontal direction. Unit: px. |
| y | number | 是 | The distance in pixels to move in the vertical direction. Unit: px. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyTranslateSync(pixelMap: image.PixelMap) {
  const translateX: number = 50.0;
  const translateY: number = 10.0;
  try {
    pixelMap.applyTranslateSync(translateX, translateY);
    console.info('Succeeded in translating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to translate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## clone

```TypeScript
clone(): Promise<PixelMap>
```

Copies this PixelMap object. This API uses a promise to return the result.

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;PixelMap & gt; | Promise used to return the PixelMap object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [501](../errorcode-image.md#501-无法调用接口) | Resource unavailable. |
| [62980102](../errorcode-image.md#62980102-图片分配内存错误) | Image malloc abnormal. This status code is thrown when an error occurs during the process of copying data. |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | Image YUV And ASTC types are not supported. |
| [62980104](../errorcode-image.md#62980104-图片初始化错误) | Image initialization abnormal. This status code is thrown when an error occurs during the process of creating empty pixelmap. |
| [62980106](../errorcode-image.md#62980106-图片数据太大) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function clone(pixelMap: image.PixelMap) {
  pixelMap.clone().then((clonedPixelMap: image.PixelMap) => {
    console.info('Succeeded in cloning the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to clone the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## cloneSync

```TypeScript
cloneSync(): PixelMap
```

Copies this PixelMap object. This API returns the result synchronously.

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | PixelMap object. If the operation fails, an error is thrown. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [501](../errorcode-image.md#501-无法调用接口) | Resource unavailable. |
| [62980102](../errorcode-image.md#62980102-图片分配内存错误) | Image malloc abnormal. This status code is thrown when an error occurs during the process of copying data. |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | Image YUV And ASTC types are not supported. |
| [62980104](../errorcode-image.md#62980104-图片初始化错误) | Image initialization abnormal. This status code is thrown when an error occurs during the process of creating empty pixelmap. |
| [62980106](../errorcode-image.md#62980106-图片数据太大) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function cloneSync(pixelMap: image.PixelMap) {
  try {
    let clonedPixelMap: image.PixelMap = pixelMap.cloneSync();
    console.info('Succeeded in cloning the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to clone the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## convertPixelFormat

```TypeScript
convertPixelFormat(targetPixelFormat: PixelMapFormat): Promise<void>
```

The method is used for the transformation of the image formats. Pixel data will be changed by calling this method.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetPixelFormat | [PixelMapFormat](arkts-image-image-pixelmapformat-e.md) | 是 | The pixel format for pixelmap conversion. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid input parameter. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | The image source data is incomplete. |
| [62980274](../errorcode-image.md#62980274-图片转换失败) | The conversion failed. |
| [62980276](../errorcode-image.md#62980276-不支持图片转换目标类型) | The type to be converted is an unsupported target pixel format. |
| [62980178](../errorcode-image.md#62980178-pixelmap创建失败) | Failed to create the pixelmap. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function convertPixelFormat(pixelMap: image.PixelMap) {
  // 设置目标像素格式为NV12。
  let targetPixelFormat = image.PixelMapFormat.NV12;
  pixelMap.convertPixelFormat(targetPixelFormat).then(() => {
    console.info('Succeeded in converting pixel format.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to convert pixel format. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## createAlphaPixelmap

```TypeScript
createAlphaPixelmap(): Promise<PixelMap>
```

Creates a PixelMap object that contains only the alpha channel information. This object can be used for the shadow effect. It is invalid for YUV images. This API uses a promise to return the result.Starting from API 26.0.0, it is recommended to use [extractAlphaPixelMap](#extractalphapixelmap) instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;PixelMap & gt; | Promise used to return the PixelMap object. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createAlphaPixelmap(pixelMap: image.PixelMap) {
  pixelMap.createAlphaPixelmap().then((alphaPixelMap: image.PixelMap) => {
    console.info('Succeeded in creating alpha PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create alpha PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## createAlphaPixelmap

```TypeScript
createAlphaPixelmap(callback: AsyncCallback<PixelMap>): void
```

Creates a PixelMap object that contains only the alpha channel information. This object can be used for the shadow effect. It is invalid for YUV images. This API returns the result through a callback.Starting from API 26.0.0, it is recommended to use [extractAlphaPixelMap](#extractalphapixelmap) instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;PixelMap&gt; | 是 | Callback used to return the result. If the operation is successful, **err** is undefined and **data** is the PixelMap object obtained; otherwise, **err** is an error object. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createAlphaPixelmap(pixelMap: image.PixelMap) {
  pixelMap.createAlphaPixelmap((err: BusinessError, alphaPixelMap: image.PixelMap) => {
    if (err) {
      console.error(`Failed to create alpha PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in creating alpha PixelMap.');
  });
}
```

## createAlphaPixelmapSync

```TypeScript
createAlphaPixelmapSync(): PixelMap
```

Creates a PixelMap object that contains only the alpha channel information. This object can be used for the shadow effect. This API returns the result synchronously. It is invalid for YUV images.Starting from API 26.0.0, it is recommended to use [extractAlphaPixelMapSync](#extractalphapixelmapsync) instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | PixelMap object. If the operation fails, an error is thrown. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createAlphaPixelmapSync(pixelMap: image.PixelMap) {
  try {
    let alphaPixelMap: image.PixelMap = pixelMap.createAlphaPixelmapSync();
    if (alphaPixelMap == undefined) {
      console.error(`Failed to create alpha PixelMap.`);
      return;
    }
    console.info('Succeeded in creating alpha PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create alpha PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## createCroppedAndScaledPixelMap

```TypeScript
createCroppedAndScaledPixelMap(region: Region, x: number, y: number, level?: AntiAliasingLevel): Promise<PixelMap>
```

Creates an image that has been cropped and resized based on the specified cropping area, scale factors of the width and height, and anti-aliasing level. This API uses a promise to return the result.

**起始版本：** 22

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | Region | 是 | Area to crop. It must be within the original image's dimension (in pixels). |
| x | number | 是 | Scale factor of the width. It must not be **0**. |
| y | number | 是 | Scale factor of the height. It must not be **0**. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | 否 | Anti-aliasing level. Default value: **NONE**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;PixelMap & gt; | Promise used to return the PixelMap object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | The PixelMap has been released. |
| [7600204](../errorcode-image.md#7600204-无效的区域) | Invalid region. |
| [7600205](../errorcode-image.md#7600205-不支持的内存格式或像素格式) | Unsupported memory format or pixel format. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Memory alloc failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createCroppedAndScaledPixelMap(pixelMap: image.PixelMap) {
  const imageInfo = pixelMap.getImageInfoSync();
  const region: image.Region = {
    size: { width: imageInfo.size.width / 2, height: imageInfo.size.height / 2 },
    x: imageInfo.size.width / 4,
    y: imageInfo.size.height / 4
  };
  const scaleX: number = 2.0;
  const scaleY: number = 2.0;
  pixelMap.createCroppedAndScaledPixelMap(region, scaleX, scaleY, image.AntiAliasingLevel.HIGH)
    .then((croppedAndScaled: image.PixelMap) => {
      console.info('Succeeded in creating cropped and scaled PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to create cropped and scaled PixelMap. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## createCroppedAndScaledPixelMapSync

```TypeScript
createCroppedAndScaledPixelMapSync(region: Region, x: number, y: number, level?: AntiAliasingLevel): PixelMap
```

Creates an image that has been cropped and resized based on the specified cropping area, scale factors of the width and height, and anti-aliasing level. This API returns the result synchronously.

**起始版本：** 22

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | Region | 是 | Area to crop. It must be within the original image's dimension (in pixels). |
| x | number | 是 | Scale factor of the width. It must not be **0**. |
| y | number | 是 | Scale factor of the height. It must not be **0**. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | 否 | Anti-aliasing level. Default value: **NONE**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | PixelMap object. If the operation fails, an error is thrown. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | The PixelMap has been released. |
| [7600204](../errorcode-image.md#7600204-无效的区域) | Invalid region. |
| [7600205](../errorcode-image.md#7600205-不支持的内存格式或像素格式) | Unsupported memory format or pixel format. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Memory alloc failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createCroppedAndScaledPixelMapSync(pixelMap: image.PixelMap) {
  const imageInfo = pixelMap.getImageInfoSync();
  const region: image.Region = {
    size: { width: imageInfo.size.width / 2, height: imageInfo.size.height / 2 },
    x: imageInfo.size.width / 4,
    y: imageInfo.size.height / 4
  };
  const scaleX: number = 2.0;
  const scaleY: number = 2.0;
  try {
    const croppedAndScaled = pixelMap.createCroppedAndScaledPixelMapSync(region, scaleX, scaleY, image.AntiAliasingLevel.HIGH);
    console.info('Succeeded in creating cropped and scaled PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create cropped and scaled PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## createScaledPixelMap

```TypeScript
createScaledPixelMap(x: number, y: number, level?: AntiAliasingLevel): Promise<PixelMap>
```

Creates an image that has been resized based on the specified anti-aliasing level and the scale factors of the width and height. This API uses a promise to return the result.

**起始版本：** 18

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
| Promise & lt;PixelMap & gt; | Promise used to return the PixelMap object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createScaledPixelMap(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  pixelMap.createScaledPixelMap(scaleX, scaleY, image.AntiAliasingLevel.LOW).then((scaledPixelMap: image.PixelMap) => {
    console.info('Succeeded in creating scaled PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create scaled PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## createScaledPixelMapSync

```TypeScript
createScaledPixelMapSync(x: number, y: number, level?: AntiAliasingLevel): PixelMap
```

Creates an image that has been resized based on the specified anti-aliasing level and the scale factors of the width and height. This API returns the result synchronously.

**起始版本：** 18

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
| PixelMap | PixelMap object. If the operation fails, an error is thrown. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createScaledPixelMapSync(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  try {
    let scaledPixelMap = pixelMap.createScaledPixelMapSync(scaleX, scaleY, image.AntiAliasingLevel.LOW);
    console.info('Succeeded in creating scaled PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create scaled PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## crop

```TypeScript
crop(region: Region, callback: AsyncCallback<void>): void
```

Crops this image based on a given size. This API uses an asynchronous callback to return the result.Starting from API 26.0.0, it is recommended to use [applyCrop](#applycrop) instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | Region | 是 | Size of the image after cropping. The value cannot exceed the width or height of the image. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function crop(pixelMap: image.PixelMap) {
  const region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  pixelMap.crop(region, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to crop the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info("Succeeded in cropping the PixelMap.");
  });
}
```

## crop

```TypeScript
crop(region: Region): Promise<void>
```

Crops a PixelMap based on a given size. This API uses a promise to return the result.Starting from API 26.0.0, it is recommended to use [applyCrop](#applycrop) instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | Region | 是 | Size of the image after cropping. The value cannot exceed the width or height of the image. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise that returns no value. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function crop(pixelMap: image.PixelMap) {
  const region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  pixelMap.crop(region).then(() => {
    console.info('Succeeded in cropping the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to crop the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## cropSync

```TypeScript
cropSync(region: Region): void
```

Crops this image based on a given size. This API returns the result synchronously.Starting from API 26.0.0, it is recommended to use [applyCropSync](#applycropsync) instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | Region | 是 | Size of the image after cropping. The value cannot exceed the width or height of the image. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function cropSync(pixelMap: image.PixelMap) {
  const region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  try {
    pixelMap.cropSync(region);
    console.info('Succeeded in cropping the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to crop the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## extractAlphaPixelMap

```TypeScript
extractAlphaPixelMap(): Promise<PixelMap>
```

Extracts the alpha channel from the current PixelMap to create a new ALPHA_U8 format PixelMap.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;PixelMap & gt; | A Promise of the new ALPHA_U8 format PixelMap. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The current PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The current PixelMap has been passed across threads. |
| [7600305](../errorcode-image.md#7600305-创建pixelmap失败) | Failed to create the PixelMap. Possible cause: Current PixelMap data is corrupted. |
| [7600306](../errorcode-image.md#7600306-数据转换失败) | Failed to convert the data. Possible causes: 1. Failed to perform pixel format conversion. 2. The system is out of memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function extractAlphaPixelMap(pixelMap: image.PixelMap) {
  pixelMap.extractAlphaPixelMap()
    .then((alphaMap: image.PixelMap) => {
      console.info('Succeeded in creating alpha PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to create alpha PixelMap. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## extractAlphaPixelMapSync

```TypeScript
extractAlphaPixelMapSync(): PixelMap
```

Extracts the alpha channel from the current PixelMap to create a new ALPHA_U8 format PixelMap.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | A new ALPHA_U8 format PixelMap. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The current PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The current PixelMap has been passed across threads. |
| [7600305](../errorcode-image.md#7600305-创建pixelmap失败) | Failed to create the PixelMap. Possible cause: Current PixelMap data is corrupted. |
| [7600306](../errorcode-image.md#7600306-数据转换失败) | Failed to convert the data. Possible causes: 1. Failed to perform pixel format conversion. 2. The system is out of memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function extractAlphaPixelMapSync(pixelMap: image.PixelMap) {
  try {
    const alphaMap = pixelMap.extractAlphaPixelMapSync();
    console.info('Succeeded in creating alpha PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create alpha PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## flip

```TypeScript
flip(horizontal: boolean, vertical: boolean, callback: AsyncCallback<void>): void
```

Flips this image horizontally or vertically, or both. This API uses an asynchronous callback to return the result.Starting from API 26.0.0, it is recommended to use [applyFlip](#applyflip) instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontal | boolean | 是 | Whether to flip the image horizontally. **true** to flip the image horizontally, **false** otherwise. |
| vertical | boolean | 是 | Whether to flip the image vertically. **true** to flip the image vertically, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function flip(pixelMap: image.PixelMap) {
  const horizontal: boolean = true;
  const vertical: boolean = false;
  pixelMap.flip(horizontal, vertical, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to flip the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info("Succeeded in flipping the PixelMap.");
  });
}
```

## flip

```TypeScript
flip(horizontal: boolean, vertical: boolean): Promise<void>
```

Flips a PixelMap based on a given angle. This API uses a promise to return the result.Starting from API 26.0.0, it is recommended to use [applyFlip](#applyflip) instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontal | boolean | 是 | Whether to flip the image horizontally. **true** to flip the image horizontally, **false** otherwise. |
| vertical | boolean | 是 | Whether to flip the image vertically. **true** to flip the image vertically, **false** otherwise. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise that returns no value. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function flip(pixelMap: image.PixelMap) {
  const horizontal: boolean = true;
  const vertical: boolean = false;
  pixelMap.flip(horizontal, vertical).then(() => {
    console.info('Succeeded in flipping the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to flip the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## flipSync

```TypeScript
flipSync(horizontal: boolean, vertical: boolean): void
```

Flips this image horizontally or vertically, or both. This API returns the result synchronously.Starting from API 26.0.0, it is recommended to use [applyFlipSync](#applyflipsync) instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontal | boolean | 是 | Whether to flip the image horizontally. **true** to flip the image horizontally, **false** otherwise. |
| vertical | boolean | 是 | Whether to flip the image vertically. **true** to flip the image vertically, **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function flipSync(pixelMap: image.PixelMap) {
  const horizontal: boolean = true;
  const vertical: boolean = false;
  try {
    pixelMap.flipSync(horizontal, vertical);
    console.info('Succeeded in flipping the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to flip the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## getBytesNumberPerRow

```TypeScript
getBytesNumberPerRow(): number
```

Obtains the number of bytes per row of this image. Unit: bytes.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Number of bytes per row. |

**示例**

```TypeScript
function getBytesNumberPerRow(pixelMap: image.PixelMap) {
  let rowBytes: number = pixelMap.getBytesNumberPerRow();
}
```

## getColorSpace

```TypeScript
getColorSpace(): colorSpaceManager.ColorSpaceManager
```

Obtains the color space of this image.

**起始版本：** 10

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

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getColorSpace(pixelMap: image.PixelMap) {
  try {
    const csm = pixelMap.getColorSpace();
    console.info(`Succeeded in getting color space: ${csm.getColorSpaceName()}.`);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to get color space. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## getDensity

```TypeScript
getDensity(): number
```

Obtains the pixel density of this image. Unit: ppi (pixels/inch)

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Pixel density, in ppi. |

**示例**

```TypeScript
function getDensity(pixelMap: image.PixelMap) {
  let density: number = pixelMap.getDensity();
}
```

## getImageInfo

```TypeScript
getImageInfo(): Promise<ImageInfo>
```

Obtains the image information of a PixelMap. This API uses a promise to return the result.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ImageInfo](arkts-image-image-imageinfo-i.md)&gt; | Promise used to return the image information. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getImageInfo(pixelMap: image.PixelMap) {
  pixelMap.getImageInfo().then((imageInfo: image.ImageInfo) => {
    console.info(`Succeeded in obtaining information of the PixelMap with size ${imageInfo.size} and pixel format ${imageInfo.pixelFormat}.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to obtain information of the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## getImageInfo

```TypeScript
getImageInfo(callback: AsyncCallback<ImageInfo>): void
```

Obtains the image information. This API uses an asynchronous callback to return the result.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ImageInfo](arkts-image-image-imageinfo-i.md)&gt; | 是 | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the image information obtained; otherwise, **err** is an error object. |

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

## getImageInfoSync

```TypeScript
getImageInfoSync(): ImageInfo
```

Obtains the image information. This API returns the result synchronously.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageInfo](arkts-image-image-imageinfo-i.md) | Image information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getImageInfoSync(pixelMap: image.PixelMap) {
  try {
    let imageInfo: image.ImageInfo = pixelMap.getImageInfoSync();
    console.info(`Succeeded in obtaining information of the PixelMap with size ${imageInfo.size} and pixel format ${imageInfo.pixelFormat}.`);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to obtain information of the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## getMetadata

```TypeScript
getMetadata(key: HdrMetadataKey): HdrMetadataValue
```

Obtains the value of the metadata with a given key in this PixelMap.

**起始版本：** 12

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource unavailable. |
| [62980173](../errorcode-image.md#62980173-dma内存空间错误) | The DMA memory does not exist. |
| [62980302](../errorcode-image.md#62980302-内存拷贝失败) | Memory copy failed. Possibly caused by invalid metadata value. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getMetadata(context: Context) {
  // 此处'app.media.startIcon'需要替换为本地HDR图片。
  let img = context.resourceManager.getMediaContentSync($r('app.media.startIcon').id);
  let imageSource = image.createImageSource(img.buffer.slice(0));
  let decodingOptions: image.DecodingOptions = {
    desiredDynamicRange: image.DecodingDynamicRange.AUTO
  };
  let pixelMap = imageSource.createPixelMapSync(decodingOptions);
  if (pixelMap != undefined) {
    console.info('Succeeded in creating the PixelMap object.');
    try {
      let staticMetadata = pixelMap.getMetadata(image.HdrMetadataKey.HDR_STATIC_METADATA);
      console.info('Succeeded in getting the metadata.');
    } catch (e) {
      const err = e as BusinessError;
      console.error(`Failed to get the metadata. Code: ${err.code}, message: ${err.message}`);
    }
  } else {
    console.error('Failed to create the PixelMap.');
  }
}
```

## getPixelBytesNumber

```TypeScript
getPixelBytesNumber(): number
```

Obtains the total number of bytes of this image. Unit: bytes.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Total number of bytes. |

**示例**

```TypeScript
function getPixelBytesNumber(pixelMap: image.PixelMap) {
  let pixelBytesNumber: number = pixelMap.getPixelBytesNumber();
}
```

## getUniqueId

```TypeScript
getUniqueId(): number
```

Obtains the unique ID of this PixelMap.

**起始版本：** 22

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Unique ID. The value is a positive integer. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | The PixelMap has been released. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getUniqueId(pixelMap: image.PixelMap) {
  try {
    const uniqueId: number = pixelMap.getUniqueId();
    console.info(`Succeeded in getting the unique ID: ${uniqueId}.`);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to get the unique ID. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## isReleased

```TypeScript
isReleased(): boolean
```

Checks whether this PixelMap object is released. If released, any attempt to access the internal data of this object will fail.

> **NOTE：**
> 
> Release occurs when an ArkTS object relinquishes control over its associated native object. The memory occupied
> by the native object is reclaimed only after all managing ArkTS objects have relinquished their control.

**起始版本：** 22

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for whether the PixelMap object is released. **true** if released; **false** otherwise. |

**示例**

```TypeScript
async function isReleased(pixelMap: image.PixelMap) { // 未释放的PixelMap。
  pixelMap.isReleased(); // 返回false。
  await pixelMap.release();
  pixelMap.isReleased(); // 返回true。
}
```

## marshalling

```TypeScript
marshalling(sequence: rpc.MessageSequence): void
```

Marshals this PixelMap object and writes it to a MessageSequence object.

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sequence | rpc.MessageSequence | 是 | MessageSequence object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980097](../errorcode-image.md#62980097-pixelmap序列化传输失败) | IPC error. Possible cause: 1.IPC communication failed. 2. Image upload exception. 3. Decode process exception. 4. Insufficient memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

class MySequence implements rpc.Parcelable {
  picture: image.Picture | null = null;
  constructor(conPicture: image.Picture) {
    this.picture = conPicture;
  }
  marshalling(messageSequence: rpc.MessageSequence) {
    if(this.picture != null) {
      this.picture.marshalling(messageSequence);
      console.info('Succeeded in marshalling a picture.');
      return true;
    } else {
      console.error('Failed to marshall a picture.');
      return false;
    }
  }
  unmarshalling(messageSequence : rpc.MessageSequence) {
    this.picture = image.createPictureFromParcel(messageSequence);
    this.picture.getMainPixelmap().getImageInfo().then((imageInfo : image.ImageInfo) => {
      console.info(`Succeeded in unmarshalling a picture and getting main PixelMap information. Height: ${imageInfo.size.height}, width: ${imageInfo.size.width}.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to unmarshall a picture. Code: ${error.code}, message: ${error.message}.`);
    });
    return true;
  }
}

async function Marshalling_UnMarshalling(pictureObj : image.Picture) {
  if (pictureObj != null) {
    let parcelable: MySequence = new MySequence(pictureObj);
    let data: rpc.MessageSequence = rpc.MessageSequence.create();
    // 序列化。
    data.writeParcelable(parcelable);
    let ret: MySequence = new MySequence(pictureObj);
    // 反序列化。
    data.readParcelable(ret);
  } else {
    console.error('Picture object is null.');
  }
}
```

```TypeScript
// EntryAbility.ets
import { rpc } from '@kit.IPCKit';

class MySequence implements rpc.Parcelable {
  pixelMap: image.PixelMap;
  constructor(pixelMap: image.PixelMap) {
    this.pixelMap = pixelMap;
  }
  marshalling(messageSequence: rpc.MessageSequence) {
    this.pixelMap.marshalling(messageSequence);
    console.info('Marshalled the PixelMap.');
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence) {
    image.createPixelMap(new ArrayBuffer(96), {size: { height: 4, width: 6 }}).then((pixelParcel: image.PixelMap) => {
      pixelParcel.unmarshalling(messageSequence).then(async (pixelMap: image.PixelMap) => {
        this.pixelMap = pixelMap;
        pixelMap.getImageInfo().then((imageInfo: image.ImageInfo) => {
          console.info(`Unmarshalled information: height = ${imageInfo.size.height}, width = ${imageInfo.size.width}.`);
        });
      });
    });
    return true;
  }
}

async function marshal() {
  const color: ArrayBuffer = new ArrayBuffer(96);
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = 0x80;
  }
  let opts: image.InitializationOptions = {
    editable: true,
    pixelFormat: image.PixelMapFormat.BGRA_8888,
    size: { height: 4, width: 6 },
    alphaType: image.AlphaType.UNPREMUL
  };
  let pixelMap: image.PixelMap | undefined = await image.createPixelMap(color, opts);
  if (pixelMap != undefined) {
    // 序列化。
    let parcelable: MySequence = new MySequence(pixelMap);
    let data: rpc.MessageSequence = rpc.MessageSequence.create();
    data.writeParcelable(parcelable);

    // 反序列化rpc获取到data。
    let seq: MySequence = new MySequence(pixelMap);
    data.readParcelable(seq);
  }
}
```

## opacity

```TypeScript
opacity(rate: number, callback: AsyncCallback<void>): void
```

Sets an opacity rate for this image. This API uses an asynchronous callback to return the result. It is invalid for YUV images.Starting from API 26.0.0, it is recommended to use [setOpacity](#setopacity) instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | number | 是 | Opacity rate. The value range is (0,1]. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function opacity(pixelMap: image.PixelMap) {
  const rate: number = 0.5;
  pixelMap.opacity(rate, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to set opacity. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info("Succeeded in setting opacity.");
  });
}
```

## opacity

```TypeScript
opacity(rate: number): Promise<void>
```

Sets an opacity rate for this image. It is invalid for YUV images. This API uses a promise to return the result.Starting from API 26.0.0, it is recommended to use [setOpacity](#setopacity) instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | number | 是 | Opacity rate. The value range is (0,1]. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise that returns no value. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function opacity(pixelMap: image.PixelMap) {
  const rate: number = 0.5;
  pixelMap.opacity(rate).then(() => {
    console.info('Succeeded in setting opacity.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set opacity. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## opacitySync

```TypeScript
opacitySync(rate: number): void
```

Sets an opacity rate for this image. This API returns the result synchronously. It is invalid for YUV images.Starting from API 26.0.0, it is recommended to use [setOpacitySync](#setopacitysync) instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | number | 是 | Opacity rate. The value range is (0,1]. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function opacitySync(pixelMap: image.PixelMap) {
  const rate: number = 0.5;
  try {
    pixelMap.opacitySync(rate);
    console.info('Succeeded in setting opacity.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to set opacity. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## readAllPixelsToBuffer

```TypeScript
readAllPixelsToBuffer(dst: ArrayBuffer): Promise<void>
```

Reads all the pixel data from the PixelMap and writes the data to a buffer. The resulting data will be in the same pixel format as the PixelMap.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | ArrayBuffer | 是 | The buffer to receive the pixel data from the PixelMap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible cause: Size of the buffer is too small. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Failed to copy the memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readAllPixelsToBuffer(pixelMap: image.PixelMap) {
  const readBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());

  pixelMap.readAllPixelsToBuffer(readBuffer)
    .then(() => {
      console.info('Succeeded in reading pixel data from the PixelMap to readBuffer.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to read pixel data. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## readAllPixelsToBufferSync

```TypeScript
readAllPixelsToBufferSync(dst: ArrayBuffer): void
```

Reads all the pixel data from the PixelMap and writes the data to a buffer. The resulting data will be in the same pixel format as the PixelMap.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | ArrayBuffer | 是 | The buffer to receive the pixel data from the PixelMap. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible cause: Size of the buffer is too small. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Failed to copy the memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readAllPixelsToBufferSync(pixelMap: image.PixelMap) {
  const readBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());

  try {
    pixelMap.readAllPixelsToBufferSync(readBuffer);
    console.info('Succeeded in reading pixel data from the PixelMap to readBuffer.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to read pixel data. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## readPixels

```TypeScript
readPixels(area: PositionArea): Promise<void>
```

Reads the pixels in the area specified by [PositionArea](arkts-image-image-positionarea-i.md).region of this PixelMap object in the BGRA_8888 format and writes the data to the [PositionArea](arkts-image-image-positionarea-i.md).pixels buffer. This API uses a promise to return the result. You can use a formula to calculate the size of the memory to be applied for based on **PositionArea**. YUV region calculation formula: region to read (region.size{width * height}) * 1.5 (1 * Y component + 0.25 * U component + 0.25 * V component) RGBA region calculation formula: region to read (region.size{width * height}) * 4 (1 * R component + 1 * G component + 1 * B component + 1 * A component)Starting from API 26.0.0, it is recommended to use [readPixelsToArea](#readpixelstoarea) instead for better exception handling capabilities.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area from which the pixels will be read. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise that returns no value. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsRGBA(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8), // 8为需要创建的像素缓冲区大小，取值为：width * height * 4。
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  pixelMap.readPixels(area).then(() => {
    console.info('Succeeded in reading the image data in the area from the specified area.');
    console.info('BGRA data: ', new Uint8Array(area.pixels));
  }).catch((err: BusinessError) => {
    console.error(`Failed to read the image data from the specified area. Code: ${err.code}, message: ${err.message}`);
  });
}

function readPixelsYUV(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(6),  // 6为需要创建的像素缓冲区大小，取值为：width * height * 1.5。
    offset: 0,
    stride: 8,
    region: { size: { height: 2, width: 2 }, x: 0, y: 0 }
  };
  pixelMap.readPixels(area).then(() => {
    console.info('Succeeded in reading the image data in the area from the specified area.');
    console.info('YUV data: ', new Uint8Array(area.pixels));
  }).catch((err: BusinessError) => {
    console.error(`Failed to read the image data from the specified area. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## readPixels

```TypeScript
readPixels(area: PositionArea, callback: AsyncCallback<void>): void
```

Reads the pixels in the area specified by [PositionArea](arkts-image-image-positionarea-i.md).region of this PixelMap object in the BGRA_8888 format and writes the data to the [PositionArea](arkts-image-image-positionarea-i.md).pixels buffer. This API uses an asynchronous callback to return the result. You can use a formula to calculate the size of the memory to be applied for based on **PositionArea**. YUV region calculation formula: region to read (region.size{width * height}) * 1.5 (1 * Y component + 0.25 * U component + 0.25 * V component) RGBA region calculation formula: region to read (region.size{width * height}) * 4 (1 * R component + 1 * G component + 1 * B component + 1 * A component)Starting from API 26.0.0, it is recommended to use [readPixelsToArea](#readpixelstoarea) instead for better exception handling capabilities.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area from which the pixels will be read. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsRGBA(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8), // 8为需要创建的像素缓冲区大小，取值为：width * height * 4。
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  pixelMap.readPixels(area, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to read the image data from the specified area. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in reading the image data from the specified area.');
    console.info('BGRA data: ', new Uint8Array(area.pixels));
  });
}

function readPixelsYUV(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(6), // 6为需要创建的像素缓冲区大小，取值为：width * height * 1.5。
    offset: 0,
    stride: 8,
    region: { size: { height: 2, width: 2 }, x: 0, y: 0 }
  };
  pixelMap.readPixels(area, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to read the image data from the specified area. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in reading the image data from the specified area.');
    console.info('YUV data: ', new Uint8Array(area.pixels));
  });
}
```

## readPixelsSync

```TypeScript
readPixelsSync(area: PositionArea): void
```

Reads the pixels in the area specified by [PositionArea](arkts-image-image-positionarea-i.md).region of this PixelMap object in the BGRA_8888 format and writes the data to the [PositionArea](arkts-image-image-positionarea-i.md).pixels buffer. This API returns the result synchronously.Starting from API 26.0.0, it is recommended to use [readPixelsToAreaSync](#readpixelstoareasync) instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area from which the pixels will be read. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsSync(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8),
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  try {
    pixelMap.readPixelsSync(area);
    console.info('Succeeded in reading the image data from the specified area.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to read the image data from the specified area. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## readPixelsToArea

```TypeScript
readPixelsToArea(area: PositionArea): Promise<void>
```

Reads pixel data from a certain area of the PixelMap to a buffer. The resulting data will be in BGRA_8888 format.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area of the PixelMap to read the data. Data will be read from the PixelMap and copied into PositionArea.pixels. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible causes: 1. PositionArea.pixels is too small. 2. PositionArea.region is out of range. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Failed to copy the memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsToAreaRGBA(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(24), // 24为需要创建的像素缓冲区大小，取值为：width * height * 4。
    offset: 0,
    stride: 8, // 跨距，即每行像素所占的字节数，在没有行末填充字节的情况下取值为：width * 4。
    region: {
      size: { width: 2, height: 3 },
      x: 0,
      y: 0
    }
  };

  pixelMap.readPixelsToArea(area)
    .then(() => {
      console.info('Succeeded in reading pixel data from the specified area of the PixelMap to area.pixels.');
      console.info('BGRA data: ', new Uint8Array(area.pixels));
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to read pixel data. Code: ${err.code}, message: ${err.message}`);
    });
}

function readPixelsToAreaYUV(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(9), // 9为需要创建的像素缓冲区大小，取值为：width * height * 1.5。
    offset: 0,
    stride: 2, // 跨距，即每行像素所占的字节数，在没有行末填充字节的情况下取值为：width * 1（1倍Y分量）。
    region: {
      size: { width: 2, height: 3 },
      x: 0,
      y: 0
    }
  };

  pixelMap.readPixelsToArea(area)
    .then(() => {
      console.info('Succeeded in reading pixel data from the specified area of the PixelMap to area.pixels.');
      console.info('YUV data: ', new Uint8Array(area.pixels));
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to read pixel data. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## readPixelsToAreaSync

```TypeScript
readPixelsToAreaSync(area: PositionArea): void
```

Reads pixel data from a certain area of the PixelMap to a buffer. The resulting data will be in BGRA_8888 format.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area of the PixelMap to read the data. Data will be read from the PixelMap and copied into PositionArea.pixels. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible causes: 1. PositionArea.pixels is too small. 2. PositionArea.region is out of range. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Failed to copy the memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsToAreaSyncRGBA(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(24), // 24为需要创建的像素缓冲区大小，取值为：width * height * 4。
    offset: 0,
    stride: 8, // 跨距，即每行像素所占的字节数，在没有行末填充字节的情况下取值为：width * 4。
    region: {
      size: { width: 2, height: 3 },
      x: 0,
      y: 0
    }
  };

  try {
    pixelMap.readPixelsToAreaSync(area);
    console.info('Succeeded in reading pixel data from the specified area of the PixelMap to area.pixels.');
    console.info('BGRA data: ', new Uint8Array(area.pixels));
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to read pixel data. Code: ${err.code}, message: ${err.message}`);
  }
}

function readPixelsToAreaSyncYUV(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(9), // 9为需要创建的像素缓冲区大小，取值为：width * height * 1.5。
    offset: 0,
    stride: 2, // 跨距，即每行像素所占的字节数，在没有行末填充的字节情况下取值为：width * 1（1倍Y分量）。
    region: {
      size: { width: 2, height: 3 },
      x: 0,
      y: 0
    }
  };

  try {
    pixelMap.readPixelsToAreaSync(area);
    console.info('Succeeded in reading pixel data from the specified area of the PixelMap to area.pixels.');
    console.info('YUV data: ', new Uint8Array(area.pixels));
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to read pixel data. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## readPixelsToBuffer

```TypeScript
readPixelsToBuffer(dst: ArrayBuffer): Promise<void>
```

Reads the pixels of this PixelMap object based on the PixelMap's pixel format and writes the data to the buffer. This API uses a promise to return the result.Starting from API 26.0.0, it is recommended to use [readAllPixelsToBuffer](#readallpixelstobuffer) instead for better exception handling capabilities.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | ArrayBuffer | 是 | Buffer to which the pixels will be written. The buffer size is obtained by calling [getPixelBytesNumber](#getpixelbytesnumber). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise that returns no value. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsToBuffer(pixelMap: image.PixelMap) {
  const readBuffer: ArrayBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  pixelMap.readPixelsToBuffer(readBuffer).then(() => {
    console.info('Succeeded in reading image pixel data.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to read image pixel data. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## readPixelsToBuffer

```TypeScript
readPixelsToBuffer(dst: ArrayBuffer, callback: AsyncCallback<void>): void
```

Reads the pixels of this PixelMap object based on the PixelMap's pixel format and writes the data to the buffer. This API uses an asynchronous callback to return the result.Starting from API 26.0.0, it is recommended to use [readAllPixelsToBuffer](#readallpixelstobuffer) instead for better exception handling capabilities.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | ArrayBuffer | 是 | Buffer to which the pixels will be written. The buffer size is obtained by calling [getPixelBytesNumber](#getpixelbytesnumber). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsToBuffer(pixelMap: image.PixelMap) {
  const readBuffer: ArrayBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  pixelMap.readPixelsToBuffer(readBuffer, (err: BusinessError, res: void) => {
    if (err) {
      console.error(`Failed to read image pixel data. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in reading image pixel data.');
  });
}
```

## readPixelsToBufferSync

```TypeScript
readPixelsToBufferSync(dst: ArrayBuffer): void
```

Reads the pixels of this PixelMap object based on the PixelMap's pixel format and writes the data to the buffer. This API returns the result synchronously.Starting from API 26.0.0, it is recommended to use [readAllPixelsToBufferSync](#readallpixelstobuffersync) instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | ArrayBuffer | 是 | Buffer to which the pixels will be written. The buffer size is obtained by calling [getPixelBytesNumber](#getpixelbytesnumber). |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsToBufferSync(pixelMap: image.PixelMap) {
  const readBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  try {
    pixelMap.readPixelsToBufferSync(readBuffer);
    console.info('Succeeded in reading image pixel data.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to read image pixel data. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases this PixelMap instance. After the release, any attempt to access the internal data of this object will fail. This API uses an asynchronous callback to return the result. Images occupy a large amount of memory. When you finish using a PixelMap instance, call this API to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

> **NOTE：**
> 
> Release occurs when an ArkTS object relinquishes control over its associated native object. The memory occupied
> by the native object is reclaimed only after all managing ArkTS objects have relinquished their control.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

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

Releases this PixelMap instance. After the release, any attempt to access the internal data of this object will fail. This API uses a promise to return the result. Images occupy a large amount of memory. When you finish using a PixelMap instance, call this API to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

> **NOTE：**
> 
> Release occurs when an ArkTS object relinquishes control over its associated native object. The memory occupied
> by the native object is reclaimed only after all managing ArkTS objects have relinquished their control.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise that returns no value. |

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

## rotate

```TypeScript
rotate(angle: number, callback: AsyncCallback<void>): void
```

Rotates this image based on a given angle. This API uses an asynchronous callback to return the result.Starting from API 26.0.0, it is recommended to use [applyRotate](#applyrotate) instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | Angle to rotate. Unit: degrees. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function rotate(pixelMap: image.PixelMap) {
  const angle: number = 90.0;
  pixelMap.rotate(angle, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to rotate the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info("Succeeded in rotating the PixelMap.");
  });
}
```

## rotate

```TypeScript
rotate(angle: number): Promise<void>
```

Rotates a PixelMap based on a given angle. This API uses a promise to return the result.Starting from API 26.0.0, it is recommended to use [applyRotate](#applyrotate) instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | Angle to rotate. Unit: degrees. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise that returns no value. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function rotate(pixelMap: image.PixelMap) {
  const angle: number = 90.0;
  pixelMap.rotate(angle).then(() => {
    console.info('Succeeded in rotating the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to rotate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## rotateSync

```TypeScript
rotateSync(angle: number): void
```

Rotates this image based on a given angle. This API returns the result synchronously.Starting from API 26.0.0, it is recommended to use [applyRotateSync](#applyrotatesync) instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | Angle to rotate. Unit: degrees. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function rotateSync(pixelMap: image.PixelMap) {
  const angle: number = 90.0;
  try {
    pixelMap.rotateSync(angle);
    console.info('Succeeded in rotating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to rotate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## scale

```TypeScript
scale(x: number, y: number, callback: AsyncCallback<void>): void
```

Scales this image based on the scale factors of the width and height. This API uses an asynchronous callback to return the result.Starting from API 26.0.0, it is recommended to use [applyScale](#applyscale) instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | Scale factor of the width. |
| y | number | 是 | Scale factor of the height. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function scale(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  pixelMap.scale(scaleX, scaleY, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info("Succeeded in scaling the PixelMap.");
  });
}
```

## scale

```TypeScript
scale(x: number, y: number): Promise<void>
```

Scales this image based on the scale factors of the width and height. This API uses a promise to return the result.Starting from API 26.0.0, it is recommended to use [applyScale](#applyscale) instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | Scale factor of the width. |
| y | number | 是 | Scale factor of the height. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise that returns no value. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function scale(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  pixelMap.scale(scaleX, scaleY).then(() => {
    console.info('Succeeded in scaling the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## scale

```TypeScript
scale(x: number, y: number, level: AntiAliasingLevel): Promise<void>
```

Scales this image based on the specified anti-aliasing level and the scale factors for the width and height. This API uses a promise to return the result.Starting from API 26.0.0, it is recommended to use [applyScale](#applyscale) instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

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
| Promise & lt;void & gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function scaleSync(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  pixelMap.scale(scaleX, scaleY, image.AntiAliasingLevel.LOW).then(() => {
    console.info('Succeeded in scaling the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## scaleSync

```TypeScript
scaleSync(x: number, y: number): void
```

Scales this image based on the scale factors of the width and height. This API returns the result synchronously.Starting from API 26.0.0, it is recommended to use [applyScaleSync](#applyscalesync) instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | Scale factor of the width. |
| y | number | 是 | Scale factor of the height. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function scaleSync(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  try {
    pixelMap.scaleSync(scaleX, scaleY);
    console.info('Succeeded in scaling the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## scaleSync

```TypeScript
scaleSync(x: number, y: number, level: AntiAliasingLevel): void
```

Scales this image based on the specified anti-aliasing level and the scale factors for the width and height. This API returns the result synchronously.Starting from API 26.0.0, it is recommended to use [applyScaleSync](#applyscalesync) instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function scaleSync(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  try {
    pixelMap.scaleSync(scaleX, scaleY, image.AntiAliasingLevel.LOW);
    console.info('Succeeded in scaling the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## setColorSpace

```TypeScript
setColorSpace(colorSpace: colorSpaceManager.ColorSpaceManager): void
```

Set color space of pixel map.This method is only used to set the colorspace property of pixelmap, while all pixel data remains the same after calling this method. If you want to change colorspace for all pixels, use method {@Link #applyColorSpace(colorSpaceManager.ColorSpaceManager)} or {@Link #applyColorSpace(colorSpaceManager.ColorSpaceManager, AsyncCallback&lt;void&gt;)}.

**起始版本：** 12

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

**示例**

```TypeScript
import { colorSpaceManager } from '@kit.ArkGraphics2D';
import { BusinessError } from '@kit.BasicServicesKit';

function setColorSpace(pixelMap: image.PixelMap) {
  const colorSpaceName = colorSpaceManager.ColorSpace.SRGB;
  const csm: colorSpaceManager.ColorSpaceManager = colorSpaceManager.create(colorSpaceName);
  try {
    pixelMap.setColorSpace(csm);
    console.info('Succeeded in setting color space.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to set color space. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## setMemoryNameSync

```TypeScript
setMemoryNameSync(name: string): void
```

Sets a memory name for this PixelMap.

**起始版本：** 13

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | Memory name, which can be set only for a PixelMap with the DMA or ASHMEM memory format. The name length for DMA memory settings should be within the range of 1 to 255 bytes. For ASHMEM memory settings, the name length should be within the range of 1 to 244 bytes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.The length of the input parameter is too number. 2.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource unavailable. |
| [62980286](../errorcode-image.md#62980286-pixelmap设置内存标识符失败) | Memory format not supported. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setMemoryNameSync(pixelMap: image.PixelMap) {
  try {
    pixelMap.setMemoryNameSync("PixelMapName Test");
    console.info('Succeeded in setting memory name.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to set memory name. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## setMetadata

```TypeScript
setMetadata(key: HdrMetadataKey, value: HdrMetadataValue): Promise<void>
```

Sets the value for the metadata with a given key in this PixelMap. This API uses a promise to return the result.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md) | 是 | Key of the HDR metadata. |
| value | [HdrMetadataValue](arkts-image-image-hdrmetadatavalue-t.md) | 是 | Value of the metadata. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource unavailable. |
| [62980173](../errorcode-image.md#62980173-dma内存空间错误) | The DMA memory does not exist. |
| [62980302](../errorcode-image.md#62980302-内存拷贝失败) | Memory copy failed. Possibly caused by invalid metadata value. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setMetadata(pixelMap: image.PixelMap) { // 入参pixelMap内存类型需为DMA_ALLOC内存类型，其创建方法请参考上方说明。
  let staticMetadata: image.HdrStaticMetadata = {
    displayPrimariesX: [1.1, 1.1, 1.1],
    displayPrimariesY: [1.2, 1.2, 1.2],
    whitePointX: 1.1,
    whitePointY: 1.2,
    maxLuminance: 2.1,
    minLuminance: 1.0,
    maxContentLightLevel: 2.1,
    maxFrameAverageLightLevel: 2.1,
  };
  pixelMap.setMetadata(image.HdrMetadataKey.HDR_STATIC_METADATA, staticMetadata).then(() => {
    console.info('Succeeded in setting the metadata.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the metadata. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## setOpacity

```TypeScript
setOpacity(value: number): Promise<void>
```

Sets opacity of the PixelMap. Every pixel will be set to the same opacity value.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | The target opacity value to be set. Unit: Percentage, Value range: (0,1]. The valid range is (0.0, 1.0] where 1.0 is fully opaque and becoming transparent as it approaches 0.0. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible cause: The specified value is out of range. |
| [7600207](../errorcode-image.md#7600207-不支持的数据格式) | Unsupported data format. Possible cause: Alpha type is not supported. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setOpacity(pixelMap: image.PixelMap) {
  const opacity: number = 0.5;
  pixelMap.setOpacity(opacity)
    .then(() => {
      console.info('Succeeded in setting opacity.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to set opacity. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## setOpacitySync

```TypeScript
setOpacitySync(value: number): void
```

Sets opacity of the PixelMap. Every pixel will be set to the same opacity value.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | The target opacity value to be set. Unit: Percentage, Value range: (0,1]. The valid range is (0.0, 1.0] where 1.0 is fully opaque and becoming transparent as it approaches 0.0. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible cause: The specified value is out of range. |
| [7600207](../errorcode-image.md#7600207-不支持的数据格式) | Unsupported data format. Possible cause: Alpha type is not supported. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setOpacitySync(pixelMap: image.PixelMap) {
  const opacity: number = 0.5;
  try {
    pixelMap.setOpacitySync(opacity);
    console.info('Succeeded in setting opacity.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to set opacity. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## setTransferDetached

```TypeScript
setTransferDetached(detached: boolean): void
```

Sets whether to detach from the original thread when this PixelMap is transmitted across threads. This API applies to the scenario where the PixelMap needs to be released immediately.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| detached | boolean | 是 | Whether to detach from the original thread. **true** to detach, **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
// EntryAbility.ets
import { common } from '@kit.AbilityKit';
import { taskpool } from '@kit.ArkTS';

@Concurrent
// 子线程方法。
async function loadPixelMap(rawFileDescriptor: number): Promise<image.PixelMap> {
  // 创建ImageSource。
  const imageSource = image.createImageSource(rawFileDescriptor);
  // 创建PixelMap。
  const pixelMap = imageSource.createPixelMapSync();
  // 释放ImageSource。
  imageSource.release();
  // 使PixelMap在跨线程传输完成后，断开原线程的引用。
  pixelMap.setTransferDetached(true);
  // 返回PixelMap给主线程。
  return pixelMap;
}

@Entry
@Component
struct Demo {
  @State pixelMap: image.PixelMap | undefined = undefined;
  // 主线程方法。
  private loadImageFromThread(): void {
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    const resourceMgr = context.resourceManager;
    // 此处'example.jpg'仅作示例，请开发者自行替换，否则创建失败会导致后续无法正常执行。
    resourceMgr.getRawFd('example.jpg').then(rawFileDescriptor => {
      taskpool.execute(loadPixelMap, rawFileDescriptor).then(pixelMap => {
        if (pixelMap) {
          this.pixelMap = pixelMap as image.PixelMap;
          console.info('Succeeded in creating the PixelMap.');
          // 主线程释放PixelMap。由于子线程返回PixelMap前已调用setTransferDetached(true)，所以此处能够立即释放PixelMap，不需要等待子线程被销毁。
          this.pixelMap.release();
        } else {
          console.error('Failed to create the PixelMap.');
        }
      });
    });
  }
  build() {
    // ...
  }
}
```

## toSdr

```TypeScript
toSdr(): Promise<void>
```

Convert pixelmap to standard dynamic range.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980137](../errorcode-image.md#62980137-图片操作无效) | Invalid image operation. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function toSdr(context: Context) {
  // 此处'app.media.startIcon'需要替换为本地HDR图片。
  let img = context.resourceManager.getMediaContentSync($r('app.media.startIcon').id);
  let imageSource = image.createImageSource(img.buffer.slice(0));
  let decodingOptions: image.DecodingOptions = {
    desiredDynamicRange: image.DecodingDynamicRange.AUTO
  };
  let pixelmap = imageSource.createPixelMapSync(decodingOptions);
  if (pixelmap != undefined) {
    console.info('Succeeded in creating the PixelMap object.');
    pixelmap.toSdr().then(() => {
      let imageInfo = pixelmap.getImageInfoSync();
      console.info("Succeeded in converting to SDR. imageInfo.isHdr: " + imageInfo.isHdr);
    }).catch((err: BusinessError) => {
      console.error(`Failed to convert to SDR. Code: ${err.code}, message: ${err.message}`);
    });
  } else {
    console.error('Failed to create the PixelMap.');
  }
}
```

## translate

```TypeScript
translate(x: number, y: number, callback: AsyncCallback<void>): void
```

Translates this image based on given coordinates. This API uses an asynchronous callback to return the result. The size of the translated image is changed to width+X and height+Y. It is recommended that the new width and height not exceed the width and height of the screen.Starting from API 26.0.0, it is recommended to use [applyTranslate](#applytranslate) instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | X coordinate to translate, in px. |
| y | number | 是 | Y coordinate to translate, in px. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function translate(pixelMap: image.PixelMap) {
  const translateX: number = 50.0;
  const translateY: number = 10.0;
  pixelMap.translate(translateX, translateY, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to translate the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info("Succeeded in translating the PixelMap.");
  });
}
```

## translate

```TypeScript
translate(x: number, y: number): Promise<void>
```

Translates a PixelMap based on given coordinates. This API uses a promise to return the result. The size of the translated image is changed to width+X and height+Y. It is recommended that the new width and height not exceed the width and height of the screen.Starting from API 26.0.0, it is recommended to use [applyTranslate](#applytranslate) instead for better exception handling capabilities.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | X coordinate to translate, in px. |
| y | number | 是 | Y coordinate to translate, in px. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise that returns no value. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function translate(pixelMap: image.PixelMap) {
  const translateX: number = 50.0;
  const translateY: number = 10.0;
  pixelMap.translate(translateX, translateY).then(() => {
    console.info('Succeeded in translating the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to translate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## translateSync

```TypeScript
translateSync(x: number, y: number): void
```

Translates this image based on given coordinates. This API returns the result synchronously. The size of the translated image is changed to width+X and height+Y. It is recommended that the new width and height not exceed the width and height of the screen.Starting from API 26.0.0, it is recommended to use [applyTranslateSync](#applytranslatesync) instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | X coordinate to translate, in px. |
| y | number | 是 | Y coordinate to translate, in px. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function translateSync(pixelMap: image.PixelMap) {
  const translateX: number = 50.0;
  const translateY: number = 10.0;
  try {
    pixelMap.translateSync(translateX, translateY);
    console.info('Succeeded in translating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to translate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## unmarshalling

```TypeScript
unmarshalling(sequence: rpc.MessageSequence): Promise<PixelMap>
```

Unmarshals a MessageSequence object to obtain a PixelMap object. To create a PixelMap object in synchronous mode, use [createPixelMapFromParcel](arkts-image-image-createpixelmapfromparcel-f.md).

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sequence | rpc.MessageSequence | 是 | MessageSequence object that stores the PixelMap information. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;PixelMap & gt; | Promise used to return the PixelMap object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980097](../errorcode-image.md#62980097-pixelmap序列化传输失败) | IPC error. Possible cause: 1.IPC communication failed. 2. Image upload exception. 3. Decode process exception. 4. Insufficient memory. |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |

**示例**

```TypeScript
// EntryAbility.ets
import { rpc } from '@kit.IPCKit';

class MySequence implements rpc.Parcelable {
  pixelMap: image.PixelMap;
  constructor(pixelMap: image.PixelMap) {
    this.pixelMap = pixelMap;
  }
  marshalling(messageSequence: rpc.MessageSequence) {
    this.pixelMap.marshalling(messageSequence);
    console.info('Marshalled the PixelMap.');
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence) {
    image.createPixelMap(new ArrayBuffer(96), {size: { height: 4, width: 6 }}).then((pixelParcel: image.PixelMap) => {
      pixelParcel.unmarshalling(messageSequence).then(async (pixelMap: image.PixelMap) => {
        this.pixelMap = pixelMap;
        pixelMap.getImageInfo().then((imageInfo: image.ImageInfo) => {
          console.info(`Unmarshalled information: height = ${imageInfo.size.height}, width = ${imageInfo.size.width}.`);
        });
      });
    });
    return true;
  }
}

async function unmarshal() {
  const color: ArrayBuffer = new ArrayBuffer(96);
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = 0x80;
  }
  let opts: image.InitializationOptions = {
    editable: true,
    pixelFormat: image.PixelMapFormat.BGRA_8888,
    size: { height: 4, width: 6 },
    alphaType: image.AlphaType.UNPREMUL
  };
  let pixelMap: image.PixelMap | undefined = await image.createPixelMap(color, opts);
  if (pixelMap != undefined) {
    // 序列化。
    let parcelable: MySequence = new MySequence(pixelMap);
    let data: rpc.MessageSequence = rpc.MessageSequence.create();
    data.writeParcelable(parcelable);

    // 反序列化rpc获取到data。
    let seq: MySequence = new MySequence(pixelMap);
    data.readParcelable(seq);
  }
}
```

## writeAllPixelsFromBuffer

```TypeScript
writeAllPixelsFromBuffer(src: ArrayBuffer): Promise<void>
```

Reads the pixel data from a buffer and writes the data to the PixelMap. The source data must be in the same pixel format as the PixelMap.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | ArrayBuffer | 是 | The buffer that contains pixel data to be written to the PixelMap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is not editable or is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible cause: Size of the buffer is too small. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Failed to copy the memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writeAllPixelsFromBuffer(pixelMap: image.PixelMap) {
  const writeBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  const bufferArr = new Uint8Array(writeBuffer);
  for (let i = 0; i < bufferArr.length; i += 4) {
    // 假设pixelMap的像素格式为RGBA_8888，则下列数组索引依次为：R通道、G通道、B通道、A通道。
    bufferArr[i] = 0xFF;
    bufferArr[i + 1] = 0x00;
    bufferArr[i + 2] = 0x00;
    bufferArr[i + 3] = 0xFF;
  }

  pixelMap.writeAllPixelsFromBuffer(writeBuffer)
    .then(() => {
      console.info('Succeeded in writing pixel data from writeBuffer to the PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to write pixel data. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## writeAllPixelsFromBufferSync

```TypeScript
writeAllPixelsFromBufferSync(src: ArrayBuffer): void
```

Reads the pixel data from a buffer and writes the data to the PixelMap. The source data must be in the same pixel format as the PixelMap.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | ArrayBuffer | 是 | The buffer that contains pixel data to be written to the PixelMap. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is not editable or is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible cause: Size of the buffer is too small. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Failed to copy the memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writeAllPixelsFromBufferSync(pixelMap: image.PixelMap) {
  const writeBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  const bufferArr = new Uint8Array(writeBuffer);
  for (let i = 0; i < bufferArr.length; i += 4) {
    // 假设pixelMap的像素格式为RGBA_8888，则下列数组索引依次为：R通道、G通道、B通道、A通道。
    bufferArr[i] = 0xFF;
    bufferArr[i + 1] = 0x00;
    bufferArr[i + 2] = 0x00;
    bufferArr[i + 3] = 0xFF;
  }

  try {
    pixelMap.writeAllPixelsFromBufferSync(writeBuffer);
    console.info('Succeeded in writing pixel data from writeBuffer to the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to write pixel data. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## writeBufferToPixels

```TypeScript
writeBufferToPixels(src: ArrayBuffer): Promise<void>
```

Reads the pixels in the buffer based on the PixelMap's pixel format and writes the data to this PixelMap object. This API uses a promise to return the result.Starting from API 26.0.0, it is recommended to use [writeAllPixelsFromBuffer](#writeallpixelsfrombuffer) instead for better exception handling capabilities.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | ArrayBuffer | 是 | Buffer from which the pixels are read. The buffer size is obtained by calling [getPixelBytesNumber](#getpixelbytesnumber). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise that returns no value. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writeBufferToPixels(pixelMap: image.PixelMap) {
  const color: ArrayBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writeBufferToPixels(color).then(() => {
    console.info('Succeeded in writing data from the buffer to the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to write data from the buffer to the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## writeBufferToPixels

```TypeScript
writeBufferToPixels(src: ArrayBuffer, callback: AsyncCallback<void>): void
```

Reads the pixels in the buffer based on the PixelMap's pixel format and writes the data to this PixelMap object. This API uses an asynchronous callback to return the result.Starting from API 26.0.0, it is recommended to use [writeAllPixelsFromBuffer](#writeallpixelsfrombuffer) instead for better exception handling capabilities.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | ArrayBuffer | 是 | Buffer from which the pixels are read. The buffer size is obtained by calling [getPixelBytesNumber](#getpixelbytesnumber). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. If the pixels in the buffer are successfully written to the PixelMap, **err** is **undefined**; otherwise, **err** is an error object. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writeBufferToPixels(pixelMap: image.PixelMap) {
  const color: ArrayBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writeBufferToPixels(color, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to write data from the buffer to the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in writing data from the buffer to the PixelMap.');
  });
}
```

## writeBufferToPixelsSync

```TypeScript
writeBufferToPixelsSync(src: ArrayBuffer): void
```

Reads the pixels in the buffer based on the PixelMap's pixel format and writes the data to this PixelMap object. This API returns the result synchronously.Starting from API 26.0.0, it is recommended to use [writeAllPixelsFromBufferSync](#writeallpixelsfrombuffersync) instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | ArrayBuffer | 是 | Buffer from which the pixels are read. The buffer size is obtained by calling [getPixelBytesNumber](#getpixelbytesnumber). |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writeBufferToPixelsSync(pixelMap: image.PixelMap) {
  const color: ArrayBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  try {
    pixelMap.writeBufferToPixelsSync(color);
    console.info('Succeeded in writing data from the buffer to the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to write data from the buffer to the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## writePixels

```TypeScript
writePixels(area: PositionArea): Promise<void>
```

Reads the pixels in the [PositionArea](arkts-image-image-positionarea-i.md).region buffer in the BGRA_8888 format and writes the data to the area specified by [PositionArea](arkts-image-image-positionarea-i.md).pixels in this PixelMap object. This API uses a promise to return the result. You can use a formula to calculate the size of the memory to be applied for based on **PositionArea**. YUV region calculation formula: region to read (region.size{width * height}) * 1.5 (1 * Y component + 0.25 * U component + 0.25 * V component) RGBA region calculation formula: region to read (region.size{width * height}) * 4 (1 * R component + 1 * G component + 1 * B component + 1 * A component)Starting from API 26.0.0, it is recommended to use [writePixelsFromArea](#writepixelsfromarea) instead for better exception handling capabilities.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area to which the pixels will be written. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise that returns no value. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writePixelsRGBA(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8), // 8为需要创建的像素缓冲区大小，取值为：width * height * 4。
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  let bufferArr: Uint8Array = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writePixels(area).then(() => {
    console.info('Succeeded in writing pixels into the specified area.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to write pixels into the specified area. Code: ${err.code}, message: ${err.message}`);
  });
}

function writePixelsYUV(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(6), // 6为需要创建的像素缓冲区大小，取值为：width * height * 1.5。
    offset: 0,
    stride: 8, // PixelMap为YUV格式时，writePixels函数不使用该变量。
    region: { size: { height: 2, width: 2 }, x: 0, y: 0 }
  };
  let bufferArr: Uint8Array = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writePixels(area).then(() => {
    console.info('Succeeded in writing pixels into the specified area.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to write pixels into the specified area. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## writePixels

```TypeScript
writePixels(area: PositionArea, callback: AsyncCallback<void>): void
```

Reads the pixels in the [PositionArea](arkts-image-image-positionarea-i.md).region buffer in the BGRA_8888 format and writes the data to the area specified by [PositionArea](arkts-image-image-positionarea-i.md).pixels in this PixelMap object. This API uses an asynchronous callback to return the result. You can use a formula to calculate the size of the memory to be applied for based on **PositionArea**. YUV region calculation formula: region to read (region.size{width * height}) * 1.5 (1 * Y component + 0.25 * U component + 0.25 * V component) RGBA region calculation formula: region to read (region.size{width * height}) * 4 (1 * R component + 1 * G component + 1 * B component + 1 * A component)Starting from API 26.0.0, it is recommended to use [writePixelsFromArea](#writepixelsfromarea) instead for better exception handling capabilities.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area to which the pixels will be written. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writePixelsRGBA(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8), // 8为需要创建的像素缓冲区大小，取值为：width * height * 4。
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  let bufferArr: Uint8Array = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writePixels(area, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to write pixels into the specified area. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in writing pixels into the specified area.');
  });
}

function writePixelsYUV(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(6), // 6为需要创建的像素缓冲区大小，取值为：width * height * 1.5。
    offset: 0,
    stride: 8, // PixelMap为YUV格式时，writePixels函数不使用该变量。
    region: { size: { height: 2, width: 2 }, x: 0, y: 0 }
  };
  let bufferArr: Uint8Array = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writePixels(area, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to write pixels into the specified area. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in writing pixels into the specified area.');
  });
}
```

## writePixelsFromArea

```TypeScript
writePixelsFromArea(area: PositionArea): Promise<void>
```

Writes data from a buffer to a certain area of the PixelMap. The source data must be in BGRA_8888 format.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area of the PixelMap to write the data. Data will be copied from PositionArea.pixels to the PixelMap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | A Promise that resolves when the operation completes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is not editable or is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible causes: 1. PositionArea.pixels is too small. 2. PositionArea.region is out of range. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Failed to copy the memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writePixelsFromAreaRGBA(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(24), // 24为需要创建的像素缓冲区大小，取值为：width * height * 4。
    offset: 0,
    stride: 8, // 跨距，即每行像素所占的字节数，在没有行末填充字节的情况下取值为：width * 4。
    region: {
      size: { width: 2, height: 3 },
      x: 0,
      y: 0
    }
  };
  const bufferArr = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i += 4) {
    // 数据源的格式必须是BGRA_8888，下列数组索引依次为：B通道、G通道、R通道、A通道。
    bufferArr[i] = 0xFF;
    bufferArr[i + 1] = 0x00;
    bufferArr[i + 2] = 0x00;
    bufferArr[i + 3] = 0xFF;
  }

  pixelMap.writePixelsFromArea(area)
    .then(() => {
      console.info('Succeeded in writing pixel data from area.pixels to the specified area of the PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to write pixel data. Code: ${err.code}, message: ${err.message}`);
    });
}

function writePixelsFromAreaYUV(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(9), // 9为需要创建的像素缓冲区大小，取值为：width * height * 1.5。
    offset: 0,
    stride: 2, // PixelMap为YUV格式时，writePixelsFromArea函数不使用该变量。
    region: {
      size: { width: 2, height: 3 },
      x: 0,
      y: 0
    }
  };
  const bufferArr = new Uint8Array(area.pixels);
  const ySize = area.region.size.width * area.region.size.height;
  for (let i = 0; i < ySize; i++) { // Y平面。
    bufferArr[i] = 0xFF;
  }
  for (let i = ySize; i < bufferArr.length; i++) { // UV交错平面。
    bufferArr[i] = 0x80;
  }

  pixelMap.writePixelsFromArea(area)
    .then(() => {
      console.info('Succeeded in writing pixel data from area.pixels to the specified area of the PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to write pixel data. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## writePixelsFromAreaSync

```TypeScript
writePixelsFromAreaSync(area: PositionArea): void
```

Writes data from a buffer to a certain area of the PixelMap. The source data must be in BGRA_8888 format.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area of the PixelMap to write the data. Data will be copied from PositionArea.pixels to the PixelMap. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap已被释放) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap已被传递至另一个线程) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation because the PixelMap is not editable or is locked. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible causes: 1. PositionArea.pixels is too small. 2. PositionArea.region is out of range. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Failed to copy the memory. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writePixelsFromAreaSyncRGBA(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(24), // 24为需要创建的像素缓冲区大小，取值为：width * height * 4。
    offset: 0,
    stride: 8, // 跨距，即每行像素所占的字节数，在没有行末填充字节的情况下取值为：width * 4。
    region: {
      size: { width: 2, height: 3 },
      x: 0,
      y: 0
    }
  };
  const bufferArr = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i += 4) {
    // 数据源的格式必须是BGRA_8888，下列数组索引依次为：B通道、G通道、R通道、A通道。
    bufferArr[i] = 0xFF;
    bufferArr[i + 1] = 0x00;
    bufferArr[i + 2] = 0x00;
    bufferArr[i + 3] = 0xFF;
  }

  try {
    pixelMap.writePixelsFromAreaSync(area);
    console.info('Succeeded in writing pixel data from area.pixels to the specified area of the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to write pixel data. Code: ${err.code}, message: ${err.message}`);
  }
}

function writePixelsFromAreaSyncYUV(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(9), // 9为需要创建的像素缓冲区大小，取值为：width * height * 1.5。
    offset: 0,
    stride: 2, // PixelMap为YUV格式时，writePixelsFromAreaSync函数不使用该变量。
    region: {
      size: { width: 2, height: 3 },
      x: 0,
      y: 0
    }
  };
  const bufferArr = new Uint8Array(area.pixels);
  const ySize = area.region.size.width * area.region.size.height;
  for (let i = 0; i < ySize; i++) { // Y平面。
    bufferArr[i] = 0xFF;
  }
  for (let i = ySize; i < bufferArr.length; i++) { // UV交错平面。
    bufferArr[i] = 0x80;
  }

  try {
    pixelMap.writePixelsFromAreaSync(area);
    console.info('Succeeded in writing pixel data from area.pixels to the specified area of the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to write pixel data. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## writePixelsSync

```TypeScript
writePixelsSync(area: PositionArea): void
```

Reads the pixels in the [PositionArea](arkts-image-image-positionarea-i.md).region buffer in the BGRA_8888 format and writes the data to the area specified by [PositionArea](arkts-image-image-positionarea-i.md).pixels in this PixelMap object. This API returns the result synchronously.Starting from API 26.0.0, it is recommended to use [writePixelsFromAreaSync](#writepixelsfromareasync) instead for better exception handling capabilities.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | 是 | Area to which the pixels will be written. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writePixelsSync(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8),
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  let bufferArr: Uint8Array = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  try {
    pixelMap.writePixelsSync(area);
    console.info('Succeeded in writing pixels into the specified area.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to write pixels into the specified area. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## isEditable

```TypeScript
readonly isEditable: boolean
```

Whether the image pixels are editable. **true** if editable, **false** otherwise. The value **false** provides better image rendering and transmission performance.This API can be used in atomic services since API version 11.This API can be used in ArkTS widgets since API version 12.

**类型：** boolean

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## isStrideAlignment

```TypeScript
readonly isStrideAlignment: boolean
```

Whether the row data of the image is memory aligned. The value **true** means that the row data is memory-aligned, and there may be blank bytes padded at the end of each row to meet alignment requirements. The value **false** means that the row data is not memory-aligned, and rows are packed contiguously with no padding bytes at the end.

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.Core
