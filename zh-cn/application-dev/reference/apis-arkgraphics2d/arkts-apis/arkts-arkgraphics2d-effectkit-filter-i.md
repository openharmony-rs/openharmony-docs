# Filter

图像效果类，用于通过链式调用将指定效果添加到效果链表中，适用于图片滤镜处理、视觉效果增强、图像美化等场景。 在调用Filter的方法前，需要先通过[createEffect](arkts-arkgraphics2d-effectkit-createeffect-f.md)创建一个Filter实例。 在添加效果后，需调用[getEffectPixelMap](#geteffectpixelmap)获取处理后的图像。

**起始版本：** 23

<!--Device-effectKit-interface Filter--><!--Device-effectKit-interface Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { effectKit } from '@kit.ArkGraphics2D';
```

## blur

```TypeScript
blur(radius: double): Filter
```

将模糊效果添加到效果链表中，返回链表的实例。着色器平铺模式使用DECAL，如需指定平铺模式， 可使用[blur](#blur)接口。 常用于实现背景虚化效果、隐私信息遮挡、毛玻璃背景效果、弹窗背景模糊等场景。 > **说明：** > > 该接口为静态模糊接口，为静态图像提供模糊化效果，如果要对组件进行实时渲染的模糊，可以使用[动态模糊](../../../ui/arkts-blur-effect.md)。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-Filter-blur(radius: double): Filter--><!--Device-Filter-blur(radius: double): Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | double | 是 | 模糊半径，单位为px，取值范围为[0, +∞)。模糊半径值越大，模糊效果越明显。传入负数时无效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Filter | 返回已添加效果的Filter实例，用于继续添加效果或获取处理后的图像。 |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// 传入读取的图片数据
function ImageBlur(Image: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise((resolve, reject) => {
    let imageSource = image.createImageSource(Image);
    imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      let radius = 5;
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // 对图片添加效果标识
        headFilter.blur(radius);
      }
      // 按照添加的效果标识对图片进行处理并且返回处理好的图片数据
      headFilter.getEffectPixelMap().then(imageData => {
        resolve(imageData);
      })
    })
  })
}

@Entry
@Component
struct Index {
  @State imagePixelMap: image.PixelMap | null = null;
  private imageBuffer: ArrayBuffer | undefined = undefined;
  // 读取rawfile文件夹下的图片文件，也可根据需求更换读取方式，保证最终得到的是ArrayBuffer格式的图片数据即可
  async getFileBuffer(): Promise<ArrayBuffer | undefined> {
    try{
      const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      const fileData: Uint8Array = await context.resourceManager.getRawFileContent('image.png');
      const buffer: ArrayBuffer = fileData.buffer.slice(0);
      return buffer;
    }catch (err){
      return undefined
    }
  }

  async aboutToAppear(): Promise<void>{
    this.imageBuffer = await this.getFileBuffer();
    if(this.imageBuffer == undefined){
      return;
    }
    // 图片处理为异步操作，可以依据是否需要拿到处理好的图片数据再进行下一步逻辑，按需添加await进行同步
    this.imagePixelMap = await ImageBlur(this.imageBuffer);
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

## blur

```TypeScript
blur(radius: double, tileMode: TileMode): Filter
```

将模糊效果添加到效果链表中，返回链表的实例。支持选择着色器效果平铺模式， 常用于实现背景虚化效果、隐私信息遮挡、毛玻璃背景效果、弹窗背景模糊等场景。 > **说明：** > > 该接口为静态模糊接口，为静态图像提供模糊化效果，如果要对组件进行实时渲染的模糊，可以使用[动态模糊](../../../ui/arkts-blur-effect.md)。

**起始版本：** 23

<!--Device-Filter-blur(radius: double, tileMode: TileMode): Filter--><!--Device-Filter-blur(radius: double, tileMode: TileMode): Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | double | 是 | 模糊半径，单位为px，取值范围为[0, +∞)。模糊半径值越大，模糊效果越明显。传入负数时无效果。 |
| tileMode | TileMode | 是 | 着色器效果平铺模式。影响图像边缘的模糊效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Filter | 返回已添加效果的Filter实例，用于继续添加效果或获取处理后的图像。 |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// 传入读取的图片数据
function ImageBlur(Image: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise((resolve, reject) => {
    let imageSource = image.createImageSource(Image);
    imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      let radius = 30;
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // 对图片添加效果标识
        headFilter.blur(radius, effectKit.TileMode.DECAL);
      }
      // 按照添加的效果标识对图片进行处理并且返回处理好的图片数据
      headFilter.getEffectPixelMap().then(imageData => {
        resolve(imageData);
      })
    })
  })
}

@Entry
@Component
struct Index {
  @State imagePixelMap: image.PixelMap | null = null;
  private imageBuffer: ArrayBuffer | undefined = undefined;
  // 读取rawfile文件夹下的图片文件，也可根据需求更换读取方式，保证最终得到的是ArrayBuffer格式的图片数据即可
  async getFileBuffer(): Promise<ArrayBuffer | undefined> {
    try{
      const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      const fileData: Uint8Array = await context.resourceManager.getRawFileContent('image.png');
      const buffer: ArrayBuffer = fileData.buffer.slice(0);
      return buffer;
    }catch (err){
      return undefined
    }
  }

  async aboutToAppear(): Promise<void>{
    this.imageBuffer = await this.getFileBuffer();
    if(this.imageBuffer == undefined){
      return;
    }
    // 图片处理为异步操作，可以依据是否需要拿到处理好的图片数据再进行下一步逻辑，按需添加await进行同步
    this.imagePixelMap = await ImageBlur(this.imageBuffer);
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

## brightness

```TypeScript
brightness(bright: double): Filter
```

将高亮效果添加到效果链表中，返回链表的实例。该方法通过调整图像亮度实现高亮效果， 常用于暗图增亮处理、图片预览亮度增强、夜间模式图片适配等场景。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-Filter-brightness(bright: double): Filter--><!--Device-Filter-brightness(bright: double): Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bright | double | 是 | 高亮程度，取值范围为[0, 1]，取值为0时图像保持不变，取值为1时图像亮度提升到最大值。超出范围时自动修正为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Filter | 返回已添加效果的Filter实例，用于继续添加效果或获取处理后的图像。 |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// 传入读取的图片数据
function ImageBrightness(Image: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise((resolve, reject) => {
    let imageSource = image.createImageSource(Image);
    imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      let bright = 0.5;
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // 对图片添加效果标识
        headFilter.brightness(bright);
      }
      // 按照添加的效果标识对图片进行处理并且返回处理好的图片数据
      headFilter.getEffectPixelMap().then(imageData => {
        resolve(imageData);
      })
    })
  })
}

@Entry
@Component
struct Index {
  @State imagePixelMap: image.PixelMap | null = null;
  private imageBuffer: ArrayBuffer | undefined = undefined;
  // 读取rawfile文件夹下的图片文件，也可根据需求更换读取方式，保证最终得到的是ArrayBuffer格式的图片数据即可
  async getFileBuffer(): Promise<ArrayBuffer | undefined> {
    try{
      const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      const fileData: Uint8Array = await context.resourceManager.getRawFileContent('image.png');
      const buffer: ArrayBuffer = fileData.buffer.slice(0);
      return buffer;
    }catch (err){
      return undefined
    }
  }

  async aboutToAppear(): Promise<void>{
    this.imageBuffer = await this.getFileBuffer();
    if(this.imageBuffer == undefined){
      return;
    }
    // 图片处理为异步操作，可以依据是否需要拿到处理好的图片数据再进行下一步逻辑，按需添加await进行同步
    this.imagePixelMap = await ImageBrightness(this.imageBuffer);
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

## getEffectPixelMap

```TypeScript
getEffectPixelMap(): Promise<image.PixelMap>
```

获取已添加链表效果的源图像的image.PixelMap，默认使用CPU渲染，使用Promise异步回调。 如需指定渲染模式，可使用[getEffectPixelMap](#geteffectpixelmap)接口。 常用于图片处理后需要保存或显示结果的场景。 > **说明：** > > 该方法默认使用CPU渲染，着色器平铺模式仅支持DECAL，其他模式（CLAMP、REPEAT、MIRROR）暂不支持。 如需使用GPU渲染或了解渲染模式对TileMode的影响，请参见[TileMode](arkts-arkgraphics2d-effectkit-tilemode-e.md)和 [getEffectPixelMap](#geteffectpixelmap)。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-Filter-getEffectPixelMap(): Promise<image.PixelMap>--><!--Device-Filter-getEffectPixelMap(): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise对象。返回已添加链表效果的源图像的image.PixelMap。 |

**示例**

```TypeScript
import { image } from "@kit.ImageKit";
import { effectKit } from "@kit.ArkGraphics2D";

const color = new ArrayBuffer(96);
let opts : image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createEffect(pixelMap).grayscale().getEffectPixelMap().then(data => {
    console.info('getPixelBytesNumber = ', data.getPixelBytesNumber());
  })
})
```

## getEffectPixelMap

```TypeScript
getEffectPixelMap(useCpuRender : boolean): Promise<image.PixelMap>
```

获取已添加链表效果的源图像的image.PixelMap，支持指定渲染模式（CPU渲染或者GPU渲染），使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-Filter-getEffectPixelMap(useCpuRender : boolean): Promise<image.PixelMap>--><!--Device-Filter-getEffectPixelMap(useCpuRender : boolean): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| useCpuRender | boolean | 是 | 指定渲染模式。true表示使用CPU渲染，false表示使用GPU渲染。 使用GPU渲染时，着色器效果平铺模式[TileMode](arkts-arkgraphics2d-effectkit-tilemode-e.md)的支持范围与CPU渲染不同，详见TileMode说明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise对象。返回已添加链表效果的源图像的image.PixelMap。 |

**示例**

```TypeScript
import { image } from "@kit.ImageKit";
import { effectKit } from "@kit.ArkGraphics2D";

const color = new ArrayBuffer(96);
let opts : image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createEffect(pixelMap).grayscale().getEffectPixelMap(false).then(data => {
    console.info('getPixelBytesNumber = ', data.getPixelBytesNumber());
  })
})
```

## getPixelMap

```TypeScript
getPixelMap(): image.PixelMap
```

获取已添加链表效果的源图像的image.PixelMap。常用于图片处理后需要保存或显示结果的场景。 > **说明：** > > 从API version 9开始支持，从API version 11开始废弃，建议使用[getEffectPixelMap](#geteffectpixelmap)替代。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [getEffectPixelMap](#geteffectpixelmap)

<!--Device-Filter-getPixelMap(): image.PixelMap--><!--Device-Filter-getPixelMap(): image.PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| image.PixelMap | 已添加效果的源图像的image.PixelMap。 |

**示例**

```TypeScript
import { image } from "@kit.ImageKit";
import { effectKit } from "@kit.ArkGraphics2D";

const color = new ArrayBuffer(96);
let opts : image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(color, opts).then((pixelMap) => {
  let pixel = effectKit.createEffect(pixelMap).grayscale().getPixelMap();
  console.info('getPixelBytesNumber = ', pixel.getPixelBytesNumber());
})
```

## grayscale

```TypeScript
grayscale(): Filter
```

将灰度效果添加到效果链表中，返回链表的实例。该方法将彩色图像转换为灰度图像，通过加权计算RGB值得到灰度值。 常用于黑白风格照片生成、图片预处理去色、灰度图标制作等场景。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-Filter-grayscale(): Filter--><!--Device-Filter-grayscale(): Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Filter | 返回已添加效果的Filter实例，用于继续添加效果或获取处理后的图像。 |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// 传入读取的图片数据
function ImageGrayscale(Image: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise((resolve, reject) => {
    let imageSource = image.createImageSource(Image);
    imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // 对图片添加效果标识
        headFilter.grayscale();
      }
      // 按照添加的效果标识对图片进行处理并且返回处理好的图片数据
      headFilter.getEffectPixelMap().then(imageData => {
        resolve(imageData);
      })
    })
  })
}

@Entry
@Component
struct Index {
  @State imagePixelMap: image.PixelMap | null = null;
  private imageBuffer: ArrayBuffer | undefined = undefined;
  // 读取rawfile文件夹下的图片文件，也可根据需求更换读取方式，保证最终得到的是ArrayBuffer格式的图片数据即可
  async getFileBuffer(): Promise<ArrayBuffer | undefined> {
    try{
      const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      const fileData: Uint8Array = await context.resourceManager.getRawFileContent('image.png');
      const buffer: ArrayBuffer = fileData.buffer.slice(0);
      return buffer;
    }catch (err){
      return undefined
    }
  }

  async aboutToAppear(): Promise<void>{
    this.imageBuffer = await this.getFileBuffer();
    if(this.imageBuffer == undefined){
      return;
    }
    // 图片处理为异步操作，可以依据是否需要拿到处理好的图片数据再进行下一步逻辑，按需添加await进行同步
    this.imagePixelMap = await ImageGrayscale(this.imageBuffer);
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

## invert

```TypeScript
invert(): Filter
```

将反转效果添加到效果链表中，返回链表的实例。该方法将图像的RGB颜色值进行反转， 常用于实现底片效果、图片艺术处理、夜间模式适配等场景。

**起始版本：** 23

<!--Device-Filter-invert(): Filter--><!--Device-Filter-invert(): Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Filter | 返回已添加效果的Filter实例，用于继续添加效果或获取处理后的图像。 |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// 传入读取的图片数据
function ImageInvert(Image: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise((resolve, reject) => {
    let imageSource = image.createImageSource(Image);
    imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // 对图片添加效果标识
        headFilter.invert();
      }
      // 按照添加的效果标识对图片进行处理并且返回处理好的图片数据
      headFilter.getEffectPixelMap().then(imageData => {
        resolve(imageData);
      })
    })
  })
}

@Entry
@Component
struct Index {
  @State imagePixelMap: image.PixelMap | null = null;
  private imageBuffer: ArrayBuffer | undefined = undefined;
  // 读取rawfile文件夹下的图片文件，也可根据需求更换读取方式，保证最终得到的是ArrayBuffer格式的图片数据即可
  async getFileBuffer(): Promise<ArrayBuffer | undefined> {
    try{
      const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      const fileData: Uint8Array = await context.resourceManager.getRawFileContent('image.png');
      const buffer: ArrayBuffer = fileData.buffer.slice(0);
      return buffer;
    }catch (err){
      return undefined
    }
  }

  async aboutToAppear(): Promise<void>{
    this.imageBuffer = await this.getFileBuffer();
    if(this.imageBuffer == undefined){
      return;
    }
    // 图片处理为异步操作，可以依据是否需要拿到处理好的图片数据再进行下一步逻辑，按需添加await进行同步
    this.imagePixelMap = await ImageInvert(this.imageBuffer);
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

## setColorMatrix

```TypeScript
setColorMatrix(colorMatrix: Array<double>): Filter
```

通过自定义颜色矩阵对图像进行颜色变换处理，将效果添加到效果链表中，返回链表的实例。 常用于实现预设滤镜不支持的自定义颜色效果，如复古色调、冷暖色调调整等场景。

**起始版本：** 23

<!--Device-Filter-setColorMatrix(colorMatrix: Array<double>): Filter--><!--Device-Filter-setColorMatrix(colorMatrix: Array<double>): Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorMatrix | Array&lt;double&gt; | 是 | 自定义颜色矩阵。用于创建效果滤镜的4x5大小的矩阵，数组长度必须为20， 前4列对应R、G、B、A通道的变换系数，第5列为常量偏移值。建议元素取值为[-1, 1]，超出此范围可能导致颜色值溢出或产生非预期效果。数组长度不为20时返回null。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Filter | 返回已添加效果的Filter实例，用于继续添加效果或获取处理后的图像。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 输入参数错误。 |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// 传入读取的图片数据
function ImageColorFilter(Image: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise((resolve, reject) => {
    let imageSource = image.createImageSource(Image);
    imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      let colorMatrix:Array<number> = [
      0.2126,0.7152,0.0722,0,0,
      0.2126,0.7152,0.0722,0,0,
      0.2126,0.7152,0.0722,0,0,
      0,0,0,1,0
      ];
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // 对图片添加效果标识
        headFilter.setColorMatrix(colorMatrix);
      }
      // 按照添加的效果标识对图片进行处理并且返回处理好的图片数据
      headFilter.getEffectPixelMap().then(imageData => {
        resolve(imageData);
      })
    })
  })
}

@Entry
@Component
struct Index {
  @State imagePixelMap: image.PixelMap | null = null;
  private imageBuffer: ArrayBuffer | undefined = undefined;
  // 读取rawfile文件夹下的图片文件，也可根据需求更换读取方式，保证最终得到的是ArrayBuffer格式的图片数据即可
  async getFileBuffer(): Promise<ArrayBuffer | undefined> {
    try{
      const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      const fileData: Uint8Array = await context.resourceManager.getRawFileContent('image.png');
      const buffer: ArrayBuffer = fileData.buffer.slice(0);
      return buffer;
    }catch (err){
      return undefined
    }
  }

  async aboutToAppear(): Promise<void>{
    this.imageBuffer = await this.getFileBuffer();
    if(this.imageBuffer == undefined){
      return;
    }
    // 图片处理为异步操作，可以依据是否需要拿到处理好的图片数据再进行下一步逻辑，按需添加await进行同步
    this.imagePixelMap = await ImageColorFilter(this.imageBuffer);
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

