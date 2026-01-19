# @ohos.effectKit (图像效果)(系统接口)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanamaru-->
<!--Designer: @gaoweihua-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

图像效果模块提供了处理图像的基础能力，包括亮度调节、模糊化、灰度调节和智能取色等。effectKit用于离线处理图像（如pixelmap、png、jpeg）以获得视觉效果，而uiEffect则实时接入渲染服务，针对屏幕帧缓存进行处理以获得动态视觉效果。

该模块提供以下图像效果相关的常用功能：

- [ColorPicker](#colorpicker)：智能取色器。
- [Filter](#filter)：效果类，用于添加指定效果到图像源。

> **说明：**
>
> - 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 页面仅包含本模块的系统接口，其他公开接口参见[ohos.effectKit (图像效果)](js-apis-effectKit.md)。

## 导入模块

```ts
import { effectKit } from "@kit.ArkGraphics2D";
```

## PictureComplexityDegree<sup>22+</sup>

图片内容复杂度的枚举。

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

| 名称                   | 值   | 说明                           |
| ---------------------- | ---- | ------------------------------ |
| UNKNOWN_COMPLEXITY_DEGREE_PICTURE | 0 | 默认值，图片内容复杂度未知。 |
| PURE_PICTURE    | 1    | 图片内容复杂度为纯净。 |
| MODERATE_COMPLEXITY_PICTURE    | 2    | 图片内容复杂度为一般。 |
| VERY_FLOWERY_PICTURE     | 3    | 图片内容复杂度为复杂。 |

## PictureShadeDegree<sup>22+</sup>

图片颜色深浅度的枚举。

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

| 名称                   | 值   | 说明                           |
| ---------------------- | ---- | ------------------------------ |
| UNKNOWN_SHADE_DEGREE_PICTURE     | 0    | 默认值，图片颜色深浅度未知。 |
| EXTREMELY_LIGHT_PICTURE    | 1    | 图片颜色深浅度为极浅。 |
| VERY_LIGHT_PICTURE    | 2    | 图片颜色深浅度为较浅。 |
| LIGHT_PICTURE     | 3    | 图片颜色深浅度为略浅。|
| MODERATE_SHADE_PICTURE     | 4    | 图片颜色深浅度为一般。|
| DARK_PICTURE     | 5    | 图片颜色深浅度为较深。|
| EXTREMELY_DARK_PICTURE     | 6    | 图片颜色深浅度为极深。|

## ColorPicker

取色类，用于从一张图像数据中获取它的主要颜色。在调用ColorPicker的方法前，需要先通过[createColorPicker](js-apis-effectKit.md#effectkitcreatecolorpicker)创建一个ColorPicker实例。

### getTopProportionColorsAndPercentage<sup>22+</sup>

getTopProportionColorsAndPercentage(colorCount: number): Map<Color | null, number | null>

读取图像占比靠前的颜色值以及对应比例，个数由`colorCount`指定，结果写入Color与其对应比例的字典中，使用同步方式返回。

**卡片能力：** 从API version 22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名      | 类型   | 必填 | 说明              |
| ---------- | ------ | ---- | ------------------------------------------- |
| colorCount | number | 是   | 需要取主色及对应比例的个数，向下取整。<br>**说明：** 在<!--RP1-->OpenHarmony 6.1<!--RP1End-->之前，取值范围为[1, 10]，取色个数大于10视为取前10个；从<!--RP1-->OpenHarmony 6.1<!--RP1End-->开始，取值范围为[1, 20]，取色个数大于20视为取前20个。   |

**返回值：**

| 类型                                     | 说明                                            |
| :--------------------------------------- | :---------------------------------------------- |
| Map<Color \| null, number \| null> | 图像占比前`colorCount`的颜色值与对应比例的字典，比例的取值范围为[0,1]。<br>- 当实际读取的特征色个数小于`colorCount`时，字典大小为实际特征色个数。<br>- 取色失败或取色个数小于1返回`Map()`。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202  | Permission verification failed. A non-system application calls a system API. |

**示例：**

```js
import { image } from "@kit.ImageKit";
import { effectKit } from "@kit.ArkGraphics2D";

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
}
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error('Failed to create color picker.');
    } else {
      console.info('Succeeded in creating color picker.');
      let colors: Map<effectKit.Color | null, number | null> = colorPicker.getTopProportionColorsAndPercentage(2);
      colors.forEach((value: number | null, key: effectKit.Color | null) => {
        console.info('get top proportion colors and percentages: color ' + key + ', percentage ' + value);
      })
    }
  })
})
```
![zh-ch_image_Top_Proportion_Colors_And_Percentages.png](figures/zh-ch_image_Top_Proportion_Colors_And_Percentages.png)

### getShadeDegree<sup>22+</sup>

getShadeDegree(): PictureShadeDegree

获取图像颜色深浅度。

**卡片能力：** 从API version 22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型                                     | 说明                                            |
| :--------------------------------------- | :---------------------------------------------- |
| [PictureShadeDegree](#pictureshadedegree22) | 图像颜色深浅度。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202  | Permission verification failed. A non-system application calls a system API. |

**示例：**

```js
import { image } from "@kit.ImageKit";
import { effectKit } from "@kit.ArkGraphics2D";

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
}
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error('Failed to create color picker.');
    } else {
      console.info('Succeeded in creating color picker.');
      let shadeDegree: effectKit.PictureShadeDegree = colorPicker.getShadeDegree();
      console.info('The shade degree of the image is ' + shadeDegree);
    }
  })
})
```

### getComplexityDegree<sup>22+</sup>

getComplexityDegree(): PictureComplexityDegree

获取图像内容复杂度。

**卡片能力：** 从API version 22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型                                     | 说明                                            |
| :--------------------------------------- | :---------------------------------------------- |
| [PictureComplexityDegree](#picturecomplexitydegree22) | 图像内容复杂度。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202  | Permission verification failed. A non-system application calls a system API. |

**示例：**

```js
import { image } from "@kit.ImageKit";
import { effectKit } from "@kit.ArkGraphics2D";

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
}
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error('Failed to create color picker.');
    } else {
      console.info('Succeeded in creating color picker.');
      let complexityDegree: effectKit.PictureComplexityDegree = colorPicker.getComplexityDegree();
      console.info('The complexity degree of the image is ' + complexityDegree);
    }
  })
})
```

### getAlphaZeroTransparentProportion<sup>23+</sup>

getAlphaZeroTransparentProportion(): number

获取图像中完全透明的像素占比。

**卡片能力：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型                                     | 说明                                            |
| :--------------------------------------- | :---------------------------------------------- |
| number | 完全透明的像素占比，比例的取值范围为[0,1]。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202  | Permission verification failed. A non-system application calls a system API. |

**示例：**

```js
import { image } from "@kit.ImageKit";
import { effectKit } from "@kit.ArkGraphics2D";

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
}
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error('Failed to create color picker.');
    } else {
      console.info('Succeeded in creating color picker.');
        let percentage: number = colorPicker.getAlphaZeroTransparentProportion();
      console.info('Get proportion of fully transparent pixels: ' + percentage);
    }
  })
})
```

## Filter

图像效果类用于将指定效果添加到输入图像。调用Filter方法前，需先通过[createEffect](js-apis-effectKit.md#effectkitcreateeffect)创建Filter实例。



### ellipticalGradientBlur<sup>23+</sup>

ellipticalGradientBlur(blurRadius: number, center: EllipticalMaskCenter, maskRadius: EllipticalMaskRadius, fractionStops: FractionStop[]): Filter

将带有椭圆形遮罩的渐变模糊效果添加到效果链表中，返回链表的头节点。

> **说明：**
>
> 该接口为静态图像处理接口，为静态图像提供含有椭圆形遮罩的渐变模糊化效果。

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型        | 必填 | 说明                                                         |
| ------ | ----------- | ---- | ------------------------------------------------------------ |
|  blurRadius   | number | 是   | 模糊半径，取正整数，单位是px，模糊半径大于60px时自动截断。模糊效果与所设置的模糊半径值成正比，值越大效果越明显。 |
|  center   | [EllipticalMaskCenter](#ellipticalmaskcenter23) | 是 | 设置椭圆的中心点，[0, 0]表示组件的左上角，[1, 1]表示组件的右下角。 |
|  maskRadius   | [EllipticalMaskRadius](#ellipticalmaskradius23) | 是 | 第一个值表示椭圆x方向轴半径，第二个值表示椭圆y方向轴半径，两个轴半径的数值1均对应于组件的高度，取值范围均大于0。 |
|  fractionStops   | [FractionStop](../apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#fractionstop12)[] | 是 | 渐变模糊位置与程度数组。位置与程度取值都在0-1之间，椭圆中心对应位置0，椭圆边界对应位置1。 模糊程度0表示无模糊，模糊程度1表示输入的模糊半径的模糊程度，大于1的转为1。位置参数值须严格递增，二元数组个数不能小于2，最大为12。 |

**返回值：**

| 类型           | 说明                                            |
| :------------- | :---------------------------------------------- |
| [Filter](#filter) | 返回已添加的图像效果。 |

**示例：**

``` ts
import { image } from '@kit.ImageKit';	
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// 传入读取的图片数据
function ImageEllipticalGradientBlur(Image: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise((resolve, reject) => {
    let imageSource = image.createImageSource(Image);
	  let blurRadius:number = 25;
	  let fractionStops:FractionStop[] = [[0, 0.2], [0.5, 0.7]];
	  let maskRadius:effectKit.EllipticalMaskRadius = [1, 1];
	  let center:effectKit.EllipticalMaskCenter = [0.5, 0.5];
    imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // 对图片添加效果标识
        headFilter.ellipticalGradientBlur(blurRadius, center, maskRadius, fractionStops);
      }
      // 按照添加的效果标识对图片进行处理并且返回处理好的图片数据
      headFilter.getEffectPixelMap(false).then(imageData => {
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
    this.imagePixelMap = await ImageEllipticalGradientBlur(this.imageBuffer);
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

## EllipticalMaskRadius<sup>23+</sup>

type EllipticalMaskRadius = [ number, number ]

定义椭圆形遮罩的半径。

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

| 类型           | 说明                                            |
| :------------- | :---------------------------------------------- |
| [ number, number ] | 椭圆形遮罩的半径。|

## EllipticalMaskCenter<sup>23+</sup>
type EllipticalMaskCenter = [ number, number ]

定义椭圆形遮罩的中心点。

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

| 类型           | 说明                                            |
| :------------- | :---------------------------------------------- |
| [ number, number ] | 椭圆形遮罩的中心点。|