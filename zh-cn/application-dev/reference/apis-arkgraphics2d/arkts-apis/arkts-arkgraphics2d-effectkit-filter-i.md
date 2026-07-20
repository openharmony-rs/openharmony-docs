# Filter

图像效果类，用于将指定的效果添加到输入图像中。在调用Filter的方法前，需要先通过[createEffect](arkts-arkgraphics2d-effectkit-createeffect-f.md#createeffect-1)创建一个Filter实例。

**起始版本：** 9

<!--Device-effectKit-interface Filter--><!--Device-effectKit-interface Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { effectKit } from '@kit.ArkGraphics2D';
```

<a id="blur"></a>
## blur

```TypeScript
blur(radius: number): Filter
```

将模糊效果添加到效果链表中，返回链表的头节点。

> **说明：**  
>  
> 该接口为静态模糊接口，为静态图像提供模糊化效果，如果要对组件进行实时渲染的模糊，可以使用[动态模糊](docroot://ui/arkts-blur-effect.md)。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-Filter-blur(radius: double): Filter--><!--Device-Filter-blur(radius: double): Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | number | 是 | 模糊半径，单位为px。模糊效果与所设置的值成正比，值越大效果越明显。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i.md) | 返回已添加的图像效果。 |

**示例：**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// 传入读取的图片数据
function imageBlur(imageData: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise(async (resolve) => {
    // 创建图像源
    let imageSource = image.createImageSource(imageData);
    await imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      // 设置模糊半径
      let radius = 5;
      // 创建Filter实例
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // 对图片添加模糊效果
        headFilter.blur(radius);
        // 按照添加的效果标识对图片进行处理并且返回处理好的图片数据
        headFilter.getEffectPixelMap().then(imageData => {
          resolve(imageData);
        });
      }
    });
  });
}

@Entry
@Component
struct Index {
  @State imagePixelMap: image.PixelMap | null = null;
  private imageBuffer: ArrayBuffer | undefined = undefined;
  // 读取rawfile文件夹下的图片文件，也可根据需求更换读取方式，保证最终得到的是ArrayBuffer格式的图片数据即可
  async getFileBuffer(): Promise<ArrayBuffer | undefined> {
    try {
      const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      const fileData: Uint8Array = await context.resourceManager.getRawFileContent('image.png');
      const buffer: ArrayBuffer = fileData.buffer.slice(0);
      return buffer;
    } catch (err) {
      return undefined;
    }
  }

  async aboutToAppear(): Promise<void> {
    this.imageBuffer = await this.getFileBuffer();
    if (this.imageBuffer == undefined) {
      return;
    }
    // 图片处理为异步操作，可以依据是否需要拿到处理好的图片数据再进行下一步逻辑，按需添加await进行同步
    this.imagePixelMap = await imageBlur(this.imageBuffer);
  }

  build() {
    Column() {
      Image(this.imagePixelMap)
        .width(304)
        .height(305)
    }
    .height('100%')
    .width('100%')
  }
}

```

<a id="blur-1"></a>
## blur

```TypeScript
blur(radius: number, tileMode: TileMode): Filter
```

将模糊效果添加到效果链表中，返回链表的头节点。

> **说明：**  
>  
> 该接口为静态模糊接口，为静态图像提供模糊化效果，如果要对组件进行实时渲染的模糊，可以使用[动态模糊](docroot://ui/arkts-blur-effect.md)。

**起始版本：** 14

<!--Device-Filter-blur(radius: double, tileMode: TileMode): Filter--><!--Device-Filter-blur(radius: double, tileMode: TileMode): Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | number | 是 | 模糊半径，单位为px。模糊效果与所设置的值成正比，值越大效果越明显。 |
| tileMode | [TileMode](arkts-arkgraphics2d-effectkit-tilemode-e.md) | 是 | 着色器效果平铺模式。影响图像边缘的模糊效果。目前仅支持CPU渲染，所以目前着色器平铺模式仅支持DECAL。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i.md) | 返回已添加的图像效果。 |

**示例：**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// 传入读取的图片数据
function imageBlur(Image: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise(async (resolve) => {
    // 创建图像源
    let imageSource = image.createImageSource(Image);
    await imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      // 设置模糊半径
      let radius = 30;
      // 创建Filter实例
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // 对图片添加模糊效果并设置平铺模式
        headFilter.blur(radius, effectKit.TileMode.DECAL);
        // 按照添加的效果标识对图片进行处理并且返回处理好的图片数据
        headFilter.getEffectPixelMap().then(imageData => {
          resolve(imageData);
        });
      }
    });
  });
}

@Entry
@Component
struct Index {
  @State imagePixelMap: image.PixelMap | null = null;
  private imageBuffer: ArrayBuffer | undefined = undefined;
  // 读取rawfile文件夹下的图片文件，也可根据需求更换读取方式，保证最终得到的是ArrayBuffer格式的图片数据即可
  async getFileBuffer(): Promise<ArrayBuffer | undefined> {
    try {
      const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      const fileData: Uint8Array = await context.resourceManager.getRawFileContent('image.png');
      const buffer: ArrayBuffer = fileData.buffer.slice(0);
      return buffer;
    } catch (err) {
      return undefined;
    }
  }

  async aboutToAppear(): Promise<void> {
    this.imageBuffer = await this.getFileBuffer();
    if (this.imageBuffer == undefined) {
      return;
    }
    // 图片处理为异步操作，可以依据是否需要拿到处理好的图片数据再进行下一步逻辑，按需添加await进行同步
    this.imagePixelMap = await imageBlur(this.imageBuffer);
  }

  build() {
    Column() {
      Image(this.imagePixelMap)
        .width(304)
        .height(305)
    }
    .height('100%')
    .width('100%')
  }
}

```

<a id="brightness"></a>
## brightness

```TypeScript
brightness(bright: number): Filter
```

将高亮效果添加到效果链表中，返回链表的头节点。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-Filter-brightness(bright: double): Filter--><!--Device-Filter-brightness(bright: double): Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bright | number | 是 | 高亮程度，取值范围为[0, 1]，取值为0时图像保持不变，取值为1时图像达到预设的最大亮度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i.md) | 返回已添加的图像效果。 |

**示例：**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// 传入读取的图片数据
function imageBrightness(imageData: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise(async (resolve) => {
    // 创建图像源
    let imageSource = image.createImageSource(imageData);
    await imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      // 设置亮度值
      let bright = 0.5;
      // 创建Filter实例
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // 对图片添加高亮效果
        headFilter.brightness(bright);
        // 按照添加的效果标识对图片进行处理并且返回处理好的图片数据
        headFilter.getEffectPixelMap().then(imageData => {
          resolve(imageData);
        });
      }
    });
  });
}

@Entry
@Component
struct Index {
  @State imagePixelMap: image.PixelMap | null = null;
  private imageBuffer: ArrayBuffer | undefined = undefined;
  // 读取rawfile文件夹下的图片文件，也可根据需求更换读取方式，保证最终得到的是ArrayBuffer格式的图片数据即可
  async getFileBuffer(): Promise<ArrayBuffer | undefined> {
    try {
      const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      const fileData: Uint8Array = await context.resourceManager.getRawFileContent('image.png');
      const buffer: ArrayBuffer = fileData.buffer.slice(0);
      return buffer;
    } catch (err) {
      return undefined;
    }
  }

  async aboutToAppear(): Promise<void> {
    this.imageBuffer = await this.getFileBuffer();
    if (this.imageBuffer == undefined) {
      return;
    }
    // 图片处理为异步操作，可以依据是否需要拿到处理好的图片数据再进行下一步逻辑，按需添加await进行同步
    this.imagePixelMap = await imageBrightness(this.imageBuffer);
  }

  build() {
    Column() {
      Image(this.imagePixelMap)
        .width(304)
        .height(305)
    }
    .height('100%')
    .width('100%')
  }
}

```

<a id="geteffectpixelmap"></a>
## getEffectPixelMap

```TypeScript
getEffectPixelMap(): Promise<image.PixelMap>
```

获取已添加链表效果的源图像的image.PixelMap，使用CPU渲染，使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-Filter-getEffectPixelMap(): Promise<image.PixelMap>--><!--Device-Filter-getEffectPixelMap(): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | - Promise对象。返回已添加链表效果的源图像的image.PixelMap。 |

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
  // 创建Filter实例
  let headFilter = effectKit.createEffect(pixelMap);
  if (headFilter != null) {
    // 添加灰度效果并获取处理后的PixelMap
    headFilter.grayscale().getEffectPixelMap().then(data => {
      console.info('getPixelBytesNumber = ', data.getPixelBytesNumber());
    });
  }
});

```

<a id="geteffectpixelmap-1"></a>
## getEffectPixelMap

```TypeScript
getEffectPixelMap(useCpuRender : boolean): Promise<image.PixelMap>
```

获取已添加链表效果的源图像的image.PixelMap，支持指定渲染模式（CPU渲染或者GPU渲染），使用Promise异步回调。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-Filter-getEffectPixelMap(useCpuRender : boolean): Promise<image.PixelMap>--><!--Device-Filter-getEffectPixelMap(useCpuRender : boolean): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| useCpuRender | boolean | 是 | 指定渲染模式。true表示使用CPU渲染，false表示使用GPU渲染。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | - Promise对象。返回已添加链表效果的源图像的image.PixelMap。 |

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
  // 创建Filter实例、添加灰度效果并获取处理后的PixelMap
  effectKit.createEffect(pixelMap).grayscale().getEffectPixelMap(false).then(data => {
    console.info('getPixelBytesNumber = ', data.getPixelBytesNumber());
  });
});

```

<a id="getpixelmap"></a>
## getPixelMap

```TypeScript
getPixelMap(): image.PixelMap
```

获取已添加链表效果的源图像的image.PixelMap。

> **说明：**  
>  
> 从API version 9开始支持，从API version 11开始废弃，建议使用[getEffectPixelMap](arkts-arkgraphics2d-effectkit-filter-i.md#geteffectpixelmap-1)替代。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [getEffectPixelMap](arkts-arkgraphics2d-effectkit-filter-i.md#geteffectpixelmap-1)

<!--Device-Filter-getPixelMap(): image.PixelMap--><!--Device-Filter-getPixelMap(): image.PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| image.PixelMap | 已添加效果的源图像的image.PixelMap。 |

**示例：**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

const colorBuffer = new ArrayBuffer(96);
let opts : image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  let pixel = effectKit.createEffect(pixelMap).grayscale().getPixelMap();
  console.info('getPixelBytesNumber = ', pixel.getPixelBytesNumber());
});

```

<a id="grayscale"></a>
## grayscale

```TypeScript
grayscale(): Filter
```

将灰度效果添加到效果链表中，返回链表的头节点。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-Filter-grayscale(): Filter--><!--Device-Filter-grayscale(): Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i.md) | 返回已添加的图像效果。 |

**示例：**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// 传入读取的图片数据
function imageGrayscale(imageData: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise(async (resolve) => {
    // 创建图像源
    let imageSource = image.createImageSource(imageData);
    await imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      // 创建Filter实例
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // 对图片添加灰度效果
        headFilter.grayscale();
        // 按照添加的效果标识对图片进行处理并且返回处理好的图片数据
        headFilter.getEffectPixelMap().then(imageData => {
          resolve(imageData);
        });
      }
    });
  });
}

@Entry
@Component
struct Index {
  @State imagePixelMap: image.PixelMap | null = null;
  private imageBuffer: ArrayBuffer | undefined = undefined;
  // 读取rawfile文件夹下的图片文件，也可根据需求更换读取方式，保证最终得到的是ArrayBuffer格式的图片数据即可
  async getFileBuffer(): Promise<ArrayBuffer | undefined> {
    try {
      const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      const fileData: Uint8Array = await context.resourceManager.getRawFileContent('image.png');
      const buffer: ArrayBuffer = fileData.buffer.slice(0);
      return buffer;
    } catch (err) {
      return undefined;
    }
  }

  async aboutToAppear(): Promise<void> {
    this.imageBuffer = await this.getFileBuffer();
    if (this.imageBuffer == undefined) {
      return;
    }
    // 图片处理为异步操作，可以依据是否需要拿到处理好的图片数据再进行下一步逻辑，按需添加await进行同步
    this.imagePixelMap = await imageGrayscale(this.imageBuffer);
  }

  build() {
    Column() {
      Image(this.imagePixelMap)
        .width(304)
        .height(305)
    }
    .height('100%')
    .width('100%')
  }
}

```

<a id="invert"></a>
## invert

```TypeScript
invert(): Filter
```

将反转效果添加到效果链表中，返回链表的头节点。

**起始版本：** 12

<!--Device-Filter-invert(): Filter--><!--Device-Filter-invert(): Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i.md) | 返回已添加的图像效果。 |

**示例：**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// 传入读取的图片数据
function imageInvert(imageData: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise(async (resolve) => {
    // 创建图像源
    let imageSource = image.createImageSource(imageData);
    await imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      // 创建Filter实例
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // 对图片添加反转效果
        headFilter.invert();
        // 按照添加的效果标识对图片进行处理并且返回处理好的图片数据
        headFilter.getEffectPixelMap().then(imageData => {
          resolve(imageData);
        });
      }
    });
  });
}

@Entry
@Component
struct Index {
  @State imagePixelMap: image.PixelMap | null = null;
  private imageBuffer: ArrayBuffer | undefined = undefined;
  // 读取rawfile文件夹下的图片文件，也可根据需求更换读取方式，保证最终得到的是ArrayBuffer格式的图片数据即可
  async getFileBuffer(): Promise<ArrayBuffer | undefined> {
    try {
      const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      const fileData: Uint8Array = await context.resourceManager.getRawFileContent('image.png');
      const buffer: ArrayBuffer = fileData.buffer.slice(0);
      return buffer;
    } catch (err) {
      return undefined;
    }
  }

  async aboutToAppear(): Promise<void> {
    this.imageBuffer = await this.getFileBuffer();
    if (this.imageBuffer == undefined) {
      return;
    }
    // 图片处理为异步操作，可以依据是否需要拿到处理好的图片数据再进行下一步逻辑，按需添加await进行同步
    this.imagePixelMap = await imageInvert(this.imageBuffer);
  }

  build() {
    Column() {
      Image(this.imagePixelMap)
        .width(304)
        .height(305)
    }
    .height('100%')
    .width('100%')
  }
}

```

<a id="setcolormatrix"></a>
## setColorMatrix

```TypeScript
setColorMatrix(colorMatrix: Array<number>): Filter
```

将自定义效果添加到效果链表中，返回链表的头节点。

**起始版本：** 12

<!--Device-Filter-setColorMatrix(colorMatrix: Array<double>): Filter--><!--Device-Filter-setColorMatrix(colorMatrix: Array<double>): Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorMatrix | Array&lt;number&gt; | 是 | 自定义颜色矩阵。用于创建效果滤镜的 5x4 大小的矩阵，矩阵元素取值范围为[0, 1]，0和1代表的是矩阵中对应位置的颜色通道的权重，0代表该颜色通道不参与计算，1代表该颜色通道参与计算并保持原始权重。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i.md) | 返回已添加的图像效果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 输入参数错误。 |

**示例：**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// 传入读取的图片数据
function imageColorFilter(imageData: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise(async (resolve) => {
    // 创建图像源
    let imageSource = image.createImageSource(imageData);
    await imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      // 定义颜色矩阵
      let colorMatrix: Array<number> = [
        0.2126, 0.7152, 0.0722, 0, 0,
        0.2126, 0.7152, 0.0722, 0, 0,
        0.2126, 0.7152, 0.0722, 0, 0,
        0, 0, 0, 1, 0
      ];
      // 创建Filter实例
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // 对图片设置自定义颜色矩阵效果
        headFilter.setColorMatrix(colorMatrix);
        // 按照添加的效果标识对图片进行处理并且返回处理好的图片数据
        headFilter.getEffectPixelMap().then(imageData => {
          resolve(imageData);
        });
      }
    });
  });
}

@Entry
@Component
struct Index {
  @State imagePixelMap: image.PixelMap | null = null;
  private imageBuffer: ArrayBuffer | undefined = undefined;
  // 读取rawfile文件夹下的图片文件，也可根据需求更换读取方式，保证最终得到的是ArrayBuffer格式的图片数据即可
  async getFileBuffer(): Promise<ArrayBuffer | undefined> {
    try {
      const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      const fileData: Uint8Array = await context.resourceManager.getRawFileContent('image.png');
      const buffer: ArrayBuffer = fileData.buffer.slice(0);
      return buffer;
    } catch (err) {
      return undefined;
    }
  }

  async aboutToAppear(): Promise<void> {
    this.imageBuffer = await this.getFileBuffer();
    if (this.imageBuffer == undefined) {
      return;
    }
    // 图片处理为异步操作，可以依据是否需要拿到处理好的图片数据再进行下一步逻辑，按需添加await进行同步
    this.imagePixelMap = await imageColorFilter(this.imageBuffer);
  }

  build() {
    Column() {
      Image(this.imagePixelMap)
        .width(304)
        .height(305)
    }
    .height('100%')
    .width('100%')
  }
}

```

