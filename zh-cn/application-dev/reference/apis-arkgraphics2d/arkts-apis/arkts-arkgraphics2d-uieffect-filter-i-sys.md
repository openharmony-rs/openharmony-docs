# Filter

**起始版本：** 12

<!--Device-uiEffect-interface Filter--><!--Device-uiEffect-interface Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## bezierWarp

```TypeScript
bezierWarp(controlPoints: Array<common2D.Point>): Filter
```

将贝塞尔曲线变形的效果添加至组件上。该效果通过在图层边界上创建封闭的贝塞尔曲线，实现对图像的精准扭曲和形状调整。贝塞尔曲线共有四段，首尾顺次相连，每段包含一个顶点和两个切点。

**起始版本：** 20

<!--Device-Filter-bezierWarp(controlPoints: Array<common2D.Point>): Filter--><!--Device-Filter-bezierWarp(controlPoints: Array<common2D.Point>): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controlPoints | Array&lt;common2D.Point&gt; | 是 | 12个贝塞尔形变控制点，更改控制点的位置可改变形成边缘的曲线的形状，从而扭曲图像。控制点坐标为0-1坐标系，且坐标值可大于1或小于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回挂载了贝塞尔曲线变形效果的Filter。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例：**

```TypeScript
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

## blurBubblesRise

```TypeScript
blurBubblesRise(param: BlurBubblesRiseEffectParam): Filter
```

应用模糊气泡上升效果到图像，模拟气泡在液体中上升的梦幻模糊扭曲效果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Filter-blurBubblesRise(param: BlurBubblesRiseEffectParam): Filter--><!--Device-Filter-blurBubblesRise(param: BlurBubblesRiseEffectParam): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [BlurBubblesRiseEffectParam](arkts-arkgraphics2d-uieffect-blurbubblesriseeffectparam-i-sys.md) | 是 | 模糊气泡上升效果的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回模糊气泡上升滤镜。 |

**示例：**

```TypeScript
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

## colorGradient

```TypeScript
colorGradient(colors: Array<Color>, positions: Array<common2D.Point>, strengths: Array<number>,
        alphaMask?: Mask): Filter
```

为组件内容添加颜色渐变效果。

**起始版本：** 20

<!--Device-Filter-colorGradient(colors: Array<Color>, positions: Array<common2D.Point>, strengths: Array<double>,        alphaMask?: Mask): Filter--><!--Device-Filter-colorGradient(colors: Array<Color>, positions: Array<common2D.Point>, strengths: Array<double>,        alphaMask?: Mask): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colors | Array&lt;Color&gt; | 是 | 颜色数组，多个颜色的渐变。数组长度取值范围[0, 12], 每一个颜色值取值范围为大于等于0。数组长度等于0或大于12时无效果，colors、positions和strengths的数组长度不相等时无效果。 |
| positions | Array&lt;common2D.Point&gt; | 是 | 位置数组，颜色对应的分布位置。数组长度取值范围[0, 12]。数组长度等于0或大于12时无效果，colors、positions和strengths的数组长度不相等时无效果。 |
| strengths | Array&lt;number&gt; | 是 | 强度数组，颜色对应的扩散强度。数组长度取值范围[0, 12], 每一个强度值取值范围为大于等于0。数组长度等于0或大于12时无效果，colors、positions和strengths的数组长度不相等时无效果。 |
| alphaMask | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 否 | 遮罩alpha，颜色对应的alpha显示遮罩。不设置时，默认组件内容全部有颜色渐变效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回挂载了颜色渐变效果的Filter。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例：**

```TypeScript
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

## contentLight

```TypeScript
contentLight(lightPosition: common2D.Point3d, lightColor: common2D.Color, lightIntensity: number,
      displacementMap?: Mask): Filter
```

为组件内容添加3D光照效果。

**起始版本：** 20

<!--Device-Filter-contentLight(lightPosition: common2D.Point3d, lightColor: common2D.Color, lightIntensity: double,      displacementMap?: Mask): Filter--><!--Device-Filter-contentLight(lightPosition: common2D.Point3d, lightColor: common2D.Color, lightIntensity: double,      displacementMap?: Mask): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lightPosition | common2D.Point3d | 是 | 光源在组件空间的位置，[-1, -1, 0]为组件左上角，[1, 1, 0]为组件的右下角，z轴分量越大光源离组件平面越远，可照射区域越大。x分量取值范围[-10, 10]，y分量取值范围[-10, 10]，z分量取值范围[0, 10]，超出范围会自动截断。 |
| lightColor | common2D.Color | 是 | 光源颜色，各元素取值范围为[0, 1]，超出范围会自动截断。 |
| lightIntensity | number | 是 | 光源强度，取值范围[0, 1]，数值越大光源亮度越大，超出范围会自动截断。 |
| displacementMap | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 否 | 该参数暂不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回了具有内容光照效果的filter。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例：**

```TypeScript
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

## directionLight

```TypeScript
directionLight(direction: common2D.Point3d, color: Color, intensity: number, mask?: Mask, factor?: number): Filter
```

为组件内容提供基于Mask和平行光的光照效果。

**起始版本：** 20

<!--Device-Filter-directionLight(direction: common2D.Point3d, color: Color, intensity: double, mask?: Mask, factor?: double): Filter--><!--Device-Filter-directionLight(direction: common2D.Point3d, color: Color, intensity: double, mask?: Mask, factor?: double): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| direction | common2D.Point3d | 是 | 方向光的入射方向。 |
| color | [Color](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-scenetypes-color-i.md) | 是 | 光照颜色。 |
| intensity | number | 是 | 光照强度，非负数。 |
| mask | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 否 | 置换贴图，用于描述二维图像表面的三维细节，通过法线或高度图增强局部细节和光照反射效果，若输入为高度图，须与factor参数配合使用。默认为空，表现为全局无细节的平面光照效果。 |
| factor | number | 否 | 采样缩放系数。默认值为null，mask作为法线图采样；非默认值时，mask作为高度图采样，实际高度值为mask的采样值与factor的乘积。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回挂载了由置换贴图控制的光照效果的Filter。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例：**

```TypeScript
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

## displacementDistort

```TypeScript
displacementDistort(displacementMap: Mask, factor?: [number, number]): Filter
```

为组件内容添加扭曲效果。

**起始版本：** 20

<!--Device-Filter-displacementDistort(displacementMap: Mask, factor?: [double, double]): Filter--><!--Device-Filter-displacementDistort(displacementMap: Mask, factor?: [double, double]): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displacementMap | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 是 | 指定扭曲程度。与factor相乘后共同决定扭曲程度。 |
| factor | [number, number] | 否 | 指定水平、竖直方向扭曲程度系数，系数的绝对值越大，扭曲程度越明显，建议取值范围为[-10.0, 10.0]。不设置时，默认值为1.0。设置为0时，无扭曲效果。与mask相乘后共同决定扭曲程度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回挂载了扭曲效果的Filter。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例：**

```TypeScript
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

## distort

```TypeScript
distort(distortionK: number): Filter
```

将透镜畸变效果添加至组件上。

**起始版本：** 13

<!--Device-Filter-distort(distortionK: double): Filter--><!--Device-Filter-distort(distortionK: double): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| distortionK | number | 是 | 畸变系数，表示透镜畸变的程度，取值范围为[-1, 1]。畸变系数设置小于-1的值时，按值为-1处理；设置大于1的值时，按值为1处理。畸变系数小于0时，效果为桶形畸变；大于0时，效果为枕形畸变；越接近0时，畸变程度越小，等于0时，没有畸变效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回挂载了透镜畸变效果的Filter。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例：**

```TypeScript
// 将透镜畸变效果添加至组件上
let filter = uiEffect.createFilter()
filter.distort(-0.5)

```

## edgeLight

```TypeScript
edgeLight(alpha: number, color?: Color, mask?: Mask, bloom?: boolean): Filter
```

为组件内容检测边缘，并添加边缘高亮效果。

**起始版本：** 20

<!--Device-Filter-edgeLight(alpha: double, color?: Color, mask?: Mask, bloom?: boolean): Filter--><!--Device-Filter-edgeLight(alpha: double, color?: Color, mask?: Mask, bloom?: boolean): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alpha | number | 是 | 指定描边高光透明度，越大描边越明显。取值范围为[0, 1]。设置为0时无描边；设置小于0的值时，按值为0处理；设置大于1的值时，按值为1处理。 |
| color | [Color](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-scenetypes-color-i.md) | 否 | 指定描边高光颜色，不设置时，将默认使用组件内容的原始颜色。如果有值，使用指定颜色。设置不为null时，Color中的alpha不发挥作用，仅使用rgb。 |
| mask | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 否 | 指定描边高光强度。不设置时，默认组件内容全部有描边高光效果。 |
| bloom | boolean | 否 | 指定描边是否发光。设置为true时，有描边和发光效果；设置为false时，只有描边效果无发光效果；不设置时，默认为true。小于16*16的图片默认只有描边效果，无发光效果，此参数失去作用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回挂载了描边高光效果的Filter。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例：**

```TypeScript
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

## flyInFlyOutEffect

```TypeScript
flyInFlyOutEffect(degree: number, flyMode: FlyMode): Filter
```

将飞入飞出形变效果添加至组件上。

**起始版本：** 12

<!--Device-Filter-flyInFlyOutEffect(degree: double, flyMode: FlyMode): Filter--><!--Device-Filter-flyInFlyOutEffect(degree: double, flyMode: FlyMode): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| degree | number | 是 | 表示控制飞入飞出形变的程度，取值范围为[0, 1]。越靠近1，变形程度越明显。超出取值范围形变不会出现效果。 |
| flyMode | [FlyMode](arkts-arkgraphics2d-uieffect-flymode-e-sys.md) | 是 | 飞入飞出的场景模式。BOTTOM表示从设备底部飞入飞出形变场景。TOP表示从设备顶部飞入飞出形变场景。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回挂载了飞入飞出形变效果的Filter。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例：**

```TypeScript
// 将飞入飞出形变效果添加至组件上
let filter = uiEffect.createFilter()
filter.flyInFlyOutEffect(0.5, uiEffect.FlyMode.TOP)

```

## hdrBrightnessRatio

```TypeScript
hdrBrightnessRatio(ratio: number): Filter
```

为组件内容添加HDR（高动态范围成像）提亮效果。不建议嵌套使用，强行嵌套使用可能造成过曝现象。

**起始版本：** 24

**需要权限：** 
- API版本24+：ohos.permission.HDR_BRIGHTNESS

<!--Device-Filter-hdrBrightnessRatio(ratio: double): Filter--><!--Device-Filter-hdrBrightnessRatio(ratio: double): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ratio | number | 是 | 提亮倍数，取值范围为[1.0, 设备当前支持最大提亮倍数]。设置小于1.0的值时，按值为1.0处理；当值等于1.0时，不做任何处理；当值大于1.0时，会尝试触发HDR渲染管线，设置大于设备当前支持最大提亮倍数的值时，按值为设备当前支持最大提亮倍数处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回挂载了HDR提亮效果的Filter。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。<br>**适用版本：** 20 - 23 |
| [201](../../errorcode-universal.md#201-权限校验失败) | 权限校验失败，应用无权限使用该API，需要申请权限。<br>**适用版本：** 24+ |

**示例：**

```TypeScript
// 创建Filter实例
let filter: uiEffect.Filter = uiEffect.createFilter();
// 设置HDR提亮倍数为2.0
filter.hdrBrightnessRatio(2.0);

```

## heatDistortion

```TypeScript
heatDistortion(param: HeatDistortionEffectParam): Filter
```

应用热浪扭曲效果到图像，模拟热空气流动产生的视觉扭曲。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Filter-heatDistortion(param: HeatDistortionEffectParam): Filter--><!--Device-Filter-heatDistortion(param: HeatDistortionEffectParam): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [HeatDistortionEffectParam](arkts-arkgraphics2d-uieffect-heatdistortioneffectparam-i-sys.md) | 是 | 热浪扭曲效果的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回添加了热浪扭曲效果的Filter。 |

**示例：**

```TypeScript
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

## maskDispersion

```TypeScript
maskDispersion(dispersionMap: Mask, alpha: number, rFactor?: [number, number], gFactor?: [number, number],
      bFactor?: [number, number]): Filter
```

为组件内容添加由置换贴图控制的色散效果。

**起始版本：** 20

<!--Device-Filter-maskDispersion(dispersionMap: Mask, alpha: double, rFactor?: [double, double], gFactor?: [double, double],      bFactor?: [double, double]): Filter--><!--Device-Filter-maskDispersion(dispersionMap: Mask, alpha: double, rFactor?: [double, double], gFactor?: [double, double],      bFactor?: [double, double]): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dispersionMap | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 是 | 置换贴图，用于控制色散的强度、方向和透明度。建议使用PixelMapMask类型的置换贴图。 |
| alpha | number | 是 | 色散整体透明度，透明度越小效果越透明。取值范围为[0, 1.0]。透明度设置为0时色散效果不生效；透明度设置小于0的值时，按值为0处理；设置大于1.0的值时，按值为1.0处理。 |
| rFactor | [number, number] | 否 | X/Y方向上R通道的色散基础偏移，偏移越大红色色散效果越明显。每个方向上的取值范围为[-1.0, 1.0]。偏移设置小于-1.0的值时，按值为-1.0处理；设置大于1.0的值时，按值为1.0处理。 |
| gFactor | [number, number] | 否 | X/Y方向上G通道的色散基础偏移，偏移越大绿色色散效果越明显。取值范围同rFactor。 |
| bFactor | [number, number] | 否 | X/Y方向上B通道的色散基础偏移，偏移越大蓝色色散效果越明显。取值范围同rFactor。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回挂载了由置换贴图控制的色散效果的Filter。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

## maskTransition

```TypeScript
maskTransition(alphaMask: Mask, factor?: number, inverse?: boolean): Filter
```

为组件内容提供基于Mask的转场效果。

**起始版本：** 20

<!--Device-Filter-maskTransition(alphaMask: Mask, factor?: double, inverse?: boolean): Filter--><!--Device-Filter-maskTransition(alphaMask: Mask, factor?: double, inverse?: boolean): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alphaMask | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 是 | 通过遮罩指定转场效果的作用区域。 |
| factor | number | 否 | 转场过渡系数，取值范围为[0.0, 1.0]，默认值为1.0。factor值越大画面越接近转场后页面，超出范围自动截断到[0.0, 1.0]。 |
| inverse | boolean | 否 | 是否启用反向转场，true表示启用，false表示不启用，默认值为false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回挂载了转场效果的Filter。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例：**

```TypeScript
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

## pixelStretch

```TypeScript
pixelStretch(stretchSizes: Array<number>, tileMode: TileMode): Filter
```

将边缘像素扩展效果添加至组件上。

**起始版本：** 12

<!--Device-Filter-pixelStretch(stretchSizes: Array<double>, tileMode: TileMode): Filter--><!--Device-Filter-pixelStretch(stretchSizes: Array<double>, tileMode: TileMode): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| stretchSizes | Array&lt;number&gt; | 是 | 上下左右四个方向边缘像素扩展的百分比比例，取值范围为[-1, 1]。正值表示向外扩展，上下左右四个方向分别用指定原图比例的边缘像素填充。负值表示内缩，但是最终图像大小不变。注意四个方向对应的参数需统一为非正值或非负值。 |
| tileMode | [TileMode](arkts-arkgraphics2d-effectkit-tilemode-e.md) | 是 | 边缘像素扩展的像素填充模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回挂载了边缘像素扩展效果的Filter。 |

**示例：**

```TypeScript
// 将边缘像素扩展效果添加至组件上
let filter = uiEffect.createFilter()
filter.pixelStretch([0.2, 0.2, 0.2, 0.2], uiEffect.TileMode.CLAMP)

```

## radiusGradientBlur

```TypeScript
radiusGradientBlur(radius: number, gradientParam: LinearGradientBlurOptions): Filter
```

为组件内容添加半径线性渐变模糊效果。

**起始版本：** 19

<!--Device-Filter-radiusGradientBlur(radius: double, gradientParam: LinearGradientBlurOptions): Filter--><!--Device-Filter-radiusGradientBlur(radius: double, gradientParam: LinearGradientBlurOptions): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | number | 是 | 模糊半径，单位为px，模糊半径越大越模糊。取值范围为[0, 128]。模糊半径设置为0时不模糊；模糊半径设置小于0的值时，按值为0处理；设置大于128的值时，按值为128处理。 |
| gradientParam | [LinearGradientBlurOptions](../../apis-arkui/arkts-components/arkts-arkui-lineargradientbluroptions-i.md) | 是 | 线性渐变参数，包含两个部分fractionStops和direction。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回挂载了半径线性渐变模糊效果的Filter。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

## variableRadiusBlur

```TypeScript
variableRadiusBlur(radius: number, radiusMap: Mask): Filter
```

为组件内容提供基于Mask的渐变模糊效果。

**起始版本：** 20

<!--Device-Filter-variableRadiusBlur(radius: double, radiusMap: Mask): Filter--><!--Device-Filter-variableRadiusBlur(radius: double, radiusMap: Mask): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | number | 是 | 最大模糊半径，单位为px，该值越大越模糊。取值范围为[0, 128]。模糊半径设置为0时不模糊；模糊半径设置小于0的值时，按值为0处理；设置大于128的值时，按值为128处理。 |
| radiusMap | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 是 | 代表模糊程度的Mask对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回当前效果的Filter对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例：**

```TypeScript
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

## waterRipple

```TypeScript
waterRipple(progress: number, waveCount: number, x: number, y: number, rippleMode: WaterRippleMode): Filter
```

将水波纹效果添加至组件上。

**起始版本：** 12

<!--Device-Filter-waterRipple(progress: double, waveCount: int, x: double, y: double, rippleMode: WaterRippleMode): Filter--><!--Device-Filter-waterRipple(progress: double, waveCount: int, x: double, y: double, rippleMode: WaterRippleMode): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| progress | number | 是 | 表示水波纹的进度，取值范围为[0, 1]。水波纹进度越趋向于1，水波纹展示越完全。超出取值范围水波纹不会出现效果。 |
| waveCount | number | 是 | 水波纹波动时波纹的个数，取值范围为[1, 3]。水波纹的个数只能取整数，如果为浮点数或超出取值范围，水波纹不会出现效果。 |
| x | number | 是 | 水波纹中心在屏幕中第一次出现的x轴位置。水波纹对屏幕进行归一化处理，左上角的坐标为（0, 0），右上角坐标为（1, 0）。当x取值为负值时，代表在屏幕左侧。 |
| y | number | 是 | 水波纹中心在屏幕中第一次出现的y轴位置。水波纹对屏幕进行归一化处理，左上角的坐标为（0, 0），左下角坐标为（0, 1）。当y取值为负值时，代表在屏幕上方。 |
| rippleMode | [WaterRippleMode](arkts-arkgraphics2d-uieffect-waterripplemode-e-sys.md) | 是 | 水波纹的场景模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i-sys.md) | - 返回挂载了水波纹效果的Filter。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例：**

```TypeScript
// 将水波纹效果添加至组件上
let filter = uiEffect.createFilter()
filter.waterRipple(0.5, 2, 0.5, 0.5, uiEffect.WaterRippleMode.SMALL2SMALL)

```

