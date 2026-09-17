# VisualEffect

VisualEffect class, used to apply background color blending, border lighting, color gradient, and other effects to a component. Before calling VisualEffect methods, you need to first create a VisualEffect instance through createEffect.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## backgroundColorBlender

```TypeScript
backgroundColorBlender(blender: BrightnessBlender): VisualEffect
```

A blender for changing the background color of the component. Currently, only the brightness blender is supported.

**Since:** 12

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blender | [BrightnessBlender](arkts-arkgraphics2d-uieffect-brightnessblender-i-sys.md) | Yes | The blender for blending the background color. |

**Return value:**

| Type | Description |
| --- | --- |
| [VisualEffect](arkts-arkgraphics2d-uieffect-visualeffect-i-sys.md) | Returns the VisualEffect with the background color change effect attached. |

**Examples**

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
let blender: uiEffect.BrightnessBlender =
  uiEffect.createBrightnessBlender({cubicRate:1.0, quadraticRate:1.0, linearRate:1.0, degree:1.0, saturation:1.0,
    positiveCoefficient:[2.3, 4.5, 2.0], negativeCoefficient:[0.5, 2.0, 0.5], fraction:0.0});
let visualEffect = uiEffect.createEffect();
// Add the blender to the component to change the component background color.
visualEffect.backgroundColorBlender(blender);
```

## borderLight

```TypeScript
borderLight(lightPosition: common2D.Point3d, lightColor: common2D.Color, lightIntensity: number,
      borderWidth: number): VisualEffect
```

Adds a 3D lighting effect to the border of a rounded rectangle component.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lightPosition | [common2D.Point3d](arkts-arkgraphics2d-common2d-point3d-i.md) | Yes | The 3D position of the light source in the component space. [-1, -1, 0] is the top-left corner of the component, [1, 1, 0] is the bottom-right corner of the component. The larger the z-axis component, the farther the light source is from the component plane, and the larger the illuminated area. The x component range is [-10, 10], the y component range is [-10, 10], and the z component range is [0, 10]. Values outside the range will be automatically clamped. |
| lightColor | [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md) | Yes | The color of the light source. Each component range is [0, 1]. Values outside the range will be automatically clamped. |
| lightIntensity | number | Yes | The intensity of the light source. The value range is [0, 1]. A larger value indicates a brighter light source. Values outside the range will be automatically clamped. |
| borderWidth | number | Yes | The illuminated width of the component border. The value range is [0.0, 30.0]. Values outside the range will be automatically clamped. Setting it to 0.0 results in no lighting effect on the component border; a larger value results in a wider illuminated area. |

**Return value:**

| Type | Description |
| --- | --- |
| [VisualEffect](arkts-arkgraphics2d-uieffect-visualeffect-i-sys.md) | Returns the VisualEffect with the border lighting effect attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { common2D, uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct Index {
  @State borderLightPosition: common2D.Point3d = {
    x: 0, y: 0, z: 2
  };
  @State borderLightColor: common2D.Color = {
    red: 1, green: 1, blue: 1, alpha: 1
  };
  @State lightIntensity: number = 1;
  @State borderWidth_: number = 20;

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
          // Add 3D lighting effect to the border of a rounded rectangle component.
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

## colorGradient

```TypeScript
colorGradient(colors: Array<Color>, positions: Array<common2D.Point>, strengths: Array<number>,
      alphaMask?: Mask): VisualEffect
```

Adds a color gradient effect to the component.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colors | Array&lt;Color&gt; | Yes | The color array for multi-color gradient. The array length range is [0, 12], and each color value must be greater than or equal to 0. If the array length is 0 or greater than 12, or if the array lengths of colors, positions, and strengths are not equal, there will be no color gradient effect. |
| positions | Array&lt;[common2D.Point](arkts-arkgraphics2d-common2d-point-i.md)&gt; | Yes | The position array, corresponding to the positions of colors. The array length range is [0, 12]. If the array length is 0 or greater than 12, or if the array lengths of colors, positions, and strengths are not equal, there will be no color gradient effect. |
| strengths | Array&lt;number&gt; | Yes | The strength array, corresponding to the intensity of colors. The array length range is [0, 12], and each strength value must be greater than or equal to 0. If the array length is 0 or greater than 12, or if the array lengths of colors, positions, and strengths are not equal, there will be no color gradient effect. |
| alphaMask | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | No | The alpha mask corresponding to the colors. A Mask instance can be created through Mask creation methods (such as createRippleMask, createRadialGradientMask, etc.). Pass this parameter when you need to control the transparency distribution of the color gradient effect (such as local transparency or dynamic transparency effects). If not set, the transparency of the color gradient effect is entirely determined by the colors parameter. |

**Return value:**

| Type | Description |
| --- | --- |
| [VisualEffect](arkts-arkgraphics2d-uieffect-visualeffect-i-sys.md) | Returns the VisualEffect with the color gradient effect attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { common2D, uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct ColorGradientExample {
  build() {
    Stack() {
      Stack() {}
      // Adds a color gradient effect to the component.
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
      .width('1024px')
      .height('1024px')
    }
    .width('100%')
    .height('100%')
  }
}
```

## distortionCollapse

```TypeScript
distortionCollapse(distortionParam: DistortionParam): VisualEffect
```

Adds a nonlinear deformation effect to the component. Typical application scenarios include page collapse animations, window close effects, card flip animations, scene transition effects, etc.

NOTE
1. This visual effect supports drawing outside the bounds of the control,
but it is still subject to the clipping (Clip) of the parent control.
2. Because it contains a foreground Filter, some visual effects of the component itself and its child components
(e.g., BrightnessBlender or systemMaterial) are incompatible when not used in combination with the EffectComponent.
3. It supports distorting the system material, but when used in combination with the EffectComponent,
it will cause the background of the system material to be distorted.
4. When calling distortionCollapse, an offscreen canvas equal in size to the deformed area will be created.
The content of the current component (including child components) is then drawn onto this offscreen canvas, and the existing content on the canvas is drawn with deformation.
5. When using this implementation without combining with the EffectComponent, interfaces that require screen
capture, such as systemMaterial, backgroundEffect, brightness, and blur, will not be able to capture the correct screen.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| distortionParam | [DistortionParam](../../apis-arkui/arkts-components/arkts-arkui-distortionparam-i-sys.md) | Yes | The parameters of the nonlinear deformation effect. |

**Return value:**

| Type | Description |
| --- | --- |
| [VisualEffect](arkts-arkgraphics2d-uieffect-visualeffect-i-sys.md) | Returns the VisualEffect with the nonlinear deformation effect attached. |

**Examples**

```TypeScript
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

## liquidMaterial

```TypeScript
liquidMaterial(param : LiquidMaterialEffectParam, useEffectMask: Mask, distortMask?: Mask,
      brightnessParam?: BrightnessParam): VisualEffect
```

Adds a material effect to the component. The material effect simulates the optical properties (refraction, reflection) and dynamic perturbation effects of physical materials to achieve visual representations of glass, metal, and other materials. It can be used for scenarios such as glass-textured UI, fluid material animation, frosted glass effects, etc.

**Since:** 22

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [LiquidMaterialEffectParam](arkts-arkgraphics2d-uieffect-liquidmaterialeffectparam-i-sys.md) | Yes | The material-related variables used to control the material display, including the material switch, refraction coefficient, reflection coefficient, and perturbation coefficient. |
| useEffectMask | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Yes | Declares whether to use blur caching. A Mask instance created with createUseEffectMask(true) uses blur caching, suitable for scenarios that need to reuse blur results to improve performance; a Mask instance created with createUseEffectMask(false) does not use blur caching, suitable for scenarios where blur effects change frequently. |
| distortMask | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | No | The perturbation texture required for the material perturbation effect. The image texture of the Mask instance created from a pixelMap determines the pattern and direction of the perturbation effect. A Mask instance can be created through the createPixelMapMask method. When the material's perturbation coefficient (distortFactor) is not 0, this parameter must be set; otherwise, there will be no perturbation effect. When the perturbation coefficient is 0 or this parameter is not set, there is no perturbation effect. The default is not set. |
| brightnessParam | [BrightnessParam](arkts-arkgraphics2d-uieffect-brightnessparam-i-sys.md) | No | Adds a brightening effect to the material. Pass this parameter when you need to enhance the visual brightness of the material (such as highlight display, glow effects). If not set, no brightening effect is added by default, and the material maintains its original brightness. |

**Return value:**

| Type | Description |
| --- | --- |
| [VisualEffect](arkts-arkgraphics2d-uieffect-visualeffect-i-sys.md) | Returns the VisualEffect with the material effect attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

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
      .width('100%').height('100%').align(Alignment.Center)
    }
    .backgroundImage($r('app.media.bg6'), ImageRepeat.NoRepeat)
    .width('100%').height('100%').align(Alignment.Center)
  }
}
```
