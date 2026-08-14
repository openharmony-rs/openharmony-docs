# VisualEffect

VisualEffect效果类，用于将背景颜色混合、边框光照、颜色渐变等效果添加到组件上。 在调用VisualEffect的方法前，需要先通过[createEffect](arkts-arkgraphics2d-uieffect-createeffect-f.md#createEffect)创建一个VisualEffect实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-uiEffect-interface VisualEffect--><!--Device-uiEffect-interface VisualEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## backgroundColorBlender

```TypeScript
backgroundColorBlender(blender: BrightnessBlender): VisualEffect
```

用于改变组件背景颜色的blender，目前仅支持提亮混合器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-VisualEffect-backgroundColorBlender(blender: BrightnessBlender): VisualEffect--><!--Device-VisualEffect-backgroundColorBlender(blender: BrightnessBlender): VisualEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blender | [BrightnessBlender](arkts-arkgraphics2d-uieffect-brightnessblender-i-sys.md) | 是 | 用于混合背景颜色的blender。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| VisualEffect | 返回添加了背景颜色更改效果的VisualEffect。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
let blender : uiEffect.BrightnessBlender =
  uiEffect.createBrightnessBlender({cubicRate:1.0, quadraticRate:1.0, linearRate:1.0, degree:1.0, saturation:1.0,
    positiveCoefficient:[2.3, 4.5, 2.0], negativeCoefficient:[0.5, 2.0, 0.5], fraction:0.0})
visualEffect.backgroundColorBlender(blender)
```

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Context, Column, Color, Stack, State, Row, Text, $r } from '@kit.ArkUI'
import uiEffect from '@ohos.graphics.uiEffect'
import { BrightnessBlenderParam } from '@ohos.graphics.uiEffect'
import type common2D from '@ohos.graphics.common2D'

@Entry
@Component
struct BackgroundColorBlender {
  @State bgOptions: uiEffect.Blender = uiEffect.createBrightnessBlender({
    cubicRate: 0.5, quadraticRate: 0.5, linearRate: 0.5, degree: 0.5, saturation: 0.5,
    positiveCoefficient: [1.0, 1.0, 1.0] as [double, double, double],
    negativeCoefficient: [1.0, 1.0, 1.0] as [double, double ,double],
    fraction: 0.5
  } as BrightnessBlenderParam)

  build() {
    Stack() {
      Column() {
        Text("BrightnessBlender").fontSize(50).fontColor(Color.Red)
      }.backgroundColor(Color.Blue)
      .visualEffect(uiEffect.createEffect().backgroundColorBlender(this.bgOptions))
    }
  }
}
```

## borderLight

```TypeScript
borderLight(lightPosition: common2D.Point3d, lightColor: common2D.Color, lightIntensity: double,
      borderWidth: double): VisualEffect
```

为圆角矩形组件边框添加3D光照效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VisualEffect-borderLight(lightPosition: common2D.Point3d, lightColor: common2D.Color, lightIntensity: double,      borderWidth: double): VisualEffect--><!--Device-VisualEffect-borderLight(lightPosition: common2D.Point3d, lightColor: common2D.Color, lightIntensity: double,      borderWidth: double): VisualEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lightPosition | common2D.Point3d | 是 | 光源在组件空间的3D位置，[-1, -1, 0]为组件左上角，[1, 1, 0]为组件的右下角， z轴分量越大，光源离组件平面越远，可照射区域越大。 x轴分量取值范围为[-10, 10]，y轴分量取值范围为[-10, 10]，z轴分量取值范围为[0, 10]，超出范围会自动截断。 |
| lightColor | common2D.Color | 是 | 光源颜色，各元素取值范围为[0, 1]，超出范围会自动截断。 |
| lightIntensity | double | 是 | 光源强度，取值范围为[0, 1]，数值越大光源亮度越大，超出范围会自动截断。 |
| borderWidth | double | 是 | 组件边框的受光宽度，取值范围为[0.0, 30.0]，超出范围会自动截断。 设置为0.0时，组件边框无光照效果，数值越大，光可照亮的区域越宽。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| VisualEffect | 返回了具有边框光照效果的VisualEffect。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { common2D, uiEffect } from '@kit.ArkGraphics2D'

@Entry
@Component
struct Index {
  @State point1:common2D.Point3d = {
    x:0,y:0,z:2
  }
  @State color1:common2D.Color = {
    red:1,green:1,blue:1,alpha:1
  }
  @State lightIntensity1:number = 1
  @State borderWidth:number = 20

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
          .visualEffect(uiEffect.createEffect().borderLight(this.point1, this.color1, this.lightIntensity1,
            this.borderWidth))
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

ArkTS-Sta示例：

```TypeScript
import {
  Entry,
  Component,
  State,
  Column,
  Stack,
  Image,
  $r,
  FlexAlign
} from '@kit.ArkUI';

import uiEffect from '@ohos.graphics.uiEffect'
import {common2D} from '@kit.ArkGraphics2D'

@Entry
@Component
struct Index {
  @State lightIntensity1:double = 1
  @State borderWidth_:double = 20

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
          .visualEffect(uiEffect.createEffect().borderLight(
            { x:0.0, y:0.0, z:2.0 } as common2D.Point3d,
            { red:255, blue:255, green:255, alpha:255 } as common2D.Color,
            this.lightIntensity1, this.borderWidth_))
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

## colorGradient

```TypeScript
colorGradient(colors: Array<Color>, positions: Array<common2D.Point>, strengths: Array<double>,
      alphaMask?: Mask): VisualEffect
```

此方法为组件添加颜色渐变效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VisualEffect-colorGradient(colors: Array<Color>, positions: Array<common2D.Point>, strengths: Array<double>,      alphaMask?: Mask): VisualEffect--><!--Device-VisualEffect-colorGradient(colors: Array<Color>, positions: Array<common2D.Point>, strengths: Array<double>,      alphaMask?: Mask): VisualEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colors | Array&lt;Color&gt; | 是 | 颜色数组，用于实现多颜色渐变。 数组长度范围0到12，每个颜色值取值范围需大于等于0。数组长度为0或大于12， 或colors、positions和strengths的数组长度不一致，则无颜色渐变效果。 |
| positions | Array&lt;common2D.Point&gt; | 是 | 位置数组，颜色对应的位置。 数组长度范围为0到12。数组长度为0或大于12，或colors、positions和strengths的数组长度不一致，则无颜色渐变效果。 |
| strengths | Array&lt;double&gt; | 是 | 强度数组，表示颜色对应的强度。 数组长度范围为0到12，每一个强度值需大于等于0。数组长度为0或大于12，或colors、positions和strengths的数组长度不一致时，则无颜色渐变效果。 |
| alphaMask | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 否 | 遮罩alpha，颜色对应的alpha遮罩。可通过Mask类的创建方法 （如createRippleMask、createRadialGradientMask等）创建Mask实例。当需要控制颜色渐变效果的 透明度分布（如局部透明或动态透明效果）时传入此参数。不设置时，颜色渐变效果的透明度 完全由colors参数决定。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| VisualEffect | 返回具有颜色渐变效果的VisualEffect。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { common2D, uiEffect } from "@kit.ArkGraphics2D"

@Entry
@Component
struct ColorGradientExample {
  build() {
    Stack() {
      Stack() {}
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

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Column, Stack, State, Row, $r } from '@kit.ArkUI'
import uiEffect from '@ohos.graphics.uiEffect'
import type common2D from '@ohos.graphics.common2D'

@Entry
@Component
struct ColorGradient {
  @State colors: Array<uiEffect.Color> = [
    {red: 1.0, green: 0.8, blue: 0.5, alpha: 0.8} as uiEffect.Color,
    {red: 1.0, green: 1.0, blue: 0.5, alpha: 1.0} as uiEffect.Color
  ]
  @State positions: Array<common2D.Point> = [
    {x: 0.2, y: 0.2} as common2D.Point,
    {x: 0.8, y: 0.6} as common2D.Point]
  @State strengths: Array<double> = [0.3, 0.3]

  build() {
    Column() {
      Row().width("100%").height("100%")
        .backgroundFilter(uiEffect.createFilter().colorGradient(this.colors.map((v: uiEffect.Color) => v),
          this.positions.map((v: common2D.Point) => v), this.strengths.map((v: double) => v)))
    }
  }
}
```

## distortionCollapse

```TypeScript
distortionCollapse(distortionParam: DistortionParam): VisualEffect
```

为组件添加非线性形变效果。典型应用场景包括页面坍塌动画、窗口关闭特效、卡片翻转动画、场景过渡效果等。 1. 该视效支持控件范围外的绘制，但仍会受到父控件Clip的影响。 2. 因包含前景Filter，未与EffectComponent组合使用时不兼容组件自身及子组件的部分视效（如BrightnessBlender或systemMaterial）。 3. 支持对系统材质进行扭曲，但是与EffectComponent组合使用时，会导致系统材质的背景扭曲。 4. 调用distortionCollapse时，会创建与形变后区域等大的离屏画布，再将当前组件（含子组件） 的内容绘制到离屏画布上，再对画布上的已有内容进行形变绘制。 5. 使用该实现方式时，如果不与EffectComponent组合使用，将导致systemMaterial、 backgroundEffect、brightness、blur等需要截屏的接口无法截取到正确的画面。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VisualEffect-distortionCollapse(distortionParam: DistortionParam): VisualEffect--><!--Device-VisualEffect-distortionCollapse(distortionParam: DistortionParam): VisualEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| distortionParam | DistortionParam | 是 | 非线性形变效果的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| VisualEffect | 返回添加了非线性形变效果的VisualEffect。 |

## liquidMaterial

```TypeScript
liquidMaterial(param : LiquidMaterialEffectParam, useEffectMask: Mask, distortMask?: Mask,
      brightnessParam?: BrightnessParam): VisualEffect
```

此方法为组件添加材质效果。材质效果通过模拟物理材质的光学特性（折射、反射）和动态扰动效果， 实现玻璃、金属等材质的视觉呈现。可用于模拟玻璃质感UI、流体材质动画、磨砂玻璃效果等场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VisualEffect-liquidMaterial(param : LiquidMaterialEffectParam, useEffectMask: Mask, distortMask?: Mask,      brightnessParam?: BrightnessParam): VisualEffect--><!--Device-VisualEffect-liquidMaterial(param : LiquidMaterialEffectParam, useEffectMask: Mask, distortMask?: Mask,      brightnessParam?: BrightnessParam): VisualEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [LiquidMaterialEffectParam](arkts-arkgraphics2d-uieffect-liquidmaterialeffectparam-i-sys.md) | 是 | 材质所需相关变量，用于控制材质显示，包含材质开关、折射系数、反射系数和扰动系数。 |
| useEffectMask | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 是 | 声明是否使用模糊缓存。使用createUseEffectMask(true)创建的 Mask实例使用模糊缓存，适用于需要复用模糊结果的场景以提升性能； 使用createUseEffectMask(false)创建的Mask实例不使用模糊缓存， 适用于模糊效果频繁变化的场景。 |
| distortMask | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 否 | 材质扰动效果需要的扰动纹理，由pixelMap创建的Mask实例的图片纹理决定扰动效果的图案和方向。 可通过createPixelMapMask方法创建Mask实例。当材质的扰动系数（distortFactor）不为0时，需要设置此参数否则无扰动效果； 当材质的扰动系数为0或此参数不设置时，无扰动效果。默认不设置。 |
| brightnessParam | [BrightnessParam](arkts-arkgraphics2d-uieffect-brightnessparam-i-sys.md) | 否 | 为材质增加提亮效果。当需要增强材质的视觉亮度（如高亮显示、发光效果）时传入此参数。 不设置时默认不添加提亮效果，材质保持原始亮度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| VisualEffect | 返回具有材质效果的VisualEffect。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

## 示例

```TypeScript
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

  private GetMaterialVisualEffect(): uiEffect.VisualEffect {
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
          .visualEffect(this.GetMaterialVisualEffect())
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

