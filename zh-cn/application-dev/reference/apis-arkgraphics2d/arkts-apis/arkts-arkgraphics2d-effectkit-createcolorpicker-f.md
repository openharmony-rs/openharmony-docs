# createColorPicker

## 导入模块

```TypeScript
import { effectKit } from '@kit.ArkGraphics2D';
```

## createColorPicker

```TypeScript
function createColorPicker(source: image.PixelMap): Promise<ColorPicker>
```

通过传入的PixelMap创建ColorPicker实例，使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-effectKit-function createColorPicker(source: image.PixelMap): Promise<ColorPicker>--><!--Device-effectKit-function createColorPicker(source: image.PixelMap): Promise<ColorPicker>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | image.PixelMap | 是 | image模块创建的PixelMap实例。 可通过图片解码或直接创建获得，具体可见[Image Kit简介](../../../media/image/image-overview.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ColorPicker&gt; | - Promise对象。返回创建的ColorPicker实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 输入参数错误。 |

**示例：**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建用于图像效果的buffer
const colorBuffer = new ArrayBuffer(96);
// 设置图像初始化选项
let opts : image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};

// 创建PixelMap实例
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  // 创建ColorPicker实例
  effectKit.createColorPicker(pixelMap).then(colorPicker => {
    console.info('Succeeded in creating colorPicker.');
  }).catch((err : BusinessError) => {
    console.error(`Failed to create colorPicker. Code: ${err.code}, message: ${err.message}`);
  });
});

```


## createColorPicker

```TypeScript
function createColorPicker(source: image.PixelMap, region: Array<number>): Promise<ColorPicker>
```

通过传入的PixelMap创建选定取色区域的ColorPicker实例，使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-effectKit-function createColorPicker(source: image.PixelMap, region: Array<double>): Promise<ColorPicker>--><!--Device-effectKit-function createColorPicker(source: image.PixelMap, region: Array<double>): Promise<ColorPicker>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | image.PixelMap | 是 | image模块创建的PixelMap实例。 可通过图片解码或直接创建获得，具体可见[Image Kit简介](../../../media/image/image-overview.md)。 |
| region | Array&lt;number&gt; | 是 | 指定图片的取色区域。 数组第三个元素需大于第一个元素，第四个元素需大于第二个元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ColorPicker&gt; | - Promise对象。返回创建的ColorPicker实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 输入参数错误。 |

**示例：**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建用于图像效果的buffer
const colorBuffer = new ArrayBuffer(96);
// 设置图像初始化选项
let opts : image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};

// 创建PixelMap实例
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  // 创建指定取色区域的ColorPicker实例
  effectKit.createColorPicker(pixelMap, [0, 0, 1, 1]).then(colorPicker => {
    console.info('Succeeded in creating colorPicker.');
  }).catch((err : BusinessError) => {
    console.error(`Failed to create colorPicker. Code: ${err.code}, message: ${err.message}`);
  });
});

```


## createColorPicker

```TypeScript
function createColorPicker(source: image.PixelMap, callback: AsyncCallback<ColorPicker>): void
```

通过传入的PixelMap创建ColorPicker实例，使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-effectKit-function createColorPicker(source: image.PixelMap, callback: AsyncCallback<ColorPicker>): void--><!--Device-effectKit-function createColorPicker(source: image.PixelMap, callback: AsyncCallback<ColorPicker>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | image.PixelMap | 是 | image模块创建的PixelMap实例。 可通过图片解码或直接创建获得，具体可见[Image Kit简介](../../../media/image/image-overview.md)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ColorPicker&gt; | 是 | 回调函数。返回创建的ColorPicker实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 输入参数错误。 |

**示例：**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

// 创建用于图像效果的buffer
const colorBuffer = new ArrayBuffer(96);
// 设置图像初始化选项
let opts : image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
// 创建PixelMap实例
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  // 创建ColorPicker实例
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error(`Failed to create color picker. Code: ${error.code}, message: ${error.message}`);
    } else {
      console.info('Succeeded in creating color picker.');
    }
  });
});

```


## createColorPicker

```TypeScript
function createColorPicker(source: image.PixelMap, region: Array<number>, callback: AsyncCallback<ColorPicker>): void
```

通过传入的PixelMap创建选定取色区域的ColorPicker实例，使用callback异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-effectKit-function createColorPicker(source: image.PixelMap, region: Array<double>, callback: AsyncCallback<ColorPicker>): void--><!--Device-effectKit-function createColorPicker(source: image.PixelMap, region: Array<double>, callback: AsyncCallback<ColorPicker>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | image.PixelMap | 是 | image模块创建的PixelMap实例。 可通过图片解码或直接创建获得，具体可见[Image Kit简介](../../../media/image/image-overview.md)。 |
| region | Array&lt;number&gt; | 是 | 指定图片的取色区域。 数组第三个元素需大于第一个元素，第四个元素需大于第二个元素。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ColorPicker&gt; | 是 | 回调函数。返回创建的ColorPicker实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 输入参数错误。 |

**示例：**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

// 创建用于图像效果的buffer
const colorBuffer = new ArrayBuffer(96);
// 设置图像初始化选项
let opts : image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
// 创建PixelMap实例
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  // 创建指定取色区域的ColorPicker实例
  effectKit.createColorPicker(pixelMap, [0, 0, 1, 1], (error, colorPicker) => {
    if (error) {
      console.error(`Failed to create color picker. Code: ${error.code}, message: ${error.message}`);
    } else {
      console.info('Succeeded in creating color picker.');
    }
  });
});

```

