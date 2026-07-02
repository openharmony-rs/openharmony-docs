# @ohos.graphics.uiEffect (效果级联)(系统接口)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hanamaru-->
<!--Designer: @chensiyi_CE-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

本模块提供组件效果的一些基础能力，包括模糊、提亮等。效果被分为Filter和VisualEffect大类，同类效果可以级联在一个效果大类的实例下。使用该模块可以快速实现复杂的视觉效果，无需开发者掌握底层的图像处理算法，降低了开发复杂度，提升了用户体验。在实际开发中，模糊可用于背景虚化，提亮可用于亮屏显示等。

- [Filter](#filter)：用于添加指定Filter效果到组件上。
- [VisualEffect](#visualeffect)：用于添加指定VisualEffect效果到组件上。

**Filter与VisualEffect的选择：** 两者分别属于不同的效果大类，支持的视觉效果类型不同，根据实际需求的效果类型选择对应的效果类。

> **说明：**
>
> - 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 页面仅包含本模块的系统接口，其他公开接口参见[ohos.graphics.uiEffect (效果级联)](js-apis-uiEffect.md)。
> - 本模块的接口均依赖画布上已有的内容进行绘制，如果与具有离屏功能的接口（如[blendMode<sup>11+</sup>](../apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#blendmode11)的离屏模式）联合使用，可能会产生非预期效果。

## 导入模块

```ts
import { uiEffect } from "@kit.ArkGraphics2D";
```

## uiEffect.createBrightnessBlender
createBrightnessBlender(param: BrightnessBlenderParam): BrightnessBlender

创建BrightnessBlender实例用于给组件添加提亮效果。

**卡片能力：** 从API version 22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名  | 类型                                              | 必填 | 说明                        |
| ------ | ------------------------------------------------- | ---- | --------------------------- |
| param  | [BrightnessBlenderParam](#brightnessblenderparam) | 是   | 实现提亮效果的参数，包含灰度调整系数、饱和度、混合比例等配置项。 |

**返回值：**

| 类型                                     | 说明                     |
| ---------------------------------------- | ----------------------- |
| [BrightnessBlender](#brightnessblender) | 返回提亮效果的BrightnessBlender混合器。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
// 创建BrightnessBlender实例用于给组件添加提亮效果
let blender : uiEffect.BrightnessBlender =
  uiEffect.createBrightnessBlender({cubicRate:1.0, quadraticRate:1.0, linearRate:1.0, degree:1.0, saturation:1.0,
    positiveCoefficient:[2.3, 4.5, 2.0], negativeCoefficient:[0.5, 2.0, 0.5], fraction:0.0})
```

## uiEffect.createHdrBrightnessBlender<sup>20+</sup>
createHdrBrightnessBlender(param: BrightnessBlenderParam): HdrBrightnessBlender

创建[HdrBrightnessBlender](#hdrbrightnessblender20)实例用于给组件添加支持HDR的提亮效果。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名  | 类型                                              | 必填 | 说明                        |
| ------ | ------------------------------------------------- | ---- | --------------------------- |
| param  | [BrightnessBlenderParam](#brightnessblenderparam) | 是   | 实现提亮效果的参数，包含灰度调整系数、饱和度、混合比例等配置项，用于配置提亮效果。 |

**返回值：**

| 类型                                     | 说明                     |
| ---------------------------------------- | ----------------------- |
| [HdrBrightnessBlender](#hdrbrightnessblender20) | 返回具有提亮效果的混合器（支持HDR）。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202  | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { uiEffect } from '@kit.ArkGraphics2D'

// 创建支持HDR的BrightnessBlender实例
let blender : uiEffect.HdrBrightnessBlender =
  uiEffect.createHdrBrightnessBlender({cubicRate:1.0, quadraticRate:1.0, linearRate:1.0, degree:1.0, saturation:1.0,
    positiveCoefficient:[2.3, 4.5, 2.0], negativeCoefficient:[0.5, 2.0, 0.5], fraction:0.0})

@Entry
@Component
struct Example {
  build() {
    RelativeContainer() {
      Image($r("app.media.screenshot"))
        .width("100%")
        .height("100%")
        .advancedBlendMode(blender)
    }
  }
}
```
## uiEffect.createHdrDarkenBlender

createHdrDarkenBlender(hdrBrightnessRatio: number, grayscaleFactor?: [number, number, number]): HdrDarkenBlender

创建[HdrDarkenBlender](#hdrdarkenblender)实例用于HDR图层的压暗混合效果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名               | 类型                        | 必填  | 说明                                                              |
| ------------------- | -------------------------- | ----  | ---------------------------------------------------------------- |
| hdrBrightnessRatio           | number                    | 是   | HDR的提亮倍数。<br>取值范围为[1.0, 设备当前支持最大提亮倍数]。<br>设置小于1.0的值时，按值为1.0处理；<br>当值等于1.0时，为组件原本亮度；<br>设置大于设备当前支持最大提亮倍数的值时，按值为设备当前支持最大提亮倍数处理，支持最大提亮倍数 = 设备最大亮度 / 设备默认亮度。<br>设备最大亮度通过hdc命令获取：hdc shell param get const.display.brightness.max <br>设备默认亮度通过hdc命令获取：hdc shell param get const.display.brightness.default                       |
| grayscaleFactor       | [number, number, number]                      | 否   | 将RGB颜色转换为灰度值。灰度转换公式的权重可随当前色域自动调整，不同色域下使用不同的权重计算方式；适用于sRGB等标准色域场景。当需要根据特定色域或视觉效果自定义灰度转换权重时传入此参数。三个分量均无边界限制。默认值为标准灰度权重[0.299, 0.587, 0.114]。 |

**返回值：**

| 类型                                   | 说明                       |
| ---------------------------------------- | ------------------------- |
| [HdrDarkenBlender](#hdrdarkenblender) | 返回HDR压暗混合器，用于将压暗效果添加到指定的组件上。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 401  | CreateHdrDarkenBlender failed, parameter is null or undefined. |

**示例：**
```ts
import { uiEffect } from '@kit.ArkGraphics2D'

// 创建HDR压暗混合器实例
let blender : uiEffect.HdrDarkenBlender = 
  uiEffect.createHdrDarkenBlender(1.3, [0.299, 0.587, 0.114])

@Entry
@Component
struct Example {
  build() { 
    RelativeContainer() { 
      Stack(){ 
          Text("TextWord") 
          Image($r("app.media.screenshot")) 
            .width("100%") 
            .height("100%") 
            .advancedBlendMode(blender) 
      } 
    } 
  } 
}
```

## Filter

Filter效果类，用于将模糊、边缘像素扩展、水波纹等效果添加到组件上。在调用Filter的方法前，需要先通过[createFilter](js-apis-uiEffect.md#uieffectcreatefilter)创建一个Filter实例。

### pixelStretch
pixelStretch(stretchSizes: Array\<number\>, tileMode: TileMode): Filter

将边缘像素扩展效果添加至组件上。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| stretchSizes  | Array\<number\>         | 是   | 上下左右四个方向边缘像素扩展的百分比比例，取值范围为[-1, 1]。<br>正值表示向外扩展，上下左右四个方向分别用指定原图比例的边缘像素填充。负值表示内缩，但是最终图像大小不变。<br>注意四个方向对应的参数需统一为非正值或非负值，否则效果无效。|
| tileMode      | [TileMode](#tilemode) | 是   | 边缘像素扩展的像素填充模式。 |


**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [Filter](#filter) | 返回挂载了边缘像素扩展效果的Filter。 |

**示例：**

```ts
// 将边缘像素扩展效果添加至组件上
let filter = uiEffect.createFilter()
filter.pixelStretch([0.2, 0.2, 0.2, 0.2], uiEffect.TileMode.CLAMP)
```

### waterRipple
waterRipple(progress: number, waveCount: number, x: number, y: number, rippleMode: WaterRippleMode): Filter

将水波纹效果添加至组件上。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| progress  | number         | 是   | 表示水波纹的进度，取值范围为[0, 1]。<br>水波纹进度越趋向于1，水波纹展示越完全。<br>超出取值范围水波纹不会出现效果。|
| waveCount      | number | 是   | 水波纹波动时波纹的个数，取值范围为[1, 3]。<br>水波纹的个数只能取整数，如果为浮点数或超出取值范围，水波纹不会出现效果。 |
| x      | number | 是   | 水波纹中心在屏幕中第一次出现的x轴位置。<br>水波纹对屏幕进行归一化处理，左上角的坐标为（0, 0），右上角坐标为（1, 0）。<br>当x取值为负值时，代表在屏幕左侧。|
| y      | number | 是   | 水波纹中心在屏幕中第一次出现的y轴位置。<br>水波纹对屏幕进行归一化处理，左上角的坐标为（0, 0），左下角坐标为（0, 1）。<br>当y取值为负值时，代表在屏幕上方。 |
| rippleMode      | [WaterRippleMode](#waterripplemode) | 是   | 水波纹的场景模式。|


**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [Filter](#filter) | 返回挂载了水波纹效果的Filter。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202  | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
// 将水波纹效果添加至组件上
let filter = uiEffect.createFilter()
filter.waterRipple(0.5, 2, 0.5, 0.5, uiEffect.WaterRippleMode.SMALL2SMALL)
```

### flyInFlyOutEffect
flyInFlyOutEffect(degree: number, flyMode: FlyMode): Filter

将飞入飞出形变效果添加至组件上。典型应用场景包括页面切换动画、窗口进出动画、对话框弹出动画、列表项进出动画等。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| degree  | number         | 是   | 表示控制飞入飞出形变的程度，取值范围为[0, 1]。<br>越靠近1，变形程度越明显。<br>超出取值范围形变不会出现效果。|
| flyMode      | [FlyMode](#flymode) | 是   | 飞入飞出的场景模式。<br>BOTTOM表示从设备底部飞入飞出形变场景。<br>TOP表示从设备顶部飞入飞出形变场景。 |


**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [Filter](#filter) | 返回挂载了飞入飞出形变效果的Filter。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202  | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
// 将飞入飞出形变效果添加至组件上
let filter = uiEffect.createFilter()
filter.flyInFlyOutEffect(0.5, uiEffect.FlyMode.TOP)
```

### distort<sup>13+</sup>
distort(distortionK: number): Filter

将透镜畸变效果添加至组件上。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| distortionK  | number         | 是   | 畸变系数，表示透镜畸变的程度，取值范围为[-1, 1]。畸变系数设置小于-1的值时，按值为-1处理；设置大于1的值时，按值为1处理。|

![Add-Distort.png](./figures/Add-Distort.png)

如上图是对图片组件分别设置畸变参数为-1，0，0.5，1的绘制结果。畸变参数小于0时，效果为桶形畸变；大于0时，效果为枕形畸变；越接近0时，畸变程度越小，等于0时，没有畸变效果。

**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [Filter](#filter) | 返回挂载了透镜畸变效果的Filter。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
// 将透镜畸变效果添加至组件上
let filter = uiEffect.createFilter()
filter.distort(-0.5)
```


### radiusGradientBlur<sup>19+</sup>
radiusGradientBlur(value: number, options: LinearGradientBlurOptions): Filter

为组件内容添加半径线性渐变模糊效果。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| value  | number         | 是   | 模糊半径，单位为px，模糊半径越大越模糊。取值范围为[0, 128]。模糊半径设置为0时不模糊；模糊半径设置小于0的值时，按值为0处理；设置大于128的值时，按值为128处理。|
| options  | [LinearGradientBlurOptions](../apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#lineargradientbluroptions12)         | 是   | 线性渐变参数，包含两个部分fractionStops和direction。|

**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [Filter](#filter) | 返回挂载了半径线性渐变模糊效果的Filter。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { uiEffect } from '@kit.ArkGraphics2D'

@Entry
@Component
struct RadiusGradientBlurExample {
  @State blurRadiusExample: number = 64
  @State linearGradientBlurOptionsExample: LinearGradientBlurOptions =
    {fractionStops: [[0.0, 0.0], [1.0, 1.0]], direction: GradientDirection.Bottom}

  build() {
    Column() {
      Image($rawfile('test.png'))
        // 为组件内容添加半径线性渐变模糊效果
        .compositingFilter(uiEffect.createFilter().radiusGradientBlur(this.blurRadiusExample,
          this.linearGradientBlurOptionsExample))
    }
  }
}
```

### bezierWarp<sup>20+</sup>
bezierWarp(controlPoints: Array<common2D.Point>): Filter

将贝塞尔曲线变形的效果添加至组件上。该效果通过在图层边界上创建封闭的贝塞尔曲线，实现对图像的精准扭曲和形状调整。贝塞尔曲线共有四段，首尾顺次相连，每段包含一个顶点和两个切点。典型应用场景包括人脸形变特效、卡片透视变形等。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| controlPoints  | Array<[common2D.Point](js-apis-graphics-common2D.md#point12)>| 是   | 12个贝塞尔形变控制点，数组长度必须为12，更改控制点的位置可改变形成边缘的曲线形状，从而扭曲图像。控制点坐标使用归一化坐标系（默认范围为[0, 1]），且坐标值可大于1或小于0。数组长度不为12时效果不生效。|

**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [Filter](#filter) | 返回挂载了贝塞尔曲线变形效果的Filter。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { common2D, uiEffect } from '@kit.ArkGraphics2D'

@Entry
@Component
struct BezierWarpExample {
  @State valueBezier: Array<common2D.Point> = [
    { x: 0, y: 0 }, { x: 1 / 3, y: 0 }, { x: 2 / 3, y: 0 }, // top edge
    { x: 0.5, y: 0 }, { x: 0.5, y: 1 / 3 }, { x: 1, y: 2 / 3 }, // right edge
    { x: 1, y: 1 }, { x: 2 / 3, y: 1 }, { x: 1 / 3, y: 1 }, // bottom edge
    { x: 0, y: 1 }, { x: 0, y: 2 / 3 }, { x: 0, y: 1 / 3 }] // left edge

  build() {
    Column() {
      Image($rawfile('test.jpg'))
        // 将贝塞尔曲线变形的效果添加至组件上
        .foregroundFilter(uiEffect.createFilter().bezierWarp(this.valueBezier))
    }
  }
}
```

### colorGradient<sup>20+</sup>
colorGradient(colors: Array\<Color>, positions: Array\<common2D.Point>, strengths: Array\<number>, alphaMask?: Mask): Filter

为组件内容添加颜色渐变效果。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| colors  | Array\<[Color](#color20)>         | 是   | 颜色数组，多个颜色的渐变。数组长度取值范围为[0, 12]，每个颜色值取值范围需大于等于0，无上限限制。数组长度等于0或大于12时无效果，colors、positions和strengths的数组长度不相等时无效果。|
| positions  | Array\<[common2D.Point](js-apis-graphics-common2D.md#point12)>         | 是   | 位置数组，颜色对应的分布位置。数组长度取值范围为[0, 12]。数组长度等于0或大于12时无效果，colors、positions和strengths的数组长度不相等时无效果。|
| strengths  | Array\<number>         | 是   | 强度数组，颜色对应的扩散强度。数组长度取值范围为[0, 12]，每一个强度值需大于等于0，无上限限制。数组长度等于0或大于12时无效果，colors、positions和strengths的数组长度不相等时无效果。|
| alphaMask  | [Mask](#mask20)         | 否   | 控制渐变效果透明度分布的遮罩。可通过Mask类的创建方法（如[createRippleMask](#createripplemask20)、[createRadialGradientMask](#createradialgradientmask20)等）创建Mask实例。当需要控制颜色渐变效果的透明度分布（如局部透明或动态透明效果）时传入此参数。不设置时，颜色渐变效果的透明度完全由colors参数决定。|

**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [Filter](#filter) | 返回挂载了颜色渐变效果的Filter。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { common2D, uiEffect } from '@kit.ArkGraphics2D'

@Entry
@Component
struct ColorGradientExample {
  @State gradientColors: Array<uiEffect.Color> = [
    {red: 1.0, green: 0.8, blue: 0.5, alpha: 0.8},
    {red: 1.0, green: 1.5, blue: 0.5, alpha: 1.0}
  ]

  @State gradientPositions: Array<common2D.Point> = [
    {x: 0.2, y: 0.2},
    {x: 0.8, y: 0.6}]

  @State gradientStrengths: Array<number> = [0.3, 0.3]

  build() {
    Column() {
      Row()
        .width("100%")
        .height("100%")
        // 为组件内容添加颜色渐变效果
        .backgroundFilter(uiEffect.createFilter().colorGradient(this.gradientColors, this.gradientPositions, this.gradientStrengths))
    }
  }
}
```

### contentLight<sup>20+</sup>
contentLight(lightPosition: common2D.Point3d, lightColor: common2D.Color, lightIntensity: number, displacementMap?: Mask): Filter

为组件内容添加3D光照效果。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| lightPosition | [common2D.Point3d](js-apis-graphics-common2D.md#point3d12) | 是 | 光源在组件空间的位置，[-1, -1, 0]为组件左上角，[1, 1, 0]为组件的右下角，z轴分量越大光源离组件平面越远，可照射区域越大。<br> x分量取值范围为[-10, 10]，y分量取值范围为[-10, 10]，z分量取值范围为[0, 10]，超出范围会自动截断。 |
| lightColor | [common2D.Color](js-apis-graphics-common2D.md#color) | 是 | 光源颜色，RGBA各分量取值范围为[0, 1]，超出范围会自动截断。 |
| lightIntensity | number | 是 | 光源强度，取值范围为[0, 1]，数值越大光源亮度越大，超出范围会自动截断。|
| displacementMap | [Mask](#mask20) | 否 | 置换贴图参数，该参数暂不生效，不建议传入。不设置时对功能无影响。 |

**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [Filter](#filter) | 返回了具有内容光照效果的Filter。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { common2D, uiEffect } from '@kit.ArkGraphics2D'

@Entry
@Component
struct Index {
  @State contentLightPosition: common2D.Point3d = {
    x: 0, y: 0, z: 2
  }
  @State contentLightColor: common2D.Color = {
    red: 1,
    green: 1,
    blue: 1,
    alpha: 1
  }
  @State lightIntensity: number = 1

  build() {
    Column() {
      Stack() {
        Image($r('app.media.man'))
          .width('646px')
          .height('900px')
          .borderRadius(10)
          // 为组件内容添加3D光照效果
          .foregroundFilter(uiEffect.createFilter().contentLight(this.contentLightPosition, this.contentLightColor, this.lightIntensity))
      }
      .width('100%')
      .height('55%')
    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .backgroundColor('#555')
  }
}
```

### edgeLight<sup>20+</sup>
edgeLight(alpha: number, color?: Color, mask?: Mask, bloom?: boolean): Filter

为组件内容检测边缘，并添加边缘高亮效果。该效果自动检测组件内容的边缘轮廓并叠加高亮描边。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| alpha  | number         | 是   | 指定描边高光透明度，越大描边越明显。取值范围为[0, 1]。设置为0时无描边；设置小于0的值时，按值为0处理；设置大于1的值时，按值为1处理。|
| color  | [Color](#color20) | 否   | 指定描边高光颜色，RGB各分量取值范围为[0, +∞)。当需要自定义描边高光颜色（如强调特定颜色效果）时传入此参数。不设置时，默认使用组件内容的原始颜色。设置了color参数时，Color中的alpha不发挥作用，仅使用rgb。|
| mask  | [Mask](#mask20) | 否   | 指定描边高光强度遮罩。可通过Mask类的创建方法（如[createRippleMask](#createripplemask20)、[createRadialGradientMask](#createradialgradientmask20)等）创建Mask实例。当需要控制描边高光效果的作用区域（如局部高光而非全局高光）时传入此参数。不设置时，默认组件内容全部有描边高光效果。|
| bloom  | boolean | 否   | 指定描边是否发光。当需要增强视觉效果时设置为true；当需要简洁描边效果时设置为false。不设置时默认为true（带发光效果）。小于16*16的图片默认只有描边效果，无发光效果，此参数失去作用。 |

**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [Filter](#filter) | 返回挂载了描边高光效果的Filter。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { uiEffect } from '@kit.ArkGraphics2D'

@Entry
@Component
struct EdgeLightExample {
  @State edgeLightColor: uiEffect.Color = {red: 0.0, green: 1.0, blue: 0.0, alpha: 1.0}
  
  @State edgeLightMask: uiEffect.Mask = uiEffect.Mask.createRippleMask({x: 0.5, y: 0.5}, 0.2, 0.5, 0.5)
  
  build() {
    Stack() {
      Image($rawfile('test.png'))
      Row()  
        .width("100%")
        .height("100%")
        // 为组件内容检测边缘，并添加边缘高亮效果
        .backgroundFilter(uiEffect.createFilter().edgeLight(1.0, this.edgeLightColor, this.edgeLightMask, false))
    }
  }
}
```

### displacementDistort<sup>20+</sup>
displacementDistort(displacementMap: Mask, factor?: [number, number]): Filter

为组件内容添加扭曲效果。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| displacementMap | [Mask](#mask20) | 是   | 置换贴图，用于控制扭曲的方向和强度。可通过Mask类的创建方法（如[createRippleMask](#createripplemask20)、[createPixelMapMask](#createpixelmapmask20)等）创建Mask实例。与factor相乘后共同决定扭曲程度。|
| factor  | [number, number] | 否   | 指定水平、竖直方向扭曲程度系数。当需要控制扭曲的方向和强度（如单向扭曲或差异扭曲）时传入此参数。系数的绝对值越大，扭曲程度越明显，建议取值范围为[-10.0, 10.0]。不设置时默认值为[1.0, 1.0]，表示水平和竖直方向均应用默认扭曲强度。设置为[0.0, 0.0]时，无扭曲效果。Mask的灰度值控制扭曲的方向和强度，factor与Mask灰度值相乘后共同决定最终的扭曲程度，即实际扭曲值 = Mask灰度值 × factor值。 |

**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [Filter](#filter) | 返回挂载了扭曲效果的Filter。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { uiEffect } from '@kit.ArkGraphics2D'

@Entry
@Component
struct DisplacementDistortExample {
  @State distortMask: uiEffect.Mask = uiEffect.Mask.createRippleMask({x: 0.5, y: 0.5}, 0.2, 0.3, 0.0)
  
  build() {
    Stack() {
      Image($rawfile('test.png'))
      Row()  
        .width("100%")
        .height("100%")
        // 为组件内容添加扭曲效果
        .backgroundFilter(uiEffect.createFilter().displacementDistort(this.distortMask, [5.0, 5.0]))
    }
  }
}
```

### maskDispersion<sup>20+</sup>
maskDispersion(dispersionMask: Mask, alpha: number, rFactor?: [number, number], gFactor?: [number, number], bFactor?: [number, number]): Filter

为组件内容添加由置换贴图控制的色散效果，模拟光线通过棱镜时的色散现象。典型应用场景包括炫彩特效、棱镜折射模拟等。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| dispersionMask  | [Mask](#mask20)         | 是   | 置换贴图，用于控制色散的强度、方向和透明度。建议使用PixelMapMask类型的置换贴图，可通过自定义图片纹理实现对色散区域和强度的精细控制。可通过[createPixelMapMask](#createpixelmapmask20)方法创建Mask实例。|
| alpha  | number         | 是   | 色散整体透明度，透明度越小效果越透明。取值范围为[0, 1.0]。透明度设置为0时色散效果不生效；透明度设置小于0的值时，按值为0处理；设置大于1.0的值时，按值为1.0处理。|
| rFactor  | [number, number]         | 否   | X/Y方向上R通道的色散基础偏移。当需要自定义红色通道的色散强度和方向时传入此参数，偏移越大红色色散效果越明显。不传入时默认值为[0.0, 0.0]，无R通道色散偏移。每个方向上的取值范围为[-1.0, 1.0]，超出范围自动截断。|
| gFactor  | [number, number]         | 否   | X/Y方向上G通道的色散基础偏移。当需要自定义绿色通道的色散强度和方向时传入此参数。不传入时默认值为[0.0, 0.0]，无G通道色散偏移。取值范围同rFactor，为[-1.0, 1.0]，超出范围自动截断。|
| bFactor  | [number, number]         | 否   | X/Y方向上B通道的色散基础偏移。当需要自定义蓝色通道的色散强度和方向时传入此参数。不传入时默认值为[0.0, 0.0]，无B通道色散偏移。取值范围同rFactor，为[-1.0, 1.0]，超出范围自动截断。|

**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [Filter](#filter) | 返回挂载了由置换贴图控制的色散效果的Filter。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import {image} from '@kit.ImageKit'
import {common2D, uiEffect} from '@kit.ArkGraphics2D'
import {common} from '@kit.AbilityKit'

@Entry
@Component
struct MaskDispersion {
  @State pixelMap: PixelMap | null = null
  @State src: common2D.Rect = { left: 0, top: 0, right: 1.0, bottom: 1.0 }
  @State dst: common2D.Rect = { left: 0, top: 0, right: 1.0, bottom: 1.0 }
  @State fillColor: uiEffect.Color = { red: 0, green: 0, blue: 0, alpha: 0 }

  onPageShow(): void {
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext
    context.resourceManager.getMediaByName("mask_alpha").then(val => {
      let buffer = val.buffer.slice(0, val.buffer.byteLength)
      let imageSource = image.createImageSource(buffer);
      imageSource.createPixelMap().then(pixelMap => {
        this.pixelMap = pixelMap
      })
    })
  }
  
  build() {
    if (this.pixelMap) {
      Stack() {
        Image($rawfile('test.png'))
        Row()  
          .width('100%')
          .height('100%')
          // 为组件内容添加由置换贴图控制的色散效果
          .backgroundFilter(uiEffect.createFilter().maskDispersion(
            uiEffect.Mask.createPixelMapMask(this.pixelMap!, this.src, this.dst, this.fillColor),
            1.0,
            [0.5, -0.5],
            [0.0, 0.0],
            [-0.5, 0.5]))
      }
    } else {
      Stack() {
        Image($rawfile('test.png'))
      }
    }
  }
}
```

### maskTransition<sup>20+</sup>
maskTransition(alphaMask: Mask, factor?: number, inverse?: boolean): Filter

为组件内容提供基于[Mask](#mask20)的转场效果，可用于页面切换动画、场景过渡效果等场景。

不建议在屏幕尺寸发生改变的过程中使用此效果，如：旋转屏幕，折叠屏开合屏幕等。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| alphaMask     | [Mask](#mask20)       | 是   | 通过遮罩指定转场效果的作用区域。可通过Mask类的创建方法（如[createRippleMask](#createripplemask20)、[createRadialGradientMask](#createradialgradientmask20)等）创建Mask实例。Mask的灰度值决定转场效果的作用程度，灰度值越大的区域转场效果越明显。|
| factor        | number                | 否   | 转场过渡系数。当需要控制转场进度（如动画中途或动态调整）时传入此参数，值越大画面越接近转场后页面。不设置时默认值为1.0（转场完成状态）。取值范围为[0.0, 1.0]，超出范围自动截断到[0.0, 1.0]。 |
| inverse       | boolean               | 否   | 是否启用反向转场。当需要反向转场效果（如从后页面向前页面过渡）时设置为true；当需要正向转场效果（从前页面向后页面过渡）时设置为false。默认值为false（正向转场）。 |

**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [Filter](#filter) | 返回挂载了转场效果的Filter。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { uiEffect, common2D } from "@kit.ArkGraphics2D";

@Entry
@Component
struct Index {
  context = this.getUIContext()
  @State alpha: number = 0
  @State enterNewPage:boolean = false
  @State rippleMaskCenter: common2D.Point = {x:0.5, y:0.5}
  @State rippleMaskRadius: number = 0.1
  build() {
    Stack() {
      // 转场前页面
      Image($r("app.media.before")).width("100%").height("100%")
        if (this.enterNewPage) {
          // 转场后页面
          Column().width("100%").height("100%").backgroundImage($r("app.media.after"))
            // 为组件内容提供基于Mask的转场效果
            .backgroundFilter(uiEffect.createFilter()
              .maskTransition(
                uiEffect.Mask.createRadialGradientMask(this.rippleMaskCenter, this.rippleMaskRadius,this.rippleMaskRadius, [[1, 0], [1, 1]]),
                this.alpha))
            .onAppear(() => {
              this.context.animateTo({ duration: 1000 }, () => {
                this.rippleMaskRadius = 1.3
              })
              this.context.animateTo({ duration: 800 }, () => {
                this.alpha = 1
              })
            })
        }
    }.borderWidth(2)
    .onClick(()=>{
      this.enterNewPage=!this.enterNewPage;
      if (this.enterNewPage) {
        this.alpha=0;
        this.rippleMaskRadius=0.1;
      }
    })
  }
}
```

### directionLight<sup>20+</sup>
directionLight(direction: common2D.Point3d, color: Color, intensity: number, mask?: Mask, factor?: number): Filter

为组件内容提供基于[Mask](#mask20)和平行光的光照效果。平行光从统一方向照射组件平面，所有光线方向一致，不因距离衰减，光照强度在组件各处均匀分布，适合模拟太阳光等远距离光源场景。与contentLight的点光源不同，平行光无需指定光源具体位置。通过Mask可控制光照细节，通过factor可结合高度图增强浮雕效果。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| direction  | [common2D.Point3d](js-apis-graphics-common2D.md#point3d12)         | 是   | 入射光的方向，通过三维坐标表示光线的入射方向。|
| color  | [Color](#color20)         | 是   | 光照颜色。|
| intensity  | number         | 是   | 光照强度，取值范围为[0, +∞)，数值越大光源亮度越大。|
| mask  | [Mask](#mask20)         | 否   | 置换贴图，用于描述二维图像表面的三维细节。可通过Mask类的创建方法（如[createRippleMask](#createripplemask20)、[createRadialGradientMask](#createradialgradientmask20)等）创建Mask实例。当需要增强局部细节和光照反射效果（如浮雕、凹凸纹理）时传入此参数。通过法线或高度图实现，若输入为高度图需与factor参数配合使用。不设置时默认为空，表现为全局无细节的平面光照效果。|
| factor  | number         | 否   | 采样缩放系数。当使用高度图作为mask且需要控制高度缩放时传入此参数。不设置时mask作为法线图采样直接使用；设置了值时mask作为高度图采样，实际高度值为mask采样值与factor的乘积。|

**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [Filter](#filter) | 返回挂载了由置换贴图控制的光照效果的Filter。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { uiEffect, common2D } from "@kit.ArkGraphics2D";

@Entry
@Component
struct Index {
  @State rippleMaskCenter: common2D.Point = {x:0.5, y:0.5}
  @State rippleMaskRadius: number = 0.0
  @State rippleMaskWidth: number = 0.0
  @State color: Color = Color.Transparent

  build() {
    Column() {
      RelativeContainer() {
        Image($r("app.media.back")).width("100%").height("100%")
        Stack()
          .width("100%")
          .height("100%")
          .backgroundColor(this.color)
          // 为组件内容提供基于Mask和平行光的光照效果
          .backgroundFilter(uiEffect.createFilter()
            .directionLight(
              {x:0, y:0, z:-1}, {red:2.0, green:2.0, blue:2.0, alpha:1.0}, 0.5,
              uiEffect.Mask.createRippleMask(this.rippleMaskCenter, this.rippleMaskRadius, this.rippleMaskWidth, 0.0)
              ))
          .onClick(() => {
            this.getUIContext().animateTo({duration: 1000}, () => {
              this.rippleMaskWidth = 1.0;
            })
          })
      }
    }.alignItems(HorizontalAlign.Center).borderWidth(2)
  }
}
```

### variableRadiusBlur<sup>20+</sup>
variableRadiusBlur(radius: number, radiusMap: Mask): Filter

为组件内容提供基于[Mask](#mask20)的渐变模糊效果。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| radius  | number         | 是   | 最大模糊半径，单位为px，该值越大越模糊。取值范围为[0, 128]。模糊半径设置为0时不模糊；模糊半径设置小于0的值时，按值为0处理；设置大于128的值时，按值为128处理。|
| radiusMap  |  [Mask](#mask20)    | 是   | 代表模糊程度的Mask对象。Mask的灰度值代表对应位置的模糊程度，灰度值越大越模糊。|

**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [Filter](#filter) | 返回当前效果的Filter对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct VariableRadiusBlurExample {
  @State blurMask: uiEffect.Mask = uiEffect.Mask.createRippleMask({x: 0.5, y: 0.5}, 0.2, 0.1)

  build() {
    Stack() {
      Image($rawfile('test.png'))
      Row()
        .width('100%')
        .height('100%')
        // 为组件内容提供基于Mask的渐变模糊效果
        .backgroundFilter(uiEffect.createFilter().variableRadiusBlur(64, this.blurMask))
    }
  }
}
```

### heatDistortion

heatDistortion(param: HeatDistortionEffectParam): Filter

应用热浪扭曲效果到图像，模拟热空气流动产生的视觉扭曲效果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| param | [HeatDistortionEffectParam](#heatdistortioneffectparam) | 是 | 热浪扭曲效果的参数。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| [Filter](#filter) | 返回添加了热浪扭曲效果的Filter。 |

**示例：**

```ts
import { uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct HeatDistortionExample {
  @State intensity: number = 0.8;
  @State noiseScale: number = 2.0;
  @State riseWeight: number = 0.5;
  @State progress: number = 0.3;

  build() {
    Stack() {
      Image($r('app.media.test'))
        .width('100%')
        .height('100%')
        // 应用热浪扭曲效果到图像，模拟热空气流动产生的视觉扭曲
        .foregroundFilter(uiEffect.createFilter().heatDistortion({
          intensity: this.intensity,
          noiseScale: this.noiseScale,
          riseWeight: this.riseWeight,
          progress: this.progress
        }))
    }
    .width('100%')
    .height('100%')
  }
}
```

### blurBubblesRise

blurBubblesRise(param: BlurBubblesRiseEffectParam): Filter

应用模糊气泡上升效果到图像，模拟气泡在液体中上升的梦幻模糊扭曲效果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| param | [BlurBubblesRiseEffectParam](#blurbubblesriseeffectparam) | 是 | 模糊气泡上升效果的参数。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| [Filter](#filter) | 返回添加了模糊气泡上升效果的Filter。 |

**示例：**

```ts
import { uiEffect } from '@kit.ArkGraphics2D';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct BlurBubblesRiseExample {
  private context: Context | undefined = this.getUIContext().getHostContext();
  @State blurIntensity: number = 0.8;
  @State mixStrength: number = 0.6;
  @State progress: number = 0.5;
  @State maskImage: image.PixelMap | null = null;

  aboutToAppear() {
    if (this.context) {
      this.getImagePixelMap(this.context)
    }
  }

  getImagePixelMap(context: Context) {
    let resourceMgr = context.resourceManager;
    resourceMgr?.getMediaContent($r('app.media.drawBlurMask').id)
      .then((val: Uint8Array) => {
        let buffer: ArrayBuffer = val.buffer.slice(0, val.buffer.byteLength)
        let imageSource: image.ImageSource = image.createImageSource(buffer);
        imageSource.createPixelMap().then((pixelmap: image.PixelMap) => {
          this.maskImage = pixelmap as PixelMap;
        })
      })
  }

  build() {
    Stack() {
      Image($r('app.media.test'))
        .width('100%')
        .height('100%')
        // 应用模糊气泡上升效果到图像，模拟气泡在液体中上升的梦幻模糊扭曲效果
        .foregroundFilter(uiEffect.createFilter().blurBubblesRise({
          blurIntensity: this.blurIntensity,
          mixStrength: this.mixStrength,
          progress: this.progress,
          maskImage: this.maskImage
        }))
    }
    .width('100%')
    .height('100%')
  }
}
```

## TileMode
像素填充模式枚举。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

| 名称   | 值 | 说明 |
| ------ | - | ---- |
| CLAMP  | 0 | 截断。 |
| REPEAT | 1 | 重复。 |
| MIRROR | 2 | 镜像。 |
| DECAL  | 3 | 透明。 |

## WaterRippleMode
水波纹场景模式枚举。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

| 名称   | 值 | 说明 |
| ------ | - | ---- |
| SMALL2MEDIUM_RECV  | 0 | 手机碰2in1设备（接收端）。 |
| SMALL2MEDIUM_SEND  | 1 | 手机碰2in1设备（发送端）。 |
| SMALL2SMALL | 2 | 手机碰手机。 |
| MINI_RECV<sup>17+</sup> | 3 | 2in1设备与其它设备共享（键鼠共享场景）。 |

## FlyMode
飞入飞出形变场景模式枚举。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

| 名称   | 值 | 说明 |
| ------ | - | ---- |
| BOTTOM  | 0 | 从底部进行飞入飞出形变。 |
| TOP  | 1 | 从顶部进行飞入飞出形变。 |

## VisualEffect
VisualEffect效果类，用于将背景颜色混合、边框光照、颜色渐变等效果添加到组件上。在调用VisualEffect的方法前，需要先通过[createEffect](js-apis-uiEffect.md#uieffectcreateeffect)创建一个VisualEffect实例。

### backgroundColorBlender
backgroundColorBlender(blender: BrightnessBlender): VisualEffect

用于改变组件背景颜色的blender，目前仅支持提亮混合器。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名  | 类型                                      | 必填 | 说明                       |
| ------- | ---------------------------------------- | ---- | ------------------------- |
| blender | [BrightnessBlender](#brightnessblender) | 是   | 用于混合背景颜色的blender。 |

**返回值：**

| 类型                          | 说明                                               |
| ----------------------------- | ------------------------------------------------- |
| [VisualEffect](#visualeffect) | 返回添加了背景颜色更改效果的VisualEffect。 |

**示例：**

```ts
import { uiEffect } from '@kit.ArkGraphics2D'
let blender : uiEffect.BrightnessBlender =
  uiEffect.createBrightnessBlender({cubicRate:1.0, quadraticRate:1.0, linearRate:1.0, degree:1.0, saturation:1.0,
    positiveCoefficient:[2.3, 4.5, 2.0], negativeCoefficient:[0.5, 2.0, 0.5], fraction:0.0})
let visualEffect = uiEffect.createEffect();
// 将混合器添加至组件上以改变组件背景颜色
visualEffect.backgroundColorBlender(blender)
```

### borderLight<sup>20+</sup>
borderLight(lightPosition: common2D.Point3d, lightColor: common2D.Color, lightIntensity: number, borderWidth: number): VisualEffect

为圆角矩形组件边框添加3D光照效果。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| lightPosition | [common2D.Point3d](js-apis-graphics-common2D.md#point3d12) | 是 | 光源在组件空间的3D位置，[-1, -1, 0]为组件左上角，[1, 1, 0]为组件的右下角，z轴分量越大，光源离组件平面越远，可照射区域越大。<br> x轴分量取值范围为[-10, 10]，y轴分量取值范围为[-10, 10]，z轴分量取值范围为[0, 10]，超出范围会自动截断。 |
| lightColor | [common2D.Color](js-apis-graphics-common2D.md#color) | 是 | 光源颜色，各元素取值范围为[0, 1]，超出范围会自动截断。 |
| lightIntensity | number | 是 | 光源强度，取值范围为[0, 1]，数值越大光源亮度越大，超出范围会自动截断。|
| borderWidth | number | 是 | 组件边框的受光宽度，取值范围为[0.0, 30.0]，超出范围会自动截断。设置为0.0时，组件边框无光照效果，数值越大，光可照亮的区域越宽。 |

**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [VisualEffect](#visualeffect) | 返回了具有边框光照效果的VisualEffect。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**
```ts
import { common2D, uiEffect } from '@kit.ArkGraphics2D'

@Entry
@Component
struct Index {
  @State borderLightPosition: common2D.Point3d = {
    x: 0, y: 0, z: 2
  }
  @State borderLightColor: common2D.Color = {
    red: 1, green: 1, blue: 1, alpha: 1
  }
  @State lightIntensity: number = 1
  @State borderWidth_: number = 20

  build() {
    Column() {
      Stack() {
        Image($r('app.media.man'))
          .width('646px')
          .height('900px')
          .borderRadius(10)
        Column()
          .width('646px')
          .height('900px')
          .borderRadius(10)
          // 为圆角矩形组件边框添加3D光照效果
          .visualEffect(uiEffect.createEffect().borderLight(this.borderLightPosition, this.borderLightColor, this.lightIntensity,
            this.borderWidth_))
      }
      .width('100%')
      .height('55%')
    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .backgroundColor('#555')
  }
}
```

### colorGradient<sup>20+</sup>
colorGradient(colors: Array\<Color>, positions: Array\<common2D.Point>, strengths: Array\<number>, alphaMask?: Mask): VisualEffect

此方法为组件添加颜色渐变效果。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| colors  | Array\<[Color](#color20)>         | 是   | 颜色数组，用于实现多颜色渐变。数组长度范围为0到12，每个颜色值取值范围需大于等于0，无上限限制。数组长度为0或大于12，或colors、positions和strengths的数组长度不一致，则无颜色渐变效果。|
| positions  | Array\<[common2D.Point](js-apis-graphics-common2D.md#point12)>         | 是   | 位置数组，颜色对应的位置。数组长度范围为0到12。数组长度为0或大于12，或colors、positions和strengths的数组长度不一致，则无颜色渐变效果。|
| strengths  | Array\<number>         | 是   | 强度数组，表示颜色对应的强度。数组长度范围为0到12，每一个强度值需大于等于0，无上限限制。数组长度为0或大于12，或colors、positions和strengths的数组长度不一致时，则无颜色渐变效果。|
| alphaMask  | [Mask](#mask20)         | 否   | 遮罩alpha，颜色对应的alpha遮罩。可通过Mask类的创建方法（如[createRippleMask](#createripplemask20)、[createRadialGradientMask](#createradialgradientmask20)等）创建Mask实例。当需要控制颜色渐变效果的透明度分布（如局部透明或动态透明效果）时传入此参数。不设置时，颜色渐变效果的透明度完全由colors参数决定。|

**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [VisualEffect](#visualeffect) | 返回具有颜色渐变效果的VisualEffect。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**
```ts
import { common2D, uiEffect } from '@kit.ArkGraphics2D'

@Entry
@Component
struct ColorGradientExample {
  build() {
    Stack() {
      Stack() {}
      // 此方法为组件添加颜色渐变效果
      .visualEffect(uiEffect.createEffect()
        .colorGradient(
          [
            {red: 1.0, green: 0.0, blue: 0.0, alpha: 1.0},
            {red: 0.0, green: 1.0, blue: 0.0, alpha: 1.0},
            {red: 0.0, green: 0.0, blue: 1.0, alpha: 1.0},
            {red: 1.0, green: 1.0, blue: 1.0, alpha: 1.0},
          ],
          [
            {x: 0.1, y: 0.1},
            {x: 0.1, y: 0.9},
            {x: 0.9, y: 0.1},
            {x: 0.9, y: 0.9},
          ],
          [12.4, 7.8, 7.8, 10.0],
          uiEffect.Mask.createRippleMask({x: 0.5, y: 0.5}, 0.2, 0.1)
        )
      )
      .width("1024px")
      .height("1024px")
    }
    .width("100%")
    .height("100%")
  }
}
```

### liquidMaterial<sup>22+</sup>

liquidMaterial(param: LiquidMaterialEffectParam, useEffectMask: Mask, distortMask?: Mask, brightnessParam?: BrightnessParam): VisualEffect

此方法为组件添加材质效果。材质效果通过模拟物理材质的光学特性（折射、反射）和动态扰动效果，实现玻璃、金属等材质的视觉呈现。可用于模拟玻璃质感UI、流体材质动画、磨砂玻璃效果等场景。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名          | 类型                                                      | 必填 | 说明                                                         |
| --------------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| param           | [LiquidMaterialEffectParam](#liquidmaterialeffectparam22) | 是   | 材质所需相关变量，用于控制材质显示，包含材质开关、折射系数、反射系数和扰动系数。 |
| useEffectMask   | [Mask](#mask20)                                           | 是   | 声明是否使用模糊缓存。使用createUseEffectMask(true)创建的Mask实例使用模糊缓存，适用于需要复用模糊结果的场景以提升性能；使用createUseEffectMask(false)创建的Mask实例不使用模糊缓存，适用于模糊效果频繁变化的场景。 |
| distortMask     | [Mask](#mask20)                                           | 否   | 材质扰动效果需要的扰动纹理，由pixelMap创建的Mask实例的图片纹理决定扰动效果的图案和方向。可通过[createPixelMapMask](#createpixelmapmask20)方法创建Mask实例。当材质的扰动系数（distortFactor）不为0时，需要设置此参数否则无扰动效果；当材质的扰动系数为0或此参数不设置时，无扰动效果。默认不设置。 |
| brightnessParam | [BrightnessParam](#brightnessparam22)                     | 否   | 为材质增加提亮效果。当需要增强材质的视觉亮度（如高亮显示、发光效果）时传入此参数。不设置时默认不添加提亮效果，材质保持原始亮度。                     |

**返回值：**

| 类型                          | 说明                             |
| ----------------------------- | -------------------------------- |
| [VisualEffect](#visualeffect) | 返回具有材质效果的VisualEffect。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API. |

**示例：**
```ts
import { uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct Index {
  @State distortProgress: number = 0.;
  @State rippleProgress: number = 0.;
  @State distortFactor: number = 0.;
  @State materialFactor: number = 1.;
  @State refractionFactor: number = 1.;
  @State reflectionFactor: number = 1.;
  @State tintColorR: number = 1.;
  @State tintColorG: number = 1.;
  @State tintColorB: number = 1.;
  @State tintColorA: number = 1.;

  private getMaterialVisualEffect(): uiEffect.VisualEffect {
    let effect: uiEffect.VisualEffect = uiEffect.createEffect();
    effect.liquidMaterial({
      enable: true,
      distortProgress : this.distortProgress,
      rippleProgress: this.rippleProgress,
      distortFactor: this.distortFactor,
      materialFactor : this.materialFactor,
      refractionFactor : this.refractionFactor,
      reflectionFactor: this.reflectionFactor,
      tintColor : [this.tintColorR, this.tintColorG, this.tintColorB, this.tintColorA],
      ripplePosition: undefined,
    },
      uiEffect.Mask.createUseEffectMask(true),
      );
    return effect;
  }

  build() {
    Stack() {
      EffectComponent() {
        Column()
          .position({ x: 200 + 'px', y: 200 + 'px' })
          .height(553 + 'px')
          .width(553 + 'px')
          .borderRadius(12)
          .visualEffect(this.getMaterialVisualEffect())
      }
      .backgroundEffect({
        radius: 15,
      }, { disableSystemAdaptation: true })
      .width("100%").height("100%").align(Alignment.Center)
    }
    .backgroundImage($r('app.media.bg6'), ImageRepeat.NoRepeat)
    .width("100%").height("100%").align(Alignment.Center)
  }
}
```

### distortionCollapse

distortionCollapse(distortionParam: DistortionParam): VisualEffect

为组件添加非线性形变效果。典型应用场景包括页面坍塌动画、窗口关闭特效、卡片翻转动画、场景过渡效果等。

> **说明：**
>
> - 该视效支持控件范围外的绘制，但仍会受到父控件Clip的影响。
> - 因包含前景Filter，未与[EffectComponent](../apis-arkui/arkui-ts/ts-container-effectcomponent-sys.md)组合使用时不兼容组件自身及子组件的部分视效（如[BrightnessBlender](#brightnessblender)或[systemMaterial](../apis-arkui/arkui-ts/ts-universal-attributes-image-effect-sys.md#systemmaterial23)）。
> - 支持对系统材质进行扭曲，但是与[EffectComponent](../apis-arkui/arkui-ts/ts-container-effectcomponent-sys.md)组合使用时，会导致系统材质的背景扭曲。
> - 调用该接口时，会创建与形变后区域等大的离屏画布，再将当前组件（含子组件）的内容绘制到离屏画布上，再对画布上绘制的组件内容进行形变绘制。使用该实现方式时，如果不与[EffectComponent](../apis-arkui/arkui-ts/ts-container-effectcomponent-sys.md)组合使用，将导致[systemMaterial](../apis-arkui/arkui-ts/ts-universal-attributes-image-effect-sys.md#systemmaterial23)、[backgroundEffect](../apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundeffect19)、[brightness](../apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#brightness)或[blur](../apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#blur19)等需要截屏的接口无法截取到正确的画面。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**
| 参数名          | 类型                                | 必填 | 说明                   |
| --------------- | ----------------------------------- | ---- | --------------------- |
| distortionParam | [DistortionParam](../apis-arkui/arkui-ts/ts-container-distortioncomponent-sys.md#distortionparam) | 是   | 非线性形变效果的参数。设置为undefined或null时恢复为无非线性形变的效果。 |

**返回值：**

| 类型                          | 说明                                     |
| ----------------------------- | ---------------------------------------- |
| [VisualEffect](#visualeffect) | 返回添加了非线性形变效果的VisualEffect。 |

**示例：**

```ts
import { uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct Index {
  private distortionParam: DistortionParam = {
    topLeft: {x: 0.09, y: 0.007},
    topRight: {x: 0.91, y: 0.007},
    bottomRight: {x: 1.09, y: 0.702},
    bottomLeft: {x: -0.09, y: 0.702},
    barrelDistortion: {x: 0.551, y: 0.551, z: 0.092, w: 0.092},
  }

  build() {
    Column() {
      Image($r('app.media.man')).width('80%').height('80%')
        .visualEffect(uiEffect.createEffect().distortionCollapse(this.distortionParam))
    }
    .justifyContent(FlexAlign.Center)
    .height('100%')
    .width('100%')
  }
}
```

## Blender<sup>13+</sup>

type Blender = BrightnessBlender | HdrBrightnessBlender | HdrDarkenBlender

混合器类型，用于描述混合效果。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

| 类型                          | 说明                                               |
| ----------------------------- | ------------------------------------------------- |
| [BrightnessBlender](#brightnessblender) | 具有提亮效果的混合器。 |
| [HdrBrightnessBlender](#hdrbrightnessblender20)<sup>20+</sup> | 具有提亮效果的混合器（支持HDR）。 |
| [HdrDarkenBlender](#hdrdarkenblender) | 具有压暗效果的混合器（支持HDR）。<br> **起始版本：** 26.0.0 |

## BrightnessBlender
提亮混合器，用于将提亮效果添加到指定的组件上。在调用BrightnessBlender前，需要先通过[createBrightnessBlender](#uieffectcreatebrightnessblender)创建一个BrightnessBlender实例。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

| 名称                | 类型                        | 只读 | 可选 | 说明                                                              |
| ------------------- | -------------------------- | ---- | ---- | ---------------------------------------------------------------- |
| cubicRate           | number                     | 否   | 否   | 灰度调整的三阶系数。<br>取值范围为[-20, 20]，超出边界会在实现时自动截断。                        |
| quadraticRate       | number                     | 否   | 否   | 灰度调整的二阶系数。<br>取值范围为[-20, 20]，超出边界会在实现时自动截断。                        |
| linearRate          | number                     | 否   | 否   | 灰度调整的线性系数。<br>取值范围为[-20, 20]，超出边界会在实现时自动截断。                        |
| degree              | number                     | 否   | 否   | 灰度调整的比例。<br>取值范围为[-20, 20]，超出边界会在实现时自动截断。                            |
| saturation          | number                     | 否   | 否   | 提亮的基准饱和度。<br>取值范围为[0, 20]，超出边界会在实现时自动截断。                            |
| positiveCoefficient | [number, number, number]   | 否   | 否   | 基于基准饱和度的RGB正向调整参数。<br>每个number的取值范围为[-20, 20]，超出边界会在实现时自动截断。 |
| negativeCoefficient | [number, number, number]   | 否   | 否   | 基于基准饱和度的RGB负向调整参数。<br>每个number的取值范围为[-20, 20]，超出边界会在实现时自动截断。 |
| fraction            | number                     | 否   | 否   | 提亮效果的混合比例。<br>取值范围为[0, 1]，超出边界会在实现时自动截断。  |

## HdrBrightnessBlender<sup>20+</sup>
支持HDR的提亮混合器（继承自[BrightnessBlender](#brightnessblender)），用于将提亮效果添加到指定的组件上。在调用HdrBrightnessBlender前，需要先通过[createHdrBrightnessBlender](#uieffectcreatehdrbrightnessblender20)创建一个HdrBrightnessBlender实例。

该混合器参数可参考[BrightnessBlender](#brightnessblender)。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## HdrDarkenBlender

支持HDR的压暗混合器，用于将压暗效果添加到指定的组件上。在调用HdrDarkenBlender前，需要先通过[createHdrDarkenBlender](#uieffectcreatehdrdarkenblender)创建一个HdrDarkenBlender实例。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

| 名称  | 类型   | 只读 | 可选 | 说明                                     |
| ----- | ------ | ---- | ---- | ---------------------------------------- |
| hdrBrightnessRatio   | number | 否   | 否   | HDR的提亮倍数。<br>取值范围为[1.0, 设备当前支持最大提亮倍数]。<br>设置小于1.0的值时，按值为1.0处理；<br>当值等于1.0时，为组件原本亮度；<br>设置大于设备当前支持最大提亮倍数的值时，按值为设备当前支持最大提亮倍数处理，支持最大提亮倍数 = 设备最大亮度 / 设备默认亮度。<br>设备最大亮度通过hdc命令获取：hdc shell param get const.display.brightness.max <br>设备默认亮度通过hdc命令获取：hdc shell param get const.display.brightness.default |
| grayscaleFactor | [number, number, number] | 否   | 是   | 将RGB颜色转换为灰度值。灰度转换公式的权重可随当前色域自动调整，不同色域下使用不同的权重计算方式；适用于sRGB等标准色域场景。当需要根据特定色域或视觉效果自定义灰度转换权重时传入此参数。三个分量均无边界限制。默认值为标准灰度权重[0.299, 0.587, 0.114]。 |


## Color<sup>20+</sup>

RGBA格式的颜色描述。

**系统能力：** SystemCapability.Graphics.Drawing

| 名称  | 类型   | 只读 | 可选 | 说明                                     |
| ----- | ------ | ---- | ---- | ---------------------------------------- |
| red   | number | 是   | 是   | 颜色的R分量（红色）。 |
| green | number | 是   | 是   | 颜色的G分量（绿色）。|
| blue  | number | 是   | 是   | 颜色的B分量（蓝色）。 |
| alpha | number | 是   | 是   | 颜色的A分量（透明度）。 |

## LiquidMaterialEffectParam<sup>22+</sup>

材质效果参数，用于控制材质的折射、反射、扰动和叠加颜色等显示属性。

**系统能力：** SystemCapability.Graphics.Drawing

| 名称             | 类型                             | 只读 | 可选 | 说明                                                         |
| ---------------- | -------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| enable           | boolean                          | 否   | 否   | 是否开启材质效果。true表示开启，false表示关闭。 |
| distortProgress  | number                           | 否   | 否   | 扰动效果进度。取值范围为[0, 1]，小于0时取值为0，大于1时取值为1。0表示开始扰动，1表示结束扰动。 |
| distortFactor    | number                           | 否   | 否   | 扰动效果系数。值大于等于0，值小于0时表示无扰动效果。         |
| rippleProgress   | number                           | 否   | 否   | 水波效果进度。值大于等于0，值小于0时表示无水波效果。         |
| ripplePosition   | Array<[number, number]>          | 否   | 是   | 水波效果作用的位置。当需要在多个指定位置同时触发水波效果时传入此参数。不传入时默认无水波位置，水波效果不生效。数组中每个位置包含x和y两个维度，坐标为归一化坐标，[0, 0]表示左上角，[1, 1]表示右下角。最多支持10个位置坐标，超出则整体无效。 |
| refractionFactor | number                           | 否   | 否   | 折射效果系数。取值范围为[0, 10]，小于0时取值为0，大于10时取值为10。值为0表示无折射效果，值越大折射强度越高。 |
| reflectionFactor | number                           | 否   | 否   | 反射系数。取值范围为[0, 10]，小于0时取值为0，大于10时取值为10。值为0表示无反射效果，值越大反射强度越高。 |
| materialFactor   | number                           | 否   | 否   | 材质系数。取值范围为[0, 1]，小于0时取值为0，大于1时取值为1。值为0表示无材质效果，使用叠加颜色填充，值越大材质效果越明显。 |
| tintColor        | [number, number, number, number] | 否   | 否   | 材质叠加的颜色，四个变量分别对应RGBA。取值范围为[0, 1]，小于0时取值为0，大于1时取值为1。 |

## BrightnessParam<sup>22+</sup>

材质提亮参数的详细说明。

**系统能力：** SystemCapability.Graphics.Drawing

| 名称          | 类型                     | 只读 | 可选 | 说明                                                         |
| ------------- | ------------------------ | ---- | ---- | ------------------------------------------------------------ |
| rate          | number                   | 否   | 否   | 灰度调整线性系数。取值范围为[-1, 1]，小于-1时取值为-1，大于1时取值为1，值越大，灰度调整效果越强。 |
| lightUpDegree | number                   | 否   | 否   | 灰度调整比例。取值范围为[-1, 1]，小于-1时取值为-1，大于1时取值为1，值越大，灰度调整效果越强。 |
| cubicCoeff    | number                   | 否   | 否   | 灰度调整三阶系数。取值范围为[-1, 1]，小于-1时取值为-1，大于1时取值为1，值越大，灰度调整效果越强。 |
| quadCoeff     | number                   | 否   | 否   | 灰度调整二阶系数。取值范围为[-1, 1]，小于-1时取值为-1，大于1时取值为1，值越大，灰度调整效果越强。 |
| saturation    | number                   | 否   | 否   | 提亮基准饱和度。取值范围为[0, 1]，小于0时取值为0，大于1时取值为1，值越大基准饱和度越高。 |
| posRgb        | [number, number, number] | 否   | 否   | 基于基准饱和度的正向调整系数。取值范围为[-1, 1]，小于-1时取值为-1，大于1时取值为1，值越大饱和度越高。 |
| negRgb        | [number, number, number] | 否   | 否   | 基于基准饱和度的负向调整系数。取值范围为[-1, 1]，小于-1时取值为-1，大于1时取值为1，值越大饱和度越低。 |
| fraction      | number                   | 否   | 否   | 提亮效果混合比例。取值范围为[0, 1]，小于0时取值为0，大于1时取值为1，值越大，提亮效果越弱。 |


## Mask<sup>20+</sup>
Mask效果类，作为[Filter](#filter)以及[VisualEffect](#visualeffect)的输入使用。不同类型的Mask提供不同的灰度分布模式，如波环遮罩、径向渐变、像素图遮罩等。

### createRippleMask<sup>20+</sup>
static createRippleMask(center: common2D.Point, radius: number, width: number, offset?: number): Mask

通过输入波环圆心的位置、半径和宽度创建波环遮罩效果Mask实例。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名  | 类型                                      | 必填 | 说明                       |
| ------- | ---------------------------------------- | ---- | ------------------------- |
| center | [common2D.Point](js-apis-graphics-common2D.md#point12) | 是 | 设置波环圆心在组件上的位置，[0, 0]为组件左上角，[1, 1]为组件的右下角。<br>取值范围为[-10, 10]，超出边界会在实现时自动截断。 |
| radius | number | 是 | 设置波环的半径，使用归一化值。半径为1时，波环半径等于组件高度。<br>取值范围为[0, 10]，超出边界会在实现时自动截断。 |
| width | number | 是 | 设置波环的宽度，使用归一化值。宽度为1时，波环宽度等于组件高度。。<br>取值范围为[0, 10]，超出边界会在实现时自动截断。 |
| offset | number | 否 | 设置波峰位置的偏移。<br>默认值为0，表示波峰在波环的正中心；<br>-1.0表示波峰在波环的最内侧；<br>1.0表示波峰在波环的最外侧。<br>取值范围为[-1, 1]，超出边界会在实现时自动截断。 |

**返回值：**

| 类型                          | 说明                                               |
| ----------------------------- | ------------------------------------------------- |
| [Mask](#mask20) | 返回具有波环遮罩效果的Mask。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
  let mask = uiEffect.Mask.createRippleMask({x: 0.5, y: 1.0}, 0.5, 0.3, 0.0);
```

### createPixelMapMask<sup>20+</sup>
static createPixelMapMask(pixelMap: image.PixelMap, srcRect: common2D.Rect, dstRect: common2D.Rect, fillColor?: Color): Mask

通过输入的[pixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)，以及pixelMap的待绘制区域、挂载节点的绘制区域和绘制区域外填充的颜色创建具有缩放效果的Mask实例。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名  | 类型                                      | 必填 | 说明                       |
| ------- | ---------------------------------------- | ---- | ------------------------- |
| pixelMap | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | 是   | image模块创建的PixelMap实例。可通过图片解码或直接创建获得，具体可见[图片开发指导](../../media/image/image-overview.md)。   |
| srcRect | [common2D.Rect](js-apis-graphics-common2D.md#rect) | 是   | pixelMap的待绘制区域。图片最左侧和最上侧对应位置0，最右侧和最下侧对应位置1。right需大于left，bottom需大于top，违反约束时效果不生效。 |
| dstRect | [common2D.Rect](js-apis-graphics-common2D.md#rect) | 是   | pixelMap在mask挂载的节点上的绘制区域。节点最左侧和最上侧对应位置0，最右侧和最下侧对应位置1。right需大于left，bottom需大于top，违反约束时效果不生效。 |
| fillColor | [Color](#color20) | 否   |  节点上在pixelMap绘制区域之外的区域填充的颜色，各元素取值范围为[0, 1]，默认透明色，小于0的转为0，大于1的转为1。 |

**返回值：**

| 类型                          | 说明                                               |
| ----------------------------- | ------------------------------------------------- |
| [Mask](#mask20) | 返回基于pixelMap创建的Mask实例。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { image } from '@kit.ImageKit';
import { uiEffect, common2D } from '@kit.ArkGraphics2D';
import { BusinessError } from '@kit.BasicServicesKit'

const colorBuffer = new ArrayBuffer(96);
let opts : image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
}
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  let srcRect : common2D.Rect = {
    left: 0,
    top: 0,
    right: 1,
    bottom: 1
  }
  let dstRect : common2D.Rect = {
    left: 0,
    top: 0,
    right: 1,
    bottom: 1
  }
  let fillColor : uiEffect.Color = {
    red: 0,
    green: 0,
    blue: 0,
    alpha: 1
  }
  let mask = uiEffect.Mask.createPixelMapMask(pixelMap, srcRect, dstRect, fillColor);
}).catch((error: BusinessError)=>{
  console.error(`Failed to create pixelmap. code is ${error.code}, message is ${error.message}`);
})
```

### createPixelMapMask<sup>22+</sup>

static createPixelMapMask(pixelMap: image.PixelMap): Mask

通过输入的pixelMap创建[Mask](#mask20)实例。该接口不会对传入的pixelMap进行缩放处理。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| pixelMap | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | 是   | image模块创建的PixelMap实例。可通过图片解码或直接创建获得，具体可见[图片开发指导](../../media/image/image-overview.md)。 |

**返回值：**

| 类型            | 说明                     |
| --------------- | ------------------------ |
| [Mask](#mask20) | 返回具有pixelMap的Mask。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { uiEffect } from '@kit.ArkGraphics2D';
import { image } from '@kit.ImageKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State distortProgress: number = 0.;
  @State rippleProgress: number = 0.;
  @State distortFactor: number = 0.;
  @State materialFactor: number = 1.;
  @State refractionFactor: number = 1.;
  @State reflectionFactor: number = 1.;
  @State tintColorR: number = 1.;
  @State tintColorG: number = 1.;
  @State tintColorB: number = 1.;
  @State tintColorA: number = 1.;
  @State pixelMapDistort: image.PixelMap | undefined = undefined;

  aboutToAppear(): void {
    this.pixelMapDistort = this.getPixelMap();
  }

  private getPixelMap(): image.PixelMap | undefined {
    try {
      let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      // this path should be created in local
      const path: string = context.resourceDir + "/perlin_worley_noise_3d_64.bmp";
      const imageSource: image.ImageSource = image.createImageSource(path);
      if (!imageSource) {
        return undefined;
      }
      const pixelMap: image.PixelMap | null = imageSource.createPixelMapSync();
      if (!pixelMap) {
        imageSource.release();
        return undefined;
      }
      imageSource.release();
      return pixelMap;
    } catch (err) {
      return undefined;
    }
  }

  private getMaterialVisualEffect(): uiEffect.VisualEffect {
    let effect: uiEffect.VisualEffect = uiEffect.createEffect();
    let distortMask: uiEffect.Mask | undefined = undefined;
    if (this.pixelMapDistort) {
      distortMask = uiEffect.Mask.createPixelMapMask(this.pixelMapDistort);
    }
    effect.liquidMaterial({
      enable: true,
      distortProgress : this.distortProgress,
      rippleProgress: this.rippleProgress,
      distortFactor: this.distortFactor,
      materialFactor : this.materialFactor,
      refractionFactor : this.refractionFactor,
      reflectionFactor: this.reflectionFactor,
      tintColor : [this.tintColorR, this.tintColorG, this.tintColorB, this.tintColorA],
      ripplePosition: undefined,
    },
      uiEffect.Mask.createUseEffectMask(true),
      distortMask
      );
    return effect;
  }

  build() {
    Stack() {
      EffectComponent() {
        Column()
          .position({ x: 200 + 'px', y: 200 + 'px' })
          .height(553 + 'px')
          .width(553 + 'px')
          .borderRadius(12)
          .visualEffect(this.getMaterialVisualEffect())
      }
      .backgroundEffect({
        radius: 15,
      }, { disableSystemAdaptation: true })
      .width("100%").height("100%").align(Alignment.Center)
    }
    .backgroundImage($r('app.media.bg6'), ImageRepeat.NoRepeat) // the image should be created in local
    .width("100%").height("100%").align(Alignment.Center)
  }
}
```

### createRadialGradientMask<sup>20+</sup>
static createRadialGradientMask(center: common2D.Point, radiusX: number, radiusY: number, values: Array<[number, number]>): Mask

通过输入椭圆中心点的位置、长短轴和形状参数创建椭圆遮罩效果[Mask](#mask20)实例。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名  | 类型                                      | 必填 | 说明                       |
| ------- | ---------------------------------------- | ---- | ------------------------- |
| center | [common2D.Point](js-apis-graphics-common2D.md#point12)  | 是 | 设置椭圆的中心点，[0, 0]为组件左上角，[1, 1]为组件的右下角。<br>取值范围为[-10, 10]，可取浮点数，超出边界会在实现时自动截断。 |
| radiusX | number  | 是 | 设置椭圆的长轴，半径为1等于组件的高度。<br>取值范围为[0, 10]，可取浮点数，超出边界会在实现时自动截断。 |
| radiusY | number  | 是 | 设置椭圆的短轴，半径为1等于组件的高度。<br>取值范围为[0, 10]，可取浮点数，超出边界会在实现时自动截断。 |
| values | Array<[number, number]>     | 是 | 数组中保存的二元数组表示梯度：[RGBA颜色, 位置]。RGBA颜色四通道使用相同的值，可看作一个灰度值；位置表示沿径向方向向外时RGBA颜色对应的分布位置；RGBA颜色与位置的取值范围均为[0, 1]，可取浮点数，小于0的转为0，大于1的转为1。<br>位置参数值需严格递增，Array数组中二元数组个数必须大于等于2，二元数组中的元素不能为空，否则该椭圆分布效果不生效。 |

**返回值：**

| 类型                          | 说明                                               |
| ----------------------------- | ------------------------------------------------- |
| [Mask](#mask20) | 返回椭圆形状的径向分布效果的灰度Mask。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { uiEffect } from '@kit.ArkGraphics2D'
// values: [[1.0, 0.5], [1.0, 1.0]] => color0: 1.0; color1: 1.0; position0: 0.5; position1: 1.0
let mask = uiEffect.Mask.createRadialGradientMask({x: 0.0, y: 0.0}, 0.5, 0.5, [[1.0, 0.5], [1.0, 1.0]]);
@Entry
@Component
struct RadialGradientMaskExample {
  build() {
    Stack() {
      Image($rawfile('test.jpg'))
      Column()
        .width('100%')
        .height('100%')
        // Mask作为Filter的入参实现对应的效果，该效果中Mask是在屏幕左上角的四分之一圆环
        .backgroundFilter(uiEffect.createFilter().edgeLight(1.0, null, mask))
    }
  }
}
```
### createWaveGradientMask<sup>20+</sup>
static createWaveGradientMask(center: common2D.Point, width: number, propagationRadius: number, blurRadius: number, turbulenceStrength?: number): Mask

输入波源中心位置、单波参数创建单波遮罩效果[Mask](#mask20)实例。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**
| 参数名  | 类型                                      | 必填 | 说明                       |
| ------- | ---------------------------------------- | ---- | ------------------------- |
| center | [common2D.Point](js-apis-graphics-common2D.md#point12)  | 是 | 设置单波波源的中心点，[0, 0]为组件左上角，[1, 1]为组件的右下角。<br>取值范围为[-10, 10]，可取浮点数，超出边界会在实现时自动截断。 |
| width | number  | 是 | 设置单波圆环的宽度。<br>取值范围为[0, 5]，可取浮点数，超出边界会在实现时自动截断。 |
| propagationRadius | number  | 是 | 设置单波圆环的扩散外径。<br>取值范围为[0, 10]，可取浮点数，超出边界会在实现时自动截断。 |
| blurRadius | number  | 是 | 设置单波圆环的模糊外径，模糊半径为0则是实边圆环，否则是虚边圆环。<br>取值范围为[0, 5]，可取浮点数，超出边界会在实现时自动截断。 |
| turbulenceStrength | number  | 否 | 设置单波圆环的湍流强度，默认值为0，强度为0则是规则圆环，否则圆环边缘会湍流扭曲。<br>取值范围为[-1, 1]，可取浮点数，超出边界会在实现时自动截断。 |

**返回值：**

| 类型                          | 说明                                               |
| ----------------------------- | ------------------------------------------------- |
| [Mask](#mask20) | 返回单个水波形状的灰度Mask。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202 | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { uiEffect } from "@kit.ArkGraphics2D";
// center: [0.5, 0.5]；width: 0.01; propagationRadius: 0.5; blurRadius: 0.1; turbulenceStrength: 0.1
let mask = uiEffect.Mask.createWaveGradientMask({x: 0.5, y: 0.5}, 0.01, 0.5, 0.1, 0.1);
@Entry
@Component
struct WaveGradientMaskExample {
  build() {
    Stack() {
      Image($rawfile('test.jpg'))
      Column()
        .width('100%')
        .height('100%')
        // 将Mask作为Filter的参数，实现屏幕中心向四周扩散的水波形状效果。
        .backgroundFilter(uiEffect.createFilter().edgeLight(1.0, null, mask))
    }
  }
}
```
### createUseEffectMask<sup>22+</sup>

static createUseEffectMask(useEffect: boolean): Mask

创建并设置[Mask](#mask20)实例是否使用模糊缓存。此Mask实例专为[liquidMaterial](#liquidmaterial22)方法的useEffectMask参数设计，用于声明材质效果是否使用模糊缓存以提升性能。将此Mask实例用于其他Filter或VisualEffect方法时，useEffect属性可能不生效。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名    | 类型    | 必填 | 说明                                                         |
| --------- | ------- | ---- | ------------------------------------------------------------ |
| useEffect | boolean | 是   | 标记是否使用模糊缓存。值为true，表示使用，会正常显示模糊效果；值为false，表示不使用，不显示模糊效果。 |

**返回值：**

| 类型            | 说明                             |
| --------------- | -------------------------------- |
| [Mask](#mask20) | 返回标记是否使用模糊缓存的Mask实例。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API. |

**示例：**

```ts
import { uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct Index {
  @State distortProgress: number = 0.;
  @State rippleProgress: number = 0.;
  @State distortFactor: number = 0.;
  @State materialFactor: number = 1.;
  @State refractionFactor: number = 1.;
  @State reflectionFactor: number = 1.;
  @State tintColorR: number = 1.;
  @State tintColorG: number = 1.;
  @State tintColorB: number = 1.;
  @State tintColorA: number = 1.;

  private getMaterialVisualEffect(): uiEffect.VisualEffect {
    let effect: uiEffect.VisualEffect = uiEffect.createEffect();
    effect.liquidMaterial({
        enable: true,
        distortProgress : this.distortProgress,
        rippleProgress: this.rippleProgress,
        distortFactor: this.distortFactor,
        materialFactor : this.materialFactor,
        refractionFactor : this.refractionFactor,
        reflectionFactor: this.reflectionFactor,
        tintColor : [this.tintColorR, this.tintColorG, this.tintColorB, this.tintColorA],
        ripplePosition: undefined,
      },
      uiEffect.Mask.createUseEffectMask(true), // useEffectMask使用示例
    );
    return effect;
  }

  build() {
    Stack() {
      EffectComponent() {
        Column()
          .position({ x: 200 + 'px', y: 200 + 'px' })
          .height(553 + 'px')
          .width(553 + 'px')
          .borderRadius(12)
          .visualEffect(this.getMaterialVisualEffect())
      }
      .backgroundEffect({
        radius: 15,
      }, { disableSystemAdaptation: true })
      .width("100%").height("100%").align(Alignment.Center)
    }
    .backgroundImage($r('app.media.bg6'), ImageRepeat.NoRepeat)
    .width("100%").height("100%").align(Alignment.Center)
  }
}
```

## BrightnessBlenderParam
BrightnessBlender的参数列表，用于配置提亮效果的各项属性，包括灰度调整系数、饱和度和混合比例等参数。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

| 名称                | 类型                        | 只读 | 可选 | 说明                                                              |
| ------------------- | -------------------------- | ---- | ---- | ---------------------------------------------------------------- |
| cubicRate           | number                     | 否   | 否   | 灰度调整的三阶系数。<br>取值范围为[-20, 20]，超出边界会在实现时自动截断。                        |
| quadraticRate       | number                     | 否   | 否   | 灰度调整的二阶系数。<br>取值范围为[-20, 20]，超出边界会在实现时自动截断。                        |
| linearRate          | number                     | 否   | 否   | 灰度调整的线性系数。<br>取值范围为[-20, 20]，超出边界会在实现时自动截断。                        |
| degree              | number                     | 否   | 否   | 灰度调整的比例。<br>取值范围为[-20, 20]，超出边界会在实现时自动截断。                            |
| saturation          | number                     | 否   | 否   | 提亮的基准饱和度。<br>取值范围为[0, 20]，超出边界会在实现时自动截断。                            |
| positiveCoefficient | [number, number, number]   | 否   | 否   | 基于基准饱和度的RGB正向调整参数。<br>每个number的取值范围为[-20, 20]，超出边界会在实现时自动截断。 |
| negativeCoefficient | [number, number, number]   | 否   | 否   | 基于基准饱和度的RGB负向调整参数。<br>每个number的取值范围为[-20, 20]，超出边界会在实现时自动截断。 |
| fraction            | number                     | 否   | 否   | 提亮效果的混合比例。<br>取值范围为[0, 1]，超出边界会在实现时自动截断。  |

## HeatDistortionEffectParam

热浪扭曲效果的参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Graphics.Drawing

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| intensity | number | 否 | 否 | 热浪扭曲的强度。<br>取值范围为[0, 1]，超出边界会在实现时自动截断。<br>0表示无扭曲，1表示最大扭曲程度。 |
| noiseScale | number | 否 | 否 | 热浪扭曲的噪声缩放，控制噪声纹理的细度。<br>取值范围为[0.1, 5.0]，超出边界会在实现时自动截断。<br>值越大，噪声纹理越细腻。 |
| riseWeight | number | 否 | 否 | 热浪扭曲的上升权重，控制气泡的上升速度。<br>取值范围为[0, 1]，超出边界会在实现时自动截断。<br>值越大，向上运动越明显。 |
| progress | number | 否 | 否 | 热浪扭曲的动画进度。<br>取值范围为[0, 1]，超出边界会在实现时自动截断。<br>0对应动画开始，1对应动画结束。 |

## BlurBubblesRiseEffectParam

模糊气泡上升效果的参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Graphics.Drawing

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| blurIntensity | number | 否 | 否 | 模糊气泡上升效果的高斯模糊强度。<br>取值范围为[0, 1]，超出边界会在实现时自动截断。<br>0表示无模糊，1表示最大模糊程度。 |
| mixStrength | number | 否 | 否 | 原图与模糊图的混合强度。<br>取值范围为[0, 1]，超出边界会在实现时自动截断。<br>0对应原图，1对应模糊后的图像。 |
| progress | number | 否 | 否 | 模糊气泡上升效果的动画进度。<br>取值范围为[0, 1]，超出边界会在实现时自动截断。<br>0对应动画开始，1对应动画结束。 |
| maskImage | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)  | 否 | 否 | 模糊气泡上升效果的遮罩图像，控制模糊气泡区域。<br>被遮罩的区域有模糊效果，未遮罩的区域无模糊效果。 |