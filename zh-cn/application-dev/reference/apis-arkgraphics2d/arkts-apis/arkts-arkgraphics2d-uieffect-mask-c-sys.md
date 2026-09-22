# Mask（系统接口）

```TypeScript
class Mask
```

Mask效果类，作为Filter以及VisualEffect的输入使用。不同类型的Mask提供不同的灰度分布模式，如波环遮罩、径向渐变、像素图遮罩等。

**起始版本：** 20

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## createAtlasFrameMask

```TypeScript
static createAtlasFrameMask(atlasInfo: drawing.AtlasImage): Mask
```

创建用于精灵图集序列帧动画的图集帧遮罩。该遮罩携带用于驱动图集序列帧动画的图集帧参数。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| atlasInfo | [drawing.AtlasImage](arkts-arkgraphics2d-drawing-atlasimage-i-sys.md) | 是 | 图集帧参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 返回携带图集帧参数的Mask实例。 |

## createBinocularMask

```TypeScript
static createBinocularMask(radiusX: number, radiusY: number, gap: number, softness: number): Mask
```

创建一个双目蒙版。生成一个左右对称的双椭圆弧形蒙版形状，与 maskDispersion 滤镜配合使用，用于控制色散效果的作用区域和方向。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radiusX | number | 是 | 双目椭圆的半长轴。取值范围为 [0, 1.0]；超出范围的值将在内部被截断。 |
| radiusY | number | 是 | 双目椭圆的半短轴。取值范围为 [0, 1.0]；超出范围的值将在内部被截断。 |
| gap | number | 是 | 每个椭圆中心相对于原点的水平偏移。取值范围为 [0, 1.0]；超出范围的值将在内部被截断。 |
| softness | number | 是 | 双目蒙版形状的边缘柔和度。取值范围为 [0, 1.0]；超出范围的值将在内部被截断。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 带有双目蒙版效果的 Mask 实例。 |

**示例**

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct Index {
  private myFilter: uiEffect.Filter = uiEffect.createFilter()
    .maskDispersion(uiEffect.Mask.createBinocularMask(0.28, 0.48, 0.52, 0.20), 1.0, [0.026, 0.0],
      [0.0, 0.0],
      [-0.026, 0.0])

  build() {
    Stack() {
      Image($r('app.media.BG_00001'))
      Stack() {

      }
      .width('100%')
      .height('100%')
      .backgroundFilter(this.myFilter)
    }
  }
}
```

## createFractalGlassMask

```TypeScript
static createFractalGlassMask(glassNum: number, glassStrength: number, glassSoftness: number,
      isSymmetric: boolean, refractMask?: image.PixelMap): Mask
```

创建一个分形玻璃蒙版。它通过分形条纹对输入纹理进行周期性水平位移采样，产生类似玻璃折射的扭曲效果。扭曲效果关于图像垂直轴对称。配合 displacementDistort 使用，可产生光栅折射的视觉效果。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| glassNum | number | 是 | 分形玻璃条纹的数量。取值范围为 [0, 100]；超出范围的值将在内部被截断。 |
| glassStrength | number | 是 | 分形玻璃的扭曲强度。取值范围为 [0, 10]；超出范围的值将在内部被截断。 |
| glassSoftness | number | 是 | 分形玻璃条纹的边缘柔和度。取值范围为 [0, 0.01]；超出范围的值将在内部被截断。 |
| isSymmetric | boolean | 是 | 是否启用对称扭曲。「对称」指关于图像的垂直轴进行对称。 |
| refractMask | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | 否 | 由 image 模块创建的 PixelMap 实例。可选参数，用于控制分形效果的有效区域。如果提供该参数，glassNum 不再表示条纹数量；glassNum 和 glassStrength 共同决定折射强度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 带有分形玻璃蒙版效果的 Mask 实例。 |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct Index {
  private getPixelMap(): image.PixelMap | undefined {
    return this.getUIContext().getHostContext()?.resourceManager.getDrawableDescriptor($r('app.media.mask').id)?.getPixelMap();
  }

  private myFilter: uiEffect.Filter = uiEffect.createFilter()
    .displacementDistort(uiEffect.Mask.createFractalGlassMask(20.0, 1.5, 0.005, true, this.getPixelMap()), [1.0, 0.0])

  build() {
    Stack() {
      Image($r('app.media.BG_00000'))
      Stack() {

      }
      .width('100%')
      .height('100%')
      .backgroundFilter(this.myFilter)
    }
  }
}
```

## createPixelMapMask

```TypeScript
static createPixelMapMask(pixelMap: image.PixelMap, srcRect: common2D.Rect, dstRect: common2D.Rect,
      fillColor?: Color): Mask
```

通过输入的pixelMap，以及pixelMap的待绘制区域、挂载节点的绘制区域和绘制区域外填充的颜色创建具有缩放效果的Mask实例。

**起始版本：** 20

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelMap | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | 是 | image模块创建的PixelMap实例。可通过图片解码或直接创建获得。 |
| srcRect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | 是 | pixelMap的待绘制区域。图片最左侧和最上侧对应位置0，最右侧和最下侧对应位置1。right需大于left，bottom需大于top，违反约束时效果不生效。 |
| dstRect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | 是 | pixelMap在mask挂载的节点上的绘制区域。节点最左侧和最上侧对应位置0，最右侧和最下侧对应位置1。right需大于left，bottom需大于top，违反约束时效果不生效。 |
| fillColor | Color | 否 | 节点上在pixelMap绘制区域之外的区域填充的颜色，各元素取值范围为[0, 1]，默认透明色，小于0的转为0，大于1的转为1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 返回基于pixelMap创建的Mask实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { uiEffect, common2D } from '@kit.ArkGraphics2D';
import { BusinessError } from '@kit.BasicServicesKit';

const colorBuffer = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  let srcRect: common2D.Rect = {
    left: 0,
    top: 0,
    right: 1,
    bottom: 1
  };
  let dstRect: common2D.Rect = {
    left: 0,
    top: 0,
    right: 1,
    bottom: 1
  };
  let fillColor: uiEffect.Color = {
    red: 0,
    green: 0,
    blue: 0,
    alpha: 1
  };
  let mask = uiEffect.Mask.createPixelMapMask(pixelMap, srcRect, dstRect, fillColor);
}).catch((error: BusinessError)=>{
  console.error(`Failed to create pixelmap. code is ${error.code}, message is ${error.message}`);
});
```

<a id="createpixelmapmask-1"></a>

## createPixelMapMask

```TypeScript
static createPixelMapMask(pixelMap: image.PixelMap): Mask
```

通过输入的pixelMap创建Mask实例。该接口不会对传入的pixelMap进行缩放处理。

**起始版本：** 22

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelMap | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | 是 | image模块创建的PixelMap实例。可通过图片解码或直接创建获得。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 返回具有pixelMap的Mask。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例**

```TypeScript
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
      const path: string = context.resourceDir + '/perlin_worley_noise_3d_64.bmp';
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
      distortProgress: this.distortProgress,
      rippleProgress: this.rippleProgress,
      distortFactor: this.distortFactor,
      materialFactor: this.materialFactor,
      refractionFactor: this.refractionFactor,
      reflectionFactor: this.reflectionFactor,
      tintColor: [this.tintColorR, this.tintColorG, this.tintColorB, this.tintColorA],
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
      .width('100%').height('100%').align(Alignment.Center)
    }
    .backgroundImage($r('app.media.bg6'), ImageRepeat.NoRepeat) // the image should be created in local
    .width('100%').height('100%').align(Alignment.Center)
  }
}
```

## createRadialGradientMask

```TypeScript
static createRadialGradientMask(center: common2D.Point, radiusX: number, radiusY: number,
      gradients: Array<[number, number]>): Mask
```

通过输入椭圆中心点的位置、长短轴和形状参数创建椭圆遮罩效果Mask实例。

**起始版本：** 20

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| center | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md) | 是 | 设置椭圆的中心点，[0, 0]为组件左上角，[1, 1]为组件的右下角。取值范围为[-10, 10]，可取浮点数，超出边界会在实现时自动截断。 |
| radiusX | number | 是 | 设置椭圆的长轴，半径为1等于组件的高度。取值范围为[0, 10]，可取浮点数，超出边界会在实现时自动截断。 |
| radiusY | number | 是 | 设置椭圆的短轴，半径为1等于组件的高度。取值范围为[0, 10]，可取浮点数，超出边界会在实现时自动截断。 |
| gradients | Array&lt;[number, number]&gt; | 是 | 数组中保存的二元数组表示梯度：[RGBA颜色, 位置]。RGBA颜色四通道使用相同的值，可看作一个灰度值；位置表示沿径向方向向外时RGBA颜色对应的分布位置；RGBA颜色与位置的取值范围均为[0, 1]，可取浮点数，小于0的转为0，大于1的转为1。位置参数值须严格递增，Array数组中二元数组个数必须大于等于2，二元数组中的元素不能为空，否则该椭圆分布效果不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 返回椭圆形状的径向分布效果的灰度Mask。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例**

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
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

## createRippleMask

```TypeScript
static createRippleMask(center: common2D.Point, radius: number, width: number, offset?: number): Mask
```

通过输入波环圆心的位置、半径和宽度创建波环遮罩效果Mask实例。

**起始版本：** 20

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| center | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md) | 是 | 设置波环圆心在组件上的位置，[0, 0]为组件左上角，[1, 1]为组件的右下角。取值范围为[-10, 10]，超出边界会在实现时自动截断。 |
| radius | number | 是 | 设置波环的半径，使用归一化值。半径为1时，波环半径等于组件高度。取值范围为[0, 10]，超出边界会在实现时自动截断。 |
| width | number | 是 | 设置波环的宽度，使用归一化值。宽度为1时，波环宽度等于组件高度。取值范围为[0, 10]，超出边界会在实现时自动截断。 |
| offset | number | 否 | 设置波峰位置的偏移。默认值为0，表示波峰在波环的正中心；-1.0表示波峰在波环的最内侧；1.0表示波峰在波环的最外侧。取值范围为[-1, 1]，超出边界会在实现时自动截断。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 返回具有波环遮罩效果的Mask。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例**

```TypeScript
let mask = uiEffect.Mask.createRippleMask({x: 0.5, y: 1.0}, 0.5, 0.3, 0.0);
```

## createSweepRefractionMask

```TypeScript
static createSweepRefractionMask(param: SweepRefractionParam,
      options?: SweepRefractionMaskOptions): Mask
```

创建一个模拟棱镜色散效果的扫光折射遮罩 Mask 实例。该遮罩会在组件上生成一条带有颜色分离效果的扫光光带。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [SweepRefractionParam](arkts-arkgraphics2d-uieffect-sweeprefractionparam-i-sys.md) | 是 | 扫光折射遮罩的必选参数，包括mask半径、棱镜边缘厚度、折射强度、波纹宽度、扫光偏移和色散偏移. |
| options | [SweepRefractionMaskOptions](arkts-arkgraphics2d-uieffect-sweeprefractionmaskoptions-i-sys.md) | 否 | 扫光折射遮罩的可选参数，包括棱镜形状、圆角半径、棱镜尺寸和扫光中心。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 返回带有扫光折射效果的 Mask。 |

**示例**

```TypeScript
import { uiEffect, common2D } from '@kit.ArkGraphics2D';

// 构建色散颜色：RGB三通道各3个stop
let chromaColors: uiEffect.Color[] = [
  { red: 0.8, green: 0, blue: 0, alpha: 1 },
  { red: 0.8, green: 0, blue: 0, alpha: 1 },
  { red: 0.8, green: 0, blue: 0, alpha: 1 },
  { red: 0, green: 0.8, blue: 0, alpha: 1 },
  { red: 0, green: 0.8, blue: 0, alpha: 1 },
  { red: 0, green: 0.8, blue: 0, alpha: 1 },
  { red: 0, green: 0, blue: 0.8, alpha: 1 },
  { red: 0, green: 0, blue: 0.8, alpha: 1 },
  { red: 0, green: 0, blue: 0.8, alpha: 1 },
];

// 构建颜色位置：每个通道3个stop，分别对应环的起止和中间位置
let chromaPositions: common2D.Point[] = [];
for (let g = 0; g < 3; g++) {
  chromaPositions.push({ x: 0, y: 0 });
  chromaPositions.push({ x: 0.5, y: 0.5 });
  chromaPositions.push({ x: 1, y: 1 });
}

// 创建扫光折射遮罩
let mask = uiEffect.Mask.createSweepRefractionMask(
  {
    maskRadius: 0.0,
    edgeThickness: 100.0,
    refractAmount: 0.2,
    rippleWidth: 0.5,
    sweepOffset: 0.25,
    chromaDelta: 0.1
  },
  {
    shapeType: uiEffect.PrismShapeType.ROUNDED_RECT,
    cornerRadius: 0.12,
    prismWidth: 1.0,
    prismHeight: 1.0,
    sweepCenterX: 0.0,
    sweepCenterY: 0.0
  }
);

@Entry
@Component
struct SweepRefractionExample {
  build() {
    Column() {
      Row() {}
        .width('100%').height('100%')
        .hitTestBehavior(HitTestMode.None)
        .visualEffect(uiEffect.createEffect()
          .colorGradient(chromaColors, chromaPositions,
            [10.0, 10.0, 10.0, 10.0, 10.0, 10.0, 10.0, 10.0, 10.0],
            mask))
        .blendMode(BlendMode.SRC_OVER)
    }
    .width(342).height(137)
    .borderRadius(16).clip(true)
    .backgroundColor('#0A0A14')
  }
}
```

## createUseEffectMask

```TypeScript
static createUseEffectMask(useEffect: boolean): Mask
```

创建并设置Mask实例是否使用模糊缓存。此Mask实例专为liquidMaterial方法的useEffectMask参数设计，用于声明材质效果是否使用模糊缓存以提升性能。将此Mask实例用于其他Filter或VisualEffect方法时，useEffect属性可能不生效。

**起始版本：** 22

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| useEffect | boolean | 是 | 标记是否使用模糊缓存。值为true，表示使用，会正常显示模糊效果；值为false，表示不使用，不显示模糊效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 返回标记是否使用模糊缓存的Mask实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例**

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

  private getMaterialVisualEffect(): uiEffect.VisualEffect {
    let effect: uiEffect.VisualEffect = uiEffect.createEffect();
    effect.liquidMaterial({
        enable: true,
        distortProgress: this.distortProgress,
        rippleProgress: this.rippleProgress,
        distortFactor: this.distortFactor,
        materialFactor: this.materialFactor,
        refractionFactor: this.refractionFactor,
        reflectionFactor: this.reflectionFactor,
        tintColor: [this.tintColorR, this.tintColorG, this.tintColorB, this.tintColorA],
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
      .width('100%').height('100%').align(Alignment.Center)
    }
    .backgroundImage($r('app.media.bg6'), ImageRepeat.NoRepeat)
    .width('100%').height('100%').align(Alignment.Center)
  }
}
```

## createWarpedRingMask

```TypeScript
static createWarpedRingMask(ringParam: WarpedRingParam): Mask
```

创建一个表示扭曲光环的 Mask 实例。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ringParam | [WarpedRingParam](arkts-arkgraphics2d-uieffect-warpedringparam-i-sys.md) | 是 | 配置扭曲光环的形状。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 返回带有扭曲光环蒙版效果的 Mask。 |

**示例**

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';

// params that control the shape of the Mask
let param: uiEffect.WarpedRingParam = {
  radius: 0.5,
  baseHalfWidth: 0.02,
  widthVariation: 0.4,
  rotateAngle: 0.0,
  rotate3DProgress: 0.0,
  noiseEvolution: 1.0
};

// the Mask that defines the shape to be extracted from the color gradient or other effects
let exampleMask: uiEffect.Mask = uiEffect.Mask.createWarpedRingMask(param);

@Entry
@Component
struct example {
  build() {
    RelativeContainer() {
      Stack() {
        Column()
          .width(200)
          .height(200)
          .visualEffect(
            uiEffect.createEffect().colorGradient(
              [ { red:1.0, green:0.5, blue:0.75, alpha:1.0 } ],
              [ { x:1.0, y:0.5 } ],
              [ 1.0 ],
              exampleMask
            )
          )
      }
    }
  }
}
```

## createWaveGradientMask

```TypeScript
static createWaveGradientMask(center: common2D.Point, width: number, propagationRadius: number,
      blurRadius: number, turbulenceStrength?: number): Mask
```

输入波源中心位置、单波参数创建单波遮罩效果Mask实例。

**起始版本：** 20

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| center | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md) | 是 | 设置单波波源的中心点，[0, 0]为组件左上角，[1, 1]为组件的右下角。取值范围为[-10, 10]，可取浮点数，超出边界会在实现时自动截断。 |
| width | number | 是 | 设置单波圆环的宽度。取值范围为[0, 5]，可取浮点数，超出边界会在实现时自动截断。 |
| propagationRadius | number | 是 | 设置单波圆环的扩散外径。取值范围为[0, 10]，可取浮点数，超出边界会在实现时自动截断。 |
| blurRadius | number | 是 | 设置单波圆环的模糊外径，模糊半径为0则是实边圆环，否则是虚边圆环。取值范围为[0, 5]，可取浮点数，超出边界会在实现时自动截断。 |
| turbulenceStrength | number | 否 | 设置单波圆环的湍流强度，默认值为0，强度为0则是规则圆环，否则圆环边缘会湍流扭曲。取值范围为[-1, 1]，可取浮点数，超出边界会在实现时自动截断。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | 返回单个水波形状的灰度Mask。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例**

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
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
